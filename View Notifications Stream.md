#### Date: 07/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### Step 1:

Next action in index.php is to call function **viewNotifications** from index to controller which will is used to get the notification list view, when user clicks on notification.

- Function **getUserID** will get the user id by calling wsdl from controller to action.
- In action ws client connection will be set and function **getUserID** will be called from AccountWS.php.
- In AccountWS.php, the parameters will be passed to ws call **get_user_id** and return the result to action page.

#### Step 2:

- Function **createAccountListInputVO** will take the input data and prepares the input value object for WSDL from controller to action.
- This function gets the values from input array and sets the values for list value to pass for WSDL call. It prepares the query and required input to create account.

#### Step 3:

- Function **getNotifications** is used to call the wsdl call for getting the account related comapny id.
- In action, first ws client connection will be set by calling function **setWSDLHandle**.
- Function **getNotifications** in AccountWS.php is used to send data to wsdl for getting the notifiaction list.
- creating the parameters for wsdl using object and pass the parameters to ws call **get_entry_list**.
- Returns the result to controller.

#### Step 4:

- Function **createNotificationsDataObjectArr** is used to create a list object array for the data to get from wsdl.
- In action, function **createNotificationsDataObject** will be called from AccountData.php which gets the values from input array and sets the values for list data object.
- The data object array will return the result to controller.

#### Step 5:

- If **$post_data['ajaxcall'] == 'yes'**, function **showNotificationsPaginationList** which takes the input data object and gives to the notification view to display the notification Pagination list view.
- In action, function **showNotificationsPaginationView** will be called from AccountView.php which is used to assign the variables for tpl page and assign the value object array to variable and redirect to notification Pagination view form tpl page.
- The display tpl page will be in views -> NotificationsPaginationViewForm.tpl


#### Step 6:

- If **$post_data['ajaxcall'] != 'yes'**, function **showNotificationsView** which takes the input data object and gives to the notification view to disply the notification list view
- In action, function **showNotificationsView** will be called from AccountView.php which is used to assign the variables for tpl page and assign the value object array to varable and redirect to notification view form tpl page.
- The display tpl page will be in views -> NotificationsViewForm.tpl.






