---
self velocity: 3@4
```
self background: Color blue
```
self size: 10@10
```
bounced ifTrue: [self velocity: vx @ vy].
```
		vx < 0
			ifTrue: [ self background: Color orange ]
			ifFalse: [ self background: Color green ]
```