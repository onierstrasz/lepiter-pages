---
	| currentProperties |
	currentProperties := LeDatabasesRegistry defaultLogicalDatabase properties.
	currentProperties
		addRegisteredDirectory: FileLocator imageDirectory / ''pharo-local'' / ''iceberg'' / '
	LeDatabasesRegistry default defaultLogicalDatabase reload'.
	baseline: ''', packageName , ''';
	repository: ''github://' , repoPath , ':main/src'';
	load