---Title: GT Keyboard shortcuts---#GT Keyboard shortcuts- [[howto]] [[lepiter]]- [[Q]]**How can I see what the currently active shortcuts are?**    - ctrl-opt-shift-click (eg. within a snippet), click to the next pane, and select the *Shortcuts* tab.- [[Q]] **How do I debug a button? How do I drill into a GUI Element?**    - See the [video clip on Discord](https://discord.com/channels/729445214812504107/735945764597006466/929117535599734845).    - - CTRL-ALT-SHIFT-click on the button
- Click on the button element
- Select the `Action` tab
- Select the browse button for the code
- Close the current view to go to the browse pane- [[Q]] **What is the Keyboard shortcut to indent a snippet (add it to the snippet above)?**    - cmd+]
cmd+[ unindents- [[Q]] **How do I zoom the UI?**    - You can zoom a Lepiter page with cmd+= and cmd+-.    - You can also scale the whole UI (see *How to scale the UI* in the GT Book).    - You can also run this script:    - GtWorld
	spaceWithId: GtWorld defaultId
	do: [ :theWorld | theWorld root properties fontSizeEm: 1.1 ]- #More to add- Command enter gives you a snippet of the same kind- Command-SHIFT-enter gives you a menu- Shift-Opt-arrow will move a snippet up or down