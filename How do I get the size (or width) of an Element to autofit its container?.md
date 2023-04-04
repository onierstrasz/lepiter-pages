---Title: How do I get the size (or width) of an Element to autofit its container?---#How do I get the size (or width) of an Element to autofit its container?- [[howto]]  [[bloc]]- (Coder methods autofit — should be able to do it the same way.)- BlElement new 
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