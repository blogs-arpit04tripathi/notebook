---
layout: post
title: URL (Uniform resource locator)
permalink: /:collection/http/url
---

- string that constitutes a reference to an Internet resource.

**Query String Encoding**
- Letters (A-Z and a-z), numbers (0-9) and the characters '.' , '-' , '~' and '_' are left as-is
- SPACE is encoded as '+' or hexadecimal (%20)
- All other characters are encoded as %FF hexadecimal representation, with any non-ASCII characters first encoded as UTF-8 (or other specified encoding)
- Typical max value for a single GET parameter value is 512 bytes


|Purpose	|Parameters|
|---|---|
|Pagination	       |?offset=x&limit=y
|Sorting	       |sort=\<criteria>&order=[ASC\|DESC]
|Max results	   |?max=n
|Dedicated elements|?id=xyz&id=abc&id=def&...


|IMPLEMENTATION|LIMIT|
|---|---|
|Firefox|Unlimited, although instability occurs with URLs reaching around 65,000 characters.|
|Safari|Unlimited.|
|Internet Explorer v6 - v7|Maximum length of a URL in Internet Explorer is 2,083 characters, with no more than 2,048 characters in the path portion of the URL.
|Internet Explorer v8+	|Maximum length of a URL in Internet Explorer is 4,095 characters, with no more than 2,048 characters in the path portion of the URL. <br>Maximum mailto: length is 500 to 512 characters long.|
|Sitemap Protocol	|\<loc> URL of the page. This URL must begin with the protocol (such as http) and end with a trailing slash, if your web server requires it. This value must be less than 2,048 characters.|
|GoogleBot crawler	|Google will index URLs up to 2047 characters in length.|
|Google search results page (SERP)|Google index-able links that will work when clicked in the SERP's is ~1855 characters in length.|
