#### Date: 06/03/2017

#### Description: This document explains the code flow of view Account first time.

#### Step 1:

Function **viewAccountFirsttime** will be called first from index.php to controller page.

- This function calls when user is logged in for first time. if user logins for first time it will redirect to account, if user login from second time it will redirect to landing page.
- Function **getUserID** will get the login user id from controller page and will be redirected to action page. 
- In action page, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action page to controller page.

#### Step 2:

- Function **createAccountListInputVO** will create the object array for input data to send parameters. 
- The parameters are module, action and userid. This function will be redirected from controller to action page.
- Here in action page, function takes the input data and prepares the input value object for WSDL from action page to AccountData.php page.
- Here function **createAccountListInputVO** from action page will be redirected to AccountData.php page which gets the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
- Result returns the account list value object array to controller page and will be passed to function **getAccount**.

#### Step 3:

- Function **getAccount** will get the list value object array in controller page and will be redirected to action page.
- The parameters list array passed are session id, query and module name.
- In action page, function will call the wsdl call for getting the account details.
- First, it will set the wsdl client by function **setWSDLHandle** from AccountWS.php page which is included in action page.
- Next, function **getListArray** will get the account details by ws call **get_entry_list_acc**.
- Parameters passed for above function are session id, module name, query, orderby, offset, max result, deleted.
- Result returns the account list array to controller page.

#### Step 4:

- Function **createAccountListDataObjectArr** will create a data object array for data in controller page and redirected to action page.
- The parameters passed will be account list array.
- Will create the object array for result of wsdl from action to AccountData.php which is included in action.
- From action, Function **createAccountListDataObject** will be redirected to AccountData.php which will get the values from input array and sets the values for list data object. 
- Result returns the account object data array to controller page.

#### Step 5:

- if **$createdby == 1**, function **showAccountFirsttime** will be called from controller page and will be redirected to action page which takes the input data object and gives to the account view to dispaly the account details for first time login.
- Input parameters will be account details like name,location, experience, email.
- From action page, function **showAccountFirsttime** will be redirected to AccountView.php will be used to assign the variables for tpl page and assign the value object array to variable and redirect to account view which displays the first time login form tpl page.
- The display tpl page will be in views -> AccountFirsttimeLogin.tpl in views folder.
- For second time login, the header location will be redirected to landing page.


