---
layout: post
title: Creating JSP views
permalink: /:collection/spring/mvc/jsp-views
---

- TOC
{:toc}

<hr><br>

JSP has evolved over the years to include support for an expression language and custom tag libraries. Spring supports JSP views in two ways:
-	InternalResourceViewResolver can be used to resolve view names into JSP files. Moreover, if you’re using JavaServer Pages Standard Tag Library (JSTL) tags in your JSP pages, **InternalResourceViewResolver** can resolve view names into JSP files fronted by JstlView to expose JSTL locale and resource bundle variables to JSTL’s formatting and message tags.
-	Spring provides two JSP tag libraries, one for form-to-model binding and one providing general utility features.

# Configuring a JSP-ready view resolver

Whereas some view resolvers, such as ResourceBundleViewResolver, directly map a logical view name to a specific implementation of the View interface, InternalResourceViewResolver takes a more indirect approach. It follows a convention whereby a prefix and a suffix are attached to the view name to determine the physical path to a view resource in the same web application.

It’s a common practice to place JSP files under the web application’s WEB-INF folder to prevent direct access.
With this configuration of InternalResourceViewResolver in place, you can expect it to resolve logical view names into JSP files such as this:
-	home resolves to /WEB-INF/views/home.jsp
-	productList resolves to /WEB-INF/views/productList.jsp
-	books/detail resolves to /WEB-INF/views/books/detail.jsp

```java
@Bean
public ViewResolver viewResolver() {
    InternalResourceViewResolver resolver = new InternalResourceViewResolver();
    resolver.setPrefix("/WEB-INF/views/");
    resolver.setSuffix(".jsp");
    return resolver;
}
```
```xml
<bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver"
p:prefix="/WEB-INF/views/"
p:suffix=".jsp" />
```

![]({{site.cdn}}/spring/spring-mvc/logocal-view-name.png)

When a logical view name has a slash in it, that slash is carried over into the resource path name. Therefore, it maps to a JSP file that’s in a subdirectory of whatever directory is referenced by the prefix property. This offers a handy way of organizing your view templates under a hierarchy of directories rather than keeping them all in a single directory.

# Resolving JSTL Views

So far you’ve configured the basic, garden-variety InternalResourceViewResolver. It ultimately resolves logical view names into instances of InternalResourceView that reference JSP files. But if those JSP files are using JSTL tags for formatting or messages, then you may want to configure InternalResourceViewResolver to resolve a JstlView instead. JSTL’s formatting tags need a Locale to properly format locale-specific values such as dates and money. And its message tags can use a Spring message source and a Locale to properly choose messages to render in HTML. By resolving JstlView, the JSTL tags will be given the Locale and any message source configured in Spring

```java
@Bean
public ViewResolver viewResolver() {
InternalResourceViewResolver resolver = new InternalResourceViewResolver();
  resolver.setPrefix("/WEB-INF/views/");
  resolver.setSuffix(".jsp");  resolver.setViewClass(org.springframework.web.servlet.view.JstlView.class);
  return resolver;
}
```
```xml
<bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver"
p:prefix="/WEB-INF/views/"
p:suffix=".jsp"
p:viewClass="org.springframework.web.servlet.view.JstlView" />
```

# Using Spring’s JSP libraries

Tag libraries are a powerful way to bring functionality to a JSP template without resorting to writing Java code directly in scriptlet blocks. Spring offers two JSP tag libraries to help define the view of your Spring MVC web views. One tag library renders HTML form tags that are bound to a model attribute. The other has a hodgepodge of utility tags that come in handy from time to time. You’re likely to find the form-binding tag library to be the more useful of the two tag libraries. So that’s where you’ll start with Spring’s JSP tags.

# BINDING FORMS TO THE MODEL

Spring’s form-binding JSP tag library includes 14 tags, most of which render HTML form tags. But what makes these different from the raw HTML tags is that they’re bound to an object in the model and can be populated with values from the model object’s properties. The tag library also includes a tag that can be used to communicate errors to the user by rendering them into the resulting HTML. 

To use the form-binding tag library, you’ll need to declare it in the JSP pages that will use it:

