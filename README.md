csvinpg
=======

A bash script that mirrors a remote (S)FTP directory, checks, fix and reassembles downloaded csv files before import in PostgreSQL.

Script helps in a particular situation, quite common in massive postal printing. Code is well documented, shouldn't be a problem understanding how it works.
;-)

OH 1.8.1 User Manual

12/01/16

[]{#anchor}[]{#anchor-1}Table of contents

[]{#anchor-2}Intro: How to start OH
-----------------------------------

Start OH from a programming software, like Eclipse - the software used
in this description. As the application is being loaded, a splash menu
with the OH logo is shown. Then the login window appears: It has a
dropdown menu with the user list, a password field, plus the "Submit"
and the "Cancel" buttons. The administrator (admin, default password
"admin") can add and remove users, manage their passwords and
privileges.

Once the user is logged in, OH shows the main menu, with all options
granted for that user.

Considering the full administrator menu in the description of the entire
OH system, there are 11 main options, plus the "Close" button to exit
OH. Click on the "X" on the title bar, to log out and close the
application.

-   ^File:\ it\ has\ two\ options:\ "exit",\ to\ log\ out\ as\ seen\ above,\ and\ "users",\ to\ manage\ all\ OH\ users.\ The\ amministratore\ can\ create\ groups\ of\ users\ benefitting\ of\ the\ same\ set\ of\ rights.\ Click\ on\ "users"\ button\ to\ open\ a\ new\ sub-level\ with\ the\ "users"\ option\ to\ edit\ a\ single\ users's\ settings\ and\ the\ "groups"\ option\ to\ manage\ user\ groups.^
-   ^General\ Data:\ it\ manages\ all\ data\ used\ by\ the\ OH\ database.^
-   ^OPD\ (Out\ Patient\ Department):\ this\ section\ allows\ the\ user\ to\ record,\ search,\ update\ and\ edit\ the\ patient\'s\ visits.^
-   ^Pharmacy:\ OH's\ pharmacy\ records\ all\ items\ used\ by\ the\ hospital.\ This\ menu\ has\ three\ sub-levels:\ the\ "Pharmaceuticals"\ option\ to\ manage\ the\ pharmacy\ database,\ the\ "Pharmaceutical\ Stock"\ option\ to\ record\ movements\ between\ pharmacy\ and\ suppliers\ and\ the\ "Pharmaceutical\ Stock\ Ward"\ option\ to\ record\ movements\ within\ the\ hospital\ and\ its\ wards.^
-   ^Laboratory:\ this\ section\ allows\ the\ user\ to\ record,\ search\ and\ update\ the\ patient's\ exams.^
-   ^Accounting:\ OH's\ cash\ register\ records\ the\ bills\ generated\ from\ medical\ items\ and\ patient\ exams.^
-   ^Admission/Patient:\ this\ section\ allows\ the\ user\ to\ manager\ the\ patient\ database.^
-   ^Patient\ Vaccines:\ similar\ to\ the\ "Laboratory"\ menu,\ it\ records\ the\ patient's\ vaccinations.^
-   ^Statistics:\ it\ generates\ Excel\ reports\ about\ the\ hospital\ activity\ on\ a\ given\ period\ of\ time.^
-   ^Printing:\ it\ generates\ a\ document\ with\ either\ the\ exams\ list\ or\ the\ diseases\ list,\ sorted\ by\ type.^
-   Help: it opens a .PDF file with the user's guide.

[]{#anchor-3}[]{#anchor-4}[]{#anchor-5}^1.\ Login^![](Pictures/10000000000001F6000001614BE7B365A0226BDC.jpg){width="8.495cm" height="5.967cm"}[]{#anchor-6}
-----------------------------------------------------------------------------------------------------------------------------------------------------------

When starting OH for the first time, once it is being loaded, the main
menu is immediately shown, as login is disabled. Open the project in
Eclipse, click on triangles near the project name, the sub-folder "rsc"
(below), and the file "generalData.properties", containing all system
settings. Row 3 shows by default the string "SINGLEUSER=yes". Replacing
"yes" with "no" on this string, the login window (on the bottom on the
page)
is![](Pictures/10000201000002670000021DE0CF2B4E6B1E17A7.png){width="11.649cm"
height="10.248cm"} enabled. The user chooses his/her name from the
dropdown menu with the user list, then enters the corresponding
password. If username and password don't match, an error window opens,
showing the "password incorrect: retry", message. Click OK to close this
window and enable the login window again. If the password is correct,
the user enters the OH system. The main menu is shown, with all the
options granted for the given
user.![](Pictures/10000000000001450000009B1F1220F695E0497A.jpg){width="7.29cm"
height="3.477cm"}

The admin menu (left) has
all![](Pictures/10000000000000D20000015284C2056A5612EAC0.jpg){width="5.465cm"
height="8.797cm"} the options enabled, while
a![](Pictures/10000000000000D6000001E40D31DA1C8755FB36.jpg){width="5.152cm"
height="11.654cm"} guest menu (i.e., "Eduardo" menu, see also chapter
2.1.2) has a limited set of options. The administrator can edit all
user's privileges.

Data:

-   user.US\_ID\_A (username)
-   user.US\_PASSWD (password)

[]{#anchor-7}[]{#anchor-8}[]{#anchor-9}2. File menu![](Pictures/10000000000003EC0000036C295AF0E9413B5504.jpg){width="17cm" height="14.827cm"}
---------------------------------------------------------------------------------------------------------------------------------------------

The "File" menu contains two sub-menus: "exit", to close OH, and
"users", where the administrator can manage user access to the system.

Focusing on "users" option and clicking on its button, the new window
shows two options, "users" and "groups". The former allows the
administrator to manage a given user's privileges, while the latter
allows to create user groups.

***2.1 Users (editing a single
user)***![](Pictures/100000000000026D00000156DA4C176B08B8FDAD.jpg){width="10.506cm"
height="5.779cm"}

The "Users browser" shows the full list of signed users. When OH is
opened for the first name, the list comprises of two users: the
administrator, only person of the eponymous group, and a guest from the
"guest" group (see chapter 1).

The bottom part of the menu disposes of some buttons to manage the
table.

Data:

-   user.US\_ID\_A (primary key, username)
-   usergroup.UG\_ID\_A (foreign key referencing the user group)
-   user.US\_DESC (user description)

***2.1.1 Select group***

Shows only users of the selected group. When the "Users browser" opens,
the dropdown menu is set on "ALL", and the full list is visible. Select
the group from the menu, and the corrispondono row are automatically
shown.

Data:

same of chapter 2.1

***2.1.2 New
User***![](Pictures/10000000000001420000014E5B0B659A8D341A69.jpg){width="6.138cm"
height="6.368cm"}

Adds a new OH user to the "user" database. Choose the user group from
the dropdown menu, enter the username in the "Name" field, then type the
password, retype it on the "Retype password" field, and add an optional
description to help identify the user. Click "OK" to confirm, or
"Cancel" to return to the users table. If "OK" was clicked and no
password was inserted, an error window shows the "please insert a
password" message. Click "OK" to return to "New User Record" window. If
the two passwords don't match, an error window shows the "password
incorrect, please retype". Click "OK" to return to "New User Record" and
retype the passwords. If they match, the new user is added to the users
table (top on next page).

Data:

all "user" attributes

![](Pictures/1000000000000332000001C3DC60070800A2A7DB.jpg){width="15.182cm"
height="8.37cm"}

[]{#anchor-10}[]{#anchor-11}[]{#anchor-12}2.1.3 Edit user![](Pictures/1000000000000144000000DE2204AD365CC81F2A.jpg){width="7.728cm" height="5.295cm"}
=====================================================================================================================================================

Updates the user description. Select a row from the "Users browser" and
click "Edit". An "Editing user record" window opens. The "Description"
field is freely editable. Click "OK" to save changes, or "Cancel" to
return to the users menu.

If a row is not selected before clicking "Edit", a "please select a row"
window opens. Click "OK" to close the window to return to the user menu.
This message will appear on every OH table, for all editing and deleting
options.

Data:

-   user.US\_ID\_A (primary key, username)
-   user.US\_DESC (user description)

[]{#anchor-13}[]{#anchor-14}[]{#anchor-15}2.1.4 Reset Password![](Pictures/1000000000000112000000AAA887A4914DBD78D8.jpg){width="5.685cm" height="3.528cm"}
==========================================================================================================================================================

To change the password for a given user, select a row from the users
browser and click "Reset Password". Insert the new password on the new
window (left).

Then click "OK". Retype the new password on a second window similar to
the first one and click "OK".

![](Pictures/1000000000000128000000A65A4CA89B532F4264.jpg){width="5.685cm"
height="3.187cm"}![](Pictures/1000020100000150000000A80657692E14CBA539.png){width="5.747cm"
height="2.879cm"}

If the passwords don't match, an error message (left) is shown, else a
confirmation window opens (right) and the new password is stored in the
users DB (bottom window). Clicking "Cancel" anytime, the operation is
aborted and there will be no changes to the users DB.

Data:

-   user.US\_ID\_A (username)
-   usergroup.UG\_ID\_A (password)

[]{#anchor-16}[]{#anchor-17}[]{#anchor-18}2.1.5 Delete User![](Pictures/100000000000028A0000016412F1CA68C1F1291D.jpg){width="10.977cm" height="6.015cm"}
========================================================================================================================================================

Removes the selected user from the user list. Select a row and click
"Delete". As in most "delete" operations, a confirmation window opens:
click "Yes" to definitely remove the user from the list, or "No" to
abort the operation.

Data:

-   user.US\_ID\_A (primary key, username)

[]{#anchor-19}[]{#anchor-20}[]{#anchor-21}2.1.6 Close Users browser
===================================================================

Closes the "Users browser" window. Click "Close" to return to the main
menu.

[]{#anchor-22}[]{#anchor-23}[]{#anchor-24}2.2 Groups (editing user groups)![](Pictures/10000000000002B5000000DC28117CF32A5A104D.jpg){width="11.714cm" height="3.717cm"}
=======================================================================================================================================================================

The groups feature helps the administrator assign the same set of
privileges to a multitude of users. A hospital likely has more than a
single pharmacist, or surgeon, etc. , so it's useful to aggregate users
by their role in the hospital. The "Groups browser" window shows the
name of the group, and a description. Default groups are "admin", for
the administrator(s), and "guest", with read-only functions enabled. On
the bottom side of the table, there are five buttons to manage the
groups:

Data:

-   usergroup.UG\_ID\_A (primary key, group name)
-   usergroup.UG\_DESC (group description)

[]{#anchor-25}[]{#anchor-26}[]{#anchor-27}2.2.1 New Group![](Pictures/10000201000002280000013398563A5F0839138F.png){width="9.35cm" height="5.202cm"}
====================================================================================================================================================

Creates a new user group. Click "New" on the "groups browser". Add the
name and an optional description in the new window, then click "OK" to
confirm. If the name doesn't exist in the "usergroup\" database, the
group will be added, else a "the group is already present" message
appears. If no name is inserted, a "please insert a valid user group"
message is
shown.![](Pictures/10000201000002D4000000E48A988E785775B08A.png){width="11.148cm"
height="3.51cm"} Click "OK" after both unsuccessful cases to add a
proper name. Once a valid name is entered, the new group is added to the
"group browser" table (right).

Data:

both "usergroup" attributes

[]{#anchor-28}[]{#anchor-29}[]{#anchor-30}2.2.2 Edit Group
==========================================================

Edits the group's description. It's similar to the "Edit User" option
(2.1.3). Select a row, click "Edit" and type the (optional) description
in the new window. Click "OK" to save changes, or "Cancel" to abort the
operation.

Data:

both "usergroup" attributes

[]{#anchor-31}[]{#anchor-32}[]{#anchor-33}2.2.3 Delete Group
============================================================

Removes an existing group, except the "admin" and groups which have
users assigned to.

Select a row from the "Group Browser" and click "Delete". The
confirmation window is shown: click "No" to abort the operation, or
"Yes" to remove the group. If "admin" is selected, a "You can't delete
admin" message appears; if there are users belonging to the selected
group, a "This group has users" window is shown. The "usergroup"
database remains unchanged after both unsuccessful cases. For the latter
case, first remove those users before deleting the group. Then create a
new group (2.2.1) and add the users (2.1.2).

Data:

-   usergroup.UG\_ID\_A (primary key, group name)
-   user.US\_UG\_ID\_A (foreign key referencing user group, to which the
    user belongs; if the selected group has users, it can't be deleted)

[]{#anchor-34}[]{#anchor-35}[]{#anchor-36}2.2.4 Group Menu![](Pictures/10000201000002BB000001E14E5F274A7D1DD7D9.png){width="11.83cm" height="8.139cm"}
======================================================================================================================================================

Allows the administrator, and all the users with this feature enabled,
to manage privileges for every group in the "usergroup" database. Select
a group from the "Group Browser" window and click "GroupMenu". A new
window "Menu Item Browser" (left), reproducing OH's main menu, opens.
Click on the triangles to expand the menu items. Enabled functions are
shown in black, while disabled options are shown in light grey. Double
click on a single option to activate/deactivate it. Click "Update" to
save changes, or close the window to abort the operation.

As seen in chapter
1,![](Pictures/10000201000002BF000002207ECB1F67ED58FFE1.png){width="11.94cm"
height="9.232cm"} "Eduardo" can't read the user menu ("HELP" option) by
default. The administrator, or any user with permission to edit groups,
selects the "guest" row, clicks "GroupMenu", then double-clicks "HELP"
on the "Menu
Item![](Pictures/10000201000000D50000016EF472D8212DA7F544.png){width="4.72cm"
height="8.112cm"} Browser" window (left) and clicks "Update". Now
Eduardo can access the user guide, as the menu pictured on the right
shows the "HELP" button.

Data:

-   groupmenu.GM\_ID (primary key, option ID)
-   groupmenu.GM\_UG\_ID\_A (user)
-   groupmenu.GM\_MNI\_ID\_A (option name)
-   groupmenu.GM\_ACTIVE (Y if the option is enabled, else N)

[]{#anchor-37}[]{#anchor-38}[]{#anchor-39}2.2.5 Close Groups Browser menu
=========================================================================

Closes the "groups browser" window. Click "Close" to return to the main
menu.

[]{#anchor-40}[]{#anchor-41}[]{#anchor-42}3. General Data menu
--------------------------------------------------------------

[]{#anchor-43}[]{#anchor-44}[]{#anchor-45}3.1 Types![](Pictures/10000000000001EE000002077996C87FDFFB82E6.jpg){width="8.384cm" height="8.807cm"}
===============================================================================================================================================

All data the hospital needs to work with - such as, medicals, exams,
operations, diseases, etc. - are sorted by type. This menu shows users
the list of categories for all data used in the OH databases. Users can
define new types according to their needs.

OH's categorized elements are:

-   Admission type (the way the patient is admitted in the hospital)
-   Discharge type: (the way the patient is dismissed from the hospital)
-   Delivery type: (normal, caesarian, ...)
-   Delivery result type
    (childbirth's![](Pictures/10000201000000CF0000023270A1EB129158A14D.png){width="4.512cm"
    height="12.248cm"} outcome)
-   Disease type
-   Exam type: il tipo di esame
-   Medicals Stock movement type (charge, discharge, donation)
-   Medicals type
-   Operation type
-   Pregnant treatment (treatments for pregnant mothers)
-   Other prices (for extra services the hospital provides)
-   Age type
-   Vaccine type

All "Types" sub-menus, when clicked, open a window showing the list of
the elements for the given type. There are "New", "Edit" and "Delete"
buttons to customize the tables, except for "Age Type", having the
"Edit" button only.

[]{#anchor-46}[]{#anchor-47}[]{#anchor-48}3.1.1 Admission Type![](Pictures/1000020100000234000000882F599A2D1076EAE0.png){width="10.619cm" height="2.559cm"}![](Pictures/100000000000027300000118E5AD98AA3B7B2B6F.jpg){width="10.619cm" height="4.741cm"}
========================================================================================================================================================================================================================================================

The "Admission Type Browsing" table shows the different ways a patient
is admitted in to the hospital. Default types are:

-   "A" (Ambulance, an ambulance carries the patient)
-   "R" (Referral, patient coming from another hospital / ward)
-   "I" (Self, patient coming by him/herself). Below is a screenshot
    from the "New Admission" option (8.5.1), where a dropdown menu is
    used to select admission
    types.![](Pictures/10000201000003EA000001E2CA915D28333A9131.png){width="16.99cm"
    height="8.172cm"}

Data:

-   admissiontype.ADMT\_ID\_A (primary key, admission type ID)
-   admissiontype.ADMT\_DESC (admission type description)

[]{#anchor-49}[]{#anchor-50}[]{#anchor-51}3.1.1.1 New Admission Type![](Pictures/100002010000022400000169292FE9C6FB33EB04.png){width="9.777cm" height="6.435cm"}
================================================================================================================================================================

Click "New" on "Admission type browsing". Enter a character code and a
description on the "New admission type record" window, then click "OK"
to confirm, or "Cancel" to abort the operation. Both elements are
mandatory; if "OK" is clicked but almost one field is empty, either a
"Please insert a code" or "Please insert a valid description" window is
shown. If the code already exists, a "Code already in use" window opens.
After all unsuccessful cases, click "OK" on the error window to return
to the "New admission type record" panel.

Data:

both "admissiontype" attributes (3.1.1)

[]{#anchor-52}[]{#anchor-53}[]{#anchor-54}3.1.1.2 Edit Admission Type![](Pictures/10000201000000FF000000B2284CAF0B4ADB7635.png){width="4.919cm" height="3.448cm"}
=================================================================================================================================================================

Select a row from "Admission Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing admission type
record" panel.

Data:

both "admissiontype" attributes (3.1.1)

[]{#anchor-55}[]{#anchor-56}[]{#anchor-57}3.1.1.3 Delete admission type
=======================================================================

Removes a row from the "admissiontype" database. Select a row from
"Admission Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

admissiontype.ADMT\_ID\_A

[]{#anchor-58}[]{#anchor-59}[]{#anchor-60}3.1.1.4 Close Admission Type menu
===========================================================================

Click "Close" on the "Admission Type Browsing" window to return to main
menu.

[]{#anchor-61}[]{#anchor-62}[]{#anchor-63}3.1.2 Discharge Type![](Pictures/1000000000000309000001537E772D29BC97EE2A.jpg){width="13.162cm" height="5.754cm"}![](Pictures/1000020100000281000000A4EAE92A82E7B1CBB7.png){width="10.88cm" height="2.782cm"}
=======================================================================================================================================================================================================================================================

The "Discharge type browsing" table defines the different ways a patient
can be dismissed from the hospital. Default types are: "D" (Dead,
patient deceased), "ES" (Escape, the patient escaped from the hospital),
"EQ" (Normal Discharge), "B" (Referred, a further visit is planned for
that patient).

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)
-   dischargetype.DIST\_DESC (discharge type description)

[]{#anchor-64}[]{#anchor-65}[]{#anchor-66}3.1.2.1 New Discharge Type![](Pictures/1000020100000109000000B43F6EA7FCECA4C4EE.png){width="5.659cm" height="3.844cm"}
================================================================================================================================================================

Click "New" on the "Discharge type browsing" table. Enter the character
code and a description (used in the "New Discharge" option) on the "New
Discharge Type Record" window. Click "OK" to confirm or "Cancel" to
abort the operation. Both fields are mandatory; see 3.1.1.1 for error
messages.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)
-   dischargetype.DIST\_DESC (discharge type description)

[]{#anchor-67}[]{#anchor-68}[]{#anchor-69}3.1.2.2 Edit Discharge Type![](Pictures/100002010000010D000000C6FBB0AF0B97F86664.png){width="5.89cm" height="4.346cm"}
================================================================================================================================================================

Select a row from "Discharge Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing discharge type
record" panel.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)
-   dischargetype.DIST\_DESC (discharge type description)

[]{#anchor-70}[]{#anchor-71}[]{#anchor-72}3.1.2.3 Delete Discharge Type
=======================================================================

Removes a row from the "dischargetype" database. Select a row from
"Discharge Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)

[]{#anchor-73}[]{#anchor-74}[]{#anchor-75}3.1.2.4 Discharge Type menu
=====================================================================

Click "Close" on the "Discharge Type Browsing" window to return to main
menu.

[]{#anchor-76}[]{#anchor-77}[]{#anchor-78}3.1.3 Delivery Type![](Pictures/10000000000002960000011E11674490B4C96EC7.jpg){width="11.217cm" height="4.851cm"}
==========================================================================================================================================================

The "Delivery type browsing" table defines the ways of assisting
pregnant mothers in the event of a delivery. Default types are: "C"
(Caesarian delivery), "V" (Vacuum extraction), "N" (No assistance).

![](Pictures/10000201000001B20000008AF3EA0AB08120A329.png){width="9.571cm"
height="3.053cm"}

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)
-   deliverytype.DRT\_DESC (delivery type ID)

[]{#anchor-79}[]{#anchor-80}[]{#anchor-81}3.1.3.1 New Delivery Type
===================================================================

Click "New" on the "Delivery type browsing" table. Enter the
one-character code and a description on the "New Delivery Type Record"
window. Click "OK" to confirm or "Cancel" to abort the operation. Both
fields are mandatory; see 3.1.1.1 for error messages.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)
-   deliverytype.DRT\_DESC (delivery type ID)

[]{#anchor-82}[]{#anchor-83}[]{#anchor-84}3.1.3.2 Edit Delivery Type![](Pictures/1000020100000131000000E4D24435ADD44F49C2.png){width="5.158cm" height="3.866cm"}
================================================================================================================================================================

Select a row from "Delivery Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing delivery type
record" panel.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)
-   deliverytype.DRT\_DESC (delivery type ID)

[]{#anchor-85}[]{#anchor-86}[]{#anchor-87}3.1.3.3 Delete Delivery Type
======================================================================

Removes a row from the "deliverytype" database. Select a row from
"Delivery Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)

[]{#anchor-88}[]{#anchor-89}[]{#anchor-90}3.1.3.4 Close Delivery Type menu
==========================================================================

Click "Close" on the "Delivery Type Browsing" window to return to the
main menu.

[]{#anchor-91}[]{#anchor-92}[]{#anchor-93}3.1.4 Delivery Result Type![](Pictures/10000000000002C60000012C35E6030951B9A6E8.jpg){width="12.007cm" height="5.089cm"}
=================================================================================================================================================================

The "Delivery result type browsing" table defines the different delivery
outcomes. Default types are shown
below:![](Pictures/1000020100000157000000A136DBA57675145C0E.png){width="6.482cm"
height="3.036cm"}

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)
-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#anchor-94}[]{#anchor-95}[]{#anchor-96}3.1.4.1 New Delivery Result Type![](Pictures/1000020100000130000000B7D191A5481129888D.png){width="5.258cm" height="3.164cm"}
======================================================================================================================================================================

Click "New" on the "Delivery result type browsing" table. Enter the
one-character code and a description on the "New Delivery Result Type
Record" window. Click "OK" to confirm or "Cancel" to abort the
operation. Both fields are mandatory; see 3.1.1.1 for error messages.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)
-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#anchor-97}[]{#anchor-98}[]{#anchor-99}3.1.4.2 Edit Delivery Result Type![](Pictures/100002010000012D000000AF476CFAB9A95F4CE6.png){width="5.096cm" height="2.949cm"}
=======================================================================================================================================================================

Select a row from "Delivery Result Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing delivery result
type record" panel.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)
-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#anchor-100}[]{#anchor-101}[]{#anchor-102}3.1.4.3 Delete Delivery Result Type
================================================================================

Removes a row from the "deliveryresulttype" database. Select a row from
"Delivery Result Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)

[]{#anchor-103}[]{#anchor-104}[]{#anchor-105}3.1.4.4 Close Delivery Result Type menu
====================================================================================

Click "Close" on the "Delivery Result Type Browsing" window to return to
the main menu.

[]{#anchor-106}[]{#anchor-107}[]{#anchor-108}3.1.5 Disease Type![](Pictures/10000000000002920000011AD8C1B9B626829143.jpg){width="11.157cm" height="4.773cm"}
============================================================================================================================================================

The table "Disease type browsing" defines the different disease
categories used in OH, including "OPD". Default types: "ND" (Notifiable
diseases), "OC" (Infective diseases), "MP" (Maternal / perinatal
diseases), "NC" (Non communicable diseases), "AO" (All other
diseases).![](Pictures/10000201000001EC0000009F8162C19B618C06D1.png){width="8.308cm"
height="2.685cm"}

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)
-   diseasetype.DCL\_DESC (disease type description)

[]{#anchor-109}[]{#anchor-110}[]{#anchor-111}3.1.5.1 New Disease Type![](Pictures/1000020100000153000000B66017E2C2BC7ECB3B.png){width="7.983cm" height="4.286cm"}
=================================================================================================================================================================

Click "New" on the "Disease type browsing" table. Enter the character
code and a description on the "New Disease Type Record" window. Click
"OK" to confirm or "Cancel" to abort the operation. Both fields are
mandatory; see 3.1.1.1 for error messages.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)
-   diseasetype.DCL\_DESC (disease type description)

[]{#anchor-112}[]{#anchor-113}[]{#anchor-114}3.1.5.2 Edit Disease Type![](Pictures/1000020100000166000000B76A98309EAA95E12E.png){width="7.278cm" height="3.722cm"}
==================================================================================================================================================================

Select a row from "Disease Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing disease type
record" panel.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)
-   diseasetype.DCL\_DESC (disease type description)

[]{#anchor-115}[]{#anchor-116}[]{#anchor-117}3.1.5.3 Delete Disease Type
========================================================================

Removes a row from the "diseasetype" database. Select a row from
"Disease Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)

[]{#anchor-118}[]{#anchor-119}[]{#anchor-120}3.1.5.4 Close Disease Type menu
============================================================================

Click "Close" on the "Disease Type Browsing" window to return to the
main menu.

[]{#anchor-121}[]{#anchor-122}[]{#anchor-123}3.1.6 Exam Type![](Pictures/10000000000002C600000134CB989BFF8851BD2C.jpg){width="12.026cm" height="5.214cm"}
=========================================================================================================================================================

The "Exam Type Browsing" table defines the different exam categories
used in OH, including "Laboratory". Default types are shown below:

![](Pictures/1000020100000191000001019AE8484FF1B7D413.png){width="6.789cm"
height="4.362cm"}

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)
-   examtype.EXC\_DESC (exam type description)

[]{#anchor-124}[]{#anchor-125}[]{#anchor-126}3.1.6.1 New Exam Type![](Pictures/100002010000015F000000B44F8D631D49B6DFA7.png){width="7.682cm" height="3.944cm"}
==============================================================================================================================================================

Click "New" on the "Exam type browsing" table. Enter the character code
and a description on the "New Exam Type Record" window. Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)
-   examtype.EXC\_DESC (exam type description)

[]{#anchor-127}[]{#anchor-128}[]{#anchor-129}3.1.6.2 Edit Exam Type![](Pictures/1000020100000158000000AFC9E01DCD9175DF39.png){width="6.914cm" height="3.505cm"}
===============================================================================================================================================================

Select a row from "Exam Type Browsing" and click "Edit". The description
field is freely editable. Click "OK" to save changes, or "Cancel" to
abort the operation. If "OK" is clicked but the description field is
empty, a "Please insert a valid description" window is shown. Click "OK"
on the error window to return to the "Editing exam type" panel.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)
-   examtype.EXC\_DESC (exam type description)

[]{#anchor-130}[]{#anchor-131}[]{#anchor-132}3.1.6.3 Delete Exam Type
=====================================================================

Removes a row from the "examtype" database. Select a row from "Exam Type
Browsing" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)

[]{#anchor-133}[]{#anchor-134}[]{#anchor-135}3.1.6.4 Close Exam Type Menu
=========================================================================

Click "Close" on the "Exam Type Browsing" window to return to the main
menu.

[]{#anchor-136}[]{#anchor-137}[]{#anchor-138}3.1.7 Medical Stock Movement Type![](Pictures/10000000000002B000000173BA7E6A96339D97A2.jpg){width="11.652cm" height="6.287cm"}
===========================================================================================================================================================================

The "Medicals Stock Movement Type Browsing" table shows the different
money movements involving the hospital. The two basic elements (below)
are: "Charge", for incomes (+), and "Discharge", for payments
(-).![](Pictures/100002010000015700000078D5B0264814913EB5.png){width="6.796cm"
height="2.371cm"}

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)
-   medicaldsrstockmovtype.MMVT\_ID\_DESC (movement type description)
-   medicaldsrstockmovtype.MMVT\_ID\_A ("+" or "-")

[]{#anchor-139}[]{#anchor-140}[]{#anchor-141}3.1.7.1 New Medical Stock Movement Type![](Pictures/1000020100000105000000E7F9AC579A314CF223.png){width="4.886cm" height="4.32cm"}
===============================================================================================================================================================================

Click "New" on the "Medicals Stock Movement Type Browsing" window. Enter
a character code, a description (i.e. the name of the movement) and
select the type (income or outcome)
from![](Pictures/1000020100000158000000A4E8CDD18C6080380D.png){width="6.796cm"
height="3.233cm"} the dropdown menu. Click "OK" to confirm or "Cancel"
to abort the operation. Both fields are mandatory; see 3.1.1.1 for error
messages. Pictured left is an example, where a "donation" category is
added to the "medicaldsrstockmovtype" database (right).

Data:

see chapter 3.1.7

[]{#anchor-142}[]{#anchor-143}[]{#anchor-144}3.1.7.2 Edit Medical Stock Movement Type![](Pictures/1000020100000106000000EA455145E91221802C.png){width="5.299cm" height="4.717cm"}
=================================================================================================================================================================================

Select a row from "Medicals Stock Movement Type Browsing" and click
"Edit". The description field is freely editable. Click "OK" to save
changes, or "Cancel" to abort the operation. If "OK" is clicked but the
description field is empty, a "Please insert a valid description" window
is shown. Click "OK" on the error window to return to the "Editing exam
type" panel.

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)
-   medicaldsrstockmovtype.MMVT\_ID\_DESC (movement type description)

[]{#anchor-145}[]{#anchor-146}[]{#anchor-147}3.1.7.3 Delete Medical Stock Movement Type
=======================================================================================

Removes a row from the "medicaldsrstockmovtype" database. Select a row
from "Medicals Stock Movement Type Browsing" and click "Delete". Click
"OK" on the confirmation window, or "Cancel" to abort the operation.

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)

[]{#anchor-148}[]{#anchor-149}[]{#anchor-150}3.1.7.4 Close Medical Stock Movement Type menu
===========================================================================================

Click "Close" on the "Medical Stock Movement Type Browsing" window to
return to main menu.

[]{#anchor-151}[]{#anchor-152}[]{#anchor-153}3.1.8 Medical Type![](Pictures/100000000000028F00000126C875180152383733.jpg){width="11.077cm" height="4.972cm"}
============================================================================================================================================================

The "Medical Type Browsing" table defines the different categories for
medicals and other items used by the hospital. Default types are shown
below.

![](Pictures/10000201000001610000009AB47D7C6737656B74.png){width="6.884cm"
height="3.016cm"}

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)
-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#anchor-154}[]{#anchor-155}[]{#anchor-156}3.1.8.1 New Medical Type![](Pictures/1000020100000157000000B080559A6474816FC0.png){width="7.588cm" height="3.895cm"}
=================================================================================================================================================================

Click "New" on the "Medical Type Browsing" window. Enter a one-character
code and a description (i.e. the name of the item). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)
-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#anchor-157}[]{#anchor-158}[]{#anchor-159}3.1.8.2 Edit Medical Type![](Pictures/100002010000015D000000B5D27902EAB34E7D81.png){width="7.588cm" height="3.953cm"}
==================================================================================================================================================================

Select a row from "Medical Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing Medical type"
panel.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)
-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#anchor-160}[]{#anchor-161}[]{#anchor-162}3.1.8.3 Delete Medical Type
========================================================================

Removes a row from the "medicaldsrtype" database. Select a row from
"Medicals Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)

[]{#anchor-163}[]{#anchor-164}[]{#anchor-165}3.1.8.4 Close Medical Type Menu
============================================================================

Click "Close" on the "Medical Type Browsing" window to return to main
menu.

[]{#anchor-166}[]{#anchor-167}[]{#anchor-168}3.1.9 Operation Type![](Pictures/10000000000002D1000001371DEE90CB09B5BD30.jpg){width="12.208cm" height="5.256cm"}
==============================================================================================================================================================

The "Operation Type Browsing" table defines the operation categories.
Default types are shown below:

![](Pictures/1000020100000158000000B8D782BFF25DB65851.png){width="6.622cm"
height="3.528cm"}

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)
-   operationtype.OCL\_DESC (operation type description)
-   operationtype.OCL\_TYPE (operation status, can be "MAJOR" or
    "MINOR"; currently unused)

[]{#anchor-169}[]{#anchor-170}[]{#anchor-171}3.1.9.1 New Operation Type![](Pictures/1000020100000109000000B2FAFD42CFD91E45C4.png){width="6.787cm" height="4.565cm"}
===================================================================================================================================================================

Click "New" on the "Operation Type Browsing" window. Enter a character
code and a description (i.e. the name of the operation). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)
-   operationtype.OCL\_DESC (operation type description)

[]{#anchor-172}[]{#anchor-173}[]{#anchor-174}3.1.9.2 Edit Operation Type![](Pictures/100002010000010D000000B40999FB8525EF2AA2.png){width="6.077cm" height="4.073cm"}
====================================================================================================================================================================

Select a row from "Operation Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing Medical type"
panel.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)
-   operationtype.OCL\_DESC (operation type description)

[]{#anchor-175}[]{#anchor-176}[]{#anchor-177}3.1.9.3 Delete Operation Type
==========================================================================

Removes a row from the "operationtype" database. Select a row from
"Operation Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)

[]{#anchor-178}[]{#anchor-179}[]{#anchor-180}3.1.9.4 Close Operation Type Menu
==============================================================================

Click "Close" on the "Operation Type Browsing" window to return to the
main menu.

[]{#anchor-181}[]{#anchor-182}[]{#anchor-183}3.1.10 Pregnant Treatment Type![](Pictures/10000000000002C600000138EA9691A66BEA836C.jpg){width="12.033cm" height="5.278cm"}
========================================================================================================================================================================

The "Pregnant Treatment Type Browsing" table defines the types of
treatments to pregnant mothers. Default types are shown below:

![](Pictures/1000020100000155000000C610F8028D901322B3.png){width="6.246cm"
height="3.632cm"}

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)
-   pregnanttreatmenttype.DESC(pregnant treatment type description)

[]{#anchor-184}[]{#anchor-185}[]{#anchor-186}3.1.10.1 New Pregnant Treatment Type![](Pictures/1000020100000106000000B220DB913227927111.png){width="6.565cm" height="4.436cm"}
=============================================================================================================================================================================

Click "New" on the "Operation Type Browsing" window. Enter a character
code and a description (i.e. the name of the treatment). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)
-   pregnanttreatmenttype.DESC(pregnant treatment type description)

[]{#anchor-187}[]{#anchor-188}[]{#anchor-189}3.1.10.2 Edit Pregnant Treatment Type![](Pictures/1000020100000106000000B654D3A0D11805C82B.png){width="6.565cm" height="4.535cm"}
==============================================================================================================================================================================

Select a row from "Pregnant Treatment Type Browsing" and click "Edit".
The description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing Pregnant
Treatment type" panel.

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)
-   pregnanttreatmenttype.PTT\_DESC(pregnant treatment type description)

[]{#anchor-190}[]{#anchor-191}[]{#anchor-192}3.1.10.3 Delete Pregnant Treatment Type
====================================================================================

Removes a row from the "pregnanttreatmenttype" database. Select a row
from "Pregnant Treatment Type Browsing" and click "Delete". Click "OK"
on the confirmation window, or "Cancel" to abort the operation.

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)

[]{#anchor-193}[]{#anchor-194}[]{#anchor-195}3.1.10.4 Close Pregnant Treatment menu
===================================================================================

Click "Close" on the "Pregnant Treatment Type Browsing" window to return
to the main menu.

[]{#anchor-196}[]{#anchor-197}[]{#anchor-198}3.1.11 Other Prices![](Pictures/10000201000001CF000000EB3D22857892970552.png){width="7.832cm" height="3.979cm"}
============================================================================================================================================================

Defines specific prices lists, which will be stored in a separate
"pricesothers" database.

[]{#anchor-199}[]{#anchor-200}[]{#anchor-201}3.1.11.1 New List
==============================================================

Click "New" on the "Other Prices Browser" (top left). A "New Price"
window opens. Enter a code and a description (both mandatory). Click
"OK" to confirm. If data are correct, the list is added, else a "Please
insert a code
/![](Pictures/1000020100000190000000B52EB55E278BF96BE9.png){width="7.832cm"
height="3.544cm"} description" window is shown. Click "OK" to return to
the former window.

Data:

-   pricesothers.OTH\_ID (primary key, list ID, auto-increment)
-   pricesothers.OTH\_CODE (list code)
-   pricesothers.OTH\_CODE (list description)

[]{#anchor-202}[]{#anchor-203}[]{#anchor-204}3.1.11.2 Edit List
===============================================================

Select a list from the browser and click "Edit". An "Edit Price" window
opens (identical to the "New Price" in 3.1.11.1). Both code and
description are editable. Click "OK" to save changes or "Cancel" to
abort. If data are correct, the list will be updated.

Data: see chapter 3.1.11.2

[]{#anchor-205}[]{#anchor-206}[]{#anchor-207}3.1.11.3 Delete List
=================================================================

Select a list from the browser and click "Delete". Then click "OK" on
the confirmation window to remove the list from the "pricesothers" DB,
or "Cancel" to abort.

Data:

-   pricesothers.OTH\_ID

[]{#anchor-208}[]{#anchor-209}[]{#anchor-210}3.1.11.4 Close Other Prices menu
=============================================================================

Click "Close" on the "Other prices browser" to return to OH's main menu.

[]{#anchor-211}[]{#anchor-212}[]{#anchor-213}3.1.12 Age Type![](Pictures/10000000000002CD0000012831628732C2D93EC0.jpg){width="12.15cm" height="5.017cm"}
========================================================================================================================================================

When a patient is register in OH's "patient" database, it's not always
possible to determine his/her age, since the birthdate is unknown. In
this case, the user can choose the age interval from a dropdown menu in
the "New Patient" option. The "Age type browsing" table below defines
the age ranges. Every row determines, respectively, the code of the
interval, the minimum age, the maximum age, and the description of the
range.![](Pictures/100002010000015D0000009EE7DB5609866B210B.png){width="8.26cm"
height="3.739cm"}

Data:

-   agetype.AT\_CODE (primary key, age type ID)
-   agetype.AT\_FROM (minimum age)
-   agetype.AT\_TO (maximum age)
-   agetype.AT\_DESC (description of the range)

[]{#anchor-214}[]{#anchor-215}[]{#anchor-216}3.1.12.1 Edit Age Type
===================================================================

Select a row from "Age Type Browsing" and click "Edit". The description
field is freely editable. Click "OK" to save changes, or "Cancel" to
abort the operation.

Data:

-   agetype.AT\_CODE (primary key, age type ID)
-   agetype.AT\_DESC (description of the range)

[]{#anchor-217}[]{#anchor-218}[]{#anchor-219}3.1.12.2 Close Age type menu
=========================================================================

Click "Close" on the "Age Type Browsing" window to return to the main
menu.

[]{#anchor-220}[]{#anchor-221}[]{#anchor-222}3.1.13 Vaccine Type![](Pictures/100000000000022B000000EF8A7F066F0FA73AD0.jpg){width="9.403cm" height="4.048cm"}
============================================================================================================================================================

The "Vaccine Type Browsing" table defines all vaccine types. Default
categories are:

-   C (Vaccines for children)
-   P (Vaccines for pregnant women)
-   N (Vaccines for adults, except pregnant
    women)![](Pictures/1000020100000159000000835BD78E869CC1B684.png){width="9.22cm"
    height="3.477cm"}

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)
-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#anchor-223}[]{#anchor-224}[]{#anchor-225}3.1.13.1 New Vaccine Type![](Pictures/1000020100000106000000B5267348896961019E.png){width="6.322cm" height="4.367cm"}
==================================================================================================================================================================

Click "New" on the "Vaccine Type Browsing" window. Enter a one-character
code and a description (i.e. the name of the treatment). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)
-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#anchor-226}[]{#anchor-227}[]{#anchor-228}3.1.13.2 Edit Vaccine Type![](Pictures/1000020100000104000000B02317C7EDDFA3DF64.png){width="6.445cm" height="4.38cm"}
==================================================================================================================================================================

Select a row from "Vaccine Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Edit vaccine type"
panel.

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)
-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#anchor-229}[]{#anchor-230}[]{#anchor-231}3.1.13.3 Delete Vaccine Type
=========================================================================

Removes a row from the "vaccinetype" database. Select a row from
"Vaccine Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   vaccinetype.VACT\_ID\_A (chiave primaria, identificativo del tipo di
    vaccino)

[]{#anchor-232}[]{#anchor-233}[]{#anchor-234}3.1.13.4 Close Vaccine type menu
=============================================================================

Click "Close" on the "Vaccine Type Browsing" window to return to the
main menu.

[]{#anchor-235}[]{#anchor-236}[]{#anchor-237}3.2 Hospital
=========================================================

![](Pictures/10000000000002A6000001DF6D27B058CCB9AC98.jpg){width="11.486cm"
height="8.128cm"}

Hospital location data are automatically printed on reports generated by
some OH functions, such as "Pharmacy -\> Pharmaceuticals" or "Accounting
-\> Bills Manager".

When the "Hospital Informations" window opens, only the "Edit" and
"Close" buttons are enabled, and information is not editable. Click
"Edit" to update the text fields, then "Update" to
save![](Pictures/100002010000012C0000014910A548505EE991F9.png){width="7.772cm"
height="8.521cm"} changes and "Close" to close the window and return to
the main menu.

Data:

hospital.HOS\_NAME (name)

hospital.HOS\_ADDR (address)

hospital.HOS\_CITY (city)

hospital.HOS\_TELE (phone number)

hospital.HOS\_FAX (fax number)

hospital.HOS\_EMAIL (e-mail)

hospital.HOS\_CURR\_COD (hospital's currency code)

[]{#anchor-238}[]{#anchor-239}[]{#anchor-240}3.3 Ward![](Pictures/10000000000002E3000001BEA3943352D00C02F3.jpg){width="12.532cm" height="7.544cm"}
==================================================================================================================================================

The "Ward" section allows the administrator to manage hospital wards.
Here are the mandatory attributes for every ward, shown in the "Wards
browser" table:

-   ward code, a character ID
-   ward name
-   number of beds
-   number of doctors
-   number of nurses
-   "has pharmacy", (1 if the ward can access to pharmacy in the
    "Pharmacy -\> P.S. Ward" menu, else 0);
-   "male"/"female", boolean values to identify wards accessible to men
    and/or
    women.![](Pictures/100002010000047F000000B0A8F048594965D2F0.png){width="16.99cm"
    height="2.598cm"}

Optional attributes include phone number, fax number, e-mail address.

Data:

-   ward.WRD\_ID (primary key, ward ID)
-   ward.WRD\_NAME (ward name)
-   ward.WRD\_TELE (phone number)
-   ward.WRD\_FAX (fax number)
-   ward.WRD\_EMAIL (e-mail)
-   ward.WRD\_NBEDS (number of beds)
-   ward.WRD\_NQUA\_NURS (number of nurses)
-   ward.WRD\_NDOC (number of doctors)
-   ward.WRD\_IS\_PHARMACY (1 if the ward has its own pharmacy, else 0)
-   ward.WRD\_IS\_MALE (1 if men are allowed, else 0)
-   ward.WRD\_IS\_FEMALE (1 if women are allowed, else 0)

[]{#anchor-241}[]{#anchor-242}[]{#anchor-243}3.3.1 New Ward![](Pictures/1000020100000190000001B15E3B22683457E533.png){width="7.285cm" height="7.886cm"}
=======================================================================================================================================================

Adds a new ward in the hospital. Click "New" in the "Wards browser". A
"New ward record" window opens. Fill the mandatory text fields, marked
with the \* sign, and add phone, fax and e-mail contacts if necessary.
Tick the "ward with pharmacy" checkbox if the ward will have its own
pharmacy; do the same on "male ward" if it'll be allowed to men, and on
"female ward" if women can access in it. Click "OK" to confirm or
"Cancel" to abort the operation. If all data required are correct, the
ward will be added to the "ward" database, else an error window is
shown:

-   "Code already in use"
-   "Please insert a code" (if the code character has not been added)
-   "Insert a valid beds/nurses/doctors/ number" (if a non-numeric value
    has been added).

After all unsuccessful cases click "OK" to return to the "New ward
record" window.

Data:

see chapter 3.3

[]{#anchor-244}[]{#anchor-245}[]{#anchor-246}3.3.2 Edit Ward![](Pictures/100002010000018F000001B443C66B7A87938F33.png){width="7.285cm" height="7.96cm"}
=======================================================================================================================================================

Select a row form "Wards Browser" and click "Edit". An "Editing ward
record" window opens; all elements except the code are editable. Once
changes have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the ward will be updated in
the "ward" database, else an error window is shown (see 3.3.1).

Data:

see chapter 3.3

[]{#anchor-247}[]{#anchor-248}[]{#anchor-249}3.3.3 Delete Ward![](Pictures/100002010000025C00000126E9D8EC20A8957A77.png){width="10.238cm" height="4.979cm"}
===========================================================================================================================================================

Removes a ward from the "ward" database, if it has no patients
registered in the "Admission/Patient" menu. Select a row form "Wards
Browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

![](Pictures/100002010000025C000000C51DBB5C047FCDEB01.png){width="10.238cm"
height="3.337cm"}

If there's at least one patient admitted in the selected ward, there
will be no deletion and a "Selected ward has X patients" window is
shown. Pictured left is the example of the children ward, that has 123
patients
registered.![](Pictures/10000201000002100000011E07BB8FD5710BA5E7.png){width="10.238cm"
height="5.546cm"}

Here is a screenshot from the "Admission/Patient" window, where 7 of the
123 patients from the children ward are visible (codes from 474 to 482).
All patients from a ward must be discharged before removing it.

Data:

-   ward.WRD\_ID (primary key, ward ID)
-   admission.WRD\_ID\_A (foreign key referencing to "ward", to check if
    there are admitting patients in the selected ward)

[]{#anchor-250}[]{#anchor-251}[]{#anchor-252}3.3.4 Close Ward menu
==================================================================

Click "Close" on the "Wards Browser" window to return to the main menu.

[]{#anchor-253}[]{#anchor-254}[]{#anchor-255}3.4 Disease![](Pictures/10000000000002CE0000018497D26A6237C3EA17.jpg){width="12.137cm" height="6.562cm"}
=====================================================================================================================================================

The "Diseases browser" table contains all diseases registered in the
"disease" database. Every row shows the disease code, the type (3.1.5)
and the disease name.

![](Pictures/1000020100000277000001862D5A4FF25B5DA4A6.png){width="10.67cm"
height="6.595cm"}

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)
-   disease.DIS\_DCL\_ID\_A (foreign key referencing to "diseasetype")
-   disease.DIS\_DESC (disease name)

[]{#anchor-256}[]{#anchor-257}[]{#anchor-258}3.4.1 Select Disease Type![](Pictures/10000201000002100000017A2E6418DAE476875B.png){width="8.959cm" height="6.415cm"}
==================================================================================================================================================================

To help search a disease, click the dropdown menu on the bottom of the
"Diseases Browser" window, and select a type, or "ALL" to visualize all
records.

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)
-   disease.DIS\_DCL\_ID\_A (foreign key referencing to "diseasetype")

[]{#anchor-259}[]{#anchor-260}[]{#anchor-261}3.4.2 New Disease
==============================================================

Adds a new disease to the "disease" database. Click "New" on the
"Diseases browser" window. A "New disease" window opens. Select the type
from the dropdown menu, enter a code and the description (i.e. the name
of the disease, used in "OPD" and "Diagnosis IN" / "Diagnosis OUT" lists
of the "Admission/Patient" menu). Then tick at least one checkbox to
assign the disease to "OPD"
(OutPatient![](Pictures/10000201000001CB000000D6484314A0FF2015B9.png){width="8.176cm"
height="3.812cm"} Dept.), "IPD IN" ("Diagnosis IN") and "IPD OUT"
("Diagnosis OUT"). Click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the disease will be added
to the "disease" database, else an error window is shown:

-   "Code already in use"
-   "Please insert a code" (if the code character has not been added)
-   "Insert a valid description" (if the description has not been
    added).

After all unsuccessful cases click "OK" to return to the "New disease"
window.

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)
-   disease.DIS\_DCL\_ID\_A (foreign key referencing to "diseasetype")
-   disease.DIS\_DESC (disease name)
-   disease.DIS\_OPD\_INCLUDE (1 if the disease is included in the "OPD"
    list, else 0)
-   disease.DIS\_IPD\_IN\_INCLUDE (1 if the disease is included in the
    "IPD IN" list, else 0)
-   disease.DIS\_IPD\_OUT\_INCLUDE (1 if the disease is included in the
    "IPD OUT" list, else 0)

[]{#anchor-262}[]{#anchor-263}[]{#anchor-264}3.4.3 Edit Disease![](Pictures/10000201000001CD000000D6761A6CCA4A041D00.png){width="8.495cm" height="3.942cm"}
===========================================================================================================================================================

Select a row from "Diseases Browser" and click "Edit". An "Edit disease"
window opens; all elements except the code are editable. Once changes
have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the disease will be updated
in its database, else an error window is shown (see 3.4.2).

Data:

see chapter 3.4.2

[]{#anchor-265}[]{#anchor-266}[]{#anchor-267}3.4.4 Delete Disease
=================================================================

Removes a disease from its database. Select a row from "Diseases
browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)

[]{#anchor-268}[]{#anchor-269}[]{#anchor-270}3.4.5 Close Disease menu
=====================================================================

Click "Close" on the "Diseases Browser" window to return to the main
menu.

[]{#anchor-271}[]{#anchor-272}[]{#anchor-273}3.5 Exams![](Pictures/100000000000025B00000258AF4079F29A5AF05A.jpg){width="10.206cm" height="10.171cm"}
====================================================================================================================================================

The "Exams browsing" table defines all exams recorded in the "exam"
database and used in "Laboratory", "Accounting -\> New Bill" and
"Printing -\> Exams List" menus. Every row shows the exam code, the exam
type (3.1.6), its description, the procedure applied ("1" or "2") and
the default result (3.5.5).

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)
-   exam.EXA\_EXC\_ID\_A (foreign key referencing "examtype", exam type)
-   exam.EXA\_DESC (exam name)
-   exam.EXA\_PROC (exam procedure, "1" or "2")
-   exam.EXA\_DEFAULT (default
    result)![](Pictures/1000020100000438000001641940073C1D1E8274.png){width="16.99cm"
    height="5.6cm"}

[]{#anchor-274}[]{#anchor-275}[]{#anchor-276}3.5.1 Select Exam type
===================================================================

To help search an exam, click the dropdown menu on the bottom of the
"Exams Browsing" window, and select a type, or "ALL" to visualize all
records.

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)
-   exam.EXA\_EXC\_ID\_A (foreign key referencing "examtype", exam type)

[]{#anchor-277}[]{#anchor-278}[]{#anchor-279}3.5.2 New Exam![](Pictures/10000201000001AD0000012E0355301FC78F734D.png){width="7.248cm" height="5.099cm"}
=======================================================================================================================================================

Click "New" on the "Exams Browsing" window. A "New exam" window opens.
Select the exam type from the first dropdown menu, enter the code, a
description (i.e. the name of the exam), select the procedure type and
enter the default result. Click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the exam will be added to
the "exam" database, else an error window is shown:

-   "Change the code because is already in use"
-   "Insert a valid code and/or description"

After all unsuccessful cases click "OK" to return to the "New exam"
window.

Data:

see chapter 3.5

[]{#anchor-280}[]{#anchor-281}[]{#anchor-282}3.5.3 Edit Exam![](Pictures/10000201000001AC000001324A5FA05116CCE876.png){width="7.248cm" height="5.182cm"}
========================================================================================================================================================

Select a row from "Exams Browsing" and click "Edit". An "Edit exam"
window opens; only the description and default result are editable. Once
changes have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the exam will be updated in
its database, else an error window is shown (see 3.5.2).

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)
-   exam.EXA\_DESC (exam name)
-   exam.EXA\_DEFAULT (default result)

[]{#anchor-283}[]{#anchor-284}[]{#anchor-285}3.5.4 Delete Exam
==============================================================

Removes a exam from its database. Select a row from "Exams browsing" and
click "Delete". Click "OK" on the confirmation window, or "Cancel" to
abort the operation.

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)

[]{#anchor-286}[]{#anchor-287}[]{#anchor-288}3.5.5 Exam result![](Pictures/10000201000001AC000000B02B9AA33A52CE8C54.png){width="6.632cm" height="2.727cm"}
==========================================================================================================================================================

Every exam has a set of possible results (for example: positive /
negative). The outcome of an exam is reported in the "Laboratory
browsing" table, pictured left (see also chapter 6).

![](Pictures/10000201000001CC0000005701C840AF43D48B89.png){width="9.721cm"
height="1.838cm"}

OH allows to manage the set of results for every recorded exam. Select a
row from the "Exam Browsing" window and click "Result". A new window
shows a table with all outcomes, each with a code and a description.
Here is an example of the "SUGAR" glucose exam (highlighted in the table
at chapter
3.5).![](Pictures/10000201000001AF0000010D84062A129F92558E.png){width="6.632cm"
height="4.14cm"}

To add a new result, click "New", enter the description, then click "OK"
to confirm or "Cancel" to abort the operation. Considering the example
shown above, a "Very Low" level is added to "High", "Low" and "Normal".

The "Sugar results" table is updated with the new row (the code is
automatically generated since it's an auto-increment integer).

To remove a result, click "Delete" then click "OK" on the confirmation
window, or "Cancel" to abort the operation.

To close the results table, click "Close" to return to the "Exams
browsing" table.

Data:

-   exam.EXA\_ID\_A (exam ID)
-   examrow.EXR\_ID (primary key, result ID)
-   examrow.EXR\_EXA\_ID\_A (foreign key referencing to exam.EXA\_ID\_A)
-   examrow.EXR\_DESC (result description)

[]{#anchor-289}[]{#anchor-290}[]{#anchor-291}3.5.6 Close Exams menu
===================================================================

Click "Close" on the "Exam Browsing" window to return to the main menu.

[]{#anchor-292}[]{#anchor-293}[]{#anchor-294}3.6 Operation![](Pictures/10000000000002DA000001E00AD067EA3FF2FD81.jpg){width="12.351cm" height="8.124cm"}
=======================================================================================================================================================

The "Operations browser" table defines all operations recorded in the
"operation" database. Every row shows the operation code, the operation
type (3.1.9) and its description.

![](Pictures/1000020100000239000001988888D881056DE330.png){width="9.645cm"
height="6.909cm"}

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)
-   operationtype.OCL\_ID\_A (foreign key referencing "operation",
    operation type)
-   operation.OPE\_DESC (operation name)

[]{#anchor-295}[]{#anchor-296}[]{#anchor-297}3.6.1 Select operation type
========================================================================

To help search an operation, click the dropdown menu on the bottom of
the "Operations browser" window, and select a type, or "ALL" to
visualize all records.

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)
-   operationtype.OCL\_ID\_A (foreign key referencing "operation",
    operation type)

[]{#anchor-298}[]{#anchor-299}[]{#anchor-300}3.6.2 New Operation![](Pictures/1000020100000261000000DED6A5155A7C9FA370.png){width="10.388cm" height="3.785cm"}
=============================================================================================================================================================

Click "New" on the "Operations Browser" window. A "New operation record"
window opens. Select the operation type from the first menu, enter the
code, a description (i.e. the name of the operation). Status - major or
minor - is currently unused in OH, however the user can choose it with
the radio buttons. Click "OK" to confirm or "Cancel" to close the window
without saving data inserted. If all data required are correct, the
operation will be added to the "operation" database, else an error
window is shown:

-   "Code already in use"
-   "Please insert a valid description"
-   "Operation already present" (if there's one with the same
    description).

After all unsuccessful cases click "OK" to return to the "New operation
record" window.

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)
-   operationtype.OCL\_ID\_A (foreign key referencing "operation",
    operation type)
-   operation.OPE\_DESC (operation name)
-   operation.OPE\_STAT (operation status, "MAJOR" or "MINOR", currently
    unused)

[]{#anchor-301}[]{#anchor-302}[]{#anchor-303}3.6.3 Edit Operation![](Pictures/1000020100000265000000E050802B7825D89D30.png){width="10.388cm" height="3.794cm"}
==============================================================================================================================================================

Select a row from "Operations Browser" and click "Edit". An "Editing
operation record" window opens; only description and status are
editable. Once changes have been made, click "OK" to confirm or "Cancel"
to return to close the window without saving changes. If data required
are correct, the operation will be updated in its database, else an
error window is shown (see 3.6.2).

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)
-   operation.OPE\_DESC (operation name)
-   operation.OPE\_STAT (operation status, "MAJOR" or "MINOR", currently
    unused)

[]{#anchor-304}[]{#anchor-305}[]{#anchor-306}3.6.4 Delete Operation
===================================================================

Removes an operation from its database. Select a row from "Operations
browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the deletion.

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)

[]{#anchor-307}[]{#anchor-308}[]{#anchor-309}3.6.5 Close Operation menu
=======================================================================

Click Close" on the "Operations browsing" window to return to the main
menu.

[]{#anchor-310}[]{#anchor-311}[]{#anchor-312}3.7 Vaccine![](Pictures/10000000000002B3000001C5207EB70C7638B78D.jpg){width="11.68cm" height="7.68cm"}
===================================================================================================================================================

The "Vaccine browser" table defines all vaccines recorded in the
"vaccine" database. Every row shows the code ID, the vaccine type
(3.1.13) and its description.

![](Pictures/10000201000002A000000102B23AAD284F95ECC8.png){width="11.391cm"
height="4.366cm"}

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)
-   vaccine.VAC\_VACT\_ID\_A (foreign key referencing "vaccinetype"
    database)
-   vaccine.VAC\_DESC (vaccine description)

[]{#anchor-313}[]{#anchor-314}[]{#anchor-315}3.7.1 Select Vaccine Type
======================================================================

To help search a vaccine, click the dropdown menu on the bottom of the
"Operations browser" window, and select a type, or "ALL" to visualize
all records.

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)
-   vaccine.VAC\_VACT\_ID\_A (foreign key referencing "vaccinetype"
    database)

[]{#anchor-316}[]{#anchor-317}[]{#anchor-318}3.7.2 New Vaccine![](Pictures/100002010000015B000000F4329D03C4CAD0C35C.png){width="7.214cm" height="5.073cm"}
==========================================================================================================================================================

Click "New" on the "Vaccine Browser" window. A "New vaccine record"
window opens. Select the vaccine type from the dropdown menu, enter the
code and description (i.e. the name of the vaccine). Click "OK" to
confirm or "Cancel" to abort the operation. If all data required are
correct, the vaccine will be added to the "vaccine" database, else an
error window is shown:

-   "Code already in use"
-   "Please insert a code/description"

After both unsuccessful cases click "OK" to return to the "New vaccine
record" window.

Data:

-   see chapter 3.7

[]{#anchor-319}[]{#anchor-320}[]{#anchor-321}3.7.3 Edit Vaccine![](Pictures/100002010000015B000000F76BECF6DA03AB1401.png){width="7.214cm" height="5.136cm"}
===========================================================================================================================================================

Select a row from "Vaccine Browser" and click "Edit". An "Editing
vaccine record" window opens; only the description field is editable.
Once changes have been made, click "OK" to confirm or "Cancel" to return
to close the window without saving changes. If data required are
correct, the operation will be updated in its database, else an error
window is shown (see 3.7.2).

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)
-   vaccine.VAC\_DESC (vaccine description)

[]{#anchor-322}[]{#anchor-323}[]{#anchor-324}3.7.4 Delete Vaccine
=================================================================

Removes a vaccine from its database. Select a row from "Vaccine browser"
and click "Delete". Click "OK" on the confirmation window, or "Cancel"
to abort the deletion.

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)

[]{#anchor-325}[]{#anchor-326}[]{#anchor-327}3.7.5 Close Vaccine menu
=====================================================================

Click "Close" on the "Vaccine browser" window to return to the main
menu.

[]{#anchor-328}[]{#anchor-329}[]{#anchor-330}3.8 Prices Lists![](Pictures/10000000000002C50000025B594C7D5E0BF650D7.jpg){width="12.024cm" height="10.215cm"}
===========================================================================================================================================================

The "Price Lists" menu allows the administrator to manage pricing for
medicals, exams and operations, creating customized price lists for
different users. "The Prices Browser" window (below) shows all elements
for a single list, sorted in "Exams", "Operations", "Medicals" and
"Others" folders. Click on tre triangle next to each folder to expand
its content.

![](Pictures/10000201000001CB00000095ACF3BE1229D22787.png){width="7.789cm"
height="2.531cm"}

Data (for every item of the list):

-   prices.PRC\_ID (primary key, item - price list
    pair)![](Pictures/10000201000001CD00000141C606A6D47F05BA21.png){width="7.789cm"
    height="5.422cm"}
-   prices.PRC\_LST\_ID (foreign key referencing to the "pricelists"
    database)
-   prices.PRC\_GRP (item category)
-   prices.PRC\_ITEM (item ID)
-   prices.PRC\_DESC (item description)
-   prices.PRC\_PRICE (item price)

Data (for price lists):

-   pricelists.LST\_ID (primary key, price list ID)
-   pricelists.LST\_CODE (price list code)
-   pricelists.LST\_NAME (price list name)
-   pricelists.LST\_DESC (price list description)
-   pricelists.LST\_CURRENCY (currency used in the list)

[]{#anchor-331}[]{#anchor-332}[]{#anchor-333}3.8.1 Choose List![](Pictures/100002010000020C00000094E5BB332252FE5683.png){width="8.892cm" height="2.514cm"}
==========================================================================================================================================================

The "Prices Browser" window has a dropdown menu on the top, to
choose![](Pictures/100002010000015A000000AAE9948B0E9653EEB4.png){width="6.32cm"
height="3.104cm"} between the lists created with the "Manage List"
option (3.8.2). Every time the user switches to a different list, a
confirmation window (right) is shown. Click "OK" to confirm, or Cancel
to return to the current list.

Data:

-   pricelists.LST\_ID
-   pricelists.LST\_CODE

[]{#anchor-334}[]{#anchor-335}[]{#anchor-336}3.8.2 Manage Lists![](Pictures/1000020100000162000000C3874B58661C959217.png){width="5.99cm" height="3.307cm"}
==========================================================================================================================================================

Click the "Manager Lists" button on the right top of the "Prices
browser" window. A "List browser" window opens. It has a table with the
list records, showing the code, the name, the description and the
currency used.

Some buttons on the bottom allow to create, edit and delete lists.

Data:

-   pricelists.LST\_ID (primary key, not shown in the table)
-   pricelists.LST\_CODE (price list code)
-   pricelists.LST\_NAME (price list name)
-   pricelists.LST\_DESC (price list description)
-   pricelists.LST\_CURRENCY (currency used in the list)

[]{#anchor-337}[]{#anchor-338}[]{#anchor-339}3.8.2.1 New List![](Pictures/1000020100000101000000F434EEAA2ACD7EB162.png){width="5.35cm" height="5.087cm"}
========================================================================================================================================================

Click "New" on the "List Browser" window. Enter the code, the name, the
description and the currency used in the list.

Click "OK" to confirm or "Cancel" to abort the operation. If all data
have been added, the list will be added to the "pricelists" database,
else a "Please insert a code/name/description/currency" is shown,
depending of the field(s) left empty. In this case, click "OK" to return
to the "New List" window.

Data: see chapter 3.8.2

[]{#anchor-340}[]{#anchor-341}[]{#anchor-342}3.8.2.2 Copy List![](Pictures/100002010000011100000071064CFE92EB9DF368.png){width="4.611cm" height="1.921cm"}
==========================================================================================================================================================

This option creates a copy of the list selected, with prices multiplied
by a given factor. Select the list from the "List Browser" table and
click "Copy". A sequence of 4 panels
opens.![](Pictures/100002010000010F000000929490289FF1523CFD.png){width="4.611cm"
height="2.471cm"} Enter the name of the new list in the first window.
Click "OK" and enter the multiplying factor in the second panel; Click
"OK" and enter the rounding factor. Multiplied prices will be rounding
to the next higher multiple of the value inserted. After clicking "OK",
a "List Copied" message window is shown. Click "OK" to close it, and the
list will be added to the "priceslists"
database.![](Pictures/10000201000001100000008294BEC606050240A0.png){width="4.611cm"
height="2.208cm"}

Data:

see chapter 3.8.2

![](Pictures/10000201000001100000006D89E0C1CCE05F2978.png){width="4.611cm"
height="1.854cm"}

[]{#anchor-343}[]{#anchor-344}[]{#anchor-345}3.8.2.3 Edit List![](Pictures/10000201000000FE000000EB0D9AB4A86AF478E3.png){width="5.632cm" height="5.211cm"}
==========================================================================================================================================================

Select a row from "List browser" and click "Edit". The "Edit List"
window opens. All data are freely editable. Click "OK to confirm or
"Cancel" to abort the operation. If all data have been added, the list
will be updated, else an error window is shown (3.8.2.1).

Data :

see chapter 3.8.2

[]{#anchor-346}[]{#anchor-347}[]{#anchor-348}3.8.2.4 Delete List![](Pictures/10000201000001DF000000A9F628DE31939AEE90.png){width="9.029cm" height="3.186cm"}
============================================================================================================================================================

Removes a price list from its database. Select a row from "List browser"
and click "Delete". Click "OK" on the confirmation window (left), or
"Cancel" to abort the deletion.

Data:

-   pricelists.LST\_ID

[]{#anchor-349}[]{#anchor-350}[]{#anchor-351}3.8.2.5 Close List Browser
=======================================================================

Click "Close" on the "List Browser" window to return to OH's main menu.

[]{#anchor-352}[]{#anchor-353}[]{#anchor-354}3.8.3 Save List![](Pictures/1000020100000180000000ACF2946C63D5ABDF02.png){width="6.657cm" height="2.981cm"}
========================================================================================================================================================

After editing the items within a price list, changes must be saved
before closing the "Prices browser" window. Click the "SAVE" button and
then "OK" on the confirmation window (left). To discard changes, click
"Cancel".

[]{#anchor-355}[]{#anchor-356}[]{#anchor-357}3.8.4 Print List
=============================================================

Generates a report containing the rows of the selected list. Click
"Print" on the "Prices Browser" window. The Jasper Viewer opens; it has
some buttons (below) to save in .PDF, print, update, scroll the pages,
fit the document to the computer screen and
zoom.![](Pictures/10000201000001A80000001C1D499928612D5AFC.png){width="14.958cm"
height="0.988cm"}

[]{#anchor-358}[]{#anchor-359}[]{#anchor-360}3.8.5 Close Price Lists menu
=========================================================================

Click "Close" on the "Prices Browser" menu to return to the main menu.

[]{#anchor-361}[]{#anchor-362}[]{#anchor-363}3.9 Supplier![](Pictures/100000000000029800000211C174DB70395BFC51.jpg){width="11.229cm" height="8.966cm"}
======================================================================================================================================================

The "Supplier Browser" menu tracks the list of the hospital's suppliers.
Every row shows the ID, the name, and some information about the
supplier (address, tax number, phone and fax numbers, e-mail address,
optional notes). The "Deleted" checkbox is ticked after a "Delete
Supplier" operation (see 3.9.3).

![](Pictures/10000201000003EC000000995686DD3E79C893E3.png){width="16.99cm"
height="2.586cm"}

Data:

-   supplier.SUP\_ID (primary key, supplier ID)
-   supplier.SUP\_NAME (supplier name)
-   supplier.SUP\_ADDRESS (supplier address)
-   supplier.SUP\_TAXCODE (supplier tax number ID)
-   supplier.SUP\_PHONE (supplier phone number)
-   supplier.SUP\_FAX (supplier fax number)
-   supplier.SUP\_EMAIL (supplier e-mail address)
-   supplier.SUP\_NOTE (optional notes)
-   supplier.SUP\_DELETED ("Y" if the supplier was deleted with after
    the "Delete Supplier", else "N")

![](Pictures/100002010000013A0000015CAD012F505FFDF623.png){width="5.308cm"
height="5.883cm"}

[]{#anchor-364}[]{#anchor-365}[]{#anchor-366}3.9.1 New Supplier
===============================================================

Click "New" on the "Supplier Browser" window. A "New supplier" window
opens. Enter the attributes seen in chapter 3.9. "Name" is the only
mandatory field, while "ID" is auto-generated. Click "OK" to confirm or
"Cancel" to abort the operation. If the name has been inserted, the
supplier will be added to the "supplier" database, else a "Please insert
a name" window is shown. In this case, click "OK" to return to the "New
supplier" window.

Data:

-   supplier.SUP\_NAME (supplier name)
-   supplier.SUP\_ADDRESS (supplier address)
-   supplier.SUP\_TAXCODE (supplier tax number ID)
-   supplier.SUP\_PHONE (supplier phone number)
-   supplier.SUP\_FAX (supplier fax number)
-   supplier.SUP\_EMAIL (supplier e-mail address)
-   supplier.SUP\_NOTE (optional notes)

[]{#anchor-367}[]{#anchor-368}[]{#anchor-369}3.9.2 Edit Supplier![](Pictures/10000201000001390000015E63F8C418B249E7C8.png){width="5.308cm" height="5.916cm"}
============================================================================================================================================================

Select a row from "Supplier browser" and click "Edit". The "Edit List"
window opens. All data except the ID, are freely editable. If the
"Deleted" checkbox has been previously ticked, the editing options
allows to undelete the supplier (see 3.9.3). If the name has been
inserted, the supplier will be updated, else a "Please insert a name"
window is shown. In this case, click "OK" to return to the "Edit
supplier" window.

Data:

see chapter 3.9

[]{#anchor-370}[]{#anchor-371}[]{#anchor-372}3.9.3 Delete Supplier
==================================================================

Select a row from "Supplier browser" and click "Delete". This operation
is different from other deletion operations. The record is not removed
from the database, it will be unactive for the OH menus needing the
supplier DB. Click "Yes" on the confirmation window to virtually remove
the supplier, else "No" to abort the operation. If the "deletion" is
confirmed, the "Deleted" checkbox on the "Supplier browser" table is
checked. To undelete a supplier, select it and, click "Edit" and
deselect the checkbox
(3.9.2).![](Pictures/10000201000003EC00000097345F5A956CDA91C2.png){width="16.99cm"
height="2.554cm"}

Data:

-   supplier.SUP\_ID
-   supplier.SUP\_DELETED

[]{#anchor-373}[]{#anchor-374}[]{#anchor-375}3.9.4 Close Supplier menu
======================================================================

Click "Close" on the "Supplier Browser" window to return to the main
menu.

[]{#anchor-376}[]{#anchor-377}[]{#anchor-378}3.10 SMS Manager![](Pictures/10000000000001E7000001F26213B861E1F95509.jpg){width="8.232cm" height="8.44cm"}
========================================================================================================================================================

The SMS option allows the user to automatically send messages to
patients with a memo of their scheduled hospital visits. The "SMS
Manager" window shows all messages sent in the period between two given
dates. The table reports the date of the message's sending, the date and
the time of the scheduled visit, the patient's telephone number, the
text of the SMS and a "Sent" status, to acknowledge if the message has
been sent to the patient's phone.

Data:

-   sms.SMS\_ID (primary key, message ID)
-   sms.SMS\_DATE (date and time of the message's sending)
-   sms.SMS\_DATE\_SCHED (date and
    time![](Pictures/10000201000002030000009C89BC65B111C7E7EC.png){width="10.121cm"
    height="3.064cm"} of the visit)
-   sms.SMS\_NUMBER (patient's phone number)
-   sms.SMS\_TEXT (SMS text)
-   sms.SMS\_USER (OH user which sent the message)
-   sms.SMS\_MOD (OH menu from which the SMS was sent)
-   sms.SMS\_MOD\_ID (patient ID - retained from patient.PAT\_ID - who
    receives the message)

[]{#anchor-379}[]{#anchor-380}[]{#anchor-381}3.10.1 Select date interval![](Pictures/1000020100000256000000E2905BA2E3C41B4C0B.png){width="9.088cm" height="3.434cm"}
====================================================================================================================================================================

To help search SMS sent on a given time interval, the user can type the
DD/MM/YYYY "from" and "to" dates on the top of the "SMS Manager" window,
or choosing them clicking on the calendar icons. This will open a
calendar application. Choose the month from the dropdown menu and the
year, then click on the day number; the selected date is automatically
inserted. If the dates are correct, they'll be showed in green, and the
table will show only SMS sent in the selected range.

Data:

-   sms.SMS\_ID
-   sms.SMS\_DATE

[]{#anchor-382}[]{#anchor-383}[]{#anchor-384}3.10.2 New SMS![](Pictures/1000020100000172000000FACDAAC170A838195D.png){width="6.265cm" height="4.23cm"}
======================================================================================================================================================

To send an SMS, click "New" on the "SMS Manager" window. Enter the
patient's scheduled date either by typing it in a DD/MM/YY format or by
clicking on the calendar icon (3.10.1).

![](Pictures/1000020100000173000000C8F15DB21CA5107FE7.png){width="6.265cm"
height="3.381cm"}

Then enter the scheduled time either by typing it in HH:MM format or by
clicking on the clock icon. Click on the hour and the minute on the new
window (right), then click "OK" to confirm and return to the "New SMS"
window.![](Pictures/1000020100000252000001773B6C1235D550EC4A.png){width="10.04cm"
height="6.334cm"}

Type the phone number, or choose it by clicking on the tag icon. A
"Patient Selection" window opens (left). Select a row and click
"Select"; the number will be automatically inserted. Finally, enter the
message and click "OK" to send the SMS. If the text and the phone number
have been inserted, the message will be sent, else an error window is
shown:

-   "Please insert a text"
-   "Please insert a valid telephone number"

After all unsuccessful cases click "OK" to return to the "New SMS"
window.

Data: see chapter 3.10

[]{#anchor-385}[]{#anchor-386}[]{#anchor-387}3.10.3 Delete SMS
==============================================================

Select a row from "SMS manager" and click "Delete". Click "Yes" on the
confirmation window to remove the sms form the "sms" database, else "No"
to abort the operation.

Data:

-   sms.SMS\_ID

[]{#anchor-388}[]{#anchor-389}[]{#anchor-390}3.10.4 Close SMS Manager menu
==========================================================================

Click "Close" on the "SMS manager" window to return to the main menu.

[]{#anchor-391}[]{#anchor-392}[]{#anchor-393}4. OPD (OutPatient Department)![](Pictures/1000000000000222000002793674260E11153137.jpg){width="9.23cm" height="10.702cm"}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

The "OPD" table records all patient's visits. It shows the date, the
visit ID, the patient's name, its sex and age, the disease for which the
patient entered the hospital, the disease type and the patient's status.
The current OPD table, with extended features, has been implemented
since OH 1.3. Row 16 in the rsc/generalData.properties is
"OPDEXTENDED=yes"; replace "yes" with "no" to open the "OPD" menu with
the old version.

Data:

-   opd.OPD\_DATE (visit date)
-   opd.OPD\_ID (primary key, visit ID)
-   opd.OPD\_PAT\_ID (foreign key referencing the "patient" database)
-   opd.OPD\_SEX (patient sex)
-   opd.OPD\_AGE (patient age)
-   opd.OPD\_DIS\_ID\_A (foreign key referencing the "disease" database,
    patient diagnosis)
-   disease.DIS\_DCL\_ID\_A (foreign key referencing the "diseasetype"
    DB, diagnosis type)
-   opd.OPD\_NEW\_PAT (patient status. "N" for "New Attendance","R" for
    "Re-attendance", see chapter
    4.2)![](Pictures/10000201000002F9000001306FF97B791206AF46.png){width="12.903cm"
    height="5.159cm"}

[]{#anchor-394}[]{#anchor-395}[]{#anchor-396}4.1 Search Patient
===============================================================

The left-side panel provides some tools that can be combined to help
search records:

-   Disease search: On the top of the window, there are two related
    dropdown menus. Choose the disease type from the first one, or "All
    Type" for all elements defined in the "General Data -\> Types
    -\>Disease Type". Then select a disease from the second menu, or
    "All Disease". If a specific type has been chosen, the menu shows
    only the elements belonging to that type.
-   Date search: Type two dates in the "Date From" and "Date To" fields,
    in a DD, MM, YYYY format, to seek records added in a determined date
    interval. If "Date From" is greater than "Date To", a "Date from
    must be lower than date to" window pops up. Click "OK" to return to
    the OPD browser.
-   Age search: Type two values in the "Age From" and "Age To" fields to
    seek records of patients in a determined age range. If "Age From" is
    greater than "Age To", an "Age from must be lower than Age to"
    window pops up. Click "OK" to return to the OPD browser. Default
    values are both 0, meaning no patient age restriction.
-   Sex: Select between "All", "Male" and "Female" radio buttons,
    according to patient sex.
-   OH Patient: Select between "All", "New attendance" and "Female"
    radio buttons, according to the status. A new attending patient is
    making the first visit for a certain diagnosis, while a re-attending
    patient returns - once or multiple times - for the
    same![](Pictures/10000201000002E20000012DC05273E12D278144.png){width="12.502cm"
    height="5.096cm"} diagnosis, after being a "new" the first time.

Once the filters have been selected, click "Search" to visualize the
results. The number of matching records is shown under the button.

Data:

see chapter 4.

[]{#anchor-397}[]{#anchor-398}[]{#anchor-399}4.2 New OPD registration![](Pictures/10000201000002B4000001ED4AE81DF72A70213E.png){width="11.742cm" height="8.366cm"}
==================================================================================================================================================================

Click "New" on the OPD browser. A "New OPD registration" window opens.
Select the patient status clicking on the buttons on the top of the
window (see chapter 4.1). In case of re-attendance, the last OPD's visit
is visible after selecting the patient.

![](Pictures/100002010000023700000065B1AE3A726840DB13.png){width="9.613cm"
height="1.72cm"}

Enter the patient's name clicking either on the magnifier icon or the
pencil icon. The former opens a dropdown menu with the list of
registered patients (left); choose one from this list. The latter opens
a "New Patient" window, if it's not recorded in OH (see chapter 8.1). To
help search an existing name, type a sub-string in the "Search" field,
then click the magnifier icon to choose the patient whose name contains
that
sub-string.![](Pictures/100002010000019B000001F96498189437E434FB.png){width="6.966cm"
height="8.555cm"}

Once the attendee has been chosen, his/her information is shown on the
lower half of the "New OPD" panel; if it's a re-attendance, the most
recent recorded visit appears ("Last OPD visit", pictured left). Choose
the disease type and the diagnosis (same dropdown menus seen in 4.1).
It's possible to record two more diagnoses ("Diagnosis n. 2 / n. 3").

The user can add optional notes about the visit on the "Note & Symptom"
textfield.

Finally, click "OK" to add the visit to the "opd" database.

If necessary, before recording the visit the user can add some further
data about the patient clicking the "Examination" button and adding
weight, height, blood pressure, heart rating, oxygen saturation and body
temperature (see chapter 8.6).

Data:

-   opd.OPD\_DATE
-   opd.OPD\_NEW\_PAT
-   opd.OPD\_DATE\_VISIT
-   opd.OPD\_PROG\_YEAR (visit serial number in the current year,
    starting from 1)
-   disease.DIS\_DCL\_ID\_A
-   opd.OPD\_DIS\_ID\_A (foreign key referencing "disease" DB, main
    diagnosis)
-   opd.OPD\_DIS\_ID\_A\_2 (foreign key referencing "disease" DB,
    optional second diagnosis)
-   opd.OPD\_DIS\_ID\_A\_3 foreign key referencing "disease" DB,
    optional third diagnosis)
-   opd.OPD\_REFERRAL\_FROM (ward where the patient was assisted)
-   opd.OPD\_REFERRAL\_TO (ward where the patient will be assisted)
-   opd.OPD\_PAT\_ID (foreign key referencing to the "patient" DB)
-   opd.USR\_ID\_A (user that added the new record, default "admin")

[]{#anchor-400}[]{#anchor-401}[]{#anchor-402}4.3 Edit OPD Registration![](Pictures/100002010000023A000001967CAA025D0DC8089B.png){width="9.65cm" height="6.876cm"}
=================================================================================================================================================================

Select a row from the OPD browser and click "Edit". An "Edit OPD
registration" window opens. All data except the OPD ID and patient data,
are editable. Once changes have been made, click "OK" to update or
"Cancel" to abort the operation.

Data:

same of chapter 4.2, except opd.OPD\_PAT\_ID, opd.USR\_ID\_A

[]{#anchor-403}[]{#anchor-404}[]{#anchor-405}4.4 Delete OPD registration
========================================================================

Select a row from the OPD browser and click "Delete". Click "Yes" on the
confirmation window to remove the visit from its database, else "No" to
abort the operation.

Data:

opd.OPD\_PAT\_ID

[]{#anchor-406}[]{#anchor-407}[]{#anchor-408}4.5 Close OPD menu
===============================================================

Click "Close" on the OPD browser to return to the main menu.

[]{#anchor-409}[]{#anchor-410}[]{#anchor-411}5. Pharmacy![](Pictures/10000201000001AE000001E2BD660B918128A7E9.png){width="11.772cm" height="13.196cm"}
------------------------------------------------------------------------------------------------------------------------------------------------------

It is the hospital's pharmacy, where all medicals and other items are
managed. The "Pharmacy" menu has 3 sub-menus:

-   "Pharmaceuticals": shows the list of the hospital items.
-   "Pharmaceutical Stock": records all item movements between hospital
    and suppliers, and between hospital and wards.
-   "Pharmaceutical Stock Ward": records all item movements between a
    patient and the ward where he/she has been admitted in. This option
    is active by default ("INTERNALPHARMACIES=yes" in the
    rsc/generalData.properties).

[]{#anchor-412}[]{#anchor-413}[]{#anchor-414}5.1 Pharmaceuticals![](Pictures/100000000000038A000003299695195277AD5AE4.jpg){width="15.346cm" height="13.711cm"}
==============================================================================================================================================================

Click "Pharmaceuticals" in the "Pharmacy" menu to open the
"Pharmaceutical Browsing" window. The table below shows all hospital
items recorded in the "medicaldsr" database. The columns in the table
include:![](Pictures/10000201000003AC000001C00F20A56749A81E83.png){width="16.99cm"
height="8.096cm"}

-   Item type (3.1.8)
-   Code (optional)
-   Description (name of the item)
-   Pieces X Pack (for pills / tablets)
-   Stock (available quantity)
-   Critical Level (minimum availability required)
-   Out of Stock (if ticked, Stock = 0.0).

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A (foreign key referencing to the
    "medicaldsrtype" database, item type)
-   medicaldsr.MDSR\_ID (primary key, item ID)
-   medicaldsr.MDSR\_CODE (optional)
-   medicaldsr.MDSR\_DESC (item name)
-   medicaldsr.MDSR\_PCS\_X\_PCK (pieces X pack)
-   medicaldsr.MDSR\_INI\_STOCK\_QTI (stock quantity)
-   medicaldsr.MDSR\_MIN\_STOCK\_QTI (crirical level quantity)

[]{#anchor-415}[]{#anchor-416}[]{#anchor-417}5.1.1 Select Type![](Pictures/10000201000003AD000001BFC3B36F219BBAD265.png){width="16.99cm" height="8.072cm"}
==========================================================================================================================================================

Filters the "Pharmaceutical browsing" table by item type. Choose the
type from the dropdown menu on the bottom of the window, or "ALL" to
visualize the full list.

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A
-   medicaldsr.MDSR\_ID

[]{#anchor-418}[]{#anchor-419}[]{#anchor-420}5.1.2 New Pharmaceutical![](Pictures/100002010000020F000000EFDD052E5159D0276E.png){width="8.909cm" height="4.036cm"}
=================================================================================================================================================================

Adds a new item to the "medicaldsr" database. Click "New" on the
"Pharmaceutical Browsing" window. A "New medical record" window opens.
Select the item type from the dropdown menu, then enter a code, a
description (i.e. the name of the item), the number of pieces in a
single packet (for pills or tablets; insert 0 for other indivisible
items) and the critical level (insert 0 if no minimum quantity
required). All data except "code" are mandatory. Click "OK" to confirm
or "Cancel" to abort the operation. If the required data have been
inserted, the item will be added to the "medicaldsr" database, else a
"Insert a valid value" window is shown. In this case, click "OK" to
return to the "New medical record" window. When a item is added, the
"Out of Stock" checkbox is ticked. Pictured below is the table after
adding aspirin as seen
above.![](Pictures/10000201000003AE000000781AB17E57FC290223.png){width="16.99cm"
height="2.17cm"}

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A
-   medicaldsr.MDSR\_ID
-   medicaldsr.MDSR\_DESC
-   medicaldsr.MDSR\_CODE
-   medicaldsr.MDSR\_PCS\_X\_PCK
-   medicaldsr.MDSR\_MIN\_STOCK\_QTI

[]{#anchor-421}[]{#anchor-422}[]{#anchor-423}5.1.3 Edit Pharmaceutical![](Pictures/1000020100000210000000ECFEA54BFD29D5A45D.png){width="8.909cm" height="3.995cm"}
==================================================================================================================================================================

Select a row from the "Pharmaceutical browsing" window and click "Edit".
An "Editing medical record OPD registration" window opens. All data
except the type are editable. Once changes have been made, click "OK" to
update or "Cancel" to abort the operation. If the required data have
been inserted, the item will be updated, else an error window is shown
(5.1.2).

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A
-   medicaldsr.MDSR\_ID
-   medicaldsr.MDSR\_DESC
-   medicaldsr.MDSR\_CODE
-   medicaldsr.MDSR\_PCS\_X\_PCK
-   medicaldsr.MDSR\_MIN\_STOCK\_QTI

[]{#anchor-424}[]{#anchor-425}[]{#anchor-426}5.1.4 Delete Pharmaceutical![](Pictures/100002010000019E000000AF6A8B7C3A5045F19A.png){width="8.968cm" height="3.792cm"}
====================================================================================================================================================================

Removes an item form the "medicaldsr" database, if it has no recorded
stock movements. Select a row from "Pharmaceutical Browsing" and click
"Delete". Click "Yes" on the confirmation window (left) to remove item
from its database, else "No" to abort the
operation.![](Pictures/10000201000002110000008CF09035BA126F65AA.png){width="8.968cm"
height="2.364cm"}

If there's at least one stock movement in the "medicaldsrstockmov"
database, containing the selected item, the deletion will be aborted and
an error window (left) opens.

Data:

-   medicaldsr.MDSR\_ID
-   medicaldsrstockmov.MMV\_MDSR\_ID (foreign key referenicing to the
    "medicaldsr" database)

[]{#anchor-427}[]{#anchor-428}[]{#anchor-429}5.1.5 Export![](Pictures/10000201000001710000011912A04F1DFA1C6609.png){width="6.228cm" height="4.771cm"}
=====================================================================================================================================================

Saves an .xls copy of the current "medicaldsr" database on the computer.
Click "Export" on the "Pharmaceutical browsing" window. A "Save" window
opens; enter the name of the file in the "Save As" field, and select the
folder where the file will be saved. To save the file in a non-existing
folder, click
"New![](Pictures/10000201000001270000008EC07EB9E66CD1D3E0.png){width="6.23cm"
height="2.997cm"} Folder", enter the name in the new window, and click
"Create". The new folder appears in the "Save" window, in the current
visible path. Complete the operation clicking "Save" (or "Cancel" to
abort).

Data: see chapter 5.1

[]{#anchor-430}[]{#anchor-431}[]{#anchor-432}5.1.6 STOCK![](Pictures/1000020100000185000002449A77E096E9651D5F.png){width="6.569cm" height="9.816cm"}
====================================================================================================================================================

Generates a report with the current "medicaldsr" database. Click "STOCK"
on the "Pharmaceutical Browsing" window. The Jasper Viewer opens (see
3.8.4 for .PDF export / print / zoom / navigation operations). The
document shows first all in stock items, sorted alphabetically by name,
with the in stock and critical level quantities, then all out of stock
items.

Data:

-   medicaldsr.MDSR\_ID
-   medicaldsr.MDSR\_DESC
-   medicaldsr.MDSR\_INI\_STOCK\_QTI
-   medicaldsr.MDSR\_MIN\_STOCK\_QTI

[]{#anchor-433}[]{#anchor-434}[]{#anchor-435}5.1.7 Order![](Pictures/100002010000018700000237CBB8BDCB0069390B.png){width="6.62cm" height="9.59cm"}
==================================================================================================================================================

Click "Order" on the "Pharmaceutical Browsing" window. The Jasper Viewer
opens (see 3.8.4 for .PDF export / print / zoom / navigation
operations). The document shows all items, sorted by item name, with the
in stock quantitites and the critical level. If the former value is
greater, the difference between stock and the minimum required is shown
in the "Still" column, else the "Order" column reports the amount to
reach the critical level.

Data:

-   medicaldsr.MDSR\_ID
-   medicaldsr.MDSR\_DESC
-   medicaldsr.MDSR\_INI\_STOCK\_QTI
-   medicaldsr.MDSR\_MIN\_STOCK\_QTI

[]{#anchor-436}[]{#anchor-437}[]{#anchor-438}5.1.8 Expiring![](Pictures/10000201000000F800000092D3979B1CADC469BD.png){width="5.069cm" height="2.985cm"}
=======================================================================================================================================================

This option generates a Jasper document (see 3.8.4 for .PDF export /
print / zoom / navigation operations), containing medical stocks expired
or close to due date. Click "Expiring" on the "Pharmaceutical Browsing"
window. Select the period on the new window (left). There are three
options:
"Today",![](Pictures/100002010000012500000085A05B1911B535A2E6.png){width="5.101cm"
height="2.316cm"} "This month" and "Other month" (opens a window,
pictured right, to choose the month and the year; click "OK" to
confirm). The document will report all medicals to order, depending on
the chosen period, each with the code, the description and the necessary
amount to reach the critical level.

[]{#anchor-439}[]{#anchor-440}[]{#anchor-441}5.1.9 Close Pharmaceuticals menu
=============================================================================

Click "Close" on the "Pharmaceutical Browsing" window to return to the
main menu.

[]{#anchor-442}[]{#anchor-443}[]{#anchor-444}5.2 Pharmaceutical Stock![](Pictures/10000000000003B2000002A82744ED17A4F30EAF.jpg){width="16.025cm" height="11.516cm"}
===================================================================================================================================================================

This sub-menu of "Pharmacy" allows the administrator to track the
movements generated by hospital items, managing purchases form suppliers
("Charge") e and item assignation to the wards ("Discharge"). Pictured
below is the table after two charges (5.2.2) and a discharge
(5.2.3).![](Pictures/100002010000049700000288E9EBAE1F3DA28BE3.png){width="16.99cm"
height="9.37cm"}

Data:

-   medicaldsrstockmov.MMV\_ID (primary key, movement ID; not seen in
    the table)
-   medicaldsrstockmov.MMV\_REFNO (reference number)
-   medicaldsrstockmov.MMV\_DATE (reference date)
-   medicaldsrstockmov.MMV\_MMVT\_ID\_A (foreign key referencing to the
    "medicaldsrstockmovtype" database, see chapter 3.1.7)
-   medicaldsrstockmov.MMV\_WRD\_ID\_A (foreign key referencing to the
    "ward" database, ward the item will be assigned to, if not for
    internal use)
-   medicaldsrstockmov.MMV\_QTY (amount of items in the lot)
-   medicaldsrstockmov.MMV\_MDSR\_ID (foreign key referencing to the
    "medicaldsr" database, nome dell'articolo)
-   medicaldsrstockmov.MMV\_LT\_ID\_A (lot number)
-   medicaldsrlot.LT\_PREP\_DATE (lot preparation date)
-   medicaldsrlot.LT\_DUE\_DATE (lot due date)
-   supplier.SUP\_ID (lot's supplier ID)
-   medicaldsrlot.LT\_COST (price per unit of a single item)
-   medicaldsrstockmov.MMV\_QTY \* medicaldsrlot.LT\_COST (lot price)

[]{#anchor-445}[]{#anchor-446}[]{#anchor-447}5.2.1 Filter
=========================================================

The left side of the "Stock Movement Browser" window provides a
selection panel to help search stock movements. It has 4 main sections:

-   Pharmaceutical: Select an item from the "Description" dropdown, or
    "ALL" to show all item's records.
-   Movement: Select a movement type (3.1.7) from the "Type" dropdown or
    "ALL" to show all movement's records. Add dates, in DD / MM / YYYY
    format, in the "From" and "To" fields format to filter by movement
    date.
-   Lot preparation date: enter values, in DD / MM / YYYY format, in the
    "From" and "To" fields format to filter by lot preparation date.
-   Lot due date: enter values, in DD / MM / YYYY format, in the "From"
    and "To" fields format to filter by lot due date.

Tick the "Keep" checkbox to keep these filters active after clicking on
Filter.

Once the selections have been made, click "Filter" to show only the
matching movements.

Data:

-   medicaldsrstockmov.MMV\_ID
-   medicaldsrstockmov.MMV\_REFNO
-   medicaldsrstockmov.MMV\_DATE
-   medicaldsrstockmov.MMV\_MMVT\_ID\_A
-   medicaldsrstockmov.MMV\_WRD\_ID\_A
-   medicaldsrstockmov.MMV\_MDSR\_ID
-   medicaldsrlot.LT\_PREP\_DATE
-   medicaldsrlot.LT\_DUE\_DATE

[]{#anchor-448}[]{#anchor-449}[]{#anchor-450}5.2.2 Charge![](Pictures/10000201000001F5000000D1A293A84C62DEB2EC.png){width="8.495cm" height="3.549cm"}
=====================================================================================================================================================

Click "Charge" on the "Stock Movement Browser" window. A "Stock
Movement" window opens; charge information is shown on the top. Type the
reference number on the "Reference No." field, then choose the charge
type (3.1.7) and the supplier (3.9). Enter part of the name or of the
code on the "Type a code or a description and press ENTER". After
clicking the "Enter" button on the computer, select the medical among
the ones matching the string inserted and click
"Yes".![](Pictures/100002010000015000000086C050FDC76FB8B66A.png){width="5.674cm"
height="2.27cm"}

Once the medical has been selected, insert the quantity in the "Input"
window and click "OK" to confirm.

A "Lot informations" window opens. Assign the lot
number![](Pictures/10000201000001F5000000A1CD615F39BDC6EBBF.png){width="8.495cm"
height="2.731cm"} (it will be assigned automatically if
"AUTOMATICLOT=yes" in the rsc/generalData.properties file) and enter the
lot preparation and due dates, in a DD/MM/YYYY format (see 3.10.1 for
the calendar icon). After clicking "OK", the "Stock Movement" window
(below)
shows![](Pictures/100002010000029E000000FB3B3AA212F4989E1F.png){width="11.352cm"
height="4.263cm"} the new charge.

Click "Save" to save the charge, else "Cancel" to discard.

If the data required have been inserted, the charge will be added to the
stock movement DB, else an error window is shown:

-   "The inserted reference number already exists"
-   "Please select a supplier"

Click "OK" to return to the "Stock Movement" window.

Data:

-   medicaldsrstockmov.MMV\_REFNO
-   medicaldsrstockmov.MMV\_DATE
-   medicaldsrstockmov.MMV\_MMVT\_ID\_A
-   medicaldsrstockmov.MMV\_WRD\_ID\_A
-   medicaldsrstockmov.MMV\_QTY
-   medicaldsrstockmov.MMV\_MDSR\_ID
-   medicaldsrstockmov.MMV\_LT\_ID\_A (lot number)
-   medicaldsrtype.MDSRT\_DESC
-   medicaldsrlot.LT\_PREP\_DATE
-   medicaldsrlot.LT\_DUE\_DATE
-   medicaldsrlot.LT\_COST

[]{#anchor-451}[]{#anchor-452}[]{#anchor-453}5.2.3 Discharge![](Pictures/10000201000001E7000000ACA92B6B798394F6DA.png){width="8.237cm" height="2.907cm"}
========================================================================================================================================================

Assigns an item ordered after a "Charge" operation. Click "Discharge" on
the "Stock Movement Browser" window. The "Stock Movement" panel is
similar to the one seen in chapter 5.2.2. The differences are in both
dropdown menus: the first includes all discharge types ("-" sign), the
second contains the hospital wards, to which the medical is discharged.
See 5.2.2 for reference number and medical
selection.![](Pictures/1000020100000187000000A72321E5EF9D11D46C.png){width="6.826cm"
height="2.916cm"}

Once the medical has been selected, insert the quantity in the "Input"
window and click "OK" to confirm. Quantity must not exceed the "Lying in
stock" shown.

![](Pictures/10000201000001C7000000DC3A151E3093407420.png){width="7.703cm"
height="3.729cm"}

After confirming the quantity, the "Lot informations" window opens.
Select the lot among those recorded in the database (the previously
created 012 in this example), then click "OK". Now the "Stock Movement"
window (below) shows the new discharge. Now the "Stock Movement" window
shows the new discharge. Click "Save" to save the
discharge,![](Pictures/10000201000003250000013D12C053F5E2A61CB8.png){width="12.555cm"
height="4.944cm"} else "Cancel" to discard.

If the data required have been inserted, the charge will be added to the
stock movement DB, else an error window is shown:

![](Pictures/100002010000013D000000A8324B5C915825DFA6.png){width="5.674cm"
height="3.007cm"}

-   "The inserted reference number already exists"
-   "Please select a ward"
-   "The quantity is not available" (right)

Click "OK" to return to the "Stock Movement" window. Picture below is
the movements browser after the charge and the discharge.

Data: see chapter
5.2.2![](Pictures/10000201000003EB0000009875CB452E197E5ADE.png){width="16.99cm"
height="2.566cm"}

[]{#anchor-454}[]{#anchor-455}[]{#anchor-456}5.2.4 Export
=========================================================

Saves an .xls copy of the current "medicaldsrstockmov" database on the
computer. Click "Export on excel" on the "Stock Movement Browser"
window. The function is identical to the pharmacy export seen in chapter
5.1.5.

[]{#anchor-457}[]{#anchor-458}[]{#anchor-459}5.2.5 Close Pharmaceutical Stock menu
==================================================================================

Click "Close" on the "Stock Movement Browser" window to return to the
main menu.

[]{#anchor-460}[]{#anchor-461}[]{#anchor-462}5.3 Pharmaceutical Stock Ward![](Pictures/100000000000039F0000027BEABF3C8CAB40C2E4.jpg){width="15.679cm" height="10.749cm"}
========================================================================================================================================================================

This sub-menu manages item assignment within the hospital. The internal
management is active by default, since row 20 in the
rsc/generalData.properties file is "INTERNALPHARMACIES=yes". Replace
"yes" with "no" nella stringa to disable it.

Data:

-   medicaldsrward.MDSRWRD\_WRD\_ID\_A (foreign key referencing to the
    "ward" database, ward code)
-   medicaldsrward.MDSRWRD\_MDSR\_ID (foreign key referencing to the
    "medicaldsr" database, item code)
-   medicaldsrward.MDSRWRD\_IN\_QTI (available quantity)
-   medicaldsrward.MDSRWRD\_OUT\_QTI (quantity to allocate to the ward)
-   medicaldsrstockmovward.MMVN\_ID (primary key, ID of the movement
    from hospital pharmacy to ward pharmacy)
-   medicaldsrstockmovward.MMVN\_DATE (movement date)
-   medicaldsrstockmovward.MMVN\_IS\_PATIENT (0 for internal use,
    else 1)
-   medicaldsrstockmovward.MMVN\_PAT\_ID (foreign key referencing to the
    "patient" DB)
-   medicaldsrstockmovward.MMVN\_PAT\_AGE (patient age)
-   medicaldsrstockmovward.MMVN\_PAT\_WEIGHT (patient weight)
-   medicaldsrstockmovward.MMVN\_DESC (patient full name)
-   medicaldsrstockmovward.MMVN\_MDSR\_QTY (item quantity)
-   medicaldsrstockmovward.MMVN\_UNITS (number of units of the item)

[]{#anchor-463}[]{#anchor-464}[]{#anchor-465}5.3.1 Ward Pharmacy
================================================================

Click "Pharmaceutical Stock Ward" in the "Pharmacy" menu. A small window
(left) opens. Select the ward among those having an own pharmacy (3.3).
Once the ward has been selected, the "Ward Pharmacy" expands as pictured
below. The internal pharmacy, too, has a selection panel to help search
records. Type two dates in the "From" and "To" fields on the right top
of the window, in a DD/MM/YY format, or choose them clicking on the
calendar icons (3.10.1). Then select medical type and item from the
dropdown menus (4.1), filter by patient sex and weight range (4.1).
Click "Filter" to show only matching records. Click "Reset" to remove
all filters.

The "Ward Pharmacy" browser provides three different tables. Click on
the tabs above the table to choose
between:![](Pictures/10000201000002AD0000018541A01A3087897817.png){width="11.585cm"
height="6.583cm"}

-   ![](Pictures/10000201000002340000006D50F4E39103575564.png){width="8.523cm"
    height="1.647cm"}"Drugs": the table shown when opening the P.S. Ward
    menu, records all available items in the selected ward.
-   "Incomings": shows all discharges from the main pharmacy (5.2.2).
-   "Outcomes": shows all movements from the main pharmacy to the ward
    pharmacies. The buttons on the bottom of the window are referred to
    this visualization.

Data:

see chapter 5.3

[]{#anchor-466}[]{#anchor-467}[]{#anchor-468}5.3.2 New Outcome![](Pictures/100002010000021E0000020F9BD75E725018A016.png){width="9.16cm" height="8.918cm"}
=========================================================================================================================================================

Click "New" on the "Ward Pharmacy" window to add a new movement. A
"New/Edit" window (left) opens. Select the destination clicking on the
"Patient" or the "Internal use" radio button. If the former is selected,
click "Pick Patient" to open the "Patient selection" window (or create a
new one, if not already registered in the "patient" DB, clicking on the
pencil icon; see chapter 8 "Admission/Patient").

Click on the magnifier icon to show the patient list (if a string has
been written in the "Search Patient" field, only rows containing that
string are visibile) Once selected the
row,![](Pictures/100002010000019D000000A60E17DC071FCB1E0B.png){width="6.853cm"
height="2.755cm"} click "Select". If no weight data are available, a
"The selected patient has no weight defined" warning is shown (left; see
chapter 8.6 to add weight and other information). Click "OK" to return
to the "New/Edit" window. The "Pick Patient" buttons becomes "Change
Patient", and the nearby icon to delete the inserted name, is
enabled.![](Pictures/1000020100000108000000B766707F426937D61E.png){width="5.57cm"
height="3.856cm"}![](Pictures/100002010000013800000093CC1A96B57F6DBBE8.png){width="6.05cm"
height="2.849cm"}

Select the medical(s) to assign. Click "+ Medical" on the "New/Edit"
window. Pick an item from the dropdown menu (left) and click "OK".

Then enter the quantity (right) and click "OK". Quantity must not exceed
the available stock shown in the "Quantity"
window.![](Pictures/10000201000002140000020B860E76931B0AAF9E.png){width="9.028cm"
height="8.869cm"}

Repeat the operation to add more medicals to the movement. To remove an
item, select it and click "X Remove Item". Pictured left is the
"New/Edit" window after inserting 3 units of Albendazole. Click "OK" to
add the record to the "Outcomes" table.

In case of items to assign to the ward (internal use), the record will
be shown in bold blue in the "Outcomes" browser. Pictured below is the
table after a record for a given patient of the children's ward, and a
record for internal use in that ward.

![](Pictures/1000020100000321000001C4CD3986EA317678AA.png){width="12.742cm"
height="7.191cm"}

Data: see chapter 5.3

[]{#anchor-469}[]{#anchor-470}[]{#anchor-471}5.3.3 Report![](Pictures/100002010000025C000001AE5FF55259F80F4D6F.png){width="10.204cm" height="7.276cm"}
======================================================================================================================================================

Click "Report" on the "Ward Pharmacy" window. The Jasper Viewer opens
(see 3.8.4 for .PDF export / print / zoom / navigation operations). The
document shows all outcome records, sorted by date and medical, each
with the quantities for internal and patient use.

Data:

-   medicaldsrward.MDSRWRD\_WRD\_ID\_A
-   medicaldsrward.MDSRWRD\_MDSR\_ID (foreign key referencing to the
    "medicaldsr", item ID)
-   medicaldsrward.MDSRWRD\_IN\_QTI (available quantity)
-   medicaldsrstockmovward.MMVN\_DATE
-   medicaldsrstockmovward.MMVN\_UNITS

[]{#anchor-472}[]{#anchor-473}[]{#anchor-474}5.3.4![](Pictures/10000201000001E3000000DC99D5CDA765B6A896.png){width="8.192cm" height="3.725cm"} Excel
====================================================================================================================================================

Saves an .csv copy of the data shown in chapter 5.3.3. Click "Export" on
the "Ward Pharmacy" window. The function is identical to the pharmacy
export seen in chapter 5.1.5.

[]{#anchor-475}[]{#anchor-476}[]{#anchor-477}5.3.5 Rectify![](Pictures/100002010000028F0000017D95A3264D849F0CB6.png){width="11.061cm" height="6.438cm"}
=======================================================================================================================================================

Click "Rectify" in "Ward Pharmacy". The "Rectify" window opens. It
allows the user to update the stock in the ward pharmacy, if the item is
damaged or stolen. Select an item form the dropdown menu and enter the
new actual quantity. Add the reason for the rectifying operation, if
necessary. Click "OK" to update or "Cancel" to abort.

[]{#anchor-478}[]{#anchor-479}[]{#anchor-480}5.3.6 Close Pharmaceutical Stock Ward menu
=======================================================================================

Click "Close" on the "Ward Pharmacy" window, to return to the main menu.

[]{#anchor-481}[]{#anchor-482}[]{#anchor-483}6. Laboratory![](Pictures/10000000000003EC0000021D62C918BE95A39960.jpg){width="16.99cm" height="9.155cm"}
------------------------------------------------------------------------------------------------------------------------------------------------------

The "Laboratory browsing" window records all laboratory exams. It
provides a selection panel on the left side, and the lab table, where
every row shows the exam date, the patient examined, the exam type and
the exam
result.![](Pictures/10000201000003F00000021A1797A4F5B6D76B8B.png){width="16.99cm"
height="9.068cm"}

Data:

-   laboratory.LAB\_ID (primary key, exam ID, not shown in the table)
-   laboratory.LAB\_DATE (exam date)
-   laboratory.LAB\_PAT\_ID (foreign key referencing to the "patient"
    database)
-   laboratory.LAB\_EXA\_ID\_A (foreign key referencing to the "exam"
    DB, exam name)
-   laboratory.LAB\_RES (exam result)

[]{#anchor-484}[]{#anchor-485}[]{#anchor-486}6.1 Search Exam![](Pictures/100002010000029F000001799F28026F4B79A9CB.png){width="11.338cm" height="6.378cm"}
=========================================================================================================================================================

To help search exams, the selection panel allows to choose an exam type
from the dropdown menu and/or a date range, entering the dates, in
DD/MM/YYYY format, in the "Date From" and "Date To" fields. Then click
"Search" to visualize matching records.

Data:

see chapter 6

[]{#anchor-487}[]{#anchor-488}[]{#anchor-489}6.2 New Exam![](Pictures/100002010000021800000121284315D0F8819AF6.png){width="9.095cm" height="4.912cm"}
=====================================================================================================================================================

Click "New" while on "Laboratory Browsing". A "New Patient Exams" window
is shown. If necessary, change date and time typing in DD/MM/YYYY
HH:MM:SS format (default is the moment the window opens) or selecting
the date by clicking the calendar icon (3.10.1). Pick the patient as
seen in chapter 5.3.2. Check the
radio![](Pictures/100002010000010800000091356BE9341EC6C0D6.png){width="5.115cm"
height="2.81cm"} button to record the patient status ("OPD" if admitted,
or "IP" if not admitted yet).

Add one or more exams clicking on "+ Exam". Select the element examined
(left) from the "Material" dropdown menu and click "OK".

![](Pictures/100002010000029600000125003E4D0B0AB06C82.png){width="10.231cm"
height="4.528cm"}

Then select the exam (right), among those registered in the "exam" DB
and click "OK".

Finally, insert the exam result. Select the outcome from
the![](Pictures/1000020100000109000000C85CCB6C5ED413FA5A.png){width="5.054cm"
height="3.814cm"} dropdown menu (3.5.5) and click "OK" to return to the
"New Patient Exams" window. Repeat these operations to add more exams.
To remove an exam, select it and click "X Remove". Add optional notes in
the "Notes" field on the bottom on the window. Once data have been
inserted, click "OK" to save the exam in the
database.![](Pictures/10000201000002BC000000C8BD92012B7A8ABEE7.png){width="11.875cm"
height="3.394cm"}

Pictured left is the "Lab browsing" table after adding the exam whose
steps have been shown in this page.

![](Pictures/10000201000001F5000001091BF9E346DA290EE6.png){width="8.495cm"
height="4.503cm"}

If something's missing in the "New Exam" operation, an error window
opens, showing one of the following messages:

-   "Please select a patient"
-   "Please insert a date"
-   "No exams
    inserted"![](Pictures/10000201000002A40000009E2F4F992691872CEE.png){width="11.432cm"
    height="2.679cm"}

If more than one exam has been added, the "Lab Browsing" window will
have one row for each exam, with the same date and patient name (left).

Data:

-   laboratory.LAB\_ID
-   laboratory.LAB\_DATE
-   laboratory.LAB\_EXA\_ID\_A
-   laboratory.LAB\_RES
-   laboratory.LAB\_MATERIAL
-   laboratory.LAB\_PAT\_ID
-   laboratory.LAB\_NOTE (optional notes)
-   laboratory.LAB\_PAT\_INOUT ("I" for IPD, "O" for OPD, else "R" for
    re-attendance)

[]{#anchor-490}[]{#anchor-491}[]{#anchor-492}6.3 Edit Exam![](Pictures/10000201000001AE0000020395FEC40A7BAEF660.png){width="7.28cm" height="8.731cm"}
=====================================================================================================================================================

Select a row from the "Laboratory browsing" window and click "Edit". An
"Edit Laboratory exam" window opens (left). All data, except patient's,
are editable. Click "OK" to update the record or "Cancel" to abort.

Data: see chapter 6.2

[]{#anchor-493}[]{#anchor-494}[]{#anchor-495}6.4 Delete Exam
============================================================

Select a row from the "Laboratory browsing" window and click "Delete".
Click "Yes" on the confirmation window to remove item from its database,
else "No" to abort the operation.

Data:

-   laboratory.LAB\_ID

[]{#anchor-496}[]{#anchor-497}[]{#anchor-498}6.5 Print table
============================================================

Generates a report with the current "exam" database. Click "Print table"
on the "Laboratory Browsing" window. The Jasper Viewer opens (see 3.8.4
for .PDF export / print / zoom / navigation operations).

[]{#anchor-499}[]{#anchor-500}[]{#anchor-501}6.6 Close Laboratory menu
======================================================================

Click "Close" on the "Laboratory Browsing" menu to return to the main
menu.

[]{#anchor-502}[]{#anchor-503}[]{#anchor-504}7. Accounting![](Pictures/10000000000002CE000003268E9AADFF73DA612A.jpg){width="12.164cm" height="13.67cm"}![](Pictures/1000020100000178000001D7FC9219DC2983CCF6.png){width="8.495cm" height="10.642cm"}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The "Accounting" menu manages payments and bills. It provides a submenu
with two options: "New Bill" to record a new payment, and "Bills
Manager", where all bills are stored.

[]{#anchor-505}[]{#anchor-506}[]{#anchor-507}7.1 New Bill![](Pictures/10000201000002640000021E3370FE109304B68E.png){width="10.213cm" height="9.045cm"}
======================================================================================================================================================

Click "New Bill" in the "Accounting" menu to open the "New Patient Bill"
window.

Date and time refer to when the window has been opened. If necessary,
enter a specific value, in DD/MM/YYYY - HH:MM:SS format, or select the
date by clicking on the calendar icon (3.10.1). If values are correct,
they will be shown in green, else in red. Then select the patient the
bill is assigned to, as seen in chapter 5.3.2. Select the pricing list
from the dropdown menu. Now add the items (medicals, operations, exam,
etc.) to the receipt, clicking on the buttons
on![](Pictures/10000201000001BF0000011F4B9437E9F071B72B.png){width="6.777cm"
height="4.352cm"} the right side.

-   "+ Medical": adds a new medical (left). Select the item from the
    "Medical" window and click "OK".

![](Pictures/100002010000016D0000008DB5D3A47E7E511224.png){width="6.777cm"
height="2.618cm"}

Then enter the quantity and click "OK".

![](Pictures/10000201000002820000016143D54EF81674FDA3.png){width="10.853cm"
height="5.96cm"}

Pictured left is the bill with the selected medical, the quantity
entered, and the total money amount for that item (price of a single
unit \* quantity).

-   "+ Operation": adds a new operation (left). Select
    the![](Pictures/100002010000014C0000011E5A7968A753A25FD5.png){width="5.808cm"
    height="5.002cm"} item from the "Operation" window and click "OK".
    Below is a detail of the bill after adding the
    operation.![](Pictures/1000020100000254000000EC8E0F23DA4290075B.png){width="10.522cm"
    height="4.17cm"}

![](Pictures/100002010000028F00000119BC13493D6A4994EC.png){width="10.795cm"
height="4.63cm"}

-   "+ Exam": adds a new exam (left). Select the item from the "Exam"
    window and click "OK". The exam is added to the "New Bill" window.

![](Pictures/1000020100000108000000909B7B666BA21F013A.png){width="6.507cm"
height="3.549cm"}

-   "+ Other": used for medicals not recorded in OH's databases. Select
    the frequency (left; default: "Amount per day"), and click "OK".
    Then enter
    the![](Pictures/100002010000016B0000008E0744E2E0C2A2C9B0.png){width="6.195cm"
    height="2.424cm"} number of times the medical is required (below)
    and click "OK".

![](Pictures/10000201000001580000008EAA236D58F3DA0B78.png){width="6.507cm"
height="2.685cm"}

-   "+ Custom": used for items not recorded in OH's databases. Enter a
    description on the "Custom item" window (left) and click "OK". Then
    digit the price (below) and click
    "OK".![](Pictures/10000201000001680000009157086BCC074CFD93.png){width="6.195cm"
    height="2.496cm"}

![](Pictures/100002010000024C00000200B4446684D831BC69.png){width="10.719cm"
height="9.335cm"}The bill can contain more than one item of the same
type, just repeat the operations shown in this chapter. Pictured left is
the "New patient bill" window after the five steps previously explained.
The "TO PAY" row shows the total amount of the bill, while the "BALANCE"
row shows the money the patient owes the hospital. No payments were
recorded for now, so the balance equals the value of the receipt. Before
saving the bill in the database, it's possible to remove an element.
Select it and click "X Remove Item".

Data:

-   billitems.BLI\_ID (primary key, item ID)
-   billitems.BLI\_ID\_BILL (foreign key referencing the "bills"
    database, bill ID)
-   billitems.BLI\_IS\_PRICE (1 if the item price is recorded in the
    "priceslists" DB, else 0)
-   billitems.BLI\_ID\_PRICE (item ID)
-   billitems.BLI\_ITEM\_DESC (item description)
-   billitems.BLI\_ITEM\_AMOUNT (item price)
-   billitems.BLI\_QTY (item
    quantity)![](Pictures/100002010000016B0000009067E8A1703C7D1970.png){width="7.782cm"
    height="3.087cm"}

Once the items have been added to the receipt, record the payment adding
the total amount, the money the patient pays the hospital and the change
to give him/her if necessary. Use buttons on the right side, on the
bottom half of the
window.![](Pictures/10000201000001F6000001B77301542749256C08.png){width="8.495cm"
height="7.424cm"}

-   "+ Payment": add the amount of a payment to the hospital. Enter the
    quantity and click for the "OK". The amount, the date and the time
    of the payment will be shown on the bottom table. In this case, the
    patient still owes one unit of currency, since "BALANCE" is 1.

-   "+ Refund": it's the opposite of "+ Payment". Enter the quantity as
    seen above and click "OK".

Repeat the operations shown to add more payments/refunds; to remove a
payment/refund, select it and click "X Remove Payment".

![](Pictures/10000201000002670000021EB3B667A80600153B.png){width="12.478cm"
height="10.996cm"}Pictured left is the "New patient bill" window after
two payments and a refund.

-   Save: saves the receipt, adding it to the "Bills Manager" as a
    "Pending" bill. See chapter 7.2 for further information.
-   Paid: closes the bill. Status in the bills manager turns to "C" (see
    chapter 7.2).
-   Close (in the "New patient bill window): closes the "New patient
    bill" window without saving it.

If a patient has not been selected, a "Please select a patient" message
window opens. Click "OK" to return to the former window to add patient
name as seen before.

Other buttons include: "Give Change" to calculate change to give to the
patient, and "Payment Receipt", (enabled in "Bills Manager" mode only,
if "RECEIPTPRINTER=yes" in the rsc/generalData.properties file) to print
the receipt.

Data:

-   billpayments.BLP\_ID (primary key, payment/refund ID)
-   billpayments.BLP\_ID\_BILL (foreign key referencing the "bills"
    database, bill ID)
-   billpayments.BLP\_DATE (payment/refund date and time)
-   billpayments.BLP\_AMOUNT (payment amount if positive; refund amount
    if negative)
-   billpayments.BLP\_USR\_ID\_A (user recording the payment/refund,
    default "admin")

[]{#anchor-508}[]{#anchor-509}[]{#anchor-510}7.2 Bills Manager![](Pictures/1000020100000296000001B51C0BA537C1F726E5.png){width="11.201cm" height="7.398cm"}
===========================================================================================================================================================

Click "Bills Manager" in the "Accounting" menu. A "Patients Bills
Management" window opens (left), where all receipts are recorded.

The data shown in the table include:

-   ID
-   date and time
-   patient ID
-   patient name
-   amount
-   date and time of the last payment/refund recorded with the "+
    Payment"/"+ Refund"
-   status ("O" for "Open" / "Pending"; "C" for "Closed"; "D" for
    "Deleted" from the bills to report; see chapter 7.2.3).
-   balance the patient owes the hospital.

The tabs over the table allow to filter bill records according to the
status: default is "Bills" to show all, "Pending" to show pending bills
only, and "Closed", to see closed bills only. Enter dates in DD/MM/AA in
the "From" and "To" fields to filter bills by date, or choose them by
clicking on the calendar icons (3.10.1). You can also select a specific
month and a year.

Data:

-   bills.BLL\_ID (primary key, bill ID)
-   bills.BLL\_DATE (date and time the bill was created)
-   bills.BLL\_PAT\_ID (foreign key referencing the "patient" database,
    patient ID)
-   bills.BLL\_PAT\_NAME (patient ID)
-   bills.BLL\_AMOUNT (bill amount)
-   bills.BLL\_UPDATE (date and time of the "last payment" shown in the
    table)
-   bills.BLL\_STATUS
-   bills.BLL\_BALANCE

[]{#anchor-511}[]{#anchor-512}[]{#anchor-513}7.2.1 New Bill
===========================================================

See chapter 7.1.

[]{#anchor-514}[]{#anchor-515}[]{#anchor-516}7.2.2 Edit Bill![](Pictures/100002010000014B000000A78D2B1131CCFCADD2.png){width="5.108cm" height="2.577cm"}
========================================================================================================================================================

Select a row from "Patients Bills Management" and click "Edit". The "New
Bill" window opens; you can add items, payments and refunds as seen in
chapter 7.1."X Remove Item" and "X Remove Payment" buttons are disabled,
while "Print Receipt" is enabled. Click on it, then click "Yes" on the
confirmation window (left). If the rsc/generalData.properties file shows
"RECEIPTPRINTER=yes" and the printer is connected to the computer, the
bill will be printed.

Data: attributes from "billitems" and "billpayments"

[]{#anchor-517}[]{#anchor-518}[]{#anchor-519}7.2.3 Delete Bill![](Pictures/100002010000027E000001A5918AE271AA5B5E9E.png){width="10.781cm" height="7.124cm"}
===========================================================================================================================================================

The function doesn't remove the bill from the "bills" database. It turns
its status to "D" (for Deleted); so it'll be visible only under the
"Bills" tab. "Deleted" rows are shown in red (left) and their amounts
won't be calculated in the reports. Select an open or close bill, and
click "Edit". Click "Yes" on the confirmation window, or "No" to abort
the operation.

Data:

-   bills.BLL\_ID
-   bills.BLL\_STATUS

[]{#anchor-520}[]{#anchor-521}[]{#anchor-522}7.2.4 Receipt
==========================================================

Select a bill from "Patients Bills Management" and click "Receipt", to
print the bill and its items. The function is similar to the "Print
Receipt" button in "Edit Bill" (7.2.2).

[]{#anchor-523}[]{#anchor-524}[]{#anchor-525}7.2.5 Report![](Pictures/10000201000001060000008DB42A8A9121545D9A.png){width="6.673cm" height="3.591cm"}
=====================================================================================================================================================

Creates a Jasper Viewer (see 3.8.4 for .PDF export / print / zoom /
navigation operations), to show bills recorded (and the total amount of
them) in a given period of time. Click "Report" on the "Patient bills
management" window.

Select the time period form the dropdown menu. Options include:

-   Today (closure): only amounts of the current day
-   Today: bills of the current day
-   Period: bills of the period chosen in the "Patients Bills
    Management" window (7.2).
-   This Month: bills of the current month
-   Other Month: bills of a month chosen from the calendar that opens if
    this option is selected.

Then click "OK" to
confirm.![](Pictures/1000020100000172000000962B8B3BBA8ED05805.png){width="6.673cm"
height="2.715cm"}

Once the time option is selected, if it's not "Today (closure)", a
"Report" window opens (left). Select between two options:

-   Short report: returns pending bills, and the total amount of the
    closed ones.
-   Full report: returns closed and pending bills in detail.

Click "OK" to confirm and generate the document
(below).![](Pictures/100002010000020C00000122AB0C690D188385CD.png){width="8.869cm"
height="4.911cm"}

Data:

-   bills.BLL\_ID
-   bills.BLL\_DATE
-   bills.BLL\_PAT\_ID
-   bills.BLL\_USR\_ID\_A (user genersting the report, default "admin")
-   sum(bills.BLL\_AMOUNT) (sum of all amounts in the given period)
-   bills.BLL\_STATUS

[]{#anchor-526}[]{#anchor-527}[]{#anchor-528}7.2.6 Close Bills Manager
======================================================================

Click "Close" on the "Patients Bill Management" window to return to OH's
main menu.

[]{#anchor-529}[]{#anchor-530}[]{#anchor-531}8. Admission/Patient
-----------------------------------------------------------------

The "Patients Browser" window stores all patient data. Records are used
in most OH features. The table shows the main attributes (ID, name, age,
sex, city, address, ward for admitted patients). On the left side a
selection panel aims to help search records. Buttons on the bottom
include the functions described in the following paragraphs.

Data:

-   admission.ADM\_IN (1 if the patient has been admitted, else 0)
-   admission.ADM\_ID (primary key, admission ID)
-   admission.ADM\_PAT\_ID (foreign key referencing the "patient"
    database)
-   patient.PAT\_AGE (patient age)
-   patient.PAT\_SEX (patient sex)
-   patient.PAT\_ADDR (patient address)
-   patient.PAT\_CITY (city of residence)
-   patient.PAT\_TELE (phone number)
-   patient.PAT\_NOTE (optional notes about the patient)
-   admission.ADM\_WRD\_ID\_A (foreign key referencing the "ward", ward
    in which the patient has been admitted to)

[]{#anchor-532}[]{#anchor-533}[]{#anchor-534}8.1 Search Patient![](Pictures/100000000000023D0000014E05170A05F0716C3B.jpg){width="9.694cm" height="5.657cm"}
===========================================================================================================================================================

To help search patient data, the browser provides some filter tools.
Options are intended with "ENHANCEDSEARCH=no" in the
rsc/generalData.properties file, meaning filters are automatically
applied according to the following selections:

-   Patient status: select from the dropdown menu ("All",
    "Admitted",![](Pictures/1000020100000305000000E7FB1E650C4AD47E19.png){width="13.115cm"
    height="3.925cm"} "Not Admitted").
-   Ward: tick the checkboxes to visualize records of patients admitted
    in a given ward. If none are selected, no ward filter is applied.
-   Search Key: enter a substring to show only records matching either
    the patient ID / name / city / address / telephone number / notes.

The number of matching records is shown under the "Ward" checkboxes.

Data: see chapter 8.

[]{#anchor-535}[]{#anchor-536}[]{#anchor-537}8.2 New Patient![](Pictures/100000000000028B00000202BAC05DCCC94EF6A0.jpg){width="11.038cm" height="8.707cm"}
=========================================================================================================================================================

Adds a new patient to the database. Click "New Patient" on the "Patients
Browser" window. A "New Patient" window opens. Add first name, second
name and select sex. Then enter the patients age, selecting the radio
button corresponding to the age format:

![](Pictures/100002010000031D000001F614D666BA9F66AD8A.png){width="13.333cm"
height="8.398cm"}![](Pictures/10000201000001300000006197B6A212AA8CAADB.png){width="5.373cm"
height="1.715cm"}

-   "Age": type the number of years, months and days in the three fields
    below.![](Pictures/100002010000013500000060E430AED6104A2409.png){width="5.373cm"
    height="1.669cm"}

-   "Birth date": enter the DD/MM/YYYY birthdate or select it clickcing
    on the calendar icon (3.10.1). To enter a different date, click on
    the basket icon and then enter the new
    value.![](Pictures/100002010000013600000062AF3B6E66E4BD5EEA.png){width="5.373cm"
    height="1.699cm"}

-   "Description": select the age type (3.1.12) from the first dropdown
    menu. If "Newborn" is selected, the second dropdown is enabled to
    determine the age in months (0-23).

Since OH 1.6, an extended set of attributes has been implemented. If
"PATIENTEXTENDED=yes" in the rsc/generalData.properties file, you can
also add optional information including:

-   Tax Number ID
-   Address
-   City
-   Next Kin
-   Telephone number
-   Blood type
-   Father name / Mother name
-   Parents together (if patient's parents live together)
-   Has insurance (if the patient is covered by medical insurance)
-   Photo of the patient
-   Optional
    notes![](Pictures/10000201000000A400000105404AA0A77CFE38EA.png){width="4.022cm"
    height="6.399cm"}![](Pictures/100002010000021F0000019F79D0CBD8302E4AA0.png){width="8.26cm"
    height="6.313cm"}

To add a photo of the patient, save the photo in the computer running
OH. Click "Load File" on the browser window, choose the directory in
which the photo is stored, select the file and click "Open" (left).
Pictured right is the photo, surrounded by a red square. Drag it to fit
the photo and click "Save" to load the picture in the "New Patient"
window (below). Finally, click "OK" (in "New Patient"). If required
fields (\*) have all been filled, the patient will be added to the
database, else an error message is shown:

-   "Insert First name"
-   "Insert Second name"
-   "Insert valid age"
-   "Insert age or birth date"
-   "Please select a sex"

Click "OK" to return to the former window to add required elements.

Data:

-   patient.PAT\_ID (primary key, patient ID; auto-increment )
-   patient.PAT\_FNAME (first name)
-   patient.PAT\_SNAME (second name)
-   patient.PAT\_TAXCODE
-   patient.PAT\_BDATE (birthdate)
-   patient.PAT\_AGE (age)
-   patient.PAT\_AGETYPE (age type)
-   patient.PAT\_SEX
-   patient.PAT\_ADDR (address)
-   patient.PAT\_CITY
-   patient.PAT\_TELE phone number)
-   patient.PAT\_NOTE (optional notes)
-   patient.PAT\_NEXT\_KIN
-   patient.PAT\_BTYPE (blood type; "U" if unknown)
-   patient.PAT\_MOTH\_NAME (mother's name)
-   patient.PAT\_MOTH\_CHAR ("A" if patient's mother still alive, "D" if
    deceased, "U" if unknown)
-   patient.PAT\_FATH\_NAME (father's name)
-   patient.PAT\_FATH\_CHAR ("A" if patient's father still alive, "D" if
    deceased, "U" if unknown)
-   patient.PAT\_PTOGE ("Y" if patient's parents live together, else
    "N"; "U" if unknown)
-   patient.PAT\_ESTA ("Y" if the patient has medical insurance, else
    "N"; "U" if unknown)
-   patient.PAT\_PHOTO

[]{#anchor-538}[]{#anchor-539}[]{#anchor-540}8.3 Edit Patient![](Pictures/100000000000024C000001BEBFED4C353E25E0E3.jpg){width="9.957cm" height="7.564cm"}
=========================================================================================================================================================

![](Pictures/100002010000020E000001554EC1FDDBFA6918BA.png){width="8.916cm"
height="5.787cm"}

Select a row from "Patients Browser" and click "Edit patient". All data
are editable (bottom right). If no photo was added, click "Load File" to
add a photo (8.2), else a red X is shown on the
photo![](Pictures/1000020100000199000000A21C3D0E165F6C2142.png){width="6.865cm"
height="2.718cm"} to remove it. If the X is clicked, then click "Yes" on
the confirmation window (bottom left), else click "No" to keep the
current image.

Data: see chapter 8.2

[]{#anchor-541}[]{#anchor-542}[]{#anchor-543}8.4 Delete patient![](Pictures/10000000000001E8000000EDD098B5BC20FC78A3.jpg){width="8.266cm" height="4.016cm"}
===========================================================================================================================================================

Select a row from "Patients Browser" and click "Delete patient". Click
"Yes" on the confirmation window to remove the record, else "No" to
abort. If the patient is deleted, all foreign keys referencing the
patient will be removed.

Data: patient.PAT\_ID

[]{#anchor-544}[]{#anchor-545}[]{#anchor-546}8.5 Admission![](Pictures/10000000000002FD0000030B9F0CF1076BF385AF.jpg){width="12.963cm" height="13.196cm"}
========================================================================================================================================================

If the patient has not been admitted, the "Admission" buttons allows to
assign the patient a ward (8.5.1), else the button allows to edit
admission information (8.5.2).

[]{#anchor-547}[]{#anchor-548}[]{#anchor-549}8.5.1 New Admission
================================================================

Select a "Not Admitted" patient (the ones where "Ward" column is empty)
and click "Admission". A "New Admission" window opens (below). It has
three tabs (four for female patients). Add in the first one,
"Admission/Discharge", the following data:

-   Ward: select the ward from the dropdown menu
-   From Health Unit: optional, if the patient comes form another
    hospital / ward
-   admission date (DD/MM/YY or by calendar icon)
-   admission type (3.1.1)
-   malnutrition: if checked, patient has malnutrition issues; see
    chapter 8.9.3)
-   the diagnosis for which the patient is admitted.
-   the diagnoses for which the patient is dismissed (optional)
-   discharge type (if it's the same of the admission type, click "Yes"
    on the confirmation window)
-   optional notes

Click the "Operation" tab to add optional information on operations
related to
the![](Pictures/10000201000003EE000001ED21502BF21643E995.png){width="16.99cm"
height="8.326cm"} diagnosis. Click the "Delivery" tab to add optional
information about the delivery (for female patients). Click on the
"Notes" tab to add optional notes about the admission record. Finally,
click "Save" to save the admission data. If all required fields (\*)
have been filled, the admission record is saved, and the patient is
included in the "admitted" table; else a ìn error message is shown:

-   "Ward without free beds"
-   "Please select a valid Diagnosis -IN-")
-   "Please select a valid admission type")
-   "Please select a valid discharge type")
-   "Future date not allowed, please insert a valid discharge date"
-   "Discharge date must be after admission date"

Data:

-   admission.ADM\_PAT\_ID (foreign key referencing to the "patient"
    database, patient ID)
-   admission.ADM\_WRD\_ID\_A (foreign key referencing to the "ward"
    database, ward in which the patient is admitted to)
-   admission.ADM\_FHU ("From health unit")
-   admission.ADM\_YPROG (serial admission number in a calendar year, 1
    ... N)
-   admission.ADM\_DATE (admission date)
-   admission.ADM\_ADMT\_ID\_A\_ADM (foreign key referencing to the
    "admissiontype" database)
-   admission.ADM\_IN\_DIS\_ID\_A (foreign key referencing to the
    "disease" database, admission diagnosis
-   admission.ADM\_OUT\_DIS\_ID\_A (foreign key referencing to the
    "disease" database, discharge diagnosis)
-   admission.ADM\_OUT\_DIS\_ID\_A\_2 (foreign key referencing to the
    "disease" database, second optional discharge diagnosis)
-   admission.ADM\_OUT\_DIS\_ID\_A\_3 (foreign key referencing to the
    "disease" database, third optional discharge diagnosis)
-   admission.ADM\_DATE\_DIS (discharge date)
-   admission.ADM\_DIST\_ID\_A (foreign key referencing to the
    "dischargetype" database)
-   admission.ADM\_NOTE (optional notes)
-   admission.ADM\_OPE\_ID\_A (foreign key referencing to the
    "operation" database)
-   admission.ADM\_DATE\_OP (operation date)
-   admission.ADM\_RESOP (operation result: "P" if positive, "N" if
    negative, "U" if unknown)
-   admission.ADM\_TRANS (transfusional unit)

[]{#anchor-550}[]{#anchor-551}[]{#anchor-552}8.5.2 Edit admission![](Pictures/10000201000003A3000001C3E80435810F7D945A.png){width="15.743cm" height="7.622cm"}
==============================================================================================================================================================

Discharges an admitted patient. Select an "Admitted" row from "Patients
Browser", (the ones where the "Ward" column is not empty vuota) and
click "Admission". An "Edit Admission Record, window opens (below). All
data seen in chapter 8.5.1 are editable. Click "Save" to update
information. If all conditions previously explained have been respected,
the data will be updated.

Data: see chapter 8.5.1

[]{#anchor-553}[]{#anchor-554}[]{#anchor-555}8.6 Examination![](Pictures/10000000000002AC000002190470012AFD8A8380.jpg){width="11.589cm" height="9.075cm"}![](Pictures/10000201000002450000011AB27C7BBAF03D43ED.png){width="9.862cm" height="4.784cm"}
=====================================================================================================================================================================================================================================================

The "Examination" feature collects weight, height, arterial pressure,
heart rate, temperature and oxygen saturation of the patient, plus the
date and time of the examination. Select a patient from the patients
browser and click "Examination" (or click this button on the "New / Edit
Admission" window; see chapters 8.5.1, 8.5.2).

Date and time refer to when the new window opens (left). If necessary,
enter a DD/MM/YYYY - HH:MM or click the calendar icon (3.10.1). Type
height (0-250 cm) and weight (0-400 kg), or select them with the slider.
Tick the checkboxes to enable the arterial pressure fields, the heart
rate slider (0-200 bpm), the temperature slider (0-50 °C) and the oxygen
saturation slider
(0-100%).![](Pictures/10000201000002630000010F245E359A861946FC.png){width="10.345cm"
height="4.597cm"} Add optional notes in the "Complain" textfield. Then
click "Save" to save the data. Every time the window referring to the
same patient is opened, former measurements will be visible (right),
each with its date and time. Note 0, 0.0 and 0/0 values mean those data
were not collected (checkboxes not ticked).

Data:

-   PEX\_ID (primary key, measurement ID)
-   PEX\_DATE (date and time)
-   PEX\_PAT\_ID (foreign key referencing the "patient" database)
-   PEX\_HEIGHT
-   PEX\_WEIGHT
-   PEX\_PA\_MIN (minimum arterial pression)
-   PEX\_PA\_MAX (maximum arterial pression)
-   PEX\_FC (heart rate)
-   PEX\_TEMP (temperature)
-   PEX\_SAT (oxygen saturation)
-   PEX\_NOTE (optional notes)

[]{#anchor-556}[]{#anchor-557}[]{#anchor-558}8.7 OPD
====================================================

If "OPDEXTENDED=yes" in the rsc/generalData.properties file, you can
access to the OPD menu, by selecting a patient and clicking "OPD" (see
chapter 4).

[]{#anchor-559}[]{#anchor-560}[]{#anchor-561}8.8 Bill
=====================================================

Select a patient and click "Bill" to access the "Accounting -\> New
Bill" to record a new bill for that patient (see chapter 7.1).

[]{#anchor-562}[]{#anchor-563}[]{#anchor-564}8.9 Patient Data![](Pictures/10000000000003330000026A5B62AB1AD010048F.jpg){width="13.882cm" height="10.465cm"}![](Pictures/10000201000002860000017A37D382FAB23809F9.png){width="10.918cm" height="6.394cm"}
========================================================================================================================================================================================================================================================

Select a patient from the browser and click "Data". The "Patient Data"
window opens (left). Admission history is reported on the right half.
Date, ward, admission diagnosis, discharge diagnosis and discharge date
are shown. Buttons on the bottom allow to manage these records and
update malnutrition control.

[]{#anchor-565}[]{#anchor-566}[]{#anchor-567}8.9.1 Edit Patient Data
====================================================================

Select a row of "Patient Data" and click "Edit". The "Edit admission"
opens (8.5.2).

[]{#anchor-568}[]{#anchor-569}[]{#anchor-570}8.9.2 Delete Patient Data
======================================================================

Select a row of "Patient Data" and click "Delete". Click "Yes" on the
confirmation window to remove the row, or "No" to abort.

[]{#anchor-571}[]{#anchor-572}[]{#anchor-573}8.9.3 Malnutrition Control![](Pictures/1000020100000195000000B248D809E7F1995C78.png){width="6.288cm" height="2.764cm"}
===================================================================================================================================================================

Select a row of "Patient Data" (if the "Malnutrition control" checkbox
has previously been ticked; see chapter 8.5.1), then click "Malnutrition
control". A "Malnutrition Browser" window opens (left). It provides a
table with four columns: further date (date of the measurement),
approval date (date of next scheduled measurement), height and weight
(both referred to the current measurement. These data are completely
independent from those collected via the "Examination" menu (8.6).

[]{#anchor-574}[]{#anchor-575}[]{#anchor-576}8.9.3.1 New Malnutrition Control record![](Pictures/1000020100000119000000B7F7D58E0B62390A73.png){width="4.678cm" height="3.046cm"}
================================================================================================================================================================================

To add a measurement to the malnutrition browser, click "New". A new
window opens (left). Enter DD/MM/YYYY dates of the current and next
examination, weight and height. All data are mandatory. Click "OK" to
confirm, else "Cancel" to abort. If all data are correct, the
measurement will be added to the table above, else am error message is
shown:

-   "Insert correct value in height field"
-   "Insert correct value in weight field"
-   "The data type must be dd/mm/yyyy in 'date of this/next control' "

Data:

-   malnutritioncontrol.MLN\_ID (primary key, measurement ID)
-   malnutritioncontrol.MLN\_DATE\_SUPP (date of the current
    measurement)
-   malnutritioncontrol.MNL\_DATE\_CONF (date of the next scheduled
    measurement)
-   malnutritioncontrol.MLN\_HEIGHT (height)
-   malnutritioncontrol.MLN\_WEIGHT (weight)

[]{#anchor-577}[]{#anchor-578}[]{#anchor-579}8.9.3.2 Edit Malnutrition Control record
=====================================================================================

Select a row of the malnutrition browser and click "Edit". An "Edit
Admission Record" window opens, where all data (8.9.3.1) are editable;
then click "OK" to confirm. If data are correct, the record will be
updated.

Data: see chapter 8.9.3.1

[]{#anchor-580}[]{#anchor-581}[]{#anchor-582}8.9.3.3 Delete Malnutrition Control record
=======================================================================================

Select a row of the malnutrition browser and click "Delete". Click "Yes"
on the confirmation window to remove the row, or "No" to abort.

Data:

-   malnutritioncontrol.MLN\_ID

[]{#anchor-583}[]{#anchor-584}[]{#anchor-585}8.9.3.4 Close Malnutrition Browser menu
====================================================================================

Click "Close" on the "Malnutrition Browser" window to return to the
"Patient Data" window.

[]{#anchor-586}[]{#anchor-587}[]{#anchor-588}8.9.4 Close Patient Data menu
==========================================================================

Click "Close" on the "Patient Data" window to return to OH's main menu.

[]{#anchor-589}[]{#anchor-590}[]{#anchor-591}8.10 Clinical sheet![](Pictures/100000000000023B0000019ABF608B196B906DE3.jpg){width="9.675cm" height="6.936cm"}
============================================================================================================================================================

Select a patient from the browser and click "Clinical Sheet". A window
similar to "Patient Data" (8.9) opens (below), but it has different
buttons, aiming to generate Jasper Viewer reports (see 3.8.4 for .PDF
export / print / zoom / navigation operations) about the patient's OPD
history. If "DICOMMODULEENABLED=yes" in the rsc/generalData.properties,
you can access to the DICOM Viewer to analyze sonograms (8.10.5).

[]{#anchor-592}[]{#anchor-593}[]{#anchor-594}8.10.1 OPD Chart![](Pictures/10000201000002A70000017F4A791DE5E918C5AB.png){width="11.485cm" height="6.472cm"}
==========================================================================================================================================================

Select a row from "Patient Data" where the column "Ward" is "OPD" (left)
and click "OPD Chart". This generates a report with a summary of the
visit. Information includes patient data and visit details (ID, date,
type, diagnosis, notes).

If there are no "OPD" records, a "Please select an OPD" window is shown.
Click "OK" to close
it.![](Pictures/10000201000002130000016018E67477EFC77D3F.png){width="9.001cm"
height="5.962cm"}

Data:

-   patient.PAT\_ID
-   patient.PAT\_NAME (patient's first and second name, concatenated)
-   patient.PAT\_SEX
-   patient.PAT\_BDATE
-   patient.PAT\_AGE
-   patient.PAT\_CITY
-   patient.PAT\_HEIGHT
-   patient.PAT\_WEIGHT
-   patient.PAT\_PHOTO
-   opd.OPD\_ID
-   opd.OPD\_DATE
-   opd.OPD\_TYPE
-   opd.OPD\_NOTE ("Clinical Remarks")
-   opd.OPD\_DIS\_ID\_A
-   opd.OPD\_DIS\_ID\_A\_1
-   opd.OPD\_DIS\_ID\_A\_2

[]{#anchor-595}[]{#anchor-596}[]{#anchor-597}8.10.2 Admission Chart![](Pictures/10000201000002C300000186CF4D56A81347BB53.png){width="11.979cm" height="6.611cm"}
================================================================================================================================================================

Select a row from "Patient Data" where the column "Ward" has the name of
a ward (left). and click "Admission Chart". This generates a report with
a summary of the visit. Information includes patient data and admission
details (ID, date, type, admission diagnosis, notes, duration, discharge
diagnosis).

![](Pictures/10000201000002190000016A84409749130ED7D5.png){width="9.086cm"
height="6.121cm"}

Data:

-   all "patient" attributes used in 8.10.1
-   admission.ADM\_ID
-   admission.ADM\_WRD\_ID\_A
-   admission.ADM\_FHU
-   admission.ADM\_YPROG
-   admission.ADM\_DATE
-   admission.ADM\_ADMT\_ID\_A\_ADM
-   admission.ADM\_IN\_DIS\_ID\_A
-   admission.ADM\_OUT\_DIS\_ID\_A
-   admission.ADM\_OUT\_DIS\_ID\_A\_2
-   admission.ADM\_OUT\_DIS\_ID\_A\_3
-   admission.ADM\_DATE\_DIS
-   admission.ADM\_DIST\_ID\_A

[]{#anchor-598}[]{#anchor-599}[]{#anchor-600}8.10.3 Discharge Chart![](Pictures/10000201000002A300000177E4E0B8CA009B1B22.png){width="11.405cm" height="6.334cm"}
================================================================================================================================================================

Select a row from "Patient Data" where the column "Ward" has the name of
a ward (left). and click "Discharge Chart". This generates the admission
chart seen in chapter 8.10.2, plus the discharge details.

Data: see chapter 8.10.2

![](Pictures/100002010000029A000001CDC863C26442D2C9DB.png){width="11.287cm"
height="7.819cm"}

[]{#anchor-601}[]{#anchor-602}[]{#anchor-603}8.10.4 Launch Report![](Pictures/10000201000002AA00000191E6FD86B81E5FF2D3.png){width="11.571cm" height="6.796cm"}
==============================================================================================================================================================

Select a row from "Patient Data" and click "Discharge Chart". This
generates the admission chart (8.10.2), plus a report of the patient's
exams and their results.

Data:

-   all "patient" attributes used in 8.10.1
-   exam.EXA\_DESC
-   laboratory.LAB\_DATE
-   laboratory.LAB\_RESULT

![](Pictures/1000020100000324000001E96F5E268EF6572B2F.png){width="13.612cm"
height="8.28cm"}

[]{#anchor-604}[]{#anchor-605}[]{#anchor-606}8.10.5 DICOM![](Pictures/1000020100000348000001D6A817893F4CF5A4B3.png){width="16.99cm" height="9.506cm"}
=====================================================================================================================================================

Click "DICOM" on the "Patient Data" window to activate the DICOM Viewer,
a tool used to analyze sonograms. The window has two buttons on the
bottom. When opened, only the "Load DICOM" button is enabled. Click to
upload a .dicom video. Once the file has been opened, the "Zoom" and
"Frames" sliders are enabled. The former zooms the current image, while
the latter shows the current video frame. You can load more files, and
choose the one to visualize, clicking on the thumbnails on the left side
of the window. Click "Delete DICOM" to remove a video from the window.

Data:

all attributes from the "dicom" database.

[]{#anchor-607}[]{#anchor-608}[]{#anchor-609}8.10.6 Close Clinical Sheet Menu
=============================================================================

Click "Close" on the "Patient Data" window to return to the "Patients
browser" window.

[]{#anchor-610}[]{#anchor-611}[]{#anchor-612}8.11 Therapy![](Pictures/100000000000027F000001E6220C8C5F56A23278.jpg){width="10.821cm" height="8.234cm"}
======================================================================================================================================================

Select a patient from the browser and click "Therapy". A new window
opens (left), showing the current calendar month. The user can add memos
of scheduled patient visits / therapies. To change the month and / or
year displayed, use the dropdown menu for the month and the selector for
the year, both on the left top corner of the window. Manage the
patient's calendar with the buttons on the right side, that will be
explained in the following
paragraphs.![](Pictures/10000201000002C900000187E8520390DF3868DB.png){width="12.054cm"
height="6.606cm"}

[]{#anchor-613}[]{#anchor-614}[]{#anchor-615}8.11.1 Add Therapy![](Pictures/100002010000027E0000015BF01E5995D0D39C35.png){width="10.821cm" height="5.863cm"}
============================================================================================================================================================

To add a new therapy for the selected patient, click "Add Therapy". A
"Therapy Entry Form - New" window opens. Select the medical, determine
the quantity either typing the number or using the slider. Select the
daily frequency clicking on the "1", "2", "3" or "4" radio buttons. Type
the interval in days ("frequency within period").

Fill the fields on the right side to determine the duration of the
therapy (in months, weeks and days), then select the start date either
by clicking on the calendar icon or typing the DD/MM/YY date. Finally,
add optional date if necessary. Once the data have been inserted, click
"OK" (or "Cancel" to abort the operation. If the data are correct, the
therapy memo will be added to the calendar, else an error window will be
shown:

-   "Select a pharmaceutical"
-   "Please insert a quantity greater than 0" (for numeric fields)

Data:

-   therapies.THR\_ID (primary key, therapy ID)
-   therapies.THR\_PAT\_ID (foreign key referencing the "patient"
    database)
-   therapies.THR\_STARTDATE (therapy start date)
-   therapies.THR\_ENDDATE (therapy end date)
-   therapies.THR\_MDSR\_ID (medical ID)
-   therapies.THR\_QTY (quantity)
-   therapies.THR\_FREQINDAY (daily frequence)
-   therapies.THR\_FREQINPRD (fréquence)
-   therapies.THR\_NOTE (optional notes)
-   therapies.THR\_SMS (1 if a notification SMS was sent to the patient,
    else 0; see 8.11.7)

[]{#anchor-616}[]{#anchor-617}[]{#anchor-618}8.11.2 Edit Therapy![](Pictures/10000201000002A700000177E5376C4F3B3BA42D.png){width="11.511cm" height="6.355cm"}
=============================================================================================================================================================

Select a therapy stored in the calendar and click "Edit Therapy". All
data are editable. Click "OK" to update, or "Cancel" to abort.

Data: see chapter 8.11.1

[]{#anchor-619}[]{#anchor-620}[]{#anchor-621}8.11.3 Remove Therapy
==================================================================

Select a therapy stored in the calendar and click "Remove Therapy". It
will be automatically deleted.

Data:

-   therapies.THR\_ID

[]{#anchor-622}[]{#anchor-623}[]{#anchor-624}8.11.4 Check Availability![](Pictures/1000020100000190000000B015D9DAF4F699AA3E.png){width="6.914cm" height="3.048cm"}
==================================================================================================================================================================

Checks the availability of the medical for every stored therapy. When
the therapy is added, it is "NOT CHECKED". Select a therapy and click
"Check Availability". If the medical is available in the pharmacy the
icon shown under that button turns to "AVAILABLE", else a message window
opens as a warning to the user (left). To update the medical DB, see
chapter 5.1.

[]{#anchor-625}[]{#anchor-626}[]{#anchor-627}8.11.5 Add visit
=============================================================

To add a visit for the selected patient, click "Add Visit". Enter the
DD/MM/YY date or choose it clicking on the calendar icon (3.10.1). Then
type the scheduled HH:MM time or select it clicking on the clock icon
(3.10.2). Once date and time have been inserted, click "OK" to confirm.

Data:

-   visits.VST\_ID (primary key, visit ID)
-   visits.VST\_PAT\_ID (foreign key referencing the "patient" database)
-   patient.PAT\_TELE (patient's phone number for SMS; see 8.11.7)
-   visits.VST\_DATE (visit date and time)
-   visits.VST\_NOTE (optional notes)
-   visits.VST\_SMS (1 if a notification SMS was sent to the patient,
    else 0; see 8.11.7)

[]{#anchor-628}[]{#anchor-629}[]{#anchor-630}8.11.6 Remove Visit
================================================================

Select a visit stored in the calendar and click "Remove Visit". It will
be automatically deleted.

Data:

-   visits.VST\_ID

[]{#anchor-631}[]{#anchor-632}[]{#anchor-633}8.11.7 SMS![](Pictures/10000201000001BB00000087ED7867B6A3CCC04D.png){width="7.525cm" height="2.282cm"}
===================================================================================================================================================

Select a visit / therapy and tick the "SMS" checkbox to send a text
notification, with the scheduled date and time, to the patient. If
the![](Pictures/10000201000001480000008671E334F798D5E719.png){width="5.547cm"
height="2.261cm"} patient has no phone number recorded, a message window
(left) asks the user to add a number. If "OK" is clicked, type the
number on the new window (right), to add it to the "patient" database.

Data:

-   visits.VST\_ID
-   visits.VST\_PAT\_ID
-   patient.PAT\_TELE

[]{#anchor-634}[]{#anchor-635}[]{#anchor-636}8.11.8 Save![](Pictures/100002010000010E000000A5663C7E4CDA8FDC33.png){width="4.763cm" height="2.91cm"}
===================================================================================================================================================

Saves data inserted / edited. Click "Save" and a confirmation window
(left) appears. Click "OK" to close it and return to the calendar. If
changes are not saved, the "Close" window (right) is shown. Click:

-   "Yes" (saves changes and closes the calendar window)
-   "No" (closes the calendar window without saving changes)
-   "Cancel" (back to the calendar).

[]{#anchor-637}[]{#anchor-638}[]{#anchor-639}8.11.9 Close Therapy calendar![](Pictures/10000201000001270000009CFA67CA40F386A947.png){width="4.999cm" height="2.651cm"}
======================================================================================================================================================================

Click "Close" on the calendar window to return to the "Admission /
Patient" menu. If changes have been made after the last saving, the
"Close" window opens; see 8.11.8 for options.

[]{#anchor-640}[]{#anchor-641}[]{#anchor-642}8.12 Merge![](Pictures/10000000000001EC00000150BF047ED3C0528179.jpg){width="8.32cm" height="5.69cm"}
=================================================================================================================================================

The merging function is enabled if "MERGEFUNCTION=yes" in the
rsc/generalData.properties. It helps remove double registrations of the
same patient. To merge the data, both records must be "Not Admitted".
Select the two similar records and click "Merge". Click "Yes" on the
confirmation window (below), else "No" to abort the operation.

If the data are correct, the merger takes place and the old record (ID
510 in this example) will be automatically deleted;
else![](Pictures/1000020100000201000000BE264DDE4D1F0494F6.png){width="8.289cm"
height="3.069cm"} an error window is shown:

-   "Please select 2 patients"
-   "Cannot merge admitted patients"

Click "OK" to return to the former window. Pictured below are the
patient browser before the merger, and a detail of the browser after
this
operation.![](Pictures/10000201000003EB000000E7F0468FA9BDF2928A.png){width="16.99cm"
height="3.912cm"}![](Pictures/10000201000004280000005A25C1AC5F890B4561.png){width="16.99cm"
height="1.438cm"}

Data:

two records from the "patient" database, where admission.ADM\_PAT\_ID is
null.

[]{#anchor-643}[]{#anchor-644}[]{#anchor-645}9. Vaccine![](Pictures/10000000000002E10000026EE199B434153BE3D2.jpg){width="12.492cm" height="10.541cm"}![](Pictures/100002010000027C0000016D2CE1E08A797B4943.png){width="10.786cm" height="6.182cm"}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The "patient vaccines browsing" records all vaccinations made to the
patients. The browser provides a table which records show the
vaccination date, the vaccine name (3.7) and type (3.1.13), plus the
patient's name sex and age. A selection panel on the left side helps
search the records. Buttons on the bottom, which will be explained in
the following paragraphs, aim to manage the table.

Data:

-   patientvaccine.PAV\_ID (primary key, vaccination ID; auto-increment)
-   patientvaccine.PAV\_DATE (vaccination date)
-   patientvaccine.PAV\_PAT\_ID (foreign key referencing the "patient"
    database)
-   patient.PAT\_NAME
-   patient.PAT\_SEX
-   patient.PAT\_AGE
-   patientvaccine.PAV\_PAC\_ID\_A (foreign key referencing the
    "vaccine" database)
-   vaccine.VAC\_DESC (vaccine name)
-   vaccine.VAC\_VACT\_ID\_A (foreign key referencing the "vaccinetype"
    database)
-   vaccinetype.VACT\_DESC (vaccine type)

[]{#anchor-646}[]{#anchor-647}[]{#anchor-648}9.1 Search Vaccine
===============================================================

You can easily search records in the "Patient Vaccines Browser" window
thanks to a series of filters:

-   Vaccine type and name: Select the type from the first dropdown, or
    "All type"; then choose the vaccine name from the second dropdown.
    The length of this menu depends on the type choice (only the
    selected type, or all recorded in OH).
-   Vaccination date: filter records by date entering DD/MM/YY dates or
    choosing them clicking on the calendar icon (3.10.1).
-   Age: enter minimum and maximum age of the patients.
-   Sex: select between "All", "Male" and "Female" radio buttons.

Once the filters were selected, click "Search" to visualize only the
matching records, whose number is shown under that button.

Data: see chapter 9

[]{#anchor-649}[]{#anchor-650}[]{#anchor-651}9.2 New Vaccine Record![](Pictures/10000201000002040000015FF50C318083735F75.png){width="8.387cm" height="5.706cm"}
===============================================================================================================================================================

Click "New" on the "Patient Vaccines browsing" window. A new window
opens (left). It has the date of when the record is created (if
necessary, click on calendar icon and select a different date). Then
select the patient to vaccinate, from the first dropdown menu. You can
type either a name - or part of - or his/her ID in the "Patient Code"
field, then click the magnifier icon to help search the patient; select
the vaccine from the "Vaccine" dropdown. Click "OK" to confirm. If the
patient name and the vaccine have been selected, the record will be
added to the "patientvaccine" database, else an error window will be
shown:

-   "Please select a vaccine"
-   "Please select a patient"

Click "OK" to return to the former window.

Data:

see chapter 9

[]{#anchor-652}[]{#anchor-653}[]{#anchor-654}9.3 Edit Vaccine record![](Pictures/100002010000020C000001638A5EB4AB27D92AA8.png){width="9.788cm" height="6.646cm"}
================================================================================================================================================================

Select a row of the "Patient Vaccine Browsing" and click "Edit". An
"Edit patient vaccine" window (left) opens. Date and vaccine - the
latter can be of a different type - are editable. Click "OK" to save
changes. If data are correct (9.2), the record will be updated.

Data:

-   patientvaccine.PAV\_ID
-   patientvaccine.PAV\_DATE
-   patientvaccine.PAV\_PAT\_ID
-   patientvaccine.PAV\_PAC\_ID\_A
-   vaccine.VAC\_DESC
-   vaccine.VAC\_VACT\_ID\_A
-   vaccinetype.VACT\_DESC

[]{#anchor-655}[]{#anchor-656}[]{#anchor-657}9.3 Delete vaccine record
======================================================================

Select a row of the "Patient Vaccine Browsing" and click "Delete". Click
"Yes" on the confirmation window to delete the record from the
"patientvaccine", or "No" to abort the operation.

Data:

-   patientvaccine.PAV\_ID

[]{#anchor-658}[]{#anchor-659}[]{#anchor-660}9.4 Close Vaccine menu
===================================================================

Click "Close" on the "Patient Vaccine Browsing" window to return to OH's
main menu.

[]{#anchor-661}[]{#anchor-662}[]{#anchor-663}10. Statistics
-----------------------------------------------------------

Generates reports of the hospital activity. After clicking "Statistics"
on the main menu, a "Report Launcher" window (below) opens. It has a
dropdown menu to select the data to report, two DD/MM/YYYY fields to
select the date range, and buttons to create reports, either in Jasper
or Excel format.

[]{#anchor-664}[]{#anchor-665}[]{#anchor-666}10.1 Launch report
===============================================================

Select the data to report from the dropdown menu (above) and the
dat![](Pictures/10000000000002DA000001835BEAF3418C43B235.jpg){width="12.338cm"
height="6.57cm"}![](Pictures/100002010000034C0000007BFCD1EF43241C8652.png){width="16.99cm"
height="2.477cm"}![](Pictures/10000201000001BB0000018AA81092FB77CB94C1.png){width="7.512cm"
height="6.685cm"}![](Pictures/10000201000001BC000000EAD2EC3AB4DAEA930A.png){width="7.512cm"
height="3.958cm"}![](Pictures/100002010000021900000116B84EE14BDEC56654.png){width="9.082cm"
height="4.706cm"}e interval, and click "Launch Report". A Jasper Report
document is generated (see 3.8.4 for .PDF export / print / zoom /
navigation operations).

Here are some example of data than can be reported:

-   number of registered patients (left)
-   number of admitted patients
-   numero of diagnoses of the admitted patients
-   laboratory inventory (bottom right)
-   epidemiology reports.
-   financial reports (bottom left).
-   etc.

[]{#anchor-667}[]{#anchor-668}[]{#anchor-669}10.2 Excel
=======================================================

Same as 10.1, with data exported in .csv files, that can be read by
Microsoft Excel. See chapter 5.1.5 to save the generated file.

[]{#anchor-670}[]{#anchor-671}[]{#anchor-672}10.3 Close Stats menu
==================================================================

Click "Close" on the "Report Launcher" window to return to OH's main
menu.

[]{#anchor-673}[]{#anchor-674}[]{#anchor-675}11. Printing![](Pictures/10000000000003C50000016102310C643032BEEF.jpg){width="16.344cm" height="5.978cm"}
------------------------------------------------------------------------------------------------------------------------------------------------------

After clicking "Printing" on the main menu, a sub menu opens, with two
options "Exams List" and "Diseases list". According to the option
selected, a Jasper Viewer document opens, reporting respectively:

-   the list of exams recorded in OH and the set of results stored
-   the list of all diseases recorded in OH, sorted by type

See chapter 3.8.4 for .PDF export / print / zoom / navigation
operations.

[]{#anchor-676}[]{#anchor-677}[]{#anchor-678}12. Help![](Pictures/10000201000001EF000001CB741897FC93D0FC06.png){width="8.394cm" height="7.772cm"}
-------------------------------------------------------------------------------------------------------------------------------------------------

Click "Help" on the main menu to open OH's .pdf user manual, in a new
window (left).

[]{#anchor-679}[]{#anchor-680}[]{#anchor-681}13. The OH database
----------------------------------------------------------------

The database running in OpenHospital is made of three functional
elements:

-   the login DB: manages the access to OpenHospital (13.1)

<!-- -->

-   the main DB: links the main entities, such as patient, medicals,
    wards, exams, operations, etc. (13.2)
-   the rest of the database: a series of independent tables for the
    secondary functions (13.3)

[]{#anchor-682}[]{#anchor-683}[]{#anchor-684}13.1 The login DB![](Pictures/10000201000000BE000001926954D122A5577A02.png){width="4.403cm" height="9.317cm"}
==========================================================================================================================================================

[]{#anchor-685}[]{#anchor-686}[]{#anchor-687}13.2 The main DB![](Pictures/10000000000003EC000005B12312CB11974AB580.png){width="16.99cm" height="24.649cm"}
==========================================================================================================================================================

[]{#anchor-688}[]{#anchor-689}[]{#anchor-690}13.3 Other tables![](Pictures/100000000000029B000003EC5E6C6D55EF16533C.png){width="11.298cm" height="16.99cm"}
===========================================================================================================================================================
