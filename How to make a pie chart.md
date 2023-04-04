---
In context, the count is the number of times I've tagged some period of time with that name (averaging out to 45 minutes per tag)
The tag also has a duration but I've not used that for anything here.”
piAngles := tagDict associations collect: [:assoc | assoc key -> ((assoc value / pingCount) * 360) ].

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