---
layout: wiki
title: Maven
categories: Maven
description: Maven
keywords: Maven
---

# 一、使用 Maven 构建应用

## Maven安装配置

### 配置环境

- 下载 `Maven.zip` ：http://maven.apache.org/download.cgi
- 添加 `MAVEN_HOME` 环境变量到 Windows 环境变量，并将其指向你的 Maven 文件夹。![image-20210214101850032](https://i.loli.net/2021/02/14/Ww3hxnpsqdiGKto.png)
- 添加`%MAVEN_HOME%\bin` 到 `PATH` ![image-20210214102112777](https://i.loli.net/2021/02/14/o4WHZaDwVr1RJXY.png)
- 使用`mvn -version`验证：![image-20210214102237029](https://i.loli.net/2021/02/14/CiADJV7FzT2Hr6x.png)

### 仓库

Maven 的本地资源库是用来存储所有项目的依赖关系(插件 Jar 和其他文件，这些文件被 Maven 下载)到本地文件夹。很简单，当你建立一个 Maven 项目，所有相关文件将被存储在你的 Maven 本地仓库。

默认情况下，Maven 的本地资源库默认为 `.m2` 目录文件夹：

- Unix/Mac OS X：`~/.m2`
- Windows：`C:\Documents and Settings\{your-username}\.m2`

通常情况下，可改变默认的 `.m2` 目录下的默认本地存储库文件夹到其他更有意义的名称，例如， maven-repo 找到 `{M2_HOME}\conf\setting.xml`, 更新 `localRepository` 到其它名称。

![image-20210214102555097](https://i.loli.net/2021/02/14/Ajv4INEZCQ5wzDK.png)

执行之后，新的 Maven 本地存储库现在改为 `D:/apache-maven-3.5.2/repo`

![image-20210214102622855](https://i.loli.net/2021/02/14/Dra2CAOzi9lojKV.png)

## Maven 应用

## POM 的例子

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>
   <groupId>com.lusifer</groupId>
   <artifactId>project</artifactId>
   <version>1.0</version>
<project>
```

要注意的是，每个项目只有一个 POM 文件

- 所有的 POM 文件要项目元素必须有三个必填字段: groupId，artifactId，version
- 在库中的项目符号是：`groupId:artifactId:version`
- `pom.xml` 的根元素是 project，它有三个主要的子节点。

| 节点       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| groupId    | 这是项目组的编号，这在组织或项目中通常是独一无二的。 例如，一家银行集团 `com.company.bank` 拥有所有银行相关项目。 |
| artifactId | 这是项目的 ID。这通常是项目的名称。 例如，`consumer-banking`。 除了 groupId 之外，artifactId 还定义了 artifact 在存储库中的位置。 |
| version    | 这是项目的版本。与 groupId 一起使用，artifact 在存储库中用于将版本彼此分离。 例如：`com.company.bank:consumer-banking:1.0`，`com.company.bank:consumer-banking:1.1` |

## Template

### 目录结构

Java Web 的 Maven 基本结构如下：

```text
├─src
│  ├─main
│  │  ├─java
│  │  ├─resources
│  │  └─webapp
│  │      └─WEB-INF
│  └─test
│      └─java
```

src：源码目录

- `src/main/java`：Java 源码目录
- `src/main/resources`：资源文件目录
- `src/main/webapp`：Web 相关目录
- `src/test`：单元测试

### pom.xml

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.jiaolong</groupId>
    <artifactId>name</artifactId>
    <version>1.0.0-SNAPSHOT</version>
    <packaging>war</packaging>
</project>
~~~

- `packaging`：打包方式，这里是 `war` 包，表示为 Java Web 应用程序
- `dependencies`：项目依赖配置，整个项目生命周期中所需的依赖都在这里配置

###  Maven Repository

~~~xml
<!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>4.0.1</version>
    <scope>provided</scope>
</dependency>

<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-webmvc</artifactId>
	<version>4.3.17.RELEASE</version>
</dependency>

<!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.2.12.RELEASE</version>
</dependency>


<!-- https://mvnrepository.com/artifact/org.springframework/spring-web -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-web</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>


<!-- https://mvnrepository.com/artifact/junit/junit -->
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
</dependency>

<!-- https://mvnrepository.com/artifact/org.slf4j/slf4j-log4j12 -->
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.30</version>
</dependency>


<!-- https://mvnrepository.com/artifact/javax.servlet/jstl -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
</dependency>


<!-- https://mvnrepository.com/artifact/org.apache.commons/commons-lang3 -->
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.8.1</version>
</dependency>


<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.16</version>
    <scope>provided</scope>
</dependency>

~~~



# 	模块化开发

> 在多人协同开发时，特别是规模较大的项目，为了方便日后的代码维护和管理，我们会将每个开发人员的工作细分到具体的功能和模块上。随着项目的不断扩大，模块也会越来越多，后续会更加难以维护和扩展，为了应对这种情况后期我们还会采用微服务架构的方式进行开发。

以当前教程为例，我们可以将模块划分为如下形式：

- 统一的依赖管理（dependencies）
- 通用的工具类（commons）
- 领域模型（domain）
- 管理后台（admin）
- 商城前端（ui）
- 接口模块（api）

整个模块化开发过程主要是在开发思想上稍作了一些转变，只需要按照下面的流程操作即可。

## 1.创建根项目（工程）

`pom.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.funtl</groupId>
    <artifactId>my-shop</artifactId>
    <version>1.0.0-SNAPSHOT</version>
    <packaging>pom</packaging>
    
    <modules>
    
    </modules>
</project>
```



## 2.创建统一的依赖管理

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>com.funtl</groupId>
        <artifactId>my-shop</artifactId>
        <version>1.0.0-SNAPSHOT</version>
        <relativePath>../pom.xml</relativePath>
    </parent>

    <artifactId>my-shop-dependencies</artifactId>
    <packaging>pom</packaging>

    <name>my-shop-dependencies</name>
    <description></description>

    <properties>
        <!-- 环境配置 -->
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>

        <!-- 统一的依赖管理 -->
        <commons-lang3.version>3.5</commons-lang3.version>
        <jstl.version>1.2</jstl.version>
        <log4j.version>1.2.17</log4j.version>
        <servlet-api.version>3.1.0</servlet-api.version>
        <slf4j.version>1.7.25</slf4j.version>
        <spring.version>4.3.17.RELEASE</spring.version>
    </properties>

    <dependencyManagement>
        <dependencies>
            <!-- Spring Begin -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-context</artifactId>
                <version>${spring.version}</version>
            </dependency>
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-webmvc</artifactId>
                <version>${spring.version}</version>
            </dependency>
            <!-- Spring End -->

            <!-- Servlet Begin -->
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>javax.servlet-api</artifactId>
                <version>${servlet-api.version}</version>
                <scope>provided</scope>
            </dependency>
            <dependency>
                <groupId>javax.servlet</groupId>
                <artifactId>jstl</artifactId>
                <version>${jstl.version}</version>
            </dependency>
            <!-- Servlet End -->

            <!-- Log Begin -->
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>slf4j-api</artifactId>
                <version>${slf4j.version}</version>
            </dependency>
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>slf4j-log4j12</artifactId>
                <version>${slf4j.version}</version>
            </dependency>
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>jcl-over-slf4j</artifactId>
                <version>${slf4j.version}</version>
            </dependency>
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>jul-to-slf4j</artifactId>
                <version>${slf4j.version}</version>
            </dependency>
            <dependency>
                <groupId>log4j</groupId>
                <artifactId>log4j</artifactId>
                <version>${log4j.version}</version>
            </dependency>
            <!-- Log End -->

            <!-- Commons Begin -->
            <dependency>
                <groupId>org.apache.commons</groupId>
                <artifactId>commons-lang3</artifactId>
                <version>${commons-lang3.version}</version>
            </dependency>
            <!-- Commons End -->
        </dependencies>
    </dependencyManagement>

    <build>
        <plugins>
            <!-- Compiler 插件, 设定 JDK 版本 -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.7.0</version>
                <configuration>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
                    <encoding>${project.build.sourceEncoding}</encoding>
                    <showWarnings>true</showWarnings>
                </configuration>
            </plugin>
        </plugins>

        <!-- 资源文件配置 -->
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <excludes>
                    <exclude>**/*.java</exclude>
                </excludes>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
            </resource>
        </resources>
    </build>
</project>
```

# Q & A

## 01. Error:java: 错误: 不支持发行版本 5

> 解决办法：复制以下代码，进`pod.xml` ,修改版本号为对应版本。

```xml
<properties>
     <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
     <maven.compiler.encoding>UTF-8</maven.compiler.encoding>
     <java.version>11</java.version>
     <maven.compiler.source>11</maven.compiler.source>
     <maven.compiler.target>11</maven.compiler.target>
</properties>
```