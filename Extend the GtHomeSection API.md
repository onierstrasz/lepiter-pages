---Title: Extend the GtHomeSection API---#Extend the GtHomeSection API- [[todo]]- See {{gtPage:How to set up a Home Section|db=2j9m7db2i4oz116bexd7wbdxo}}- [[AC]] suggests “Why not have a more generic builder pattern like we do for views? The section could offer an API to add different types of cards”.- [[TG]] says “We already have constructor methods in the superclass of section”- Examples other than opening Lepiter pages are spawning a tool or an inspector.- [[AC]]: This is a very rough example    - BlElement new
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
				andDescription: 'View the Book') ]    - Feels like what is missing is a home section that would  put this under a simpler API