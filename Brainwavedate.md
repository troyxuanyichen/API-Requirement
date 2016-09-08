**Brainwave Data**
========================
Note:  
Name of database: Brainwavedata  
Name of collection: brainwave  
One user may take 30 minutes to finish a session.  
Session is not bound to game.  
Maximum 40 sessions.  
Data package will be sent every minute.  

-------------
**Brainwave difinition:**

Datapackage: 

	[
	Attention level: 1 int per second.  
	SMR : 

		{
      	"SMR0": DATATYPE.[DOUBLE],
      	"SMR1: DATATYPE.[DOUBLE],
      	"SMR2: DATATYPE.[DOUBLE]
    	}
    
	Beta: 1 double per 1/2 second.  
	Theta: 1 double per 1/2 second.  
	Session number: 1 int, indent every session.
	]
	
Time: timestamp.  
