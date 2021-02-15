---
layout: post
title: 后台与门户的通信问题
categories: JavaWeb
description: 后台与门户的通信问题
keywords: JavaWeb
topmost: false
---

> 后台与门户的通信过程

## 概述

![2021_2_15](https://i.loli.net/2021/02/15/fvXRysAhdOGEVFo.png)

后台管理仅复制维护数据库，门户不允许直接操作数据库，通过中间层，调用应用接口请求数据库信息，从而展示到页面。

**优点：**

- 前后分离
- 前后台部署在不同服务器，安全
- 重新部署时相互不影响

## 实现

### 使用HttpClient类库

> HttpClient 是 Apache Jakarta Common 下的子项目，用来提供高效的、最新的、功能丰富的支持 HTTP 协议的客户端编程工具包，并且它支持 HTTP 协议最新的版本和建议。HttpClient 已经应用在很多的项目中，比如 Apache Jakarta 上很著名的另外两个开源项目 Cactus 和 **HTMLUnit** 都使用了 HttpClient。

### Apache HttpClient 使用流程

使用 HttpClient 发送请求、接收响应很简单，一般需要如下几步即可。

- 创建 `HttpClient` 对象。
- 创建请求方法的实例，并指定请求 URL。如果需要发送 GET 请求，创建 `HttpGet` 对象；如果需要发送 POST 请求，创建 `HttpPost` 对象。
- 如果需要发送请求参数，可调用 `HttpGet`、`HttpPost` 共同的 `setParams(HttpParams params)` 方法来添加请求参数；对于 `HttpPost` 对象而言，也可调用 `setEntity(HttpEntity entity)` 方法来设置请求参数。
- 调用 `HttpClient` 对象的 `execute(HttpUriRequest request)` 发送请求，该方法返回一个 `HttpResponse`。
- 调用 `HttpResponse` 的 `getAllHeaders()`、`getHeaders(String name)` 等方法可获取服务器的响应头；调用 `HttpResponse` 的 `getEntity()` 方法可获取 `HttpEntity` 对象，该对象包装了服务器的响应内容。程序可通过该对象获取服务器的响应内容。
- 释放连接。无论执行方法是否成功，都必须释放连接

## Apache HttpClient 使用实例

### POM

`pom.xml` 配置如下：

```xml
<!-- Apache Http Begin -->
<dependency>
    <groupId>org.apache.httpcomponents</groupId>
    <artifactId>httpclient</artifactId>
    <version>4.5.5</version>
</dependency>
<dependency>
    <groupId>org.apache.httpcomponents</groupId>
    <artifactId>fluent-hc</artifactId>
    <version>4.5.5</version>
</dependency>
<dependency>
    <groupId>org.apache.httpcomponents</groupId>
    <artifactId>httpmime</artifactId>
    <version>4.5.5</version>
</dependency>
<!-- Apache Http End -->
```

主要增加了 `org.apache.httpcomponents:httpclient`、`org.apache.httpcomponents:fluent-hc`、`org.apache.httpcomponents:httpmime` 三个依赖



### 创建 HttpGet 请求

案例代码如下：

```java
package com.funtl.hello.httpclient;

import org.apache.http.HttpEntity;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.util.EntityUtils;

import java.io.IOException;

public class MyTest {
    public static void main(String[] args) {
        get();
    }

    private static void get() {
        // 创建 HttpClient 客户端
        CloseableHttpClient httpClient = HttpClients.createDefault();

        // 创建 HttpGet 请求
        HttpGet httpGet = new HttpGet("http://localhost:8080/content/page?draw=1&start=0&length=10");
        // 设置长连接
        httpGet.setHeader("Connection", "keep-alive");
        // 设置代理（模拟浏览器版本）
        httpGet.setHeader("User-Agent", "Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36");
        // 设置 Cookie
        httpGet.setHeader("Cookie", "UM_distinctid=16442706a09352-0376059833914f-3c604504-1fa400-16442706a0b345; CNZZDATA1262458286=1603637673-1530123020-%7C1530123020; JSESSIONID=805587506F1594AE02DC45845A7216A4");

        CloseableHttpResponse httpResponse = null;
        try {
            // 请求并获得响应结果
            httpResponse = httpClient.execute(httpGet);
            HttpEntity httpEntity = httpResponse.getEntity();
            // 输出请求结果
            System.out.println(EntityUtils.toString(httpEntity));
        } catch (IOException e) {
            e.printStackTrace();
        }

        // 无论如何必须关闭连接
        finally {
            if (httpResponse != null) {
                try {
                    httpResponse.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }

            if (httpClient != null) {
                try {
                    httpClient.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```



>  其中Cookie及User-Agent查看方式：![image-20210215174948453](https://i.loli.net/2021/02/15/M1Ulnu2tAR74IPo.png)



### 创建 HttpPost 请求

案例代码如下：

```java
package com.funtl.hello.httpclient;

import org.apache.http.HttpEntity;
import org.apache.http.client.ClientProtocolException;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.ArrayList;
import java.util.List;

public class MyTest {
    public static void main(String[] args) {
        post();
    }

    private static void post() {
        // 创建 HttpClient 客户端
        CloseableHttpClient httpClient = HttpClients.createDefault();

        // 创建 HttpPost 请求
        HttpPost httpPost = new HttpPost("http://localhost:8080/content/page");
        // 设置长连接
        httpPost.setHeader("Connection", "keep-alive");
        // 设置代理（模拟浏览器版本）
        httpPost.setHeader("User-Agent", "Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36");
        // 设置 Cookie
        httpPost.setHeader("Cookie", "UM_distinctid=16442706a09352-0376059833914f-3c604504-1fa400-16442706a0b345; CNZZDATA1262458286=1603637673-1530123020-%7C1530123020; JSESSIONID=805587506F1594AE02DC45845A7216A4");

        // 创建 HttpPost 参数
        List<BasicNameValuePair> params = new ArrayList<BasicNameValuePair>();
        params.add(new BasicNameValuePair("draw", "1"));
        params.add(new BasicNameValuePair("start", "0"));
        params.add(new BasicNameValuePair("length", "10"));

        CloseableHttpResponse httpResponse = null;
        try {
            // 设置 HttpPost 参数
            httpPost.setEntity(new UrlEncodedFormEntity(params, "UTF-8"));
            httpResponse = httpClient.execute(httpPost);
            HttpEntity httpEntity = httpResponse.getEntity();
            // 输出请求结果
            System.out.println(EntityUtils.toString(httpEntity));
        } catch (UnsupportedEncodingException e) {
            e.printStackTrace();
        } catch (ClientProtocolException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }

        // 无论如何必须关闭连接
        finally {
            try {
                if (httpResponse != null) {
                    httpResponse.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if (httpClient != null) {
                    httpClient.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```