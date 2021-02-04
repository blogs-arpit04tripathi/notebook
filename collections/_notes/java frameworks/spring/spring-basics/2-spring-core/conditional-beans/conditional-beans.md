---
layout: post
title: Conditional Beans
permalink: /:collection/spring/conditional-beans
---

If you want one or more beans to be configured 
-	only if some library is available in the application’s classpath. 
-	only if a certain other bean is also declared.
-	only if a specific environment variable is set.

```java
@Bean
@Conditional(MagicExistsCondition.class)
public MagicBean magicBean() {
    return new MagicBean(); 
}
```
```java
public class MagicExistsCondition implements Condition {
 public boolean matches(ConditionContext context, AnnotatedTypeMetadata metadata) {
    Environment env = context.getEnvironment();
    return env.containsProperty("magic");
 }
}
```
matches() true, @Conditional-annotated beans are created otherwise not.

**ConditionContext**, you can do the following:
-	Check for bean definitions via the BeanDefinitionRegistry returned from getRegistry().
-	Check for the presence of beans, and even dig into bean properties via the ConfigurableListableBeanFactory returned from getBeanFactory().
-	Check the presence and values of environment variables via the Environment retrieved from getEnvironment().
-	Read and inspect the contents of resources loaded via the ResourceLoader returned from getResourceLoader().
-	Load and check for the presence of classes via the ClassLoader returned from getClassLoader().

**AnnotatedTypeMetadata** offers a chance to inspect annotations that may also be placed on the @Bean method.
```java
public interface AnnotatedTypeMetadata {
  boolean isAnnotated(String annotationType);
  Map<String, Object> getAnnotationAttributes(String annotationType);
  Map<String, Object> getAnnotationAttributes(String annotationType, boolean classValuesAsString);
  MultiValueMap<String, Object> getAllAnnotationAttributes(String annotationType);
  MultiValueMap<String, Object> getAllAnnotationAttributes(String annotationType, boolean classValuesAsString);
}
```

The @Profile annotation looks like this:
```java
@Retention(RetentionPolicy.RUNTIME)
@Target({
    ElementType.TYPE,
    ElementType.METHOD
})
@Documented
@Conditional(ProfileCondition.class)
public @interface Profile {
    String[] value();
}
```
```java
class ProfileCondition implements Condition {
    public boolean matches(ConditionContext context, AnnotatedTypeMetadata metadata) {
        if (context.getEnvironment() != null) {
            MultiValueMap < String, Object > attrs = metadata.getAllAnnotationAttributes(Profile.class.getName());
            if (attrs != null)
                for (Object value: attrs.get("value"))
                    if (context.getEnvironment().acceptsProfiles((String[]) value))
                        return true;
            return false;
        }
        return true;
    }
}
```
Here, ProfileCondition fetches all the annotation attributes for the @Profile annotation from AnnotatedTypeMetadata. With that, it checks explicitly for the value attribute, which contains the name of the bean’s profile. It then consults with the Environment retrieved from the ConditionContext to see whether the profile is active (by calling the **acceptsProfiles()** method).
