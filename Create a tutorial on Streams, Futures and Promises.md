---
  ^ aVariable ifNil: [ aVariable := [ NeoJSONObject fromString: (Znclient new get: 'https://a.big.json.response') ] asAsyncFuture await ]
  <gtView>
  ^ aView explicit
    title: 'Raw Data';
    priority: 1;
    stencil: [
    	BrAsyncWidget new
	    matchParent;
	    stencil: [ self expensiveComputation wait.
	      (self expensiveComputation 
  ]