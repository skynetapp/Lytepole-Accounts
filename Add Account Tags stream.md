#### Date: 07/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **addAccountTags** will be called first from index.php to controller.

- This function will be used to add account related tags like skill, location, employee type etc.
- Function **createAddMeetingTagsInputVO** will take the input data and prepares the input value object for WSDL.
- In action, function **createAddMeetingTagsInputVO** will be called from AccountData.php which gets the values from input array and sets the values for list object data.
- The input array parameters list - skills, location, company, experience, account id, employment options.
- will set the account tags list input value object and returns the result.

#### Step 2:

Function **createAccountTags** is used to create tags related to account.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **createAccountTags** in AccountWS.php will send data to wsdl for creating account tags.
- creating parameters for wsdl using object and passing the parameters to ws call **set_entries**
- Returns the result as tag id.


