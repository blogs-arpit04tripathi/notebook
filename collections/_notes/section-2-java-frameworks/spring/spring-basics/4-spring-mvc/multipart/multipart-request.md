---
layout: post
title: Multipart Requests
permalink: /:collection/spring/mvc/multipart
---

- Multipart form data
  - breaks a form into individual parts, with one part per field.
  - Each part can have its own type.
  - Typical form fields have textual data in their parts
  - but when something is being uploaded, the part can be binary.
- In this multipart request
  - profilePicture part has its own Content-Type header indicating JPEG image.
  - body of profilePicture part is binary data instead of simple text.

```
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="firstName"
Charles
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="lastName"
Xavier
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="email"
charles@xmen.com
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="username"
professorx
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="password"
letmein01
------WebKitFormBoundaryqgkaBn8IHJCuNmiW
Content-Disposition: form-data; name="profilePicture"; filename="me.jpg"
Content-Type: image/jpeg
[[ Binary image data goes here ]]
------WebKitFormBoundaryqgkaBn8IHJCuNmiW--
```

**Configuring a multipart resolver**
- DispatcherServlet doesn’t implement any logic for parsing the multipart request.
- It delegates to an implementation of Spring’s MultipartResolver interface.
  -	**StandardServletMultipartResolver** - Relies on Servlet 3.0 support for multipart requests.
  -	**CommonsMultipartResolver** - Resolves multipart requests using ***Jakarta Commons FileUpload***.
