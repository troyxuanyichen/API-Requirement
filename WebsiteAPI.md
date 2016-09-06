**API Documentation**
========================
Note:  


pledgeuserinfo/(POST)
-------------
To add pledge user.  

**HttpHeader:** null     
**Content-Type:** "application/json"  
**Request Body:**
   
	{
      "firstName": "Xuanyi",
      "lastName: "Chen",
      "email": "troychenehehe@bu.edu",
      "gender": "Male",
      "age": "18",
      "purposeOfUse": "For Test Only"
    }
    
**Response Body:**

	response: 
	{
		"statusMsg": "Pledge success."
	}
	
	

pledgeuserinfo/(GET)
-------------
To get all the pledge user.  

**HttpHeader:** null     
**Content-Type:** null  
**Request Body:** null  
**Response Body:**

	response: 
	{
		  "Pledge User": 
		      [
		          {
		              "firstName": "Xuanyi",
                      "lastName": "Chen",
                      "email": "troychenehehe@bu.edu",
                      "gender": "Male",
                      "age": "18",
                      "purposeOfUse": "For Test Only"
		          }
		      ]
	}
	

subscribeusers/(POST)
-------------
To add subscribe user.  

**HttpHeader:** null     
**Content-Type:** "application/json"  
**Request Body:**
   
	{
      "firstName": "Xuanyi",
      "lastName: "Chen",
      "email": "troychenehehe@bu.edu"
    }
    
**Response Body:**

	response: 
	{
		"statusMsg": "Subscribe success."
	}


subscribeusers/(GET)
-------------
To get all the subscribe user.  

**HttpHeader:** null     
**Content-Type:** null  
**Request Body:** null  
**Response Body:**

	response: 
	{
		  "Subscribe User": 
		      [
		          {
		              "firstName": "Xuanyi",
                      "lastName": "Chen",
                      "email": "troychenehehe@bu.edu"
		          }
		      ]
	}
	
	
usermessage/(POST)
-------------
To leave message.  

**HttpHeader:** null     
**Content-Type:** "application/json"  
**Request Body:**
   
	{
      "userName": "Xuanyi",
      "email": "troychenehehe@bu.edu",
      "subject": "service",
      "msgBody": "I am disappointed."
    }
    
**Response Body:**

	response: 
	{
		"statusMsg": "Leave message success."
	}


usermessage/(GET)
-------------
To get all the user message.  

**HttpHeader:** null     
**Content-Type:** null  
**Request Body:** null  
**Response Body:**

	response: 
	{
		  "User message": 
		      [
		          {
		              "userName": "Xuanyi",
                      "email": "troychenehehe@bu.edu",
                      "subject": "service",
                      "msgBody": "I am disappointed."
		            }
		        ]
	  }
	



	
