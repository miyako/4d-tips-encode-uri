# 4d-tips-encode-uri

5 different methods to perform [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding).

[RFC 2396](https://tools.ietf.org/html/rfc2396) of 1998 specifies that the following character are not escaped:

``-`` ``_`` ``.`` ``~`` ``!`` ``*`` ``'`` ``(`` ``)``

JavaScript ([encodeURI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI) and [encodeURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)) follow this convension.

### Example

[encodeURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)

```
ASSERT("-_.~!*'()"=URL_Encode ("-_.~!*'()";RFC 2396))
ASSERT("-_.~"=URL_Encode ("-_.~";RFC 3986))
ASSERT("%21%2A%27%28%29"=URL_Encode ("!*'()";RFC 3986))
```

[encodeURI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)

```
ASSERT("https://www.google.com/?q=%E3%83%95%E3%82%A9%E3%83%BC%E3%83%87%E3%82%A3%E3%83%BC"=\
URL_Encode ("https://www.google.com/?q=フォーディー";RFC 2396 URI))

ASSERT("https://www.google.com/?q=%E3%83%95%E3%82%A9%E3%83%BC%E3%83%87%E3%82%A3%E3%83%BC"=\
URL_Encode ("https://www.google.com/?q=フォーディー";RFC 3986 URI))
```

QueryEscape()

```
ASSERT("abc+def"=URL_Encode ("abc def";WWW FORM))
```
