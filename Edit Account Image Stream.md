#### Date: 07/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Function **editAccountImage** will be called in index.php to controller which will update the account image of login user and uploads to sugar folder using curl.

- Function **getUserID** will get the login user id from controller to action. 
- In action, first ws client connection will be set and will get the login session from AccountWS.php by ws call **get_user_id**.
- The result will be returned from action to controller.

#### Step 2:

- Function **createAccountImageListInputVO** will create the object array for input data to send to WSDL from controller to action.
- In action, function **createAccountImageListInputVO** will get the input array values and sets the values for list data.
- The result will be returned from action to controller.

#### Step 3:

- Function **editAccountImage** will update the image or add a new image to account. 
- In action, we will set the ws client connection and function **editAccountImage** in AccountWS.php will send the data to wsdl for updating the account image by ws call **set_entry**.
- The result will be returned from action to controller. 

#### Step 4:

- Function **createAccountImageRelation** will set the relation with login account and uploaded image.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **createAccountImageRelation** in AccountWS.php will send data to wsdl for set relation between image and account.
- Create parameters and pass the parameters to ws call **set_relationship** and return the result.

#### Step 5:

- Upload images to sugar images folder using curl.

#### Step 6:

- Redirects the header location to account view. 
