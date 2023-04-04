---Title: Pharo Days notes---#Pharo Days notes- [[randomnote]]- See the [Pharo Days schedule](https://days.pharo.org/#schedule).- # Day 1    - 2022-03-03 INRIA Lille- # Pharo 10 (Stef)    - Fluid class syntax uses cascades so unneeded parameters can be left out.
New implementation of refactorings will replace old one.- # Pharo 11 (possible points)    - Ephemerons
Concurrency
Multi windows
HDPI (?)
Pakbot remodularization    - *Pharo 11 high priority*
VM memory management for large images (Lifeware contract)
New image format (authenticated images)- # Pharo VM (Polito/Tesone)    - Support for ARM64 (many platforms)
Added lots of tests
Using concolic testing/execution to ensure that interpreter and JIT compiler do the same thing
Improved Slang compilation
New block closures
All socket implementations are now unified
Pure FFI implementation allows all plugins to be moved to FFI

Permanent Space
Permanent Objects that waste time for GC
Should be mostly ignored, but need to be checked to avoid memory leaks

New image format
Support multiple object spaces
Extensible to new metadata
Support memory mapping
Based on directories/bundles (like MoacOS package)
Metadata should be user and machine readable (STON?)

NB: all memory optimizations are thrown out when you save the image, because the image format is from 20+ years ago; forces reoptimization effort.- # Restore Database    - [John Aspinall](https://github.com/rko281)    - Originally built for Dolphin Smalltalk in early 2000s    - Revived as Open Ssource in 2017    - [ReStore for Pharo 2019](https://github.com/rko281/ReStoreForPharo)        - Shared codebase for Pharo & Dolphin        - Can use multiple RDBs underneath (eg SQLite)        - Generates SQL        - Any class can implement reStoreDefinition mapping slots to fields
Uses Collection API to hide SQL
Uses a prototype object to capture the message sends in the query block to generate SQL (may generate an error if not translatable)        - NB: In the demo used [DB browser for SQLite](https://sqlitebrowser.org)        - Doesn't create indices of foreign keys — must add these manually to the DB- # Expressive Systems    - Erik Stel / Jonathan van Alteren (Object Guild)
Business application framework
Inspired by Object Thinking (David West), Naked Objects, RDD/BDD
“Human-centered software”
Architecture: Objects and Presenters on server side; Views on client side
Views are HTML WebComponents
running in a tiny (200kb) ST image (Code Paradise built with Pharo Bootstrap)
Uses SqueakJS VM
Every browser (tab) has a single image instance
* TODO : check out Dawson's Naked Object demo (translate to GT?)
Demo: can introduce entities; drag and drop them to fields of other entities- # PHEPS — Pharo Enhancements    - See [pharo-project/pheps](https://github.com/pharo-project/pheps).- # Day 2    - 2022-03-04- #Spec2    - [Esteban Lorenzano](https://github.com/estebanlm) on Spec2    - See [https://github.com/pharo-spec/](https://github.com/pharo-spec/)    - Quick, make me this app! (Spec2)
Esteban Lorenzano    - Subclass {{gtClass:SpApplication}}.    - implement start method
Subclass SpPresenter or SpModel
Or use traits SpTModel

[[Q]] Would it make sense to adapt spec to GT (so spec apps will run with Bloc)?    - Athens is built-in vector graphics package.- # How to customize Pharo Tools    - [Milton Mamani Torres](https://github.com/akevalion)    - Running example: adding a new dependency visualization for Baselines    - Start: prototype script of 85 lines. Convert to a project        - See [github.com/akevalion/BaselineMap](https://github.com/akevalion/BaselineMap)    - Add this to the Calypso browser, Inspector etc.- #Debugger tools and infrastructure    - [Steven Costiou](https://kloum.io/costiou/en/index.html)    - How debug how the debugger is opened? (Use the GTDebugger to debug this ...)    - Problem: many different ways to open the Morphic debugger — hard to understand; hard to extend and leverage.    - Now every debugger must use the trait {{gtClass:TDebugger}}.    - Shows how to implement a custom debugger that captures and freezes, then terminates a debug session to inspect it post mortem.    - Sets the priority high to override other debuggers.        - NB: If a debugger fails, the next highest priority debugger will be invoked.    - Overrides {{gtMethod:name=TDebugger class>>handlesContext:}} so it only will be triggered for the package of interest.- #APart Form Editor    - [Pavel Krivanek](https://github.com/pavel-krivanek).    - [APart](https://github.com/bauing-schmidt/APart) is a UI Builder for Pharo.    - [tweet with screenshot](https://twitter.com/pavelkrivanek1/status/1369553244138184704)    - Serializes to JSON.    - Leverages Magritte!- #Method trackers    - Massimo Nocentini    - [Slides](https://bauing-schmidt.github.io/MethodTracker/PharoDays22.slides.html#/)    - Yet another instrumentation tool for debugging, tracing and inspecting execution flow.    - Inspired by [method proxies](https://github.com/pharo-contributions/MethodProxies).    - Demo showing the expansion of `16 factorialRecursive` (non-tail-recursive version).    - (For me hard to see what the tool does beyond the regular debugger. What is the central idea?)- # Configurable Roassal Layouts in PDM    - Richard Uttner, [Projector Software](https://projector.de/impressum-en.html)        - Also works for [Schmidt ingenieurbuero fuer Bauwesen](https://www.bauing-schmidt.de/?page_id=245#)    - Migrated old business app to tree layouts with Roassal. Challenges to display lots of data in a scalable way.- #Client-Server Development with PharoJS    - [Noury Bouraqadi](https://github.com/bouraqadi) (work together with [Dave Mason](https://sarg.ryerson.ca/dmason/))    - [PharoJS github repo](https://github.com/PharoJS/PharoJS)    - There is a [Smalltalk REPL](https://pharojs.org/repl) [implemented in PharoJS](https://github.com/PharoJS/WebStREPL/blob/main/README.md) .- #Using Pharo launcher from the command line    - [David Bajger](https://github.com/Bajger)    - Separate [github](https://github.com/PharoLauncherCmdLine/CommandLineLauncher) repo.    - Can launch or kill an image; send messages.- #Scriptable debugging    - [Maximilian Willembrinck](https://github.com/maxwills)    - Demo with [github demo repo](https://github.com/maxwills/PharoDays2022).    - How to get debugging information without opening the debugger?    - Running examples:    - Q How many times is OrderedCollection>>#add: called in our app?        - Shows conditional breakpoints and conditional logging.    - Q How many times is any `#add:` message sent?        - Shows instrumentation with metalinks.    - Adding a metalink:        - `(OrderedCollectiom>>#add:) ast link: metalink`    - A {{gtClass:MetaLink}}  is a spec of what to do.    - Can add metalinks to all implementers.    - Same problems solved with [MetaProxies](https://github.com/pharo-contributions/MethodProxies). (Needs to be separately loaded.)    - See examples 3 and 4 in the demo repo.    - Again, same problems solved with scriptable debuggers.    - Example: {{gtClass:SindarinDebugger}} (included in Pharo).    - Needs to be enabled (see the example script).    - Example shows how to debug without modifying the source code at all.    - Finally showing [Seeker](https://github.com/maxwills/SeekerDebugger), a new “time traveling” debugger. Can step backwards by reversing the execution.    - Load and enable seeker. Select code and open Seeker.    - Scriptable (like Sindarin).    - Also supports *querying* as opposed to scripting. Similar to SQL or LINQ, using a collections style API.    - More concise than scripting interface.    - Returns all the matching messages — can then time travel to that point in the execution!