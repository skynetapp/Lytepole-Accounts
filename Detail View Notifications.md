#### Date: 06/03/2017

#### Description: This document explains the code flow of detail view notifications.

#### Function: detailviewNotifications

- Function **detailviewNotifications** is used to update the notification count, means if we view the notication it updates in database and reduce the count of notifications in header view.

#### Step 1: getUserID

- Function **getUserID** will get the user id from account action page.
- In action page, first wsdl client connection will be set and will get the login session which will be redirected to AccountWS.php by ws call **get_user_id**.
- The result will be returned from action page to controller page.


#### Step 2: updateNotification

#### Step 2.1

- Function **updateNotification** is used to get  update notification count.
- Parameters passed will be Module Name = based on notification, Action Name = Detailview ,record = sugar record id and id = notification sugar record id.

#### Step 2.2

- In action page, first wsdl client connection will be set by calling function **setWSDLHandle** which will be redirected to AccountWS.php.

#### 2.2.1

- From action page, Function **updateNotification** which will be redirected to AccountWS.php which is used to send data to wsdl for getting the update notification view.
- creating parameters for wsdl using object and passing the paramaeters array list to ws call **set_entry**.
- Returns the result from account ws page to account action page.

#### Step 2.3

- The action page returns the result to controller page.
- **Result** - notification id.


#### Step 3: showNotificationsDetailView

#### Step 3.1 

- Function **showNotificationsDetailView** will be redirected to account action page which shows the notification detail view of select one.
- Parameters will be sugar record id, modulename = based the notification(like meeting,message,payment etc).

#### Step 3.2

- In account action page, function **showNotificationsDetailView** will be redirected to AccountView.php which is used to assign the variables for tpl page and assign the value object array to varable and redirect to notification detail view form tpl page.

#### Step 3.2.1

- The display tpl page will be in views -> NotificationsDetailViewForm.tpl.
- The result will return to notification detail view form.

