---Title: How to contribute to Pharo---#How to contribute to Pharo- [[randomnote]]- See this nice [Discord post](https://discord.com/channels/223421264751099906/299884664795955200/953420692756525107)    - Iceberg seems very complicated and quite buggy.  Is it trying to do too much?
 
astares — Yesterday at 11:33 PM
A standard Pharo USER (non-contributor) usually can ignore them or use the "Forget repository" action from the context menu. So if you work on own stuff you can usually ignore them as you build projects on top of Pharo.

But they make absolutely sense when you are a CONTRIBUTOR to Pharo itself - because usually you have an own fork from the different repos (Pharo, Iceberg, Spec2, ...) and then just connect to work with them (edited)
[11:34 PM]
Lets take the first entry for example "pharo"
Image
[11:36 PM]
The official Pharo repo is at:   https://github.com/pharo-project/pharo

Usually you use the "Fork" action button on Github page to fork into an own git repo. For me this is https://github.com/astares/pharo
So once I downloaded a fresh image I use the "Repair" function:
[11:36 PM]
Image
[11:41 PM]
to clone from my fork locally (or connect to a local clone if I still have it on the disk). Then I can make own branch(es) for each issue to fix based on the latest commit in default branch "Pharo10" and once my fix is ready it can get commited via Iceberg and pushed back to github. Then it can be submitted as a Pull Request (PR) and when reviewed and accepted it will be merged into the official Pharo repo. 

Thats the usual git workflow when you contribute using Iceberg.
[11:45 PM]
The repos one needs to fork and send PR against are:
- https://github.com/pharo-project/pharo
- https://github.com/pharo-spec/NewTools
- https://github.com/ObjectProfile/Roassal3
- https://github.com/pillar-markup/Microdown
- https://github.com/pillar-markup/BeautifulComments
- https://github.com/pharo-vcs/iceberg
- https://github.com/pharo-vcs/libgit2-pharo-bindings
- https://github.com/pharo-vcs/tonel
in the order included in Iceberg.