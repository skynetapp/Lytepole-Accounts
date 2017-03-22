#### Date: 07/03/2017

#### Description: This document explains the code flow of view notifications.

#### Step 1:

Next action in index.php is to call function **viewNotifications** from index.php to controller page which will is used to get the notification list view, when user clicks on notification.

- Function **getUserID** will get the user id by calling wsdl from controller page and will be redirected to action page.
- In action page, ws client connection will be set and function **getUserID** will be redirected to AccountWS.php.
- In AccountWS.php, the parameters will be passed to ws call **get_user_id** and return the result to action page.

#### Step 2:

- Function **createAccountListInputVO** will create the object array for input data to send parameters. The parameters are module,action and userid. This function will be called from controller page and will be redirected to action page.
- From action page, function will be redirected to AccountData.php which takes the input data and prepares the input value object for WSDL.
- In AccountData.php, function **createAccountListInputVO** which is included in action page will get the values from input array and sets the values for list value object to pass for WSDL call. It creates the query and required input to create account.
- Result returns the account list value object array to controller and will be passed to function **getAccount**.

#### Step 3:

- Function **getNotifications** from controller page and will be redirected to action page is used to call the wsdl call for getting the account related comapny id.
- The list parameters are session id, query, Module Name = Notifications.
- In action, first ws client connection will be set by calling function **setWSDLHandle** will be redirected to AccountWS.php.
- From action page, Function **getNotifications** will be redirected to AccountWS.php is used to send data to wsdl for getting the notifiaction list.
- creating the parameters for wsdl using object and pass the parameters to ws call **get_entry_list**.
- Returns the notification list array as result to controller page.

#### Step 4:

- Function **createNotificationsDataObjectArr** from controller page and will be redirected to action page is used to create a list object array for the data to get from wsdl.
- The input parameters are Module Name = Account, Action Name = Notification.
- From action page, function **createNotificationsDataObject** will be redirected to AccountData.php which gets the values from input array and sets the values for list data object.
- The data object array will return the result to controller page.

#### Step 5:

- If **$post_data['ajaxcall'] == 'yes'**, function **showNotificationsPaginationList** from controller page and will be redirected to action page which takes the input data object and gives to the notification view to display the notification Pagination list view.
- Parameters passed will be Notification list view data.
- From action page, function **showNotificationsPaginationView** will be redirected to AccountView.php which is used to assign the variables for tpl page and assign the value object array to variable and redirect to notification Pagination view form tpl page.
- The display tpl page will be in views -> NotificationsPaginationViewForm.tpl


#### Step 6:

- If **$post_data['ajaxcall'] != 'yes'**, function **showNotificationsView** from controller page and will be redirected to action page which takes the input data object and gives to the notification view to display the notification list view.
- Parameters passed will be Notification list view data.
- From action page, function **showNotificationsView** will be redirected to AccountView.php which is used to assign the variables for tpl page and assign the value object array to varable and redirect to notification view form tpl page.
- The display tpl page will be in views -> NotificationsViewForm.tpl.






