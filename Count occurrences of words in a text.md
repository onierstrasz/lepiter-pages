---
Anyhoo, I got tired of waiting so I interrupted the program and it ended up in {{gtMethod:name=String>>findDelimiters:startingAt:|expanded}} which, rather than calling #includes: actually iterates the delimiters and this takes forever.
skipDelimiters: delimiters startingAt: start has a similar problem.  Changing it to
start to: self size do: [ :i | 
        (delimiters includes: (self at: i)) 
            ifFalse: [ ^ i ] ].
    ^ self size + 1
```