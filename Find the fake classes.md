---Title: Find the fake classes---#Find the fake classes- (Proposed by [[JB]] on [slack](https://feenk.slack.com/archives/C3L058DSB/p1666214804684229).- How well do you know the Gt classes? Pick the real class names from the fakes:- size := 20.
realClasses := OrderedCollection new.
GtPharoIndex current globalCache
	do: [ :each | realClasses add: each ]
	startingWith: 'Gt'.
names := OrderedCollection new.
(GtPharoIndex current instVarNamed: 'classWordCache')
	do: [ :each :count | each = 'gt' ifFalse: [ names add: each capitalized withOccurrences: count ] ].
fakeNames := Set new.
[ fakeNames size < realClasses size ]
	whileTrue: [ | name |
		name := (String
				streamContents: [ :stream | 
					stream nextPutAll: 'Gt'.
					(2 to: 4) atRandom timesRepeat: [ stream nextPutAll: names atRandom ] ])
				asSymbol.
		(Smalltalk includesKey: name asSymbol) ifFalse: [ fakeNames add: name ] ].
fakeNames := fakeNames asOrderedCollection.
classNames := (1 to: size)
		collect: [ :i | 
			(SharedRandom globalGenerator next < 0.5
				ifTrue: [ realClasses ]
				ifFalse: [ fakeNames ]) atRandom ]- You can check your results with:- classNames select: [ :each | Smalltalk includesKey: each asSymbol ]