# 4d-tips-encode-uri

5 different methods to perform [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding).


### Example

encodeURIComponent()

```
ASSERT("-_.~!*'()"=URL_Encode ("-_.~!*'()";RFC 2396))
ASSERT("-_.~"=URL_Encode ("-_.~";RFC 3986))
ASSERT("%21%2A%27%28%29"=URL_Encode ("!*'()";RFC 3986))
```

encodeURI()

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
