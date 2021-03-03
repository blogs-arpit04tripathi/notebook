---
layout: post
title: Handler Mapping
permalink: /:collection/spring/rest/handler-mapping
---

- **HandlerMapping** provides ***HandlerExecutionChain***.
- Then, DispatcherServlet execute the handler and interceptors in the chain (if any).

# BeanNameUrlHandlerMapping (Default)
- Maps incoming HTTP requests to bean names.
- By default, DispatcherServlet creates a BeanNameUrlHandlerMapping if no handler mapping can be found in the context.

```xml
<beans>
  <bean id="handlerMapping" class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping"/>
  <bean name="/editaccount.form" class="org.springframework.web.servlet.mvc.SimpleFormController">
    <property name="formView" value="account"/>
    <property name="successView" value="account-created"/>
    <property name="commandName" value="account"/>
    <property name="commandClass" value="samples.Account"/>
  </bean>
<beans>
```

# SimpleUrlHandlerMapping
- configurable in the application context
- has Ant-style path matching capabilities.

```xml
<beans>
    <!-- no 'id' required, HandlerMapping beans are automatically detected by the DispatcherServlet -->
    <bean class="org.springframework.web.servlet.handler.SimpleUrlHandlerMapping">
        <property name="mappings">
            <value>
                /*/account.form=editAccountFormController
                /*/editaccount.form=editAccountFormController
                /ex/view*.html=helpController
                /**/help.html=helpController
            </value>
        </property>
    </bean>
    <bean id="helpController" 
          class="org.springframework.web.servlet.mvc.UrlFilenameViewController"/>
    <bean id="editAccountFormController"
          class="org.springframework.web.servlet.mvc.SimpleFormController">
        <property name="formView" value="account"/>
        <property name="successView" value="account-created"/>
        <property name="commandName" value="Account"/>
        <property name="commandClass" value="samples.Account"/>
    </bean>
<beans>
```

The above two HandlerMappings have below properties :
-	**interceptors**: list of interceptors to use (HandlerInterceptors)
-	**defaultHandler**: default handler to use, when matching handler not found.
-	**order**: Spring sort all handler mappings available in the context by this property and apply the first matching handler.
- **alwaysUseFullPath**:
  - If true, Spring use full path within the current servlet context to find an appropriate handler.
  - If false (default), path within current servlet mapping will be used.
  - servlet `/testing/*`
    - true -> `/testing/viewPage.html`
    - false -> `/viewPage.html`
- **urlDecode**: 
  - default true.
  - If you prefer to compare encoded paths, switch this flag to false.
  - HttpServletRequest always exposes the servlet path in decoded form.
    - Be aware that the servlet path will not match when compared with encoded paths.
- **lazyInitHandlers**
  - Default value is false.
  - allows for lazy initialization of singleton handlers
  - prototype handlers are always lazily initialized.
