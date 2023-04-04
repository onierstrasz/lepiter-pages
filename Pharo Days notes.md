---
New implementation of refactorings will replace old one.
Concurrency
Multi windows
HDPI (?)
Pakbot remodularization
VM memory management for large images (Lifeware contract)
New image format (authenticated images)
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

NB: all memory optimizations are thrown out when you save the image, because the image format is from 20+ years ago; forces reoptimization effort.
Uses Collection API to hide SQL
Uses a prototype object to capture the message sends in the query block to generate SQL (may generate an error if not translatable)
Business application framework
Inspired by Object Thinking (David West), Naked Objects, RDD/BDD
“Human-centered software”
Architecture: Objects and Presenters on server side; Views on client side
Views are HTML WebComponents
running in a tiny (200kb) ST image (Code Paradise built with Pharo Bootstrap)
Uses SqueakJS VM
Every browser (tab) has a single image instance
* TODO : check out Dawson's Naked Object demo (translate to GT?)
Demo: can introduce entities; drag and drop them to fields of other entities
Esteban Lorenzano
Subclass SpPresenter or SpModel
Or use traits SpTModel

[[Q]] Would it make sense to adapt spec to GT (so spec apps will run with Bloc)?