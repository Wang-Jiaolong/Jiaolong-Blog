---
layout: wiki
title: 「 Jackson 」
categories: Java框架
description: Jackson
keywords: Jackson， Java
---

> Jackson 是一个简单基于 Java 应用库，Jackson 可以轻松的将 Java 对象转换成 json 对象和 xml 文档，同样也可以将 json、xml 转换成 Java 对象。Jackson 所依赖的 jar 包较少，简单易用并且性能也要相对高些，并且 Jackson 社区相对比较活跃，更新速度也比较快。

## Jackson 特点

- 容易使用 - jackson API 提供了一个高层次外观，以简化常用的用例。
- 无需创建映射 - API提供了默认的映射大部分对象序列化。
- 性能高 - 快速，低内存占用，适合大型对象图表或系统。
- 干净的 JSON - jackson 创建一个干净和紧凑的 JSON 结果，这是让人很容易阅读。
- 不依赖 - 库不需要任何其他的库，除了 JDK。
- 开源代码 - jackson 是开源的，可以免费使用。

## Jackson 注解

Jackson 类库包含了很多注解，可以让我们快速建立 Java 类与 JSON 之间的关系。

- `@JsonProperty` 注解指定一个属性用于 JSON 映射，默认情况下映射的 JSON 属性与注解的属性名称相同，不过可以使用该注解的 `value` 值修改 JSON 属性名，该注解还有一个 `index` 属性指定生成 JSON 属性的顺序，如果有必要的话。
- `@JsonIgnore` 注解用于排除某个属性，这样该属性就不会被 Jackson 序列化和反序列化。
- `@JsonIgnoreProperties` 注解是类注解。在序列化为 JSON 的时候，`@JsonIgnoreProperties({"prop1", "prop2"})` 会忽略 `pro1` 和 `pro2` 两个属性。在从 JSON 反序列化为 Java 类的时候，`@JsonIgnoreProperties(ignoreUnknown=true)` 会忽略所有没有 `Getter` 和 `Setter` 的属性。该注解在 Java 类和 JSON 不完全匹配的时候很有用。
- `@JsonIgnoreType` 也是类注解，会排除所有指定类型的属性。
- `@JsonPropertyOrder` 和 `@JsonProperty` 的 `index` 属性类似，指定属性序列化时的顺序。
- `@JsonRootName` 注解用于指定 JSON 根属性的名称。



## 实例

`pom.xml`

~~~xml
	        <jackson.version>2.9.5</jackson.version>

			<!-- Json Begin -->
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-core</artifactId>
                <version>${jackson.version}</version>
            </dependency>
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-databind</artifactId>
                <version>${jackson.version}</version>
            </dependency>
            <dependency>
                <groupId>com.fasterxml.jackson.core</groupId>
                <artifactId>jackson-annotations</artifactId>
                <version>${jackson.version}</version>
            </dependency>
            <!-- Json End -->
~~~

`java`

~~~java
import com.fasterxml.jackson.databind.JavaType;
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.ObjectMapper;

import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

public class JsonTester {
    public static void main(String[] args) {
        // 创建 ObjectMapper 对象
        ObjectMapper mapper = new ObjectMapper();
        String jsonString = "{\"draw\":1,\"recordsTotal\":1,\"recordsFiltered\":1,\"data\":[{\"id\":33,\"title\":\"ad1\",\"subTitle\":\"ad1\",\"titleDesc\":\"ad1\",\"url\":\"https://sale.jd.com/act/XkCzhoisOMSW.html\",\"pic\":\"https://m.360buyimg.com/babel/jfs/t20164/187/1771326168/92964/b42fade7/5b359ab2N93be3a65.jpg\",\"pic2\":\"\",\"content\":\"<p><br></p>\"}],\"error\":null}";

        try {
            // 反序列化 JSON 到树
            JsonNode jsonNode = mapper.readTree(jsonString);

            // 从树中读取 data 节点,只获取data数据
            JsonNode jsonData = jsonNode.findPath("data");
            System.out.println(jsonData);

            // 反序列化 JSON 到集合
            JavaType javaType = mapper.getTypeFactory().constructParametricType(ArrayList.class, TbContent.class);
            List<TbContent> tbContents = mapper.readValue(jsonData.toString(), javaType);
            for (TbContent tbContent : tbContents) {
                System.out.println(tbContent);
            }

            // 序列化集合到 JSON
            String json = mapper.writeValueAsString(tbContents);
            System.out.println(json);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

@data
class TbContent {
    private Long id;
    private String title;
    private String subTitle;
    private String titleDesc;
    private String url;
    private String pic;
    private String pic2;
    private String content;
}
~~~

> json数据项要和实体类 属性一一对应，





## Jackson工具类

[JacksonUtils]:https://blog.jiaolong.space/2021/02/15/JackonUtils/

