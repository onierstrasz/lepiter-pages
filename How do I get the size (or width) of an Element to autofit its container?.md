---
	layout: BlLinearLayout new;
	background: Color paleBlue;
	constraintsDo: [:c | 
		c horizontal matchParent.
		c vertical matchParent ];	
	addChild: (BlElement new 
		background: Color paleRed;
		layout: BlLinearLayout new;
		constraintsDo: [:c | 
			c horizontal fitContent.
			c vertical fitContent ];
		addChild: (BlTextElement new text: 'something' asRopedText))