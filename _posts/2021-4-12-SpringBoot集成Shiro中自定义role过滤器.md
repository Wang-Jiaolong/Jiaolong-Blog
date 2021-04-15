---
title: "「SprintBoot」集成Shiro中自定义role过滤器"
subtitle: "问题背景：在做毕设中，使用`SpringBoot`+`vue`实现前后分离，在使用`Shiro`实现安全框架时，由于默认在未授权或未登录时会进行重定向操作，涉及跨域问题导致403，故需要自定义Filter重写方法，返回`Json`，代替重定向。"
layout: post
author: "Jalen"
header-style: text
hidden: false
tags:
  - SpringBoot
  - Shiro
---

> 问题背景：在做毕设中，使用`SpringBoot`+`vue`实现前后分离，在使用`Shiro`实现安全框架时，由于默认在未授权或未登录时会进行重定向操作，涉及跨域问题导致403，故需要自定义Filter重写方法，返回`Json`，代替重定向。

# 相关环境

- 后端： `SpringBoot`+`Shiro`+`Redis`+`JWT`



# 解决方案（不完美）：

## 自定义角色过滤器`RolesAnyAuthorizationFilter`

```java
import com.jiaolong.myteam.cms.entity.dto.commons.BaseResult;
import com.jiaolong.myteam.cms.utils.JwtUtil;
import com.jiaolong.myteam.cms.utils.MapperUtils;
import org.apache.shiro.web.filter.AccessControlFilter;

import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.http.HttpServletRequest;
import java.io.PrintWriter;

public class RolesAnyAuthorizationFilter extends AccessControlFilter {
    @Override
    protected boolean isAccessAllowed(ServletRequest servletRequest, ServletResponse servletResponse, Object o) throws Exception {
        boolean bool = false;
        HttpServletRequest httpRequest = (HttpServletRequest)servletRequest;
        String token = httpRequest.getHeader("X-Token");    //从请求头中获取token
        String role = JwtUtil.verityToken(token,"role");    //使用工具类获取token中的role信息
        if (!role.equals("admin")){     //如果有权限

            /*--- 返回Json ---*/
            servletResponse.setContentType("application/json;charset=utf-8");
            PrintWriter out = servletResponse.getWriter();
            out.println(MapperUtils.obj2jsonIgnoreNull(BaseResult.fail(403,"未授权")));
            out.flush();
            out.close();
            /*--- /返回Json ---*/
            
        }else{
            bool = true;
        }
        return bool;
    }

    @Override
    protected boolean onAccessDenied(ServletRequest servletRequest, ServletResponse servletResponse) throws Exception {
        return false;
    }
}

```



------

**遇到的一些坑：**

本来token中只封装了`username`字段，在`filter`中，本想利用`Service`通过`username`获取到用户信息，拿到`role`，但在使用`@Autowired`注解时，发现一直返回null，后发现`Shiro`的过滤器注入会在Bean注入之前，导致无法自动注入`Service`，网上给出的一些解决方案没生效，未果，等以后有机会了再做研究，暂采用把`role字`段加密到`token`中的方式解决。