---
layout: wikis
title: PageHelper
description: PageHelper是一个Mybatis的分页插件, 负责将已经写好的sql语句, 进行分页加工。
header-img: "img/about-bg.jpg"
catalog: true
---

> `PageHelper`是一个Mybatis的分页插件, 负责将已经写好的sql语句, 进行分页加工。官网说法：如果你也在用 MyBatis，建议尝试该分页插件，这一定是最方便使用的分页插件。分页插件支持任何复杂的单表、多表分页。
>
> 优点：无需你自己去封装以及关心sql分页等问题，使用很方便，前端取数据也很方便。

# SpringBoot 中Mybatis分页插件PageHelper

### 导入依赖

      <!-- https://mvnrepository.com/artifact/com.github.pagehelper/pagehelper-spring-boot-starter -->
        <dependency>
            <groupId>com.github.pagehelper</groupId>
            <artifactId>pagehelper-spring-boot-starter</artifactId>
            <version>1.2.12</version>
        </dependency>
### Controller

```Java
@GetMapping(value = "selectAll")
public BaseResult findAllTopicByPage(int pageNum, int pageSize) {
    Page<Object> page = PageHelper.startPage(pageNum, pageSize);	//设置每页开始、大小
    try {
        List<TbUser> topicList = tbUserMapper.selectAll();	//获取全部数据
        PageInfo<TbUser> pageInfo = new PageInfo<TbUser>(topicList);
        return BaseResult.success("查询成功",pageInfo.getList());
    }catch (Exception e){
        e.printStackTrace();
        return BaseResult.fail("查询失败");
    }
}
```