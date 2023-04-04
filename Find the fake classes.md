---
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
				ifFalse: [ fakeNames ]) atRandom ]