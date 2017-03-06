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
- Will create the object array for result of wsdl from action to AccountsData.php.
- Function **createAccountListDataObject** in AccountsData.php will get the values from input array and sets the values for list data object and returns the account object data array to controller.

#### Step 4:

- Function **createAccountSkillsListInputVO** will be calling WSDL for skills from controller to action.

