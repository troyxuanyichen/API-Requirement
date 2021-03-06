**API Documentation**
========================
Note:  
Add password in the sigup API.  
Please delete all the statusCode in all API's.  
Please watch out for the httpHeader. For example, signup/login will not give you any token in the header.  
Change "x-access-token" to "authorization".  
Add deleteAccount and activeAccount api, delete the request body of logout  
Put profile no longer support upload avatar  
Change the key in response of 'get avatar' to 'profile'  
Correct content-type of 'put avatar'  
Change the method of 'upload avatar' from 'put' to 'post'  
Post avatar will return the url  
Add new api 'fast delete' for debug use only  
Add the 'quick login' api  
Important: prepend 'JWT ' to the jwt token  
Add 'users' to all the router that is ralated to user  
Add the 'add relationship' api  
Change the method of 'verify/:token' from put to get  
Change the method and url of resend email  
Add 'check identity' api  
Add relationship now requires trainee password  

users/password(PUT)
-------------
To change the user's password.

**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"  
**Request Body:**
   
	{
      "oldPwd": "oldPassword",
      "newPwd: "newPassword"
    }
    
**Response Body:**

	response: 
	{
		"statusMsg": "..."
	}

users/activateaccount(PUT)
-------------
To activate user's account  

**Content-Type:** "application/json"  
**Request Body:**   

	{
      "email": "asdfgh@gmail.com"
    }
    
**Response Body:** 

	response:
	{
		"statusMsg": "..."
	}

**Tips:** the user will use the original password to login  

users/account(PUT)
-------------
To inactive user's account and delete all the token belongint to the email  

**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"  
**Request Body:** *null*    
**Response Body:** 

	response:
	{
		"statusMsg": "..."
	}

**Tips:** the account can be activate later  

users/fastdelete(DELETE)
-------------
Fast delete user account and token in debug. Use with care.  
**Content-Type:** "application/json"   
**Request Body:**  

	{
      "email": "asdfgh@gmail.com"
    }

**Response Body:** 

	response:
	{
		"statusMsg": "..."
	}
**Tips:** delete all profile and token related to the email address.  

users/forgot(PUT)
-------------
User forget his/her password.  
**Content-Type:** "application/json"   
**Request Body:**  

	{
      "email": "asdfgh@gmail.com"
    }

**Response Body:** 

	response:
	{
		"statusMsg": "..."
	}
**Tips:** send an email with a random generated temporary password to the email address provided.  

users/checkidentity(GET)
-------
Check if the user is a guardian or trainee  
**Content-Type:** "application/json"   
**HttpHeader:** "authorization": token  
**Request Body:** *null*  
**Response Body:**  

	response:
	{
		"statusMsg": "..."
	}
**Tips:** send an email with a random generated temporary password to the email address provided. If statusMsg = 1, the user is a guardian; if statusMsg = 0, the user is a trainee.  

users/logout(DELETE)
-------
User logout.  

**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"   
**Request Body:** *null*    
**Response Body:** 

	response:
	{
		"statusMsg": "..."
	}
**Tips:** App will send you the email in request.body so that server can delete its token. Or, you can just check the token. It's up to you. **However**, if the network is not working right now, app will STILL log out, which means you might not know when the user did log out. But it's not a problem. When this user log in the next time, you should give him another token and replace the previous one.

 
users/profile(PUT)
--------
Update one user's profile excluding the email.  
 
**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"   
**Request Body:**  

	  {
		"firstName": "newFirstName",
		"lastName: "newLastName",
		"gender": "f",
		"birthday": "08/08/2009",
		"phone": "6178169142",
		"other": "somethingElse"
	  }
**Response Body:**

	response:
	{
		"statusMsg": "..."
	}
	
**Tips:** Only the following fields can be changed through this method: firstName, lastName, gender, birthday, phone, other. Password has to be changed in forget password. Email cannot be changed once register is finished.  


users/profile(GET)
-------------
Fetch one user's profile including avatar.  

**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"   
**Request Body:** *null*  
**Response Body:** 

	response:
	{
		"firstName": "newFirstName",
		"lastName: "newLastName",
		"gender": "f",
		"avatar" : "https://www.brainco.tech/img.jpg",
		"birthday": "2014/11/22",
		"phone": "6178169142",
		"other": "somethingElse"
		"statusMsg": "..."
	  }

users/login (POST)
------------
User log in. Return token.
      
**Content-Type:** "application/json"  
**Request Body:**  

	{
      "email": "troychen@bu.edu",
      "password: "HashedAtLeastSixDigit"
    }
