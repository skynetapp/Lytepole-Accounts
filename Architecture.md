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

This Accounts module used to show the user settings.

- After login into lytepole, when user clicks on settings link in left side bar it shows the user account details like image, name, company, skills, employee options, visa option etc.
- Function **viewAccount** will be called when user details page is shown. Here we will get the account details of the user, skills and contact list which will be displayed in the form by calling function **showAccount**.
