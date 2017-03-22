#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.


#### Step 1:

Function **viewAccount()** will be called first from index.php to controller. when we click on the settings link in left side bar, it shows the user account details like image, name, company, skills, employee options etc.

- Function **createAccountListInputVO** will create the object array for input data to send parameters. The parameters are module,action and userid. This function will be called from controller to action.
- Here in action, function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- Here in AccountData.php, function **createAccountListInputVO** will get the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
- Result returns the account list value object array to controller and will be passed to function **getAccount**.
 

#### Step 2:

- Function **getAccount** will get the list value object array in controller and will be passed to action.
- The list array passed are session id, query and module name.
- In action, function will call the wsdl call for getting the account details.
- First, it will set the wsdl client by function **setWSDLHandle** from AccountWS.php.
- Next, function **getListArray** will get the account details by ws call **get_entry_list_acc**.
- Parameters passed for above function are session id, module name, query, orderby, offset, max result, deleted.
- Result returns the account list array to controller.

#### Step 3:

- Function **createAccountListDataObjectArr** will create a data object array for data from controller to action.
- The parameters passed will be account list array.
- Will create the object array for result of wsdl from action to AccountData.php.
- Function **createAccountListDataObject** in AccountData.php will get the values from input array and sets the values for list data object. - Resultreturns the account object data array to controller.

#### Step 4:

- Function **createAccountSkillsListInputVO** will take the input data and prepares the input value object from controller to action.
- The parameters passed will be account list array.
- This function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
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
- The parameters will be list array (data get from wsdl based on input) and skills get from wsdl
- Function **createAccountSkillsListDataObjectNew** will get the values from input array and sets the values for list data object which create account skills list data object from AccountData.php to action
- Result returns the account skills list input value object from  AccountData.php to action.

#### Step 7:

- Function **createContactListInputVO** will create a contact list from controller to action.
- In action, first we will get the user id by function **getUserID**.
- Function **createContactListInputVO** will set the values from input array to create a contact list from action to AccountData.php.
- Parameters passed will be id, name, created by id, created by name, tags.
- Result returns the contact list input value object to controller.

#### Step 8:

- Function **getContactsList** will get the blocked contacts list from controller to action.
- The parameters passed will be session id, query, order_by, max_result.
- In action, first ws connection client will be set using function **setWSDLHandle**.
- Function **getBlockContactsArray** will send data to wsdl for getting the blocked contacts in AccountWS.php.
- will create the parameters for WSDL by ws call **get_entry_list_con** and return the contacts array as result.

#### Step 9:

- Function **createContactListDataObjectArr** will create the object array and will get the list data in controller to action.
- The parameters will be the data getting from wsdl.
- From action, it will pass the list array to **createContactListDataObject** in AccountData.php.
- parameters input list will be id, name, email, phone, mobile, query date, next offset, block, work phone.
- Function **createContactListDataObject** will create a contact list data object and returns the contact list data object as result.

#### Step 10:

- Function **showAccount** takes the input data object and gives to the account view to disply the account details.
- The input parameters contains account details like name, location, experience, skills, employee type etc
- In action, function **showAccountListView** will call the AccountView.php to show the account details.








