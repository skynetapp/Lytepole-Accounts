#### Date: 07/03/2017

#### Description: This document explains the code flow of Adding locations.

#### Step 1:

Function **addLocations** will be called first in index.php to controller.

- This function is used to add new location or edit the existing location.
- The parameters passed will be Module Name = Accounts, Action Name =Edit and location.
- Function **getUserID** will get the login user id from action which is included in controller. 
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

- Function **saveAccountSkills** will call the wsdl to save location form controller to action.
- The parameters passed will be name, location, experience, email, account id.
- In action, first ws client connection will be set by calling function **setWSDLHandle** from AccountWS.php which is included in action.
- Function **saveAccountSkills** in AccountWS.php which is included in action page will send data to wsdl for saving account skills.
- Create the parameters and pass the parameters to ws call **set_entry** and return the result as sugar record id to controller.
- Here based on tag type, parameters will be passed to wsdl call. If **type = Employment type**, then parameters will be name, tag type and value else parameters will be only name and tag type. 

#### Step 5:

- Function **saveAccountSkillsRelation** will set the relation to account and saved skills.
- The parameters will be skills ids, post_data = Account id, Module name = Accounts.
- In action, first wsdl client connection will be set by calling function **setWSDLHandle** from AccountWS.php which is included in action.
- Function **saveAccountSkillsRelation** from AccountWS.php will be called which is included in action page will send data to wsdl to set data and skills relation.
- create the parameters for wsdl using object and set the relationship using wsdl call **set_relationship** and returns the sugar relation id as result to controller.

#### Step 6:

- Redirects header location to accounts view.

