---
m nodes
    stencil: [ :each | 
        | eL |
        eL := BlElement new
                size: 5 @ 5;
                when: BlClickEvent do: [ :e | e currentTarget phlow spawnObject: each ];
                background: Color black.
        each isPage
            ifTrue: [ eL
                    background: Color blue;
                    size: 5 @ 15 ].
        eL ];
    with: nodes.
m edges
    connectToAll: [ :each | each children asArray , (each allOutgoingTextualLinks collect: #target) ].
m layout force.
m asElement