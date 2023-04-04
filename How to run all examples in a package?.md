---Title: How to run all examples in a package?---#How to run all examples in a package?- [[howto]] [[querying]]- Explicitly:- GtExplicitExampleGroup withAll:	GtLudoGame package gtExamplesAllContained- examples := GtExplicitExampleGroup 
	withAll: GtLudoGame package gtExamplesAllContained.
examples runAll- Or using filters:- filter := (#gtExample gtPragmas
& (GtSearchMethodsInPackageFilter new package: GtLudoGame package)).
GtExplicitExampleGroup withAll: (filter contents collect: #gtExample)- filter := (#gtExample gtPragmas
& (GtSearchMethodsInPackageFilter new package: GtLudoGame package)).filter gtExamples