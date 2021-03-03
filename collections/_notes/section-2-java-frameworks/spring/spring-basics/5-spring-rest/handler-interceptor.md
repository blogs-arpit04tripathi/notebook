---
layout: post
title: HandlerInterceptor
permalink: /:collection/spring/rest/handler-interceptor
---

- `org.springframework.web.servlet.HandlerInterceptor` interface - Intercepting requests
  - extremely useful when you want to apply specific functionality to certain requests, for example, checking for a principal. 
- HandlerInterceptor interface defines three methods for pre- and post-processing
  - called before the actual handler will be executed
  - called after the handler is executed
  - called after the complete request has finished.
- **preHandle(..)** returns a boolean value.
  - You can use this method to break or continue the processing of the execution chain.
  - true, handler execution chain will continue
  - false, DispatcherServlet assumes the interceptor itself has taken care of requests and does not continue executing the other interceptors and the actual handler in the execution chain.

```java
public class TimeBasedAccessInterceptor extends HandlerInterceptorAdapter {
    private int openingTime;
    private int closingTime;

    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        Calendar cal = Calendar.getInstance();
        int hour = cal.get(HOUR_OF_DAY);
        if (openingTime <= hour < closingTime) {
            return true;
        } else {
            response.sendRedirect("http://host.com/outsideOfficeHours.html");
            return false;
        }
    }
}
```
```xml
<beans>
    <bean id="handlerMapping" class="org.springframework.web.servlet.handler.SimpleUrlHandlerMapping">
        <property name="interceptors">
            <list>
                <ref bean="officeHoursInterceptor"/>
            </list>
        </property>
        <property name="mappings">
            <value>
                /*.form=editAccountFormController
                /*.view=editAccountFormController
            </value>
        </property>
    </bean>
    <bean id="officeHoursInterceptor"
          class="samples.TimeBasedAccessInterceptor">
        <property name="openingTime" value="9"/>
        <property name="closingTime" value="18"/>
    </bean>
<beans>
```

- Any request coming in, will be intercepted by the TimeBasedAccessInterceptor, and if the current time is outside office hours, the user will be redirected to a static html file, saying, for example, he can only access the website during office hours.
- Spring has an adapter class (the cunningly named **HandlerInterceptorAdapter**) to make it easier to extend the HandlerInterceptorinterface.
