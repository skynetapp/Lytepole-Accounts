#### Date: 06/03/2017

#### Description: This document explains the code flow of detail view notifications.

#### Step 1:

Function **detailviewNotifications** will be called first from index.php to controller page which is used to update the notification count, means if we view the notication it updates in database and reduce the count of notifications in header view.

- Function **getUserID** will get the login user id from controller page and will be redirected to action page. 
- In action page, first wsdl client connection will be set and will get the login session which will be redirected to AccountWS.php by ws call **get_user_id**.
- The result will be returned from action page to controller page.


#### Step 2:

- Function **updateNotification** is used to get  update notification count.
- Parameters passed will be Module Name = based on notification,Action Name = Detailview ,record = sugar record id and id = notification sugar record id.
- In action page, first wsdl client connection will be set by calling function **setWSDLHandle** which will be redirected to AccountWS.php.
- From action, Function **updateNotification** which will be redirected to AccountWS.php which is used to send data to wsdl for getting the update notifiaction view.
- creating parameters for wsdl using object and passing the paramaeters array list to ws call **set_entry**.
- Result returns the notification id to controller page.


#### Step 3:

- Function **showNotificationsDetailView** will be called from controller page and will be redirected to action page which shows the notification detail view of select one.
- Parameters will be sugar record id, modulename = based the notification(like meeting,message,payment etc).
- In action, function **showNotificationsDetailView** will be called which will be redirected to AccountView.php which is used to assign the variables for tpl page and assign the value object array to varable and redirect to notification detail view form tpl page.
- The display tpl page will be in views -> NotificationsDetailViewForm.tpl
- The result will return to notification detail view form.

