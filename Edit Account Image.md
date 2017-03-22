#### Date: 07/03/2017

#### Description: This document explains the code flow of editing account image.

#### Step 1:

Function **editAccountImage** will be called in index.php to controller page which will update the account image of login user and uploads to sugar folder using curl.

- Function **getUserID** will get the login user id from controller page and will be redirected to action page. 
- In action page, first wsdl client connection will be set and will get the login session which will be redirected to AccountWS.php by ws call **get_user_id**.
- The result will be returned from action page to controller page.

#### Step 2:

- Function **createAccountImageListInputVO** will create the object array for input data to send to WSDL from controller page and will be redirected to action page.
- Input parameters will be Image id, Module Name = Accounts and Action Name = related to call in function.
- From action page, function **createAccountImageListInputVO** will be called and gets redirected to AccountData.php which gets the input array and sets the values for account image.
- The result returns the image list object array from action page to controller page.

#### Step 3:

- Function **editAccountImage** from controller page is redirected to action page and will update the image or add a new image to account.
- Input parameters will be session id,account id,user id,image id,Module Name = Accounts.
- In action page, we will set the wsdl client connection by function **setWSDLHandle** which will be redirected to AccountWS.php.
- From action page, Function **editAccountImage** will be redirected to AccountWS.php which sends the data to wsdl for updating the account image by wsdl call **set_entry**.
- The result returns the image id from action page to controller page. 

#### Step 4:

- Function **createAccountImageRelation** from controller page is redirected to action page and will set the relation between login account and uploaded image.
- The parameters will be session id, account id, user id, image id, Module Name = Accounts.
- In action page, we will set the wsdl client connection by function **setWSDLHandle** which will be redirected to AccountWS.php.
- From action page, Function **createAccountImageRelation** will be redirected to AccountWS.php which sends data to wsdl for set relation between image and account.
- Create parameters and pass the parameters to ws call **set_relationship** and return the result as relation id to controller page.

#### Step 5:

- Upload images to sugar images folder using curl.

#### Step 6:

- If the state is 0, header location will be redirected to View Account First else header location will be redirected to detail view. 
