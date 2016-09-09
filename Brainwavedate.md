**Brainwave Data**
========================
Note:  
Name of database: Brainwavedata  
Name of collection: brainwave  
One user may take 30 minutes to finish a session.  
Session is not bound to game.  
Maximum 40 sessions.  
Data package will be sent every minute.  
Format json keys  

-------------
**Brainwave difinition:**

Datapackage: 

	[
	attentionLevel: 1 int per second.  
	SMR : 

		{
      	"SMR0": DATATYPE.[DOUBLE],
      	"SMR1: DATATYPE.[DOUBLE],
      	"SMR2: DATATYPE.[DOUBLE]
    	}
    
	beta: 1 double per 1/2 second.  
	theta: 1 double per 1/2 second.  
	sessionNumber: 1 int, indent every session.
	]
	
time: timestamp.  
