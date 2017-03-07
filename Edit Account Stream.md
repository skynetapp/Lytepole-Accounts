#### Date: 07/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Next action in index.php is to call function **editAccount** from index to controller which will edit the account data of login user.

- Function **getUserID** will get the user id by calling wsdl from controller to action.
- In action ws client connection will be set and function **getUserID** will be called from AccountWS.php.
- In AccountWS.php, the parameters will be passed to ws call **get_user_id** and return the result to action page.

#### Step 2:

- Function **createAccountListInputVO** will take the input data and prepares the input value object for WSDL from controller to action.
- This function gets the values from input array and sets the values for list value to pass for WSDL call. It prepares the query and required input to create account.

#### Step 3:

- Function **editAccountDetails** will edit the account details from controller to action.
- In action, ws client connection will be set and function **editAccountDetails** in AccountWS.php will create parameters for wsdl using object.
- To ws client call **set_entry**, parameters will be passed and the result will be returned. 
