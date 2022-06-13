# Microsoft_Oauth

## Installation
1.First clone the repository and build a virtual environment. 

  `python-m venv env`
 
 2.Activate the environment
 
 `source env/bin/activate`
 
 3.Install the requirements using below command
 
 `pip install -r requirements.txt`
## Integration of app for Microsoft and other API functions

This application has an integration with Microsoft AAD to sync calendars etc. Please use the following steps to register the application.

 1. Go to https://aad.portal.azure.com/
 2. Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**
 ![enter image description here](https://docs.microsoft.com/en-us/graph/tutorials/python/tutorial/images/aad-portal-app-registrations.png)
 4. Select **New registration**. On the **Register an application** page, set the values as follows.
	 - Set  **Name**  to  `CRS`.
	 - Set  **Supported account types**  to  **Accounts in any organizational directory and personal Microsoft accounts**.
	 - Under  **Redirect URI**, set the first drop-down to  `Web`  and set the value to  `http://localhost:8000/callback`.
	![enter image description here](https://docs.microsoft.com/en-us/graph/tutorials/python/tutorial/images/aad-register-an-app.png)
4. Select **Register**. On the **CRS** page, copy the value of the **Application (client) ID** and save it, you will need it in the next step.
![enter image description here](https://docs.microsoft.com/en-us/graph/tutorials/python/tutorial/images/aad-application-id.png)
5. Select **Certificates & secrets** under **Manage**. Select the **New client secret** button. Enter a value in **Description** and select one of the options for **Expires** and select **Add**.
![enter image description here](https://docs.microsoft.com/en-us/graph/tutorials/python/tutorial/images/aad-new-client-secret.png)
7. Copy the client secret value before you leave this page. You will need it in the next step.
	![enter image description here](https://docs.microsoft.com/en-us/graph/tutorials/python/tutorial/images/aad-copy-client-secret.png)
8.  Create a new file in the root of the project named  `oauth_settings.yml`, and add the following content.
     ```
    app_id: "YOUR_APP_ID_HERE"
    app_secret: "YOUR_APP_SECRET_HERE"
    redirect: "http://localhost:8000/callback"
    scopes:
      - user.read
      - mailboxsettings.read
      - calendars.readwrite
    authority: "https://login.microsoftonline.com/common"
    
    ```
    
9.  Replace  `YOUR_APP_ID_HERE`  with the application ID from the Application Registration Portal, and replace  `YOUR_APP_SECRET_HERE`  with the password you generated.


## Run the project
1.Migrate all the migration using:

`python3 manage.py migrate`

2.Run the server using the following command:

`python3 manage.py runserver`
