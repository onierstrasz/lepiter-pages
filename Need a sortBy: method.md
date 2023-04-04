---Title: Need a sortBy: method---#Need a sortBy: method- [[todo]] [[feature]]- Very often we write code like this:- Object methods sort: [ :a :b | a size <= b size ]- What we really want is to write this:- Object methods sortBy: #size- All  we need is this:- ```language=text
Collection>>#sortBy: aSelector	^ self sorted: [ :a :b | (a perform: aSelector) <= (b perform: aSelector) ]
```- Alternatively, we could implement `#value:value` in {{gtClass:name=Symbol}} as follows:- ```language=text
Symbol>>#value: anObject value: anotherObject	^ (anObject perform: self) <= (anotherObject perform: self)
```- Object methods sort: #size