#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Function : viewAccount

- When user click on settings in left side bar in webapp this function will be called.
- This function is used to show the account details of login user like image, name, skills etc.
- **Parameters** : Module = Accounts, Action = viewAccount 


#### Step 1: getUserID

- Function **getUserID** will get the user id from account action page.

#### Step 2: createAccountListInputVO
#### Step 2.1:
- Function **createAccountListInputVO** will redirect to account action page with posted parameters and user id.
- which gets the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to get account details and returns the result back to action page.
#### Step 2.2
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


#### Step 4: createAccountListDataObjectArr

#### Step 4.1:

- Function **createAccountListDataObjectArr** will be redirected to account action page which will create a data object array for data.
- The parameters will be id, mobile, name, experience, location, email, createdby etc.

#### Step 4.2

- From account action page it will redirect to account data page.

#### Step 4.3

- From account action page, Function **createAccountListDataObject** will be redirected to AccountData.php which will get the values from input array and sets the values for list data object. 
- Result returns the account object data array to account action page.

#### Step 4.4

- The action page returns the result to controller page.
- **Result** - AccountId, CreatedById, Account Name, Mobile, Account Email, start date, created by name, location, company, experience, referral perc, recruiter, image id, linkedin, github.

#### Step 5: createAccountSkillsListInputVO

#### Step 5.1:

- Function **createAccountSkillsListInputVO** will be redirected to action page which takes the input data and prepares the input value object.
- The parameters are Module Name = Account, Action Name = Skills.

#### Step 5.2:

- From account action page, function **createAccountSkillsListInputVO** will be redirected to AccountData.php page.

#### Step 5.3:

- In AccountData.php page, function **createAccountSkillsListInputVO** will create the account skills list input value object.
- Result returns the skills list data object array to account action page.

#### Step 5.4:

- The action page returns the result get from account data page to controller page.
- **Result** - login Session id, Image id, Account id.


#### Step 6: getSkills

#### Step 6.1:

- Function **getSkills** will be redirected to action page which will get the account skills .
- The parameters passed are session id, account id.

#### Step 6.2

- From account action page, it will be redirected to account ws page which sets the wsdl client connection by function **setWSDLHandle**.

#### Step 6.3

- From account action page, Function **getSkills** will be redirected to account ws page which will send data to wsdl for getting account skills by wsdl call **get_entry_list_tags** and will return the result back to account action page.
- The account action page will get the list array and return result to controller page.
- **Result** - session id, module name, module id.

#### Step 7: createAccountSkillsListDataObjectArr

#### Step 7.1

- Function **createAccountSkillsListDataObjectArr** will be redirected to action page which will create a list object array for the data.
- The parameters will be id, name, created by id, created by name, tags.

#### Step 7.2

- From action page, Function **createAccountSkillsListDataObjectNew** will be redirected to AccountData.php which will get the values from input array and sets the values for list data object which create account skills list data object.
- Result returns the account skills list input value object from  account data page to account action page.

#### Step 7.3

- The action page returns the result to controller page.
- **Result** - account id, image id, id, created by id, created by name, tag name, tag type, tag value.

#### Step 8: createContactListInputVO

#### Step 8.1

- Function **createContactListInputVO** will be redirected to action page which will create a contact list.
- Parameters passed will be id, name, created by id, created by name, tags.

#### Step 8.2

- From account action page, first we will get the user id by function **getUserID**.

#### Step 8.2.1

- From account action page, Function **createContactListInputVO** will be redirected to AccountData.php which will set the values from input array to create a contact list.
- Result returns the contact list input value object from account data page to account action page.

#### Step 8.3

- The action page returns the result to controller page.
- **Result** - session, query, user id, query date, order by, select fields, max results, deleted.

#### Step 9: getContactsList

#### Step 9.1

- Function **getContactsList** will be redirected to action page which will get the blocked contacts list.
- The parameters passed will be session id, query, order_by, max_result.

#### Step 9.2

- From account action page, it will be redirected to account ws page which sets the wsdl client connection by function **setWSDLHandle**.

#### Step 9.3

- From account action page, Function **getBlockContactsArray** will be redirected to AccountData.php which will send data to wsdl for getting the blocked contacts.
- will create the parameters for WSDL by ws call **get_entry_list_con** and return the contacts array as result to account action page.

#### Step 9.4

- The action page returns the result to controller page.
- **Result** - session, module name, query, order by, offset, max results, deleted.

#### Step 10: createContactListDataObjectArr

#### Step 10.1:

- Function **createContactListDataObjectArr** will be redirected to action page which will create the object array and will get the list data.
- The parameters will be id, name, email, phone, mobile, query date, next offset, block, work phone.

#### Step 10.2

- From account action page, Function **createContactListDataObject** will be redirected to AccountData.php page which will create a contact list data object.
- Returns the contact list data object as result to account action page.

#### Step 10.3

- The account action page returns the result to controller page.
- **Result** - id, name, mobile, work phone, mobile phone, email, block.

#### Step 11: showAccount

#### Step 11.1

- Function **showAccount** will be redirected to action page which takes the input data object and gives to the account view to display the account details.
- The input parameters contains account details like name, location, experience, skills, employee type etc

#### Step 11.2

- From account action page, function **showAccountListView** will be redirected to AccountView.php page to show the account details.
- The display tpl page will be **AccountViewForm.tpl** in views folder.








