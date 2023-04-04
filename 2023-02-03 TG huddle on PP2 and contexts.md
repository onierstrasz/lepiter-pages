---Title: 2023-02-03 TG huddle on PP2 and contexts---#2023-02-03 TG huddle on PP2 and contexts- Jan built PP2 to address two needs, performance and bounded seas.    - For the performance he had to reimplement PP to separate the parser tree from the actions.    - By sending `optimize` to a PP2 parser, a new compiled parser is generated that is 5-7 x faster (compare to SmaCC, which is 10 x faster than PP1).- Discussion about how to handle indentation. I proposed to generate DEDENT tokens, but TG says you should just keep track of indentation in the context (see {{gtClass:name=PP2Context}}).    - In PP2 use `>=>` instead of `==>` to get the context as an argument.    - #>=> gtSenders- There is a YAML parser in PP1. See [](https://github.com/moosetechnology/PetitParser).    - See [](https://github.com/moosetechnology/PetitParser/blob/5bdaf9f36793bf355e863c1accfbcc6162a6b034/src/PetitYAML/PPYAMLGrammar.class.st#L395) for how it is used.- To load Moose: (NB: just proceed if there is an error)    - Metacello new
   baseline: 'PetitParser';
   repository: 'github://moosetechnology/PetitParser/src';
   load.    - PPYAMLGrammar parse: 'verbose: false
workspace: /Users/oscar/Desktop/GT/tmp1034/glamoroustoolkit
app_version:
  major: 0
  minor: 4
  patch: 10
image_version:
  major: 0
  minor: 8
  patch: 2446
image_name: GlamorousToolkit
image_extension: image
image_seed:
  Url: "https://dl.feenk.com/pharo/Pharo10-SNAPSHOT.build.521.sha.14f5413.arch.64bit.zip"
'- Next rename the class to PP2YAMLGrammar.    - Change superclass to PP2CompositeNode    - Refactor ``@any asParser to asPParser    - Change #eof asPparser to #endOfLine asPParser    - There are some additional packages that need to be loaded ....    - Additional methods have to be added to PP2Context and PP2parser    - ... long process of migrating various packages, classes and methods, and adapting them to PP2.    - Commit to gt4petitparser2- PP2YAMLGrammar parse: 'foo'