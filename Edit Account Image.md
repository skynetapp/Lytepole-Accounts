#### Date: 07/03/2017

#### Description: This document explains the code flow of editing account image.

#### Step 1:

Function **editAccountImage** will be called in index.php to controller which will update the account image of login user and uploads to sugar folder using curl.

- Function **getUserID** will get the login user id from controller to action. 
- In action, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action to controller.

#### Step 2:

- Function **createAccountImageListInputVO** will create the object array for input data to send to WSDL from controller to action.
- Input parameters will be Image id, Module Name = Accounts and Action Name = related to call in function.
- In action, function **createAccountImageListInputVO** will be called from AccountData.php which gets the input array and sets the values for account image.
- The result returns the image list object array from action to controller.

#### Step 3:

- Function **editAccountImage** from controller to action will update the image or add a new image to account.
- Input parameters will be session id,account id,user id,image id,Module Name = Accounts.
- In action, we will set the wsdl client connection by function **setWSDLHandle** from AccountWS.php.
- Function **editAccountImage** in AccountWS.php will send the data to wsdl for updating the account image by wsdl call **set_entry**.
- The result returns the image id from action to controller. 

#### Step 4:

- Function **createAccountImageRelation** from controller to action will set the relation between login account and uploaded image.
- The parameters will be session id, account id, user id, image id, Module Name = Accounts.
- In action, first wsdl client connection will be set by calling function **setWSDLHandle** from AccountWS.php.
- Function **createAccountImageRelation** in AccountWS.php will send data to wsdl for set relation between image and account.
- Create parameters and pass the parameters to ws call **set_relationship** and return the result as relation id to controller.

#### Step 5:

- Upload images to sugar images folder using curl.

#### Step 6:

- If the state is 0, header location will be redirected to View Account First else header location will be redirected to detail view. 
