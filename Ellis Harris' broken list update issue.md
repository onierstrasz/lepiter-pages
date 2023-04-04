---
        itemStencil: [ BrHorizontalPane new
                alignCenterLeft;
                margin: (BlInsets all: 2);
                addChild: (BrCheckbox new aptitude: BrGlamorousCheckboxAptitude) as: #check;
                addChild: (BrEditor new
                            matchParent;
                            margin: (BlInsets all: 2);
                            aptitude: BrEditorAptitude + BrGlamorousInputFieldSpacingAptitude
                                    + BrGlamorousListItemAptitude + BrGlamorousInputFieldSpacingAptitude)
                    as: #cText ];
        itemDataBinder: [ :element :item | 
            (element childNamed: #check) checked: item first.
            (element childNamed: #cText) text: item second.
            element ];
        items: {{true.
                    'Not False' asRopedText}.
                {false.
                    'Not True'}};
        border: (BlBorder paint: Color purple width: 1)
Not sure if this is the direction or should I be looking at the viewModel and  its events