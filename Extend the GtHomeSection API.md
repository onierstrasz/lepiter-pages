---
	layout: BlFlowLayout new;
	constraintsDo: [ :c |
		c horizontal matchParent.
		c vertical fitContent ];
	padding: (BlInsets all: 0);
	in: [ :anElement |
		anElement addChild: (GtHomeSection new 
			newInspectorCardForObject: BlElement new).
		anElement addChild: (GtHomeSection new  
                newUrlCardWithTitle: 'GT Page' 
				description: 'View the GT page' 
				url: 'https://www.gtoolkit.com').
		anElement addChild:( GtHomeSection new 
				newLepiterPageCardForPageNamed: 'GT Book' 
				withTitle: 'Gt Book' 
				andDescription: 'View the Book') ]