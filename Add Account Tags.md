#### Date: 07/03/2017

#### Description: This document explains the code flow of Account tags.

#### Function: addAccountTags

- This function will be used to add account related tags like skill, location, employee type etc.
- **Parameters** : Module Name = Accounts,Action Name = tags and data of employee type,skills, visa status etc. 

#### Step 1: createAddMeetingTagsInputVO

#### Step 1.1:

- Function **createAddMeetingTagsInputVO** will be redirected to action page which will take the input data and prepares the input value object for WSDL.
- The parameters are skills, location, company, experience, account id, employment options.

#### Step 1.2

- From account action page, function **createAddMeetingTagsInputVO** will be redirected to AccountData.php which gets the values from input array and sets the values for list object data.	
- Returns the result back to account action page. 

#### Step 1.3

- The action page returns the result to controller page.
- **Result** - session id, name, tag type, currency, value, id, meeting id.

#### Step 2: createAccountTags

#### Step 2.1

- Function **createAccountTags** will be redirected to action page ehichis used to create tags related to account.
- The parameters will be create_meeting_tags_vo = user id,tags data, extids = tag ids already exist.

#### Step 2.2

- From account action page, first wsdl client connection will be set by calling function **setWSDLHandle** which will be redirected to AccountWS.php .

#### Step 2.2.1

- From action page, Function **createAccountTags** will be redirected to AccountWS.php which will send data to wsdl for creating account tags.
- creating parameters for wsdl using object and passing the parameters to ws call **set_entries**.
- Returns the result as tag id to account action page.

#### Step 2.3

- From account action page, result will be returned to controller page.
- If id is null, result - name, tag type, currency and value.
- If id is not null, result - name, id, tag type, currency and value.

#### Step 3:

- If **action == AddSkills**, header location will be redirected to Detail view page and page = 2.
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


