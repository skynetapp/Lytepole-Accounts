#### Date: 06/03/2017

#### Description: This document explains the code flow of view skills.

#### Step 1:

Function **viewSkills** will be called first from index.php to controller.

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

- Function **getSkills** will get the account skills from controller to action.
- The parameters passed are skills list data object array.
- In action, first we will set the client WSDL connection using function **setWSDLHandle**.
- Function **getSkills** will send data to wsdl for getting account skills in AccountWS.php by ws call **get_entry_list_tags** and will return the result to action.
- The action will get the list array and return result to controller.

#### Step 6:

- Function **createAccountSkillsListDataObjectArr** will create a list object array for the data from controller to action.
- The parameters will be list array (data get from wsdl based on input) and skills get from wsdl.
- Function **createAccountSkillsListDataObjectNew** will get the values from input array and sets the values for list data object which create account skills list data object from AccountData.php to action.
- Result returns the account skills list input value object from  AccountData.php to action.


#### Step 7:

In controller, Based on action the redirection will take place.

- If action = Location, function **showAccountLocationsListView** will be called from controller to action which takes the input data object and gives to the account view to display the account location view.
- Parameters passed will be account details like name,location, experience, email.
- In action, Function **showAccountLocationsListView** will be called from AccountView.php which is used to assign the variables for tpl page and assign the value object array to variable and redirect to account location view form tpl page. 
- Tpl page will be in views -> AccountLocationsViewForm.tpl

#### Step 8:

- If action = Skills, function **showAccountSkillsListView** will be called from controller to action which gives the account skills list view.
- Input Parameters passed will be for account list data object array - account details like name,location, experience, email and for skills list - Account related employee tags and skills.
- In action, function **showAccountSkillsListView** will be called from AccountView.pphp which display the tpl page.
- The display tpl page will be **AccountSkillsViewForm.tpl** will be called  in views folder.

- Else function **showAccountEmployetypeListView** will be executed which shows the employee type list view.
- Input Parameters will be employee tags.
- In action, function **showAccountEmployetypeListView** will be called from AccountView.pphp which display the tpl page.
- The display tpl page will be **AccountEmployetypeViewForm.tpl** will be called  in views folder.
- 








