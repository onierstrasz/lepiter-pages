---
	do: [ :p | [ p asMarkdownString ] onErrorDo: [ :err | failures add: p -> err ] ].
failures.