---Title: Kanban in Lepiter---#Kanban in Lepiter- [[todo]] [[soon]]- [[projects]] [[lepiter]] [[imad]]- The idea is to have Kanban views where the cards are Lepiter notes.- Each column could correspond to a tag or comination of tags, like `todo` or `todo` + `asap`, and `done`.- When new cards are created (or updated) with matching tags, they could be automatically added to the kanban columns.- [[Q]] Do Lepiter notes have timestamps?- The priority and position of cards could be stored in the kanban.- If a Kanban is stored in a note, the positions could be stored as party of the note. (Need a new subclass of {{gtClass:name=LePage}}?)- If a card is dragged to a new column, should the tags be automatically updated?- For drag and drop, see[Stefan Eggermont's prototype](https://github.com/StephanEggermont/GToolkitExperiments)    - See the [video on twitter](https://twitter.com/StOnSoftware/status/1375509060578013185?s=20&t=weCluonRgEIWVKIAPsPWgw)    - DTPaneCreatingReorderingHandler new fittingColumns- See also the [[IMAD]] project for the use of queries over tags.- [[AC]] says the hard part is to program the widgets. Embedding afterwards is easy.- #Other tools    - Mircea suggested to look at [Obsidian](https://obsidian.md) as a markdown based note manager.    - It also seems to have a graph visualization of pages.- #Check out Ellis Harris' workcloud stuff    - See Discord GT demos channel.
He is working on using tags to organize and track tasks.    - Word Cloud

https://discord.com/channels/729445214812504107/735949717049049129/1000972928281739324- #Queries    - Query a db for pages matching a tag.
Ask a page or db for its links or tags.
A tag is just a link without whitespace- #Views    - A query returns a set of pages.

List pages.

Tag by page number column view.
List tags with total pages, and further columns for numbers of pages with n tags.
Max n is the max # tags.
Clicking on a row generates a new query restricted to pages with that tag.

Lattice view. 
(What is the FSA algorithm?)
Lattice of nodes with just those tags.
Each level corresponds to N tags. (Bottom is 0 tags; top is all tags?)
Size of node represents number of pages with just those tags.

Which tags are interesting? Those with a min # pages? Those that appear in combination with other tags?
Some tags represent process state (todo, done) others represent the kind of task (feature, bug).

Kanban view. 
Each column is a query (eg: tag & tag & ~tag).
To configure: order of columns, and order of cards within columns.
Moving a card to a different column should cause tags to be added or removed to match queries.
[[Q]] Is this easy to compute?

Mindmap view.
Show graph starting from some page.
How to map graph to a MM tree? Which are the links to highlight?- #Use FSA to organize Lepiter tags as a lattice    - Tree-like lattice pruning away empty branches at the bottom. 
Could be used to infer partial order of tag sets a la FCA lattices. 

Check out Liechti's thesis and slides for seminar and SMA. 

Used to have an implementation of Sets as Big numbers.
Seems to have been lost in the bitbucket of time.- #TreeMaps    - Reading STM article.

Can we use TMs to display the content of a lepiter database?
Higher-level nodes are tags.

TMs are good for comparing size, but not so much structure.

How can a lattice be approximated? Where to cut the lattice?