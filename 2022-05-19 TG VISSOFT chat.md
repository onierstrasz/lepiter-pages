---
clonerSignals := GtRlClonerSignalsLogReader  readFrom:  loadingLog.
baselineCloneEvent := GtRlClonerBaselineEvent fromSignals: clonerSignals.
loaderSignals := GtRlLoaderSignalsLogReader readFrom:  loadingLog. 
actionEvents := GtRlLoaderEventsGroup fromSignals:  loaderSignals.
consolidatedEvent := GtRlLoadedConsolidatedBaselineEvent new
	initializeFrom: baselineCloneEvent.
consolidatedEvent addLoaderEvents: actionEvents.
   baseline: 'UhmoWithoutGT';
   repository: 'github://feenkcom/uhmo/src';
   load.