```xml
<%@ taglib uri="http://www.springframework.org/tags/form" prefix="sf" %>

<sf:form method="POST" commandName="spitter">
First Name: <sf:input path="firstName" /><br/>
Last Name: <sf:input path="lastName" /><br/>
Email: <sf:input path="email" /><br/>
Username: <sf:input path="username" /><br/>
Password: <sf:password path="password" /><br/>
<input type="submit" value="Register" />
</sf:form>
```

The <sf:form> tag renders an HTML <form> tag. But it also sets some context around a model object designated in the commandName attribute. Properties on the model object will be referenced in the other form-binding tags you use. In the preceding code, you set commandName to spitter. Therefore, there must be an object in the model whose key is spitter, or else the form won’t be able to render (and you’ll get JSP errors). That means you need to make a small change to SpitterController to ensure that a Spitter object is in the model under the spitter key.

```java
@RequestMapping(value="/register", method=GET)
public String showRegistrationForm(Model model) {
model.addAttribute(new Spitter());
return "registerForm";
}
```

This tweak to showRegistrationForm() now has that method adding a new Spitter instance to the model. The model key will be inferred from the object type to be spitter—exactly what you need it to be.

Once you declare the form-binding tag library, you’re afforded 14 tags. These are listed in table.

|JSP tag            |Description|
|---                |---|	
|\<sf:checkbox>     |	Renders an HTML \<input> tag with type set to checkbox.|
|\<sf:checkboxes>   |	Renders multiple HTML \<input> tags with type set to checkbox.|
|\<sf:errors>       |	Renders field errors in an HTML \<span> tag.|
|\<sf:form>         |	Renders an HTML \<form> tag and exposed binding path to inner tags for data-binding.|
|\<sf:hidden>       |	Renders an HTML \<input> tag with type set to hidden.|
|\<sf:input>        |	Renders an HTML \<input> tag with type set to text.|
|\<sf:label>        |	Renders an HTML \<label> tag.|
|\<sf:option>       |	Renders an HTML \<option> tag. The selected attribute is set according to the bound value.|
|\<sf:options>      |	Renders a list of HTML \<option> tags corresponding to the bound collection, array, or map.|
|\<sf:password>     |	Renders an HTML \<input> tag with type set to password.|
|\<sf:radiobutton>  |	Renders an HTML \<input> tag with type set to radio.|
|\<sf:radiobuttons> |	Renders multiple HTML \<input> tags with type set to radio.|
|\<sf:select>       |	Renders an HTML \<select> tag.|
|\<sf:textarea>     |	Renders an HTML \<textarea> tag.|

Going back to the form, the first three fields have had their HTML \<input> tag replaced with \<sf:input>. This tag renders an HTML \<input> tag with the type attribute set to text. Its value attribute will be set to the value of the model object’s property specified in the path attribute. For instance, if the Spitter object in the model has Jack as the value of its firstName property, then \<sf:input path="firstName"/> will render an \<input> tag with value="Jack". The password field uses \<sf:password> instead of \<sf:input>.

\<sf:password> is similar to \<sf:input> but renders an HTML \<input> whose type attribute is set to password so that the value will be masked as it’s typed.

```xml
<form id="spitter" action="/spitter/spitter/register" method="POST">
 First Name: <input id="firstName" name="firstName" type="text" value="J"/><br/>
 Last Name: <input id="lastName" name="lastName" type="text" value="B"/><br/>
 Email: <input id="email" name="email" type="text" value="jack"/><br/>
 Username: <input id="username" name="username" type="text" value="jack"/><br/>
 Password: <input id="password" name="password" type="password" value=""/><br/>
 <input type="submit" value="Register" />
</form>
```

Starting with Spring 3.1, the <sf:input> tag allows you to specify a type attribute so that you can declare HTML 5–specific type text fields such as data, range, and email, among other options.

```xml
Email: <sf:input path="email" type="email" /><br/> will rendered to HTML5 Email: <input id="email" name="email" type="email" value="jack"/><br/>
```
Using Spring’s form-binding tags gives you a slight improvement over using standard HTML tags—the form is prepopulated with the previously entered values after failed validation. But it still fails to tell the user what they did wrong. To guide the user in fixing their mistakes, you’ll need the \<sf:errors> tag.

# DISPLAYING ERRORS

