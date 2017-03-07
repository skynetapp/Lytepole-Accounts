#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **viewSkills** will be called first from index.php to controller.

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

- Function **createAccountSkillsListInputVO** will create object array for list data to get from WSDl.
- In action, function **createAccountSkillsListInputVO** will be called from AccountData.php which will get the list array and return the result to conrtoller.

#### Step 5:

- Function **getSkills** will get the account skills.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getSkills** in AccountWS.php is used to send data to   wsdl for getting the account skills.
- The parameters will be passed to ws call **get_entry_list_tags** and will return the result.

#### Step 6:

- Function **createAccountSkillsListDataObjectArr** creates a list object array for the data to get from wsdl.
- In action, function **createAccountSkillsListDataObjectNew** will be called from AccountData.php will get the values from input array and sets the values for list data.
- Returns the account skills list input value object.

#### Step 7:

In controller,Based on action the redirection will take place.

- If action = Location, function **showAccountLocationsListView** will be executed which takes the input data object and gives to the account view to display the account location view.
- In action, Function **showAccountLocationsListView** will be called from AccountView.php which is used to assign the variables for tpl page and assign the value object array to variable and redirect to account location view form tpl page. 
- Tpl page will be in views -> AccountLocationsViewForm.tpl

- If action = Skills, function **showAccountSkillsListView** will be called which gives the account skills list view else function **showAccountEmployetypeListView** will be executed which shows the employee type list view.








