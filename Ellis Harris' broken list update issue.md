---Title: Ellis Harris' broken list update issue---#Ellis Harris' broken list update issue- [[EH]] pointed out on Discord that a BrSimpleList does not update automatically, but it seems to me that he is just missing annoucnements for the updates.- targetList := BrSimpleList new
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
        border: (BlBorder paint: Color purple width: 1)- When  I  do targetList items at: 2 put: {true. 'True'},  there is no change until I click near the second item on the list or I use #items:
Not sure if this is the direction or should I be looking at the viewModel and  its events- targetList items at: 2 put: {true. 'True'}- I pointed him to:- game := GtLudoRecordingGame new autoPlay: 10- game autoPlay: 1