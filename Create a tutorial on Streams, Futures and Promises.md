---Title: Create a tutorial on Streams, Futures and Promises---#Create a tutorial on Streams, Futures and Promises- [[todo]] [[asap]][[gtbook]] [[newpage]]- TO DO — Streams, Futures pages for GT Book- #Discord discussions    - [GT > general 2022-09-16](https://discord.com/channels/729445214812504107/729445215341117522/1020396134616809563)    - [GT > help 2022-09-19](https://discord.com/channels/729445214812504107/736333725788274819/1021262305952018532)- #Lazy initialization with Promises    - botwhytho on [feedback channel 2022-10-04 @ 7h54](https://discord.com/channels/729445214812504107/737255889517543545/1026718959111786506)    - Speaking of async things, one pattern that I've caught myself using a lot recently is lazy initialization of slots with a promise, and that promise driving one or more views/Blelements/etc. For example:    - expensiveComputation
  ^ aVariable ifNil: [ aVariable := [ NeoJSONObject fromString: (Znclient new get: 'https://a.big.json.response') ] asAsyncFuture await ]    - Then using a `BrAsyncWidget` inside an explicit view:    - gtRawDataFor: aView
  <gtView>
  ^ aView explicit
    title: 'Raw Data';
    priority: 1;
    stencil: [
    	BrAsyncWidget new
	    matchParent;
	    stencil: [ self expensiveComputation wait.
	      (self expensiveComputation 	      	gtTreeFor: GtPhlowEmptyView new) asElement ]
  ]    - This keeps the UI snappy and things never hang, you get visual 'feedback' while waiting for view/response, you can cancel the future (but hopefully the underlying one is not cancelled so that even if you close inspector it may finish in the background to not waste the computation so next time you open it's not re-fetched under normal conditions, unclear cause haven't tested), you have computation/data cached for next time unless you need to recalculate so can set slot to nil and you can share computation amongst view/elements/other components.