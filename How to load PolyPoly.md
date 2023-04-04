---Title: How to load PolyPoly---#How to load PolyPoly- [[howto]] [[polypoly]] [[vissoft]] [[casestudy]]- See the [github repo](https://github.com/polypoly-eu/sociator).- Load as follows:- [
 Metacello new
  baseline: 'Sociator';
  repository: 'github://polypoly-eu/sociator/src';
  load.

 #BaselineOfSociator asClass loadLepiterKnowledgeBases.
 
 self inform: 'Loading Sociator Finished'.
] fork- As this takes a while,  it's a good idea to save the image.- Smalltalk saveAs: 'polypoly.image'