#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **viewAccountFirsttime** will be called first from index.php to controller.
- This function calls when user is logged in for first time. if user logins for first time it will redirect to account, if user login from second time it will redirect to landing page.
- Function **getUserID** will get the login user id from controller to action. 
- In action, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action to controller.

#### Step 2:

- Function **createAccountListInputVO** will create the object array for input data to send to WSDL from controller to action.
- In action, function **createAccountListInputVO** will get the input array values and sets the values for list data.
- It prepares the query and required input to create account and result will be returned from action to controller.

#### Step 3:

- Function **getAccount** will call the WSDL to get the account details.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getListArray** in AccountWS.php will send data to wsdl for getting the account list using **get_entry_list_acc**.
- The result will be returned from action to controller.

#### Step 4:

- Function **createAccountListDataObjectArr** will create the object array for data list from controller to action.
- Will create the object array for result of wsdl from action to AccountData.php.
- Function **createAccountListDataObject** in AccountData.php will get the values from input array and sets the values for list data object and returns the account object data array to controller.


#### Step 5:

- if **$createdby == 1** function **showAccountFirsttime** takes the input data object and gives to the account view to disply the account details for first time login.
- In action, function **** from AccountView.php will be used to assign the variables for tpl page and assign the value object array to variable and redirect to account view first time login form tpl page.
- The display tpl page will be in views -> AccountFirsttimeLogin.tpl.
- For second time login, the header location will be redirected to landing page.


