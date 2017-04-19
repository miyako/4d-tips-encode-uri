# 4d-tips-encode-uri

5 different methods to perform [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding).

[RFC 2396](https://tools.ietf.org/html/rfc2396) of 1998 specifies that the following character are not escaped:

``-`` ``_`` ``.`` ``~`` ``!`` ``*`` ``'`` ``(`` ``)``

JavaScript [encodeURI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI) and [encodeURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent) follow this convension.

[RFC 3986](https://tools.ietf.org/html/rfc3986) of 2005 removed ``!`` ``*`` ``'`` ``(`` ``)`` from this list. It specifies that the following character are not escaped:

``-`` ``_`` ``.`` ``~``

The difference between [encodeURI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI) and [encodeURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent) is that the former does not escape the following characters, to preserve URI integrity:

``;`` ``,`` ``/`` ``?`` ``:`` ``@`` ``&`` ``=`` ``+`` ``$``

This is similar to how the 4D commands ``OPEN URL``, ``HTTP Get``, ``HTTP Request``, ``Convert path system to POSIX``, ``WA OPEN URL``, etc. escapes certain characters.

There is a similar HTML specification in which form data posted as ``application/x-www-form-urlencoded`` should be escaped. The notable difference is that the space character is escaped as ``+``, not ``%20``.

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