When there are validation errors, the details of those errors are carried in the request along with model data. All you need to do is dig into the model and extract the errors to display to the user. Here its path attribute is set to firstName, the name of the Spitter model object property for which errors should be displayed. If there are no errors for the firstName property, then \<sf:errors> won’t render anything. But if there is a validation error, it will render that error message in an HTML \<span> tag.

```xml
<sf:form method="POST" commandName="spitter">
First Name: <sf:input path="firstName" />
<sf:errors path="firstName" /><br/>
...
</sf:form>
```

HTML Output on error -
```xml
First Name: <input id="firstName" name="firstName" type="text" value="J"/>
<span id="firstName.errors">size must be between 2 and 30</span>

<sf:form method="POST" commandName="spitter" >
First Name: <sf:input path="firstName" />
<sf:errors path="firstName" cssClass="error" /><br/>
...
</sf:form>
span.error { color: red; }
```

Displaying validation errors next to the fields that have errors is a nice way to draw the user’s attention to problems they need to fix. But it could be problematic with regard to layout. Another way to handle validation errors is to display them all together. To do this, you can remove the \<sf:errors> element from each field and place it at the top of the form like this:

```xml
<sf:form method="POST" commandName="spitter" >
<sf:errors path="*" element="div" cssClass="errors" />
...
</sf:form>
```

What’s noticeably different about this \<sf:errors> as compared to the ones you’ve used before is that its path is set to *. This is a wildcard selector that tells \<sf:errors> to render all errors for all properties. Also notice that you set the element attribute to div. By default, errors are rendered in an HTML \<span> tag, which is fine when there’s only one error to display. But when you’re rendering errors for all fields, there could easily be more than one error to display, and a \<span> tag (an inline tag) is not ideal. A block tag such as \<div> would be better. Therefore, you can set the element attribute to div so that errors render in a \<div> tag.

```css
div.errors {
background-color: #ffcccc;
border: 2px solid red;
}
```
Now you’ve shoved all the errors to the top of the form, which may make laying out the page easier. But you’ve lost the ability to highlight the fields that need to be corrected. That’s easily addressed by setting the cssErrorClass attribute on each field. You can also wrap each label with \<sf:label> and set its cssErrorClass.
```xml
<sf:form method="POST" commandName="spitter" >
<sf:label path="firstName" cssErrorClass="error">First Name</sf:label>:
<sf:input path="firstName" cssErrorClass="error" /><br/>
...
</sf:form>
```
On its own, setting the path attribute on \<sf:label> doesn’t accomplish much. But you’re also setting cssErrorClass. If the bound property has any errors, the rendered \<label> element’s class attribute will be set to error like this:
```xml
<label for="firstName" class="error">First Name</label>
```

Similarly, the \<sf:input> tag now has its cssErrorClass set to error. If there’s a validation error, the rendered \<input> tag’s class attribute will be set to error. Now you can style the label and the fields so that the user’s attention is drawn to them if there are any errors.
```java
label.error { color: red; }
input.error { background-color: #ffcccc; }
@NotNull
@Size(min=5, max=16, message="{username.size}")
private String username;
@NotNull
@Size(min=5, max=25, message="{password.size}")
private String password;
@NotNull
@Size(min=2, max=30, message="{firstName.size}")
private String firstName;
@NotNull
@Size(min=2, max=30, message="{lastName.size}")
private String lastName;
@NotNull
@Email(message="{email.valid}")
private String email;
```
For each of the fields, the @Size annotation has message set to a string whose value is wrapped in curly braces. If you left the curly braces out, the value given to message would be the error message displayed to the user. But by using curly braces, you designate a property in a properties file that contains the actual message.

```properties
firstName.size=First name must be between {min} and {max} characters long.
lastName.size=Last name must be between {min} and {max} characters long.
username.size=Username must be between {min} and {max} characters long.
password.size=Password must be between {min} and {max} characters long.
email.valid=The email address must be valid.
```

What’s nice about extracting the error messages to a properties file is that you can display language- and locale-specific messages by creating a locale-specific properties file. For example, to display the errors in Spanish, you can create a file named ValidationErrors_es.properties with the following content:
![jstl-errors]({{site.cdn}}/spring/spring-mvc/jstl-errors.png){:target="_blank"}
