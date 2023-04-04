---Title: How to make a pie chart---#How to make a pie chart- [[randomnote]] [[visualizations]]- From a [discord posting](GtMemoryCard new symbol:).- “tags is an OrderedCollection of Objects which represent the parsed output of my time tracking software (tagtime). the el count is the number of times that tag occurred in the period queried.”- “It's a type that is specific to the cli tool I was wrapping - the intent is to use this code in a gtView so I can run my tool and have the inspector give me interesting insights. But the key part for this code is that it has a count, which is a number that represents its size in proportion to the other tags (i.e. if you have two tags of count 1 then they should end up with half of the pie chart each). It also has a name, which is used for the label. 
In context, the count is the number of times I've tagged some period of time with that name (averaging out to 45 minutes per tag)
The tag also has a duration but I've not used that for anything here.”- Adapted the example to use a dictionary of tags to counts.- tagDict := { 'A' -> 10 . 'B' -> 20 . 'C' -> 30 . 'D' -> 40 } asDictionary.pingCount := tagDict values sum.
piAngles := tagDict associations collect: [:assoc | assoc key -> ((assoc value / pingCount) * 360) ].fromAngle := 0.

chart := BlElement new
    size: 700@700.
    
centerLabel := BlElement new relocate: 300@300.

piAngles do: [:el |
    | start end sec label |
    start := fromAngle.
    end := fromAngle + el value.
    sec := BlAnnulusSector new 
        startAngle: start;
        endAngle: end;
        innerRadius: 0.5.
        
    label := BlTextElement new text: (el key) asRopedText.
    label relocate: 300@300.
    
    fromAngle := el value + fromAngle.
    
    element := BlElement new
        background: (BlColorPaint color: Color random);
        size: 400@400;
        geometry: sec.
        
    element relocate: 100@100.
    
    (element addEventHandlerOn: BlMouseEnterEvent do: [ chart addChild: label as:#centerLabel ]).
    
    (element addEventHandlerOn: BlMouseLeaveEvent do: [ chart removeChildNamed: #centerLabel]).
    
    chart addChild: element.
].

chart.