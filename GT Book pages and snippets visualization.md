---Title: GT Book pages and snippets visualization---#GT Book pages and snippets visualization- [[visualizations]]- See the [discord demo discussion](https://discord.com/channels/729445214812504107/735949717049049129/998492779757965372).- This takes about 2.5 minutes (many unnamed pages). 558 pages and 3221 snippets.- pages := thisSnippet database pages.snippets := pages flatCollect: #allChildrenDepthFirst.nodes := pages.nodes addAll: snippets.- The gtBook takes about 1.5 minutes. 194 pages and 3090 snippets.- pages := LeStorageExamples new gtBook pages.snippets := pages flatCollect: #allChildrenDepthFirst.nodes := pages.nodes addAll: snippets.- m := GtMondrian new.
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