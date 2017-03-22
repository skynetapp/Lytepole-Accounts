#### Date: 07/03/2017

#### Description: This document explains the code flow of edit account.

#### Step 1:

Next action in index.php is to call function **editAccount** from index.php to controller which will edit the account data of login user.

- Function **getUserID** will get the user id by calling wsdl from controller to action.
- In action ws client connection will be set and function **getUserID** will be called from AccountWS.php.
- In AccountWS.php, the parameters will be passed to ws call **get_user_id** and return the result to action page.
- From action, result will be redirected to controller.

#### Step 2:

- Function **createAccountListInputVO** will create the object array for input data to send parameters. The parameters are module,action and userid. This function will be called from controller to action.
- Here in action, function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- Here in AccountData.php, function **createAccountListInputVO** which is included in action will get the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
- Result returns the account list value object array to controller and will be passed to function **editAccountDetails**.

#### Step 3:

- Function **editAccountDetails** will edit the account details from controller to action.
- Parameters will be name, location, experience, email,account id.
- In action, first wsdl client connection will be set by function **setWSDLHandle** from AccountWS.php.
- In action, function **editAccountDetails** will be called from AccountWS.php will create parameters for wsdl using object.
- To wsdl client call **set_entry**, parameters will be passed and the result will be returned to account detail array. 
- Header location will be redirected to detail view of accounts.
