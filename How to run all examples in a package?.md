---
	withAll: GtLudoGame package gtExamplesAllContained.
examples runAll
& (GtSearchMethodsInPackageFilter new package: GtLudoGame package)).
GtExplicitExampleGroup withAll: (filter contents collect: #gtExample)
& (GtSearchMethodsInPackageFilter new package: GtLudoGame package)).