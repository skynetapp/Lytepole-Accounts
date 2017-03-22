#### Date: 06/03/2017

#### Description: This document explains the code flow of Accounts from user.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Accounts
Views | AccountFirsttimeLogin, AccountSkillsViewForm, AccountViewForm, AccountLocationsViewForm, AccountEmployetypeViewForm, AccountCompanyViewForm, NotificationsViewForm, NotificationsPaginationViewForm, NotificationsDetailViewForm


#### Architecture:

This Accounts module is used to show the user settings.

- After login into lytepole, when user clicks on settings link in left side bar it shows the user account details like image, name, company, skills, employee options, visa option etc.
- From controller page, Function **viewAccount** will be called when user details page is shown. Here we will get the account details of the user, skills and contact list which will be displayed in the form by calling function **showAccount**.
- From controller page, Function **editAccount** will update the account data of the login user.
- From controller page, Function **editAccountImage** will update the account image of the login user, and uploads to sugar folder using curl.
- From controller page, Function **addSkills** will add new skills or edit the existing skills.
- Function **viewSkills** will be used to view the skills of user. Based on action as (Location, skills), the list view will be displayed.
- To view the list of notifications click on notifications which is on the left side of menu bar then function **viewNotifications** will be called which display the list view.
- To update the notification count, function **detailviewNotifications** from controller page will be called and if the notification is viewed it will update the DB and reduce the notification count in header view. 
- Function **notificationsCount** will get the total message count to in header.
- if user logins  for first time, function **viewAccountFirsttime** will be called in controller page which will be redirect to account.
- if user logins for second time it will redirect to landing page.
