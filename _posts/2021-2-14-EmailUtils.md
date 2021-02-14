---
layout: post
title: EmailUtils-邮件工具类
categories: Utils
description: 用于实现发送邮件
keywords: Utils,Java
topmost: false
---

> 用于实现发送邮件

## 自动注入Utils

`spring-email.xml`

~~~xml
    <bean id="emailSendUtils" class="com.jiaolong.myshop.commons.utils.EmailSendUtils" />
~~~

## 导入依赖

~~~xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-email</artifactId>
    <version>1.5</version>
</dependency>
~~~



## 工具类

`EmailSendUtils`

~~~java
import org.apache.commons.mail.DefaultAuthenticator;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;

public class EmailSendUtils {
    public void send(String subject, String msg, String... to) throws EmailException {
        Email email = new SimpleEmail();
        email.setHostName("smtp.163.com");
        email.setSmtpPort(25);//邮箱端口号
        email.setAuthenticator(new DefaultAuthenticator("username", "password"));
        email.setSSLOnConnect(true);
        email.setFrom("iwangjiaolong@163.com");
        email.setSubject(subject);
        email.setMsg(msg);
        email.addTo(to);
        email.send();
    }
}
~~~

**常用邮箱端口号**

- sohu.com:
  POP3服务器地址:pop3.sohu.com（端口：110）
  SMTP服务器地址:smtp.sohu.com（端口：25）
- 126邮箱：
  POP3服务器地址:pop.126.com（端口：110）
  SMTP服务器地址:smtp.126.com（端口：25）
- 139邮箱：
  POP3服务器地址：POP.139.com（端口：110）
  SMTP服务器地址：SMTP.139.com(端口：25)
- 163.com:
  POP3服务器地址:pop.163.com（端口：110）
  SMTP服务器地址:smtp.163.com（端口：25）
  QQ邮箱
- POP3服务器地址：pop.qq.com（端口：110）
  SMTP服务器地址：smtp.qq.com（端口：25）
- QQ企业邮箱
  POP3服务器地址：pop.exmail.qq.com （SSL启用 端口：995）
  SMTP服务器地址：smtp.exmail.qq.com（SSL启用 端口：587/465）
- Foxmail：
  POP3服务器地址:POP.foxmail.com（端口：110）
  SMTP服务器地址:SMTP.foxmail.com（端口：25）
- china.com:
  POP3服务器地址:pop.china.com（端口：110）
  SMTP服务器地址:smtp.china.com（端口：25）
- yahoo.com:
  POP3服务器地址:pop.mail.yahoo.com（端口：995）
  SMTP服务器地址:smtp.mail.yahoo.com（端口：587）
- yahoo.com.cn:
  POP3服务器地址:pop.mail.yahoo.com.cn（端口：995）
  SMTP服务器地址:smtp.mail.yahoo.com.cn（端口：587）
- HotMail
  POP3服务器地址：pop3.live.com（端口：995）
  SMTP服务器地址：smtp.live.com（端口：587）
- gmail(google.com)
  POP3服务器地址:pop.gmail.com（SSL启用端口：995）
  SMTP服务器地址:smtp.gmail.com（SSL启用 端口：587）
- 263.net:
  POP3服务器地址:pop3.263.net（端口：110）
  SMTP服务器地址:smtp.263.net（端口：25）
- 263.net.cn:
  POP3服务器地址:pop.263.net.cn（端口：110）
  SMTP服务器地址:smtp.263.net.cn（端口：25）
- x263.net:
  POP3服务器地址:pop.x263.net（端口：110）
  SMTP服务器地址:smtp.x263.net（端口：25）
- 21cn.com:
  POP3服务器地址:pop.21cn.com（端口：110）
  SMTP服务器地址:smtp.21cn.com（端口：25）
- tom.com:
  POP3服务器地址:pop.tom.com（端口：110）
  SMTP服务器地址:smtp.tom.com（端口：25）



| 邮箱                  | 方式 | 服务器地址             | 端口    |
| --------------------- | ---- | ---------------------- | ------- |
| **sohu.com**          | POP3 | pop3.sohu.com          | 110     |
|                       | SMTP | smtp.sohu.com          | 25      |
| **126邮箱**           | POP3 | pop3.126.com           | 110     |
|                       | SMTP | smtp.126.com           | 25      |
| **139邮箱**           | POP3 | pop3.139.com           | 110     |
|                       | SMTP | smtp.139.com           | 25      |
| **163.com**           | POP3 | pop3.163.com           | 110     |
|                       | SMTP | smtp.163.com           | 25      |
| **QQ邮箱**            | POP3 | pop3.qq.com            | 110     |
|                       | SMTP | smtp.qq.com            | 25      |
| **QQ企业邮箱**        | POP3 | pop.exmail.qq.com      | 995     |
|                       | SMTP | smtp.exmail.qq.com     | 587/465 |
| **Foxmail**           | POP3 | pop3.foxmail.com       | 110     |
|                       | SMTP | smtp.foxmail.com       | 25      |
| **china.com**         | POP3 | pop3.china.com         | 110     |
|                       | SMTP | smtp.china.com         | 25      |
| **yahoo.com**         | POP3 | pop.mail.yahoo.com     | 110     |
|                       | SMTP | smtp.mail.yahoo.com    | 25      |
| **yahoo.com.cn**      | POP3 | pop.mail.yahoo.com.cn  | 110     |
|                       | SMTP | smtp.mail.yahoo.com.cn | 25      |
| **HotMail**           | POP3 | pop3.live.com          | 110     |
|                       | SMTP | smtp.sohu.com          | 25      |
| **gmail(google.com)** | POP3 | pop.gmail.com          | 995     |
|                       | SMTP | smtp.gmail.com         | 587     |
| **tom.com**           | POP3 | pop.tom.com            | 110     |
|                       | SMTP | smtp.tom.com           | 25      |




## Controller层

~~~java
    //自动生成工具类
    @Autowired
    private EmailSendUtils emailSendUtils;
~~~

~~~java
  emailSendUtils.send("subject","msg", "to");//调用send方法，分别传入标题、信息、收件人
~~~

