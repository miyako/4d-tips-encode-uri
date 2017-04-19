# 4d-tips-encode-uri

5 different methods to perform [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding).


### Example

```
SET TEXT TO PASTEBOARD(Generate UUID)

  //RFC 2396 (1998) Marks (encodeURIComponent; does not encode the following)
  // - _ . ~ ! * ' ( )

  //RFC 3986 (2005) Reserved Characters (encodeURIComponent; does not encode the following)
  // - _ . ~

  //in both cases, never encode the following
  //A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
  //a b c d e f g h i j k l m n o p q r s t u v w x y z
  //0 1 2 3 4 5 6 7 8 9

ASSERT("-_.~!*'()"=URL_Encode ("-_.~!*'()";RFC 2396))
ASSERT("-_.~"=URL_Encode ("-_.~";RFC 3986))
ASSERT("%21%2A%27%28%29"=URL_Encode ("!*'()";RFC 3986))

  //encodeURIComponent() in JavaScript corresponds to the above RFC 2396
  //encodeURI() in JavaScript preserves the following to keep URI integrity
  // ; , / ? : @ & = + $ 

  //https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent
  //https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI

ASSERT("https://www.google.com/?q=%E3%83%95%E3%82%A9%E3%83%BC%E3%83%87%E3%82%A3%E3%83%BC"=\
URL_Encode ("https://www.google.com/?q=フォーディー";RFC 2396 URI))

ASSERT("https://www.google.com/?q=%E3%83%95%E3%82%A9%E3%83%BC%E3%83%87%E3%82%A3%E3%83%BC"=\
URL_Encode ("https://www.google.com/?q=フォーディー";RFC 3986 URI))

  //QueryEscape() is unrelated to RFC, it is based on HTML (application/x-www-form-urlencoded)
  //the main difference is that the space character is escaped as +, not %20

ASSERT("abc+def"=URL_Encode ("abc def";WWW FORM))
```
