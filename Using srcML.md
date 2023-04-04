---Title: Using srcML---#Using srcML- [[randomnote]]- [srcML](http://www.srcml.org) is a tool that reads source code in C, C++, Java or C#, and generates an XML-decorated version of the source code.- You can run it like this:    - ```language=text
srcml SimplePackrat.java > SimplePackrat.java.xml
```- and then you can parse the result with the {{gtClass:name=XMLDOMParser}}.