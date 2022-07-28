# Creating API Collection and Documentation using Postman

### **What is Postman?**
Postman is an application used for API testing. It is an HTTP client that tests HTTP requests, utilizing a graphical user interface, through which we obtain different types of responses that need to be subsequently validated

---------

### **Previously we have:**

- Azure Active directory account.   [*Click here*](https://github.com/PatternsTechGit/PT_AzureAD_Setup) to learn more about it. 

- From this Azure AD account we have it's **Tenant id**
![](/images/1.png)

- We have registered our API in it and we have **Client ID** from it.
![](/images/2.jpg)

- We have also generated **Client's Secret ID** to access graph API
![](/images/3.jpg)

------------

### **In this exercise we will create**

- We will access user's profile picture using **Azure AD Graph API** and **Access Token**

- We will generate API Documentation using **Postman**
- Export the collections

------------------

### **STEP : 1**

- Login to postman using an existing account or [create new account](https://identity.getpostman.com/signup?email=)

- Create new collection.

![](/images/4.jpg)

- Creating Postman Environments 
 
    **What are Postman Environments?**

    Environment is a group of variables that we can use in a Postman request. By creating Environments for production, testing, staging and so on, we can run the same URL in various Environments.

    To add new environment, click on the eye icon and select *Add*.
    ![](/images/5.jpg)

- Give name to your environment and add variables. 
    
    In our case we need *Tenant-ID , Client-ID* and *Client-Secret* for future process. So we will get these information from our Azure Account and add it to our environment's variable.
    ![](/images/6.jpg)

- Now we will *Add a **POST** request* to fetch the token. 

    - To do this, click on *Add New Request*
    - Make sure you have selected the right environment
    - Add the URL by adding  *Tenant ID* variable in URL to fetch the token. 
    
    ![](/images/7.jpg)

- Setup 4 things in the *Body* section

    - Make sure you are in body section 
    - The type will be **x-www-form-urlencoded**
    - Setup 4 items 

         1) Grant Type ( That will be gard coded )
         2) Client ID ( From the variables we created)
         3) Client Secret ( From the variables we created)
         4) Resources ( hard coded value )

    ![](/images/8.jpg)

- Now we will click 'Send' to call, it will give the access token as shown below.
![](/images/9.jpg)

- Now we will add another request to Get the list of Users.

    - We will use same procedure as above, select GET and use this URL https://graph.microsoft.com/v1.0/users for this request.
    ![](/images/10.jpg)
    - Now in the headers section of this call we will add **Authorization**.
    - In authorization we will first write **Bearer** keyword and then paste the Access Token we got from POST call
    ![](/images/11.jpg)

    - When we run this call. It will give us all users details. We will copy ID of any user to get the picture of that user.
    ![](/images/12.jpg)

- To get the profile picture of that user we will create another GET call.

    - In the newly created call we will pass **User ID** we copied in last step in the following url https://graph.microsoft.com/v1.0/users/{{UserID}}/photo/$value
    - We will also pass the same **Access Token** in headers Section 
    - This process will return User profile picture to us
    ![](/images/13.jpg)

---------------------

## STEP 2 : Generating API Documentation 

### **What is Postman Documentation and what it is used for?**
Documentation is an important part of any collection or API. Good documentation helps the people who use your collection to understand what it does and how each request works. And comprehensive API documentation lets your consumers know what endpoints are available and how to successfully interact with them.

Once you've generated documentation for your collection or API, users can view the documentation in Postman. By default your documentation is private, so only people you share a collection or API with will be able to see it. If you're creating a public API, you can publish your documentation to make it publicly available to anyone with a web browser.

To create documentation of your existing API

- Right click on API collection we created and select *View Documentation*
- On right upper corner select *Publish*.
- It will take you to a portal where you can preview your documentation before publishing and you can also edit many items like styling, colors, custom domains, etc. 
- After making all the changes select *Publish* 
![](/images/14.jpg)

- After publishing it will provide you a URL where you can see your published documentation and share it with your concerned team/individual. 
![](/images/15.jpg)

- Now our final output of documentation will look like this 
![](/images/16.jpg)

- It has all the details and we can use it for multiple purpose.
- If your team mate wants to change anything in it according to his own needs they can go to upper right corner and select **Run in Postman**
- This will direct you to open desktop or web app to Import all these tasks for further changes. 
![](/images/17.jpg)

------------------
