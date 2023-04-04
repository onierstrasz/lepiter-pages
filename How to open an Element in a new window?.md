---Title: How to open an Element in a new window?---#How to open an Element in a new window?- [[howto]] [[todo]] [[bloc]]- Here are several examples (some broken):- GtTour new create  openInSpace.- Class gtBrowse.- BlSpace new addChild: ((GtInspector withToolOn: GtPackagesCoder new)); show.- BlSpace new addChild: (GtHome new); show.- BlSpace new title: 'PlayGround'; addChild: (GtPlaygroundStencil new create); withHalos; show.- GtInspector openOn: GtABCartoonAddressBookExample new cartoonAddressBook.- aSpace := BlSpace new.
aSpace title: 'Space'.
aSpace extent: 1200 @ 600.
aSpace addChild: (BlElement new background: Color red).
aSpace withHalos.
aSpace show.- An examples explorer:- BlSpace new	addChild: (GtInspector createOn: GtRlGToolkitExamplesExplorer buildForGToolkitProject);	show- BlSpace new	addChild: thisSnippet page;	show