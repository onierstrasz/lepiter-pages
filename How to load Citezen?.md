---Title: How to load Citezen?---#How to load Citezen?- [[todo]]- Having problems loading [Citezen](https://github.com/Ducasse/Citezen) ?- Metacello new
   baseline: 'Citezen';
   repository: 'github://Ducasse/Citezen';
   load.- Need to comment out the SmaCC dependencies in {{gtMethod:name=BaselineOfCitezen>>#baseline18:}}.- All the tests pass with the GT version of SmaCC.- scgbib := ZnClient new		get: 'https://raw.githubusercontent.com/scgbern/scgbib/main/scg.bib'.input := scgbib. timeToRun := [ result := CZBibParser parse: input ] timeToRun.- result