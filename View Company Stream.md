#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **ViewCompany** will be called first from index.php to controller and is used to view the company of user.

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
- The result will be returened from action to controller.

#### Step 4:

- Function **createAccountSkillsListInputVO** will be calling WSDL for skills from controller to action.
- This function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- In AccountData.php, function **createAccountSkillsListInputVO** will create the account skills list input value object and returns the result to controller.


#### Step 5:

- Function **getCompany** is used to call the wsdl call for getting the account related company id.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getCompany** in AccountWS.php is used to send data to wsdl for getting the account company.
- Creating parameters for wsdl using object and passing to ws call **get_relationships**.
- Returns the result list to controller.

#### Step 6:

- Function **getCompanyDetails** will get the account related company details.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getCompanyDetails** in AccountWS.php used to send data to wsdl for getting the company account  .
- Creating parameters for wsdl using object and passing to ws call **get_entry**.
- Returns the result list to controller.

#### Step 7:

- Function **createAccountCompanyDataObjectArr** creates a list object array for the data.
- In action, function **createAccountCompanyDataObject** will be called from AccountData.php which gets the values from input array and sets the values for list data object.
- Returns the list data object array to controller.

#### Step 8:

- Function **showAccountCompanyView** will take the input data object and gives to the AccountView.php to display the account company view.
- In action, **showAccountCompanyView** function will be called from AccountView.php to assign the variables for tpl page and assign the value object array to varable and redirect to account company view form tpl page.
- The tpl page will be in views -> AccountCompanyViewForm.tpl



