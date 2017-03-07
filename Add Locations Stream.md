#### Date: 07/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **addLocations** will be called first in index.php to controller.

- This function is used to add new location or edit the existing location.
- Function **getUserID** will get the login user id from controller to action. 
- In action, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action to controller.

#### Step 2:

- Function **createAccountListInputVO** will take the input data and prepares the input value object for WSDL from controller to action.
- This function gets the values from input array and sets the values for list value to pass for WSDL call. It prepares the query and required input to create account.

#### Step 3:

- Function **getAccount** will call the WSDL to get the account details.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getListArray** in AccountWS.php will send data to wsdl for getting the account list using **get_entry_list_acc**.
- The result will be returened from action to controller.

#### Step 4:

- Function **saveAccountSkills** will call the wsdl to save location form controller to action.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **saveAccountSkills** in AccountWS.php will send data to wsdl for saving account skills.
- Create the parameters and pass the parameters to ws call **set_entry** and return the result to controller.

#### Step 5:

- Function **saveAccountSkillsRelation** will set the relation to account and saved skills.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **saveAccountSkillsRelation** in AccountWS.php will send data to wsdl to set data and skills relation.
- create the parameters for wsdl using object and set the relationship using ws call **set_relationship** and returns the result.

#### Step 6:

- Redirects header location to accounts view.

