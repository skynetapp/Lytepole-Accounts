#### Date: 06/03/2017

#### Description: This document explains the code flow of company view of user.

#### Step 1:

Function **ViewCompany** will be called first from index.php to controller and is used to view the company of user.

- Function **getUserID** will get the login user id from controller to action. 
- In action, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action to controller.

#### Step 2:

- Function **createAccountListInputVO** will create the object array for input data to send parameters. The parameters are module,action and userid. This function will be called from controller to action.
- Here in action, function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- Here in AccountData.php, function **createAccountListInputVO** which is included in action will get the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
- Result returns the account list value object array to controller and will be passed to function **getAccount**.
 

#### Step 3:

- Function **getAccount** will get the list value object array in controller and will be passed to action.
- The parameters list array passed are session id, query and module name.
- In action, function will call the wsdl call for getting the account details.
- First, it will set the wsdl client by function **setWSDLHandle** from AccountWS.php which is included in action.
- Next, function **getListArray** will get the account details by ws call **get_entry_list_acc**.
- Parameters passed for above function are session id, module name, query, orderby, offset, max result, deleted.
- Result returns the account list array to controller.

#### Step 4:

- Function **createAccountSkillsListInputVO** will take the input data and prepares the input value object from controller to action.
- The parameters passed will be account list array.
- This function takes the input data and prepares the input value object for WSDL from action to AccountData.php which is included in action.
- In AccountData.php, function **createAccountSkillsListInputVO** will create the account skills list input value object.
- Result returns the skills list data object array to controller.


#### Step 5:

- Function **getCompany** from controller to action is used to call the wsdl call for getting the account related company id.
- The parameters will be session id, query, Module Name = Accounts.
- In action, first ws client connection will be set by calling function **setWSDLHandle** from AccountWS.php.
- In action, Function **getCompany** will be called from AccountWS.php which is used to send data to wsdl for getting the account company.
- Creating parameters for wsdl using object and passing to ws call **get_relationships**.
- Returns the result list to controller.

#### Step 6:

- Function **getCompanyDetails** from controller to action will get the account related company details.
- Parameters will be session id, query, Module Name = Accounts.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getCompanyDetails** in AccountWS.php used to send data to wsdl for getting the company account  .
- Creating parameters for wsdl using object and passing to ws call **get_entry**.
- Returns the result as account company list array to controller.

#### Step 7:

- Function **createAccountCompanyDataObjectArr** from controller to action creates a list object array for the data.
- Parameters list array will be data get from wsdl based on input and company detals get from wsdl.
- In action, function **createAccountCompanyDataObject** will be called from AccountData.php which gets the values from input array and sets the values for list data object.
- Returns the account company data object array as result to controller.

#### Step 8:

- Function **showAccountCompanyView** from controller to action will take the input data object to display the account company view.
- The parameters will be company details.
- In action, **showAccountCompanyView** function will be called from AccountView.php to assign the variables for tpl page and assign the value object array to variable and redirect to account company view form tpl page.
- The tpl page will be in views -> AccountCompanyViewForm.tpl



