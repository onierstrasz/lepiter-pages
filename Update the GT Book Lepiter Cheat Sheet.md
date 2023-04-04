---Title: Update the GT Book Lepiter Cheat Sheet---#Update the GT Book Lepiter Cheat Sheet- [[todo]] [[soon]] [[gtbook]] [[fixpage]]- {{gtTodo:label=Update GT Lepiter pages with any missing cheat sheet hints}}- *Actually most of these are already in the book in the TextSnippet and related pages!*- Instead augment those pages with any missing stuff- Markdown mostly follows github markdown conventions, with extensions for links to pages and code.    - See, for example, the [github markdown doc](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).- #Standard markdown examples    - #Header1    - `#Header1`    - ##Header2    - `##Header2`    - ###Header3    - `###Header3`    - **Bold text**    - `**Bold text**`    - *Italic text*    - `*Italic text*`    - `Fixed size text`    - ```language=text
`Fixed size text`
```    - Link to the [GT web page](https://gtoolkit.com).    - ```language=text
Link to the [GT web page](https://gtoolkit.com).
```    - ![GT icon](https://gtoolkit.com/assets/pictures/gtoolkit-icon.png)    - ```language=text
![GT icon](https://gtoolkit.com/assets/pictures/gtoolkit-icon.png)
```- #Lepiter extensions    - ```language=text
Multi-line
quoted text
```    - [[todo]] TO DO  -- generate snippet with code for example above! {{gtTodo:label=generate snippet with code for example above!}}    - Link to [[Update the GT Book Lepiter Cheat Sheet]]    - ```language=text
Link to [[Lepiter Cheat Sheet]]
```- #Code links    - Link to class: {{gtClass:name=True}}    - ```language=text
Link to class: {{gtClass:name=True}}
```    - Link to method: {{gtMethod:name=True>>ifTrue: | expanded}}- ##About extensions
The curly brace extensions each define their own language.
The syntax can be specified individual.
Could be interesting for domain specific languages.