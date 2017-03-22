#### Date: 07/03/2017

#### Description: This document explains the code flow of Account tags.

#### Step 1:

Function **addAccountTags** will be called first from index.php to controller.

- This function will be used to add account related tags like skill, location, employee type etc.
- Function **createAddMeetingTagsInputVO** will take the input data and prepares the input value object for WSDL from controller to action.
- The parameters passed from controller to action are module name - Accounts and action name - Tags
- In action, function **createAddMeetingTagsInputVO** will be called from AccountData.php which gets the values from input array and sets the values for list object data. This function is included in action page.
- The input array parameters list - skills, location, company, experience, account id, employment options.
- will set the account tags list input value object and returns the result to controller.

#### Step 2:

- Function **createAccountTags** is used to create tags related to account from controller to action.
- The parameters will be create_meeting_tags_vo = user id,tags data, extids = tag ids already exist.
- In action, first ws client connection will be set by calling function **setWSDLHandle** from AccountWS.php which is included in action.
- In acion, Function **createAccountTags** will be called from AccountWS.php which will send data to wsdl for creating account tags.
- creating parameters for wsdl using object and passing the parameters to ws call **set_entries**
- Returns the result as tag id.

#### Step 3:

- If **action == AddSkills**, header location will be redirected to Detail view and page = 2.
- Else header location will be redirected to Detail view and page = 3.

**_Code:_**
	
```
if($post_data['action']=="AddSkills"){
			header('Location: '.$GLOBALS["base_path"].'/index.php?module=Accounts&action=DetailView&page=2');
		}
		else
		{
			header('Location: '.$GLOBALS["base_path"].'/index.php?module=Accounts&action=DetailView&page=3');
		}

```