**Response Body:**

	response:
	{
		"token" : "asjkhdbfkuyawsegbfkasdbflhsd";
		"statusMsg": "..."
	}
**Tips:** The user will get a token the first time it logs in. When the user reopen the app, the token will be validated first. If it's still valid, the user will be immediately logged in, otherwise, the user will be asked to enter login info again. 


users/signup(POST)
-------------
  
**Content-Type:** "application/json"  
**Request Body:**  

	{
		"email" : "asdfgh@gmail.com",
		"password": "hasedPassword",
		"firstName": "xuanyi",
		"lastName: "chen",
		"gender": "m",
		"birthday": "2014/11/22",
		"avatar": "Binary675tuygjhbkyt76dtjcghvgt76riftyvhjbhiyotfuvhb",
		"phone": "6178169142",
		"other": "OtherInfo",
		"isGuardian": 0
	}

 **Response Body:**

	response:
	{
		"statusMsg": "..."
	}
**Tips:** Avatar, gender, other are not required. Other fields are required.Other information cannot exceed 150 characters. This api will send the acivate email to the user provided. Default value of 'isGuardian' is 0 which means the user is not a guardian.    


users/avatar(POST)
------------
Update one user's avatar.  
  
**HttpHeader:** "authorization": token  
**Content-Type:** "multipart/form-data"   
**Request Body:** 

	{
		"avatar": "Binary675tuygjhb76rudtjcghvgt76riftyvhjbhiyotfuvhb"
	} 
**Response Body:**

	response:
	{
		"avatar": "https://www.brainco.tech/img.jpg",
		"statusMsg": "..."
	}
**Tips:** The server will receive binary data and upload the picture to s3 storage.


users/avatar(GET)
------------
Fetch one's avatar.  
**HttpHeader:** "authorization": token  
**Content-Type:** "application/json"   
**Request Body:** *null*  
**Response Body:**

	response: 
	{
		"avatar": "https://www.brainco.tech/img.jpg"
		"statusMsg": "..."
	}


users/quicklogin(POST)
------------
renew the token for the user  
**HttpHeader:** "authorization": token  
**Request Body:** 

	{
		"token": "asjkhdbfkuyawsegbfkasdbflhsdOld"
	} 
**Response Body:**

	response:
	{
		"token": "asjkhdbfkuyawsegbfkasdbflhsdNew",
		"statusMsg": "..."
	}
**Tips:** Require token and re-sign a new token

user/resend(POST)
------------
resend the activation email  
**HttpHeader:** "authorization": token  
**Request Body:**

	{
		"email": "troychen3@bu.edu"
	}
**Response Body:**

	response:
	{
		"statusMsg": "..."
	}
**Tips:** This api can only be called when register


user/verify/:token(GET)
------------
activate the user account using the link sent by mail  
**Request Parameter:** token  
**Response Body:**  

	response:
	{
		"statusMsg": "..."
	}
**Tips:** Require token and re-sign a new token

user/addrelationship(POST)
------------
Guardian add one of the trainee to their relationship  
**HttpHeader:** "authorization": token  
**Request Body:**

	{
		"traineeEmail": "troychen3@bu.edu",
		"traineePassword": "qwedfghjk43211"
	}
**Response Body:**

	response:
	{
		"statusMsg": "..."
	}
**Tips:** This api can only be called when the user is a guardian. A guardian can only add one trainee once a time, require token  

users/guardians/trainees(GET)
-------
Guardian find trainees

**HttpHeader:** "authorization": token   
**Content-Type:** "application/json"   
**Request Body:** *null*    
**Response Body:** 

	response:
	{
		"traineesList": 
		{
			"trainee1@gmail.com",
			"trainee2@gmail.com"
		}
	}
**Tips:** Call this api when a guardian user login, return the list of trainees the user is connected to. If no trainee is connected, an empty traineesList will be returned.  


**Requirements of data:**
=========================
**password:** should be at least 6 digits, do not encode;  
**firstName:** should be less than 100 characters;  
**lastName:** should be less than 100 characters;  
**email:** should be a good formatted email, eg, hehechen@bu.edu;  
**gender:** should be single character, lower case 'm' or 'f';  
**birthday:** should be like 1991/11/12;  
**avatar:** should be binary code, max 65,535 bytes;  
**phone:** should be numbers only, more than 6 digits, max 20 digits;  
**other:** should be text, max length 65,535 characters  

