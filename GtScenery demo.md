---
item1 := scenery
		addItem: [ (GtWorkingWithTheGitHubRestApiShow new responseForFeenkOrg
				gtJsonFor: GtPhlowEmptyView new)
				asElementDo: [ :e | 
					e
						background: Color white;
						aptitude: BrShadowAptitude;
						margin: (BlInsets all: 10) ] ] asStencil.
item1 extent: 400 @ 400.
item2 := scenery
		addItem: (GtInspectorSceneryStencil new target: [GhOrganization new rawData: (STON fromString: (ZnClient new get: 'https://api.github.com/orgs/feenkcom'))]).
item2 position: 600 @ 0.
item2 extent: 400 @ 400.

item3 := scenery
		addItem: [ (GtWorkingWithTheGitHubRestApiShow new responseForGToolkitRepo
				gtJsonFor: GtPhlowEmptyView new)
				asElementDo: [ :e | 
					e
						background: Color white;
						aptitude: BrShadowAptitude;
						margin: (BlInsets all: 10) ] ] asStencil.
item3 position: 600 @ 600.
item3 extent: 400 @ 400.

item4 := scenery
		addItem: (GtInspectorSceneryStencil new target: [GhRepo new rawData: (STON fromString: (ZnClient new get: 'https://api.github.com/repos/feenkcom/gtoolkit'))]).
item4 position: 1200 @ 600.
item4 extent: 400 @ 400.


scenery
	addConnection: (GtParabollaArcSceneryStencil new labelText: 'wrap & view')
	from: item1
	to: item2.

scenery
	addConnection: (GtParabollaArcSceneryStencil new labelText: 'explore')
	from: item2
	to: item3.

	scenery
	addConnection: (GtParabollaArcSceneryStencil new labelText: 'wrap & view')
	from: item3
	to: item4.


scenery