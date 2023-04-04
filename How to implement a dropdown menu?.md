---Title: How to implement a dropdown menu?---#How to implement a dropdown menu?- [[howto]]- Look at {{gtMethod:name=GtWorldElement>>#newSubSpaceButton}}- See {{gtClass:name=GtToolsMenu}} for the dropdown itself.- Also see this example by TG:- badgeButton := BrButton new
	layout: BlLinearLayout horizontal;
	constraintsDo: [ :c | 
		c horizontal fitContent.
		c vertical fitContent ];
	padding: (BlInsets all: 7);
	icon: BrGlamorousIcons hamburger asElement;
	look: 
		BrGlamorousButtonWithIconAptitude +
		(BrGlamorousWithDropdownAptitude new stencil: [ 
			| aList |
			aList := BrGlamorousSimpleContextMenuContent new.
			aList
				display:
						{('Action 1' -> [ self halt ]).
						('Action 2' -> [ self halt ]).
						('Action 3' -> [ self halt ])};
					yourself.
			BrAnchoredElement new look:
				(BrGlamorousDropdownAptitude new
					handle: (BrButton new icon: BrGlamorousIcons hamburger asElement; look:
		BrGlamorousButtonWithIconAptitude - BrGlamorousButtonExteriorAptitude);
					content: (aList
						padding: (BlInsets all: 5);
						vFitContent;
						hExact: 200)) ]);
	relocate: 200 @ 100