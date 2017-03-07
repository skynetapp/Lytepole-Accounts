#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Accounts
Views | AccountFirsttimeLogin, AccountSkillsViewForm, AccountViewForm, AccountLocationsViewForm, AccountEmployetypeViewForm, AccountCompanyViewForm, NotificationsViewForm, NotificationsPaginationViewForm, NotificationsDetailViewForm


#### Step 1:

Function **viewAccount()** will be called first when we click on the settings link in left side bar. It shows the user account details like image, name, company, skills, employee options etc.

- Function **createAccountListInputVO** will create the object array for input data to send parameters. This function will be called from controller to action.
- Here in action, function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- Here in AccountData.php, function **createAccountListInputVO** will get the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
 

#### Step 2:

- Function **getAccount** will call the WSDL for account view from controller to action.
- In action, function will call the wsdl call for getting the account details.
- First, it will set the wsdl client by function **setWSDLHandle** from AccountWS.php.
- Next, function **getListArray** will get the account details by ws call **get_entry_list_acc** and returns the result to controller.

#### Step 3:

- Function **createAccountListDataObjectArr** will create the object array for data list from controller to action.
- Will create the object array for result of wsdl from action to AccountData.php.
- Function **createAccountListDataObject** in AccountData.php will get the values from input array and sets the values for list data object and returns the account object data array to controller.

#### Step 4:

- Function **createAccountSkillsListInputVO** will be calling WSDL for skills from controller to action.
- This function takes the input data and prepares the input value object for WSDL from action to AccountData.php.
- In AccountData.php, function **createAccountSkillsListInputVO** will create the account skills list input value object and returns the result to controller.


#### Step 5:

- Function **getSkills** will get the account skills from controller to action.
- will set the client WSDL connection using function **setWSDLHandle**.
- Function **getSkills** will send data to wsdl for getting account skills in AccountWS.php by ws call **get_entry_list_tags** and will return the result to action.
- The action will get the list array and return result to controller.

#### Step 6:

- Function **createAccountSkillsListDataObjectArr** will create a list object array for the data to get from wsdl in controller to action.
- Function **createAccountSkillsListDataObjectNew** will get the values from input array and sets the value and returns the result from AccoountData.php to action.

#### Step 7:

- Function **createContactListInputVO** will create a contact list from controller to action.
- In action, first we will get the user id by function **getUserID**.
- Function **createContactListInputVO** will set the values from input array to create a contact list from action to AccountData.php and returns the result.

#### Step 8:

- Function **getContactsList** will get the blocked contacts list from controller to action.
- In action, first ws connection client will be set using function **setWSDLHandle**.
- Function **getBlockContactsArray** will send data to wsdl for getting the blocked contacts in AccountWS.php.
- will create the parameters for WSDL by ws call **get_entry_list_con** and return the result.

#### Step 9:

- Function **createContactListDataObjectArr** will create the object array and will get the list data in controller to action.
- From action, it will pass the list array to **createContactListDataObject** in AccountData.php
- Function **createContactListDataObject** will create a contact list data object and returns the array result.

#### Step 10:

- Function **showAccount** will send the data to view and display the output tpl page.
- In action, function **showAccountListView** will call the AccountView.php to show the account details.








