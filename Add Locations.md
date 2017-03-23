#### Date: 07/03/2017

#### Description: This document explains the code flow of Adding locations.

#### Function: addLocations

- This function is used to add new location or edit the existing location.
- **Parameters** - Module Name = Accounts, Action Name =Edit and location.

#### Step 1: getUserID

- Function **getUserID** will get the user id from account action page.
- In action page, wsdl client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from account action page to controller page.

#### Step 2: createAccountListInputVO

#### Step 2.1:

- Function **createAccountListInputVO** will redirect to account action page with posted parameters and user id.

#### Step 2.2:

- From account action page, function **createAccountListInputVO** will redirect to account data page.

#### Step 2.3

- In account data page, which gets the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to get account details and returns the result back to action page.

#### Step 2.4

- The action page returns the result get from account data page to controller page.
- **Result** - session, query, module, order by, offset, max results, deleted.


#### Step 3:getAccount

#### Step 3.1:

- Function **getAccount** will be redirected to action page with parameters as session id, module name, query, orderby, offset, max result, deleted.
- This function is used to call the wsdl for getting user account details.

#### Step 3.2:

 - From account action page, it will be redirected to account ws page which sets the wsdl client connection by function **setWSDLHandle**.

#### Step 3.2.1:

 - From account action page, function **getListArray** will be redirected to account ws page which get the account details by wsdl call **get_entry_list_acc** and returns the result to account action page.
 
#### Step 3.3

 - The account action page returns the result to controller page.
 - **Result** - session id, module name, query, order by, offset, max result, deleted. 


#### Step 4:

#### Step 4.1

- Function **saveAccountSkills** will be redirected to action page which will call the wsdl to save location form.
- The parameters passed will be name, location, experience, email, account id.

#### Step 4.2

- In action page, first ws client connection will be set by calling function **setWSDLHandle** which will be redirected to AccountWS.php.

#### Step 4.2.1

- From action page, Function **saveAccountSkills** will be redirected to AccountWS.php which is included in action page will send data to wsdl for saving account skills.
- Create the parameters and pass the parameters to ws call **set_entry** and return the result as sugar record id to account action page.
- Here based on tag type, parameters will be passed to wsdl call. If **type = Employment type**, then result will be name, tag type and value else result will be only name and tag type. 

#### Step 5: saveAccountSkillsRelation

#### Step 5.1

- Function **saveAccountSkillsRelation** will set the relation to account and saved skills.
- The parameters will be skills ids, Account id, Module name = Accounts.

#### Step 5.2

- In action page, first wsdl client connection will be set by calling function **setWSDLHandle** from AccountWS.php which is included in action.

#### step 5.2.1

- From action page, Function **saveAccountSkillsRelation** will be redirected to AccountWS.php  which sends data to wsdl to set data and skills relation.
- create the parameters for wsdl using object and set the relationship using wsdl call **set_relationship** and returns the  result to account action page.

#### Step 5.3

- The account action page returns the result to controller page.
- **Result** - Sugar relation record id.


#### Step 6:

- Redirects header location to accounts view.

