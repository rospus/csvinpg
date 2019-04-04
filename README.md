csvinpg
=======

A bash script that mirrors a remote (S)FTP directory, checks, fix and reassembles downloaded csv files before import in PostgreSQL.

Script helps in a particular situation, quite common in massive postal printing. Code is well documented, shouldn't be a problem understanding how it works.
;-)


OH 1.8.1 User Manual

12/01/16

Table of contents {#table-of-contents .Titolosommario}
=================

[[Intro: How to start OH]{.underline} 7](#_Toc440366947)

[[1. Login]{.underline} 8](#_Toc1)

[[2. File menu]{.underline} 10](#_Toc2)

[[2.1.3 Edit user]{.underline} 12](#_Toc3)

[[2.1.4 Reset Password]{.underline} 13](#_Toc4)

[[2.1.5 Delete User]{.underline} 13](#_Toc5)

[[2.1.6 Close Users browser]{.underline} 13](#_Toc6)

[[2.2 Groups (editing user groups)]{.underline} 14](#_Toc7)

[[2.2.1 New Group]{.underline} 14](#_Toc8)

[[2.2.2 Edit Group]{.underline} 15](#_Toc9)

[[2.2.3 Delete Group]{.underline} 15](#_Toc10)

[[2.2.4 Group Menu]{.underline} 15](#_Toc11)

[[2.2.5 Close Groups Browser menu]{.underline} 16](#_Toc12)

[[3. General Data menu]{.underline} 17](#_Toc13)

[[3.1 Types]{.underline} 17](#_Toc14)

[[3.1.1 Admission Type]{.underline} 18](#_Toc15)

[[3.1.1.1 New Admission Type]{.underline} 19](#_Toc16)

[[3.1.1.2 Edit Admission Type]{.underline} 19](#_Toc17)

[[3.1.1.3 Delete admission type]{.underline} 19](#_Toc18)

[[3.1.1.4 Close Admission Type menu]{.underline} 19](#_Toc19)

[[3.1.2 Discharge Type]{.underline} 20](#_Toc20)

[[3.1.2.1 New Discharge Type]{.underline} 20](#_Toc21)

[[3.1.2.2 Edit Discharge Type]{.underline} 21](#_Toc22)

[[3.1.2.3 Delete Discharge Type]{.underline} 21](#_Toc23)

[[3.1.2.4 Discharge Type menu]{.underline} 21](#_Toc24)

[[3.1.3 Delivery Type]{.underline} 22](#_Toc25)

[[3.1.3.1 New Delivery Type]{.underline} 22](#_Toc26)

[[3.1.3.2 Edit Delivery Type]{.underline} 22](#_Toc27)

[[3.1.3.3 Delete Delivery Type]{.underline} 23](#_Toc28)

[[3.1.3.4 Close Delivery Type menu]{.underline} 23](#_Toc29)

[[3.1.4 Delivery Result Type]{.underline} 24](#_Toc30)

[[3.1.4.1 New Delivery Result Type]{.underline} 24](#_Toc31)

[[3.1.4.2 Edit Delivery Result Type]{.underline} 24](#_Toc32)

[[3.1.4.3 Delete Delivery Result Type]{.underline} 24](#_Toc33)

[[3.1.4.4 Close Delivery Result Type menu]{.underline} 25](#_Toc34)

[[3.1.5 Disease Type]{.underline} 25](#_Toc35)

[[3.1.5.1 New Disease Type]{.underline} 25](#_Toc36)

[[3.1.5.2 Edit Disease Type]{.underline} 26](#_Toc37)

[[3.1.5.3 Delete Disease Type]{.underline} 26](#_Toc38)

[[3.1.5.4 Close Disease Type menu]{.underline} 26](#_Toc39)

[[3.1.6 Exam Type]{.underline} 26](#_Toc40)

[[3.1.6.1 New Exam Type]{.underline} 27](#_Toc41)

[[3.1.6.2 Edit Exam Type]{.underline} 27](#_Toc42)

[[3.1.6.3 Delete Exam Type]{.underline} 27](#_Toc43)

[[3.1.6.4 Close Exam Type Menu]{.underline} 27](#_Toc44)

[[3.1.7 Medical Stock Movement Type]{.underline} 28](#_Toc45)

[[3.1.7.1 New Medical Stock Movement Type]{.underline} 28](#_Toc46)

[[3.1.7.2 Edit Medical Stock Movement Type]{.underline} 29](#_Toc47)

[[3.1.7.3 Delete Medical Stock Movement Type]{.underline} 29](#_Toc48)

[[3.1.7.4 Close Medical Stock Movement Type menu]{.underline}
29](#_Toc49)

[[3.1.8 Medical Type]{.underline} 29](#_Toc50)

[[3.1.8.1 New Medical Type]{.underline} 30](#_Toc51)

[[3.1.8.2 Edit Medical Type]{.underline} 30](#_Toc52)

[[3.1.8.3 Delete Medical Type]{.underline} 30](#_Toc53)

[[3.1.8.4 Close Medical Type Menu]{.underline} 30](#_Toc54)

[[3.1.9 Operation Type]{.underline} 31](#_Toc55)

[[3.1.9.1 New Operation Type]{.underline} 31](#_Toc56)

[[3.1.9.2 Edit Operation Type]{.underline} 31](#_Toc57)

[[3.1.9.3 Delete Operation Type]{.underline} 32](#_Toc58)

[[3.1.9.4 Close Operation Type Menu]{.underline} 32](#_Toc59)

[[3.1.10 Pregnant Treatment Type]{.underline} 32](#_Toc60)

[[3.1.10.1 New Pregnant Treatment Type]{.underline} 32](#_Toc61)

[[3.1.10.2 Edit Pregnant Treatment Type]{.underline} 33](#_Toc62)

[[3.1.10.3 Delete Pregnant Treatment Type]{.underline} 33](#_Toc63)

[[3.1.10.4 Close Pregnant Treatment menu]{.underline} 33](#_Toc64)

[[3.1.11 Other Prices]{.underline} 34](#_Toc65)

[[3.1.11.1 New List]{.underline} 34](#_Toc66)

[[3.1.11.2 Edit List]{.underline} 34](#_Toc67)

[[3.1.11.3 Delete List]{.underline} 34](#_Toc68)

[[3.1.11.4 Close Other Prices menu]{.underline} 34](#_Toc69)

[[3.1.12 Age Type]{.underline} 35](#_Toc70)

[[3.1.12.1 Edit Age Type]{.underline} 35](#_Toc71)

[[3.1.12.2 Close Age type menu]{.underline} 35](#_Toc72)

[[3.1.13 Vaccine Type]{.underline} 36](#_Toc73)

[[3.1.13.1 New Vaccine Type]{.underline} 36](#_Toc74)

[[3.1.13.2 Edit Vaccine Type]{.underline} 36](#_Toc75)

[[3.1.13.3 Delete Vaccine Type]{.underline} 37](#_Toc76)

[[3.1.13.4 Close Vaccine type menu]{.underline} 37](#_Toc77)

[[3.2 Hospital]{.underline} 37](#_Toc78)

[[3.3 Ward]{.underline} 38](#_Toc79)

[[3.3.1 New Ward]{.underline} 39](#_Toc80)

[[3.3.2 Edit Ward]{.underline} 39](#_Toc81)

[[3.3.3 Delete Ward]{.underline} 40](#_Toc82)

[[3.3.4 Close Ward menu]{.underline} 40](#_Toc83)

[[3.4 Disease]{.underline} 41](#_Toc84)

[[3.4.1 Select Disease Type]{.underline} 41](#_Toc85)

[[3.4.2 New Disease]{.underline} 41](#_Toc86)

[[3.4.3 Edit Disease]{.underline} 42](#_Toc87)

[[3.4.4 Delete Disease]{.underline} 42](#_Toc88)

[[3.4.5 Close Disease menu]{.underline} 43](#_Toc89)

[[3.5 Exams]{.underline} 44](#_Toc90)

[[3.5.1 Select Exam type]{.underline} 44](#_Toc91)

[[3.5.2 New Exam]{.underline} 45](#_Toc92)

[[3.5.3 Edit Exam]{.underline} 45](#_Toc93)

[[3.5.4 Delete Exam]{.underline} 46](#_Toc94)

[[3.5.5 Exam result]{.underline} 46](#_Toc95)

[[3.5.6 Close Exams menu]{.underline} 46](#_Toc96)

[[3.6 Operation]{.underline} 47](#_Toc97)

[[3.6.1 Select operation type]{.underline} 47](#_Toc98)

[[3.6.2 New Operation]{.underline} 47](#_Toc99)

[[3.6.3 Edit Operation]{.underline} 48](#_Toc100)

[[3.6.4 Delete Operation]{.underline} 48](#_Toc101)

[[3.6.5 Close Operation menu]{.underline} 48](#_Toc102)

[[3.7 Vaccine]{.underline} 49](#_Toc103)

[[3.7.1 Select Vaccine Type]{.underline} 49](#_Toc104)

[[3.7.2 New Vaccine]{.underline} 50](#_Toc105)

[[3.7.3 Edit Vaccine]{.underline} 50](#_Toc106)

[[3.7.4 Delete Vaccine]{.underline} 50](#_Toc107)

[[3.7.5 Close Vaccine menu]{.underline} 50](#_Toc108)

[[3.8 Prices Lists]{.underline} 51](#_Toc109)

[[3.8.1 Choose List]{.underline} 52](#_Toc110)

[[3.8.2 Manage Lists]{.underline} 52](#_Toc111)

[[3.8.2.1 New List]{.underline} 52](#_Toc112)

[[3.8.2.2 Copy List]{.underline} 53](#_Toc113)

[[3.8.2.3 Edit List]{.underline} 53](#_Toc114)

[[3.8.2.4 Delete List]{.underline} 53](#_Toc115)

[[3.8.2.5 Close List Browser]{.underline} 53](#_Toc116)

[[3.8.3 Save List]{.underline} 54](#_Toc117)

[[3.8.4 Print List]{.underline} 54](#_Toc118)

[[3.8.5 Close Price Lists menu]{.underline} 54](#_Toc119)

[[3.9 Supplier]{.underline} 55](#_Toc120)

[[3.9.1 New Supplier]{.underline} 55](#_Toc121)

[[3.9.2 Edit Supplier]{.underline} 56](#_Toc122)

[[3.9.3 Delete Supplier]{.underline} 56](#_Toc123)

[[3.9.4 Close Supplier menu]{.underline} 56](#_Toc124)

[[3.10 SMS Manager]{.underline} 57](#_Toc125)

[[3.10.1 Select date interval]{.underline} 57](#_Toc126)

[[3.10.2 New SMS]{.underline} 58](#_Toc127)

[[3.10.3 Delete SMS]{.underline} 58](#_Toc128)

[[3.10.4 Close SMS Manager menu]{.underline} 58](#_Toc129)

[[4. OPD (OutPatient Department)]{.underline} 59](#_Toc130)

[[4.1 Search Patient]{.underline} 60](#_Toc131)

[[4.2 New OPD registration]{.underline} 61](#_Toc132)

[[4.3 Edit OPD Registration]{.underline} 62](#_Toc133)

[[4.4 Delete OPD registration]{.underline} 62](#_Toc134)

[[4.5 Close OPD menu]{.underline} 62](#_Toc135)

[[5. Pharmacy]{.underline} 63](#_Toc136)

[[5.1 Pharmaceuticals]{.underline} 64](#_Toc137)

[[5.1.1 Select Type]{.underline} 65](#_Toc138)

[[5.1.2 New Pharmaceutical]{.underline} 66](#_Toc139)

[[5.1.3 Edit Pharmaceutical]{.underline} 66](#_Toc140)

[[5.1.4 Delete Pharmaceutical]{.underline} 67](#_Toc141)

[[5.1.5 Export]{.underline} 67](#_Toc142)

[[5.1.6 STOCK]{.underline} 68](#_Toc143)

[[5.1.7 Order]{.underline} 68](#_Toc144)

[[5.1.8 Expiring]{.underline} 69](#_Toc145)

[[5.1.9 Close Pharmaceuticals menu]{.underline} 69](#_Toc146)

[[5.2 Pharmaceutical Stock]{.underline} 70](#_Toc147)

[[5.2.1 Filter]{.underline} 71](#_Toc148)

[[5.2.2 Charge]{.underline} 72](#_Toc149)

[[5.2.3 Discharge]{.underline} 72](#_Toc150)

[[5.2.4 Export]{.underline} 74](#_Toc151)

[[5.2.5 Close Pharmaceutical Stock menu]{.underline} 74](#_Toc152)

[[5.3 Pharmaceutical Stock Ward]{.underline} 75](#_Toc153)

[[5.3.1 Ward Pharmacy]{.underline} 76](#_Toc154)

[[5.3.2 New Outcome]{.underline} 76](#_Toc155)

[[5.3.3 Report]{.underline} 78](#_Toc156)

[[5.3.4 Excel]{.underline} 78](#_Toc157)

[[5.3.5 Rectify]{.underline} 78](#_Toc158)

[[5.3.6 Close Pharmaceutical Stock Ward menu]{.underline} 80](#_Toc159)

[[6. Laboratory]{.underline} 81](#_Toc160)

[[6.1 Search Exam]{.underline} 82](#_Toc161)

[[6.2 New Exam]{.underline} 82](#_Toc162)

[[6.3 Edit Exam]{.underline} 84](#_Toc163)

[[6.4 Delete Exam]{.underline} 84](#_Toc164)

[[6.5 Print table]{.underline} 84](#_Toc165)

[[6.6 Close Laboratory menu]{.underline} 84](#_Toc166)

[[7. Accounting]{.underline} 85](#_Toc167)

[[7.1 New Bill]{.underline} 86](#_Toc168)

[[7.2 Bills Manager]{.underline} 90](#_Toc169)

[[7.2.1 New Bill]{.underline} 90](#_Toc170)

[[7.2.2 Edit Bill]{.underline} 90](#_Toc171)

[[7.2.3 Delete Bill]{.underline} 92](#_Toc172)

[[7.2.4 Receipt]{.underline} 92](#_Toc173)

[[7.2.5 Report]{.underline} 93](#_Toc174)

[[7.2.6 Close Bills Manager]{.underline} 93](#_Toc175)

[[8. Admission/Patient]{.underline} 94](#_Toc176)

[[8.1 Search Patient]{.underline} 94](#_Toc177)

[[8.2 New Patient]{.underline} 96](#_Toc178)

[[8.3 Edit Patient]{.underline} 98](#_Toc179)

[[8.4 Delete patient]{.underline} 99](#_Toc180)

[[8.5 Admission]{.underline} 99](#_Toc181)

[[8.5.1 New Admission]{.underline} 100](#_Toc182)

[[8.5.2 Edit admission]{.underline} 101](#_Toc183)

[[8.6 Examination]{.underline} 102](#_Toc184)

[[8.7 OPD]{.underline} 103](#_Toc185)

[[8.8 Bill]{.underline} 103](#_Toc186)

[[8.9 Patient Data]{.underline} 104](#_Toc187)

[[8.9.1 Edit Patient Data]{.underline} 104](#_Toc188)

[[8.9.2 Delete Patient Data]{.underline} 104](#_Toc189)

[[8.9.3 Malnutrition Control]{.underline} 105](#_Toc190)

[[8.9.3.1 New Malnutrition Control record]{.underline} 105](#_Toc191)

[[8.9.3.2 Edit Malnutrition Control record]{.underline} 105](#_Toc192)

[[8.9.3.3 Delete Malnutrition Control record]{.underline} 105](#_Toc193)

[[8.9.3.4 Close Malnutrition Browser menu]{.underline} 106](#_Toc194)

[[8.9.4 Close Patient Data menu]{.underline} 106](#_Toc195)

[[8.10 Clinical sheet]{.underline} 107](#_Toc196)

[[8.10.1 OPD Chart]{.underline} 107](#_Toc197)

[[8.10.2 Admission Chart]{.underline} 108](#_Toc198)

[[8.10.3 Discharge Chart]{.underline} 109](#_Toc199)

[[8.10.4 Launch Report]{.underline} 110](#_Toc200)

[[8.10.5 DICOM]{.underline} 111](#_Toc201)

[[8.10.6 Close Clinical Sheet Menu]{.underline} 111](#_Toc202)

[[8.11 Therapy]{.underline} 112](#_Toc203)

[[8.11.1 Add Therapy]{.underline} 113](#_Toc204)

[[8.11.2 Edit Therapy]{.underline} 113](#_Toc205)

[[8.11.3 Remove Therapy]{.underline} 114](#_Toc206)

[[8.11.4 Check Availability]{.underline} 114](#_Toc207)

[[8.11.5 Add visit]{.underline} 114](#_Toc208)

[[8.11.6 Remove Visit]{.underline} 114](#_Toc209)

[[8.11.7 SMS]{.underline} 115](#_Toc210)

[[8.11.8 Save]{.underline} 115](#_Toc211)

[[8.11.9 Close Therapy calendar]{.underline} 115](#_Toc212)

[[8.12 Merge]{.underline} 116](#_Toc213)

[[9. Vaccine]{.underline} 117](#_Toc214)

[[9.1 Search Vaccine]{.underline} 119](#_Toc215)

[[9.2 New Vaccine Record]{.underline} 119](#_Toc216)

[[9.3 Edit Vaccine record]{.underline} 120](#_Toc217)

[[9.3 Delete vaccine record]{.underline} 120](#_Toc218)

[[9.4 Close Vaccine menu]{.underline} 120](#_Toc219)

[[10. Statistics]{.underline} 121](#_Toc220)

[[10.1 Launch report]{.underline} 121](#_Toc221)

[[10.2 Excel]{.underline} 122](#_Toc222)

[[10.3 Close Stats menu]{.underline} 122](#_Toc223)

[[11. Printing]{.underline} 123](#_Toc224)

[[12. Help]{.underline} 123](#_Toc225)

[[13. The OH database]{.underline} 124](#_Toc226)

[[13.1 The login DB]{.underline} 124](#_Toc440366455)

[[13.2 The main DB]{.underline} 125](#_Toc440366456)

[[13.3 Other tables]{.underline} 126](#_Toc229)

[]{#_Toc440366947 .anchor}Intro: How to start OH

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

File: it has two options: "exit", to log out as seen above, and "users",
to manage all OH users. The amministratore can create groups of users
benefitting of the same set of rights. Click on "users" button to open a
new sub-level with the "users" option to edit a single users's settings
and the "groups" option to manage user groups.

General Data: it manages all data used by the OH database.

OPD (Out Patient Department): this section allows the user to record,
search, update and edit the patient\'s visits.

Pharmacy: OH's pharmacy records all items used by the hospital. This
menu has three sub-levels: the "Pharmaceuticals" option to manage the
pharmacy database, the "Pharmaceutical Stock" option to record movements
between pharmacy and suppliers and the "Pharmaceutical Stock Ward"
option to record movements within the hospital and its wards.

Laboratory: this section allows the user to record, search and update
the patient's exams.

Accounting: OH's cash register records the bills generated from medical
items and patient exams.

Admission/Patient: this section allows the user to manager the patient
database.

Patient Vaccines: similar to the "Laboratory" menu, it records the
patient's vaccinations.

Statistics: it generates Excel reports about the hospital activity on a
given period of time.

Printing: it generates a document with either the exams list or the
diseases list, sorted by type.

Help: it opens a .PDF file with the user's guide.

[]{#_Toc1 .anchor}1.
Login![](media/image1.jpeg){width="3.3444455380577427in"
height="2.3495199037620296in"}

When starting OH for the first time, once it is being loaded, the main
menu is immediately shown, as login is disabled. Open the project in
Eclipse, click on triangles near the project name, the sub-folder "rsc"
(below), and the file "generalData.properties", containing all system
settings. Row 3 shows by default the string "SINGLEUSER=yes". Replacing
"yes" with "no" on this string, the login window (on the bottom on the
page) is![](media/image2.png){width="4.586369203849519in"
height="4.034513342082239in"} enabled. The user chooses his/her name
from the dropdown menu with the user list, then enters the corresponding
password. If username and password don't match, an error window opens,
showing the "password incorrect: retry", message. Click OK to close this
window and enable the login window again. If the password is correct,
the user enters the OH system. The main menu is shown, with all the
options granted for the given
user.![](media/image3.jpeg){width="2.870162948381452in"
height="1.368847331583552in"}

The admin menu (left) has
all![](media/image4.jpeg){width="2.1514818460192475in"
height="3.462863079615048in"} the options enabled, while
a![](media/image5.jpeg){width="2.028665791776028in"
height="4.588197725284339in"} guest menu (i.e., "Eduardo" menu, see also
chapter 2.1.2) has a limited set of options. The administrator can edit
all user's privileges.

Data:

-   user.US\_ID\_A (username)

-   user.US\_PASSWD (password)

[]{#_Toc2 .anchor}2. File
menu![](media/image6.jpeg){width="6.692976815398075in"
height="5.837820428696413in"}

The "File" menu contains two sub-menus: "exit", to close OH, and
"users", where the administrator can manage user access to the system.

Focusing on "users" option and clicking on its button, the new window
shows two options, "users" and "groups". The former allows the
administrator to manage a given user's privileges, while the latter
allows to create user groups.

***2.1 Users (editing a single
user)***![](media/image7.jpeg){width="4.13580927384077in"
height="2.2746948818897637in"}

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

***2.1.2 New User***![](media/image8.jpeg){width="2.4168897637795275in"
height="2.5069597550306213in"}

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

![](media/image9.jpeg){width="5.976608705161855in"
height="3.2951727909011375in"}

[]{#_Toc3 .anchor}2.1.3 Edit
user![](media/image10.jpeg){width="3.0426760717410324in"
height="2.084796587926509in"}

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

[]{#_Toc4 .anchor}2.1.4 Reset
Password![](media/image11.jpeg){width="2.2380096237970255in"
height="1.388546587926509in"}

To change the password for a given user, select a row from the users
browser and click "Reset Password". Insert the new password on the new
window (left).

Then click "OK". Retype the new password on a second window similar to
the first one and click "OK".

![](media/image12.jpeg){width="2.2380096237970255in"
height="1.2551006124234472in"}![](media/image13.png){width="2.2625984251968503in"
height="1.1334251968503937in"}

If the passwords don't match, an error message (left) is shown, else a
confirmation window opens (right) and the new password is stored in the
users DB (bottom window). Clicking "Cancel" anytime, the operation is
aborted and there will be no changes to the users DB.

Data:

-   user.US\_ID\_A (username)

-   usergroup.UG\_ID\_A (password)

[]{#_Toc5 .anchor}2.1.5 Delete
User![](media/image14.jpeg){width="4.321135170603674in"
height="2.3679615048118987in"}

Removes the selected user from the user list. Select a row and click
"Delete". As in most "delete" operations, a confirmation window opens:
click "Yes" to definitely remove the user from the list, or "No" to
abort the operation.

Data:

-   user.US\_ID\_A (primary key, username)

[]{#_Toc6 .anchor}2.1.6 Close Users browser

Closes the "Users browser" window. Click "Close" to return to the main
menu.

[]{#_Toc7 .anchor}2.2 Groups (editing user
groups)![](media/image15.jpeg){width="4.61162510936133in"
height="1.462998687664042in"}

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

[]{#_Toc8 .anchor}2.2.1 New
Group![](media/image16.png){width="3.6809875328083987in"
height="2.0475207786526686in"}

Creates a new user group. Click "New" on the "groups browser". Add the
name and an optional description in the new window, then click "OK" to
confirm. If the name doesn't exist in the "usergroup\" database, the
group will be added, else a "the group is already present" message
appears. If no name is inserted, a "please insert a valid user group"
message is shown.![](media/image17.png){width="4.388829833770779in"
height="1.3821194225721785in"} Click "OK" after both unsuccessful cases
to add a proper name. Once a valid name is entered, the new group is
added to the "group browser" table (right).

Data:

both "usergroup" attributes

[]{#_Toc9 .anchor}2.2.2 Edit Group

Edits the group's description. It's similar to the "Edit User" option
(2.1.3). Select a row, click "Edit" and type the (optional) description
in the new window. Click "OK" to save changes, or "Cancel" to abort the
operation.

Data:

both "usergroup" attributes

[]{#_Toc10 .anchor}2.2.3 Delete Group

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

[]{#_Toc11 .anchor}2.2.4 Group
Menu![](media/image18.png){width="4.657835739282589in"
height="3.2038003062117237in"}

Allows the administrator, and all the users with this feature enabled,
to manage privileges for every group in the "usergroup" database. Select
a group from the "Group Browser" window and click "GroupMenu". A new
window "Menu Item Browser" (left), reproducing OH's main menu, opens.
Click on the triangles to expand the menu items. Enabled functions are
shown in black, while disabled options are shown in light grey. Double
click on a single option to activate/deactivate it. Click "Update" to
save changes, or close the window to abort the operation.

As seen in chapter 1,![](media/image19.png){width="4.700784120734908in"
height="3.6350623359580054in"} "Eduardo" can't read the user menu
("HELP" option) by default. The administrator, or any user with
permission to edit groups, selects the "guest" row, clicks "GroupMenu",
then double-clicks "HELP" on the "Menu
Item![](media/image20.png){width="1.8586111111111112in"
height="3.1936701662292215in"} Browser" window (left) and clicks
"Update". Now Eduardo can access the user guide, as the menu pictured on
the right shows the "HELP" button.

Data:

-   groupmenu.GM\_ID (primary key, option ID)

-   groupmenu.GM\_UG\_ID\_A (user)

-   groupmenu.GM\_MNI\_ID\_A (option name)

-   groupmenu.GM\_ACTIVE (Y if the option is enabled, else N)

[]{#_Toc12 .anchor}2.2.5 Close Groups Browser menu

Closes the "groups browser" window. Click "Close" to return to the main
menu.

[]{#_Toc13 .anchor}3. General Data menu

[]{#_Toc14 .anchor}3.1
Types![](media/image21.jpeg){width="3.300586176727909in"
height="3.4674890638670166in"}

All data the hospital needs to work with - such as, medicals, exams,
operations, diseases, etc. - are sorted by type. This menu shows users
the list of categories for all data used in the OH databases. Users can
define new types according to their needs.

OH's categorized elements are:

-   Admission type (the way the patient is admitted in the hospital)

-   Discharge type: (the way the patient is dismissed from the hospital)

-   Delivery type: (normal, caesarian, ...)

-   Delivery result type
    (childbirth's![](media/image22.png){width="1.77625in"
    height="4.8224748468941385in"} outcome)

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

[]{#_Toc15 .anchor}3.1.1 Admission
Type![](media/image23.png){width="4.18036854768154in"
height="1.0075863954505686in"}![](media/image24.jpeg){width="4.180398075240595in"
height="1.8665441819772528in"}

The "Admission Type Browsing" table shows the different ways a patient
is admitted in to the hospital. Default types are:

"A" (Ambulance, an ambulance carries the patient)

"R" (Referral, patient coming from another hospital / ward)

"I" (Self, patient coming by him/herself). Below is a screenshot from
the "New Admission" option (8.5.1), where a dropdown menu is used to
select admission
types.![](media/image25.png){width="6.688889982502187in"
height="3.217240813648294in"}

Data:

-   admissiontype.ADMT\_ID\_A (primary key, admission type ID)

-   admissiontype.ADMT\_DESC (admission type description)

[]{#_Toc16 .anchor}3.1.1.1 New Admission
Type![](media/image26.png){width="3.8492639982502186in"
height="2.5335378390201226in"}

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

[]{#_Toc17 .anchor}3.1.1.2 Edit Admission
Type![](media/image27.png){width="1.9367979002624671in"
height="1.3577034120734908in"}

Select a row from "Admission Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing admission type
record" panel.

Data:

both "admissiontype" attributes (3.1.1)

[]{#_Toc18 .anchor}3.1.1.3 Delete admission type

Removes a row from the "admissiontype" database. Select a row from
"Admission Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

admissiontype.ADMT\_ID\_A

[]{#_Toc19 .anchor}3.1.1.4 Close Admission Type menu

Click "Close" on the "Admission Type Browsing" window to return to main
menu.

[]{#_Toc20 .anchor}3.1.2 Discharge
Type![](media/image28.jpeg){width="5.181883202099738in"
height="2.264867672790901in"}![](media/image29.png){width="4.283069772528434in"
height="1.0953860454943132in"}

The "Discharge type browsing" table defines the different ways a patient
can be dismissed from the hospital. Default types are: "D" (Dead,
patient deceased), "ES" (Escape, the patient escaped from the hospital),
"EQ" (Normal Discharge), "B" (Referred, a further visit is planned for
that patient).

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)

-   dischargetype.DIST\_DESC (discharge type description)

[]{#_Toc21 .anchor}3.1.2.1 New Discharge
Type![](media/image30.png){width="2.227629046369204in"
height="1.513105861767279in"}

Click "New" on the "Discharge type browsing" table. Enter the character
code and a description (used in the "New Discharge" option) on the "New
Discharge Type Record" window. Click "OK" to confirm or "Cancel" to
abort the operation. Both fields are mandatory; see 3.1.1.1 for error
messages.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)

-   dischargetype.DIST\_DESC (discharge type description)

[]{#_Toc22 .anchor}3.1.2.2 Edit Discharge
Type![](media/image31.png){width="2.318391294838145in"
height="1.7111745406824146in"}

Select a row from "Discharge Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing discharge type
record" panel.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)

-   dischargetype.DIST\_DESC (discharge type description)

[]{#_Toc23 .anchor}3.1.2.3 Delete Discharge Type

Removes a row from the "dischargetype" database. Select a row from
"Discharge Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   dischargetype.DIST\_ID\_A (primary key, discharge type ID)

[]{#_Toc24 .anchor}3.1.2.4 Discharge Type menu

Click "Close" on the "Discharge Type Browsing" window to return to main
menu.

[]{#_Toc25 .anchor}3.1.3 Delivery
Type![](media/image32.jpeg){width="4.416103455818023in"
height="1.9095538057742782in"}

The "Delivery type browsing" table defines the ways of assisting
pregnant mothers in the event of a delivery. Default types are: "C"
(Caesarian delivery), "V" (Vacuum extraction), "N" (No assistance).

![](media/image33.png){width="3.767956036745407in"
height="1.2018186789151357in"}

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)

-   deliverytype.DRT\_DESC (delivery type ID)

[]{#_Toc26 .anchor}3.1.3.1 New Delivery Type

Click "New" on the "Delivery type browsing" table. Enter the
one-character code and a description on the "New Delivery Type Record"
window. Click "OK" to confirm or "Cancel" to abort the operation. Both
fields are mandatory; see 3.1.1.1 for error messages.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)

-   deliverytype.DRT\_DESC (delivery type ID)

[]{#_Toc27 .anchor}3.1.3.2 Edit Delivery
Type![](media/image34.png){width="2.0307950568678916in"
height="1.521956474190726in"}

Select a row from "Delivery Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing delivery type
record" panel.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)

-   deliverytype.DRT\_DESC (delivery type ID)

[]{#_Toc28 .anchor}3.1.3.3 Delete Delivery Type

Removes a row from the "deliverytype" database. Select a row from
"Delivery Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   deliverytype.DRT\_ID\_A (primary key, delivery type ID)

[]{#_Toc29 .anchor}3.1.3.4 Close Delivery Type menu

Click "Close" on the "Delivery Type Browsing" window to return to the
main menu.

[]{#_Toc30 .anchor}3.1.4 Delivery Result
Type![](media/image35.jpeg){width="4.7268667979002625in"
height="2.003213035870516in"}

The "Delivery result type browsing" table defines the different delivery
outcomes. Default types are shown
below:![](media/image36.png){width="2.552544838145232in"
height="1.194730971128609in"}

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)

-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#_Toc31 .anchor}3.1.4.1 New Delivery Result
Type![](media/image37.png){width="2.070379483814523in"
height="1.2454997812773403in"}

Click "New" on the "Delivery result type browsing" table. Enter the
one-character code and a description on the "New Delivery Result Type
Record" window. Click "OK" to confirm or "Cancel" to abort the
operation. Both fields are mandatory; see 3.1.1.1 for error messages.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)

-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#_Toc32 .anchor}3.1.4.2 Edit Delivery Result
Type![](media/image38.png){width="2.0063188976377955in"
height="1.1610487751531058in"}

Select a row from "Delivery Result Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing delivery result
type record" panel.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)

-   deliveryresulttype.DRT\_DESC (delivery result type description)

[]{#_Toc33 .anchor}3.1.4.3 Delete Delivery Result Type

Removes a row from the "deliveryresulttype" database. Select a row from
"Delivery Result Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   deliveryresulttype.DRT\_ID\_A (primary key, delivery result type ID)

[]{#_Toc34 .anchor}3.1.4.4 Close Delivery Result Type menu

Click "Close" on the "Delivery Result Type Browsing" window to return to
the main menu.

[]{#_Toc35 .anchor}3.1.5 Disease
Type![](media/image39.jpeg){width="4.391943350831146in"
height="1.879225721784777in"}

The table "Disease type browsing" defines the different disease
categories used in OH, including "OPD". Default types: "ND" (Notifiable
diseases), "OC" (Infective diseases), "MP" (Maternal / perinatal
diseases), "NC" (Non communicable diseases), "AO" (All other
diseases).![](media/image40.png){width="3.2708081802274718in"
height="1.0571456692913386in"}

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)

-   diseasetype.DCL\_DESC (disease type description)

[]{#_Toc36 .anchor}3.1.5.1 New Disease
Type![](media/image41.png){width="3.143445975503062in"
height="1.6874868766404199in"}

Click "New" on the "Disease type browsing" table. Enter the character
code and a description on the "New Disease Type Record" window. Click
"OK" to confirm or "Cancel" to abort the operation. Both fields are
mandatory; see 3.1.1.1 for error messages.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)

-   diseasetype.DCL\_DESC (disease type description)

[]{#_Toc37 .anchor}3.1.5.2 Edit Disease
Type![](media/image42.png){width="2.86490813648294in"
height="1.4653608923884514in"}

Select a row from "Disease Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing disease type
record" panel.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)

-   diseasetype.DCL\_DESC (disease type description)

[]{#_Toc38 .anchor}3.1.5.3 Delete Disease Type

Removes a row from the "diseasetype" database. Select a row from
"Disease Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   diseasetype.DCL\_ID\_A (primary key, disease type ID)

[]{#_Toc39 .anchor}3.1.5.4 Close Disease Type menu

Click "Close" on the "Disease Type Browsing" window to return to the
main menu.

[]{#_Toc40 .anchor}3.1.6 Exam
Type![](media/image43.jpeg){width="4.734644575678041in"
height="2.0528871391076113in"}

The "Exam Type Browsing" table defines the different exam categories
used in OH, including "Laboratory". Default types are shown below:

![](media/image44.png){width="2.672912292213473in"
height="1.7172528433945757in"}

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)

-   examtype.EXC\_DESC (exam type description)

[]{#_Toc41 .anchor}3.1.6.1 New Exam
Type![](media/image45.png){width="3.0239096675415573in"
height="1.5529199475065616in"}

Click "New" on the "Exam type browsing" table. Enter the character code
and a description on the "New Exam Type Record" window. Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)

-   examtype.EXC\_DESC (exam type description)

[]{#_Toc42 .anchor}3.1.6.2 Edit Exam
Type![](media/image46.png){width="2.722502187226597in"
height="1.3799573490813648in"}

Select a row from "Exam Type Browsing" and click "Edit". The description
field is freely editable. Click "OK" to save changes, or "Cancel" to
abort the operation. If "OK" is clicked but the description field is
empty, a "Please insert a valid description" window is shown. Click "OK"
on the error window to return to the "Editing exam type" panel.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)

-   examtype.EXC\_DESC (exam type description)

[]{#_Toc43 .anchor}3.1.6.3 Delete Exam Type

Removes a row from the "examtype" database. Select a row from "Exam Type
Browsing" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

Data:

-   examtype.EXC\_ID\_A (primary key, exam type ID)

[]{#_Toc44 .anchor}3.1.6.4 Close Exam Type Menu

Click "Close" on the "Exam Type Browsing" window to return to the main
menu.

[]{#_Toc45 .anchor}3.1.7 Medical Stock Movement
Type![](media/image47.jpeg){width="4.587451881014873in"
height="2.475246062992126in"}

The "Medicals Stock Movement Type Browsing" table shows the different
money movements involving the hospital. The two basic elements (below)
are: "Charge", for incomes (+), and "Discharge", for payments
(-).![](media/image48.png){width="2.675971128608924in"
height="0.9333858267716535in"}

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)

-   medicaldsrstockmovtype.MMVT\_ID\_DESC (movement type description)

-   medicaldsrstockmovtype.MMVT\_ID\_A ("+" or "-")

[]{#_Toc46 .anchor}3.1.7.1 New Medical Stock Movement
Type![](media/image49.png){width="1.9236220472440946in"
height="1.7009383202099737in"}

Click "New" on the "Medicals Stock Movement Type Browsing" window. Enter
a character code, a description (i.e. the name of the movement) and
select the type (income or outcome)
from![](media/image50.png){width="2.6760433070866143in"
height="1.2733573928258968in"} the dropdown menu. Click "OK" to confirm
or "Cancel" to abort the operation. Both fields are mandatory; see
3.1.1.1 for error messages. Pictured left is an example, where a
"donation" category is added to the "medicaldsrstockmovtype" database
(right).

Data:

see chapter 3.1.7

[]{#_Toc47 .anchor}3.1.7.2 Edit Medical Stock Movement
Type![](media/image51.png){width="2.0857928696412946in"
height="1.856674321959755in"}

Select a row from "Medicals Stock Movement Type Browsing" and click
"Edit". The description field is freely editable. Click "OK" to save
changes, or "Cancel" to abort the operation. If "OK" is clicked but the
description field is empty, a "Please insert a valid description" window
is shown. Click "OK" on the error window to return to the "Editing exam
type" panel.

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)

-   medicaldsrstockmovtype.MMVT\_ID\_DESC (movement type description)

[]{#_Toc48 .anchor}3.1.7.3 Delete Medical Stock Movement Type

Removes a row from the "medicaldsrstockmovtype" database. Select a row
from "Medicals Stock Movement Type Browsing" and click "Delete". Click
"OK" on the confirmation window, or "Cancel" to abort the operation.

Data:

-   medicaldsrstockmovtype.MMVT\_ID\_A (primary key, movement type ID)

[]{#_Toc49 .anchor}3.1.7.4 Close Medical Stock Movement Type menu

Click "Close" on the "Medical Stock Movement Type Browsing" window to
return to main menu.

[]{#_Toc50 .anchor}3.1.8 Medical
Type![](media/image52.jpeg){width="4.360944881889764in"
height="1.957755905511811in"}

The "Medical Type Browsing" table defines the different categories for
medicals and other items used by the hospital. Default types are shown
below.

![](media/image53.png){width="2.7106944444444445in"
height="1.18748031496063in"}

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)

-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#_Toc51 .anchor}3.1.8.1 New Medical
Type![](media/image54.png){width="2.987876202974628in"
height="1.533396762904637in"}

Click "New" on the "Medical Type Browsing" window. Enter a one-character
code and a description (i.e. the name of the item). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)

-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#_Toc52 .anchor}3.1.8.2 Edit Medical
Type![](media/image55.png){width="2.987642169728784in"
height="1.5558016185476815in"}

Select a row from "Medical Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing Medical type"
panel.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)

-   medicaldsrtype.MMVT\_ID\_DESC (medical type description)

[]{#_Toc53 .anchor}3.1.8.3 Delete Medical Type

Removes a row from the "medicaldsrtype" database. Select a row from
"Medicals Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   medicaldsrtype.MMVT\_ID\_A (primary key, medical type ID)

[]{#_Toc54 .anchor}3.1.8.4 Close Medical Type Menu

Click "Close" on the "Medical Type Browsing" window to return to main
menu.

[]{#_Toc55 .anchor}3.1.9 Operation
Type![](media/image56.jpeg){width="4.806438101487314in"
height="2.069727690288714in"}

The "Operation Type Browsing" table defines the operation categories.
Default types are shown below:

![](media/image57.png){width="2.6071741032370954in"
height="1.3884831583552055in"}

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)

-   operationtype.OCL\_DESC (operation type description)

-   operationtype.OCL\_TYPE (operation status, can be "MAJOR" or
    "MINOR"; currently unused)

[]{#_Toc56 .anchor}3.1.9.1 New Operation
Type![](media/image58.png){width="2.672113954505687in"
height="1.7974048556430446in"}

Click "New" on the "Operation Type Browsing" window. Enter a character
code and a description (i.e. the name of the operation). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)

-   operationtype.OCL\_DESC (operation type description)

[]{#_Toc57 .anchor}3.1.9.2 Edit Operation
Type![](media/image59.png){width="2.392140201224847in"
height="1.6031911636045495in"}

Select a row from "Operation Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Editing Medical type"
panel.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)

-   operationtype.OCL\_DESC (operation type description)

[]{#_Toc58 .anchor}3.1.9.3 Delete Operation Type

Removes a row from the "operationtype" database. Select a row from
"Operation Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   operationtype.OCL\_ID\_A (primary key, operation type ID)

[]{#_Toc59 .anchor}3.1.9.4 Close Operation Type Menu

Click "Close" on the "Operation Type Browsing" window to return to the
main menu.

[]{#_Toc60 .anchor}3.1.10 Pregnant Treatment
Type![](media/image60.jpeg){width="4.737419072615923in"
height="2.077985564304462in"}

The "Pregnant Treatment Type Browsing" table defines the types of
treatments to pregnant mothers. Default types are shown below:

![](media/image61.png){width="2.459109798775153in"
height="1.4294247594050744in"}

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)

-   pregnanttreatmenttype.DESC(pregnant treatment type description)

[]{#_Toc61 .anchor}3.1.10.1 New Pregnant Treatment
Type![](media/image62.png){width="2.584448818897638in"
height="1.7465923009623796in"}

Click "New" on the "Operation Type Browsing" window. Enter a character
code and a description (i.e. the name of the treatment). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)

-   pregnanttreatmenttype.DESC(pregnant treatment type description)

[]{#_Toc62 .anchor}3.1.10.2 Edit Pregnant Treatment
Type![](media/image63.png){width="2.584650043744532in"
height="1.7854133858267716in"}

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

[]{#_Toc63 .anchor}3.1.10.3 Delete Pregnant Treatment Type

Removes a row from the "pregnanttreatmenttype" database. Select a row
from "Pregnant Treatment Type Browsing" and click "Delete". Click "OK"
on the confirmation window, or "Cancel" to abort the operation.

Data:

-   pregnanttreatmenttype.PTT\_ID\_A (primary key, pregnant treatment
    type ID)

[]{#_Toc64 .anchor}3.1.10.4 Close Pregnant Treatment menu

Click "Close" on the "Pregnant Treatment Type Browsing" window to return
to the main menu.

[]{#_Toc65 .anchor}3.1.11 Other
Prices![](media/image64.png){width="3.083480971128609in"
height="1.566742125984252in"}

Defines specific prices lists, which will be stored in a separate
"pricesothers" database.

[]{#_Toc66 .anchor}3.1.11.1 New List

Click "New" on the "Other Prices Browser" (top left). A "New Price"
window opens. Enter a code and a description (both mandatory). Click
"OK" to confirm. If data are correct, the list is added, else a "Please
insert a code /![](media/image65.png){width="3.083480971128609in"
height="1.395275590551181in"} description" window is shown. Click "OK"
to return to the former window.

Data:

pricesothers.OTH\_ID (primary key, list ID, auto-increment)

pricesothers.OTH\_CODE (list code)

pricesothers.OTH\_CODE (list description)

[]{#_Toc67 .anchor}3.1.11.2 Edit List

Select a list from the browser and click "Edit". An "Edit Price" window
opens (identical to the "New Price" in 3.1.11.1). Both code and
description are editable. Click "OK" to save changes or "Cancel" to
abort. If data are correct, the list will be updated.

Data: see chapter 3.1.11.2

[]{#_Toc68 .anchor}3.1.11.3 Delete List

Select a list from the browser and click "Delete". Then click "OK" on
the confirmation window to remove the list from the "pricesothers" DB,
or "Cancel" to abort.

Data:

pricesothers.OTH\_ID

[]{#_Toc69 .anchor}3.1.11.4 Close Other Prices menu

Click "Close" on the "Other prices browser" to return to OH's main menu.

[]{#_Toc70 .anchor}3.1.12 Age
Type![](media/image66.jpeg){width="4.7829866579177605in"
height="1.9750306211723534in"}

When a patient is register in OH's "patient" database, it's not always
possible to determine his/her age, since the birthdate is unknown. In
this case, the user can choose the age interval from a dropdown menu in
the "New Patient" option. The "Age type browsing" table below defines
the age ranges. Every row determines, respectively, the code of the
interval, the minimum age, the maximum age, and the description of the
range.![](media/image67.png){width="3.2520231846019247in"
height="1.472263779527559in"}

Data:

-   agetype.AT\_CODE (primary key, age type ID)

-   agetype.AT\_FROM (minimum age)

-   agetype.AT\_TO (maximum age)

-   agetype.AT\_DESC (description of the range)

[]{#_Toc71 .anchor}3.1.12.1 Edit Age Type

Select a row from "Age Type Browsing" and click "Edit". The description
field is freely editable. Click "OK" to save changes, or "Cancel" to
abort the operation.

Data:

-   agetype.AT\_CODE (primary key, age type ID)

-   agetype.AT\_DESC (description of the range)

[]{#_Toc72 .anchor}3.1.12.2 Close Age type menu

Click "Close" on the "Age Type Browsing" window to return to the main
menu.

[]{#_Toc73 .anchor}3.1.13 Vaccine
Type![](media/image68.jpeg){width="3.7019094488188977in"
height="1.5937970253718285in"}

The "Vaccine Type Browsing" table defines all vaccine types. Default
categories are:

-   C (Vaccines for children)

-   P (Vaccines for pregnant women)

-   N (Vaccines for adults, except pregnant
    women)![](media/image69.png){width="3.629958442694663in"
    height="1.3689840332458443in"}

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)

-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#_Toc74 .anchor}3.1.13.1 New Vaccine
Type![](media/image70.png){width="2.4889173228346455in"
height="1.7194936570428696in"}

Click "New" on the "Vaccine Type Browsing" window. Enter a one-character
code and a description (i.e. the name of the treatment). Click "OK" to
confirm or "Cancel" to abort the operation. Both fields are mandatory;
see 3.1.1.1 for error messages.

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)

-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#_Toc75 .anchor}3.1.13.2 Edit Vaccine
Type![](media/image71.png){width="2.5377307524059494in"
height="1.723928258967629in"}

Select a row from "Vaccine Type Browsing" and click "Edit". The
description field is freely editable. Click "OK" to save changes, or
"Cancel" to abort the operation. If "OK" is clicked but the description
field is empty, a "Please insert a valid description" window is shown.
Click "OK" on the error window to return to the "Edit vaccine type"
panel.

Data:

-   vaccinetype.VACT\_ID\_A (primary key, vaccine type ID)

-   vaccinetype.VACT\_DESC (vaccine type description)

[]{#_Toc76 .anchor}3.1.13.3 Delete Vaccine Type

Removes a row from the "vaccinetype" database. Select a row from
"Vaccine Type Browsing" and click "Delete". Click "OK" on the
confirmation window, or "Cancel" to abort the operation.

Data:

-   vaccinetype.VACT\_ID\_A (chiave primaria, identificativo del tipo di
    vaccino)

[]{#_Toc77 .anchor}3.1.13.4 Close Vaccine type menu

Click "Close" on the "Vaccine Type Browsing" window to return to the
main menu.

[]{#_Toc78 .anchor}3.2 Hospital

![](media/image72.jpeg){width="4.522208005249344in"
height="3.1999584426946632in"}

Hospital location data are automatically printed on reports generated by
some OH functions, such as "Pharmacy -\> Pharmaceuticals" or "Accounting
-\> Bills Manager".

When the "Hospital Informations" window opens, only the "Edit" and
"Close" buttons are enabled, and information is not editable. Click
"Edit" to update the text fields, then "Update" to
save![](media/image73.png){width="3.05953302712161in"
height="3.355287620297463in"} changes and "Close" to close the window
and return to the main menu.

Data:

hospital.HOS\_NAME (name)

hospital.HOS\_ADDR (address)

hospital.HOS\_CITY (city)

hospital.HOS\_TELE (phone number)

hospital.HOS\_FAX (fax number)

hospital.HOS\_EMAIL (e-mail)

hospital.HOS\_CURR\_COD (hospital's currency code)

[]{#_Toc79 .anchor}3.3
Ward![](media/image74.jpeg){width="4.934255249343832in"
height="2.9705424321959755in"}

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
    and/or women.![](media/image75.png){width="6.688889982502187in"
    height="1.0228018372703411in"}

Optional attributes include phone number, fax number, e-mail address.

Data:

ward.WRD\_ID (primary key, ward ID)

ward.WRD\_NAME (ward name)

ward.WRD\_TELE (phone number)

ward.WRD\_FAX (fax number)

ward.WRD\_EMAIL (e-mail)

ward.WRD\_NBEDS (number of beds)

ward.WRD\_NQUA\_NURS (number of nurses)

ward.WRD\_NDOC (number of doctors)

ward.WRD\_IS\_PHARMACY (1 if the ward has its own pharmacy, else 0)

ward.WRD\_IS\_MALE (1 if men are allowed, else 0)

ward.WRD\_IS\_FEMALE (1 if women are allowed, else 0)

[]{#_Toc80 .anchor}3.3.1 New
Ward![](media/image76.png){width="2.868293963254593in"
height="3.1049278215223097in"}

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

[]{#_Toc81 .anchor}3.3.2 Edit
Ward![](media/image77.png){width="2.868293963254593in"
height="3.1342760279965005in"}

Select a row form "Wards Browser" and click "Edit". An "Editing ward
record" window opens; all elements except the code are editable. Once
changes have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the ward will be updated in
the "ward" database, else an error window is shown (see 3.3.1).

Data:

see chapter 3.3

[]{#_Toc82 .anchor}3.3.3 Delete
Ward![](media/image78.png){width="4.030849737532808in"
height="1.9605172790901138in"}

Removes a ward from the "ward" database, if it has no patients
registered in the "Admission/Patient" menu. Select a row form "Wards
Browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

![](media/image79.png){width="4.030709755030621in"
height="1.3137325021872266in"}

If there's at least one patient admitted in the selected ward, there
will be no deletion and a "Selected ward has X patients" window is
shown. Pictured left is the example of the children ward, that has 123
patients registered.![](media/image80.png){width="4.0308169291338585in"
height="2.1833595800524934in"}

Here is a screenshot from the "Admission/Patient" window, where 7 of the
123 patients from the children ward are visible (codes from 474 to 482).
All patients from a ward must be discharged before removing it.

Data:

-   ward.WRD\_ID (primary key, ward ID)

-   admission.WRD\_ID\_A (foreign key referencing to "ward", to check if
    there are admitting patients in the selected ward)

[]{#_Toc83 .anchor}3.3.4 Close Ward menu

Click "Close" on the "Wards Browser" window to return to the main menu.

[]{#_Toc84 .anchor}3.4
Disease![](media/image81.jpeg){width="4.778264435695538in"
height="2.5836089238845146in"}

The "Diseases browser" table contains all diseases registered in the
"disease" database. Every row shows the disease code, the type (3.1.5)
and the disease name.

![](media/image82.png){width="4.2002909011373575in"
height="2.5968383639545056in"}

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)

-   disease.DIS\_DCL\_ID\_A (foreign key referencing to "diseasetype")

-   disease.DIS\_DESC (disease name)

[]{#_Toc85 .anchor}3.4.1 Select Disease
Type![](media/image83.png){width="3.5269127296587928in"
height="2.525667104111986in"}

To help search a disease, click the dropdown menu on the bottom of the
"Diseases Browser" window, and select a type, or "ALL" to visualize all
records.

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)

-   disease.DIS\_DCL\_ID\_A (foreign key referencing to "diseasetype")

[]{#_Toc86 .anchor}3.4.2 New Disease

Adds a new disease to the "disease" database. Click "New" on the
"Diseases browser" window. A "New disease" window opens. Select the type
from the dropdown menu, enter a code and the description (i.e. the name
of the disease, used in "OPD" and "Diagnosis IN" / "Diagnosis OUT" lists
of the "Admission/Patient" menu). Then tick at least one checkbox to
assign the disease to "OPD"
(OutPatient![](media/image84.png){width="3.2188626421697286in"
height="1.5007338145231846in"} Dept.), "IPD IN" ("Diagnosis IN") and
"IPD OUT" ("Diagnosis OUT"). Click "OK" to confirm or "Cancel" to abort
the operation. If all data required are correct, the disease will be
added to the "disease" database, else an error window is shown:

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

[]{#_Toc87 .anchor}3.4.3 Edit
Disease![](media/image85.png){width="3.3444455380577427in"
height="1.55251968503937in"}

Select a row from "Diseases Browser" and click "Edit". An "Edit disease"
window opens; all elements except the code are editable. Once changes
have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the disease will be updated
in its database, else an error window is shown (see 3.4.2).

Data:

see chapter 3.4.2

[]{#_Toc88 .anchor}3.4.4 Delete Disease

Removes a disease from its database. Select a row from "Diseases
browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the operation.

Data:

-   disease.DIS\_ID\_A (primary key, disease ID)

[]{#_Toc89 .anchor}3.4.5 Close Disease menu

Click "Close" on the "Diseases Browser" window to return to the main
menu.

[]{#_Toc90 .anchor}3.5
Exams![](media/image86.jpeg){width="4.01799978127734in"
height="4.004253062117235in"}

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
    result)![](media/image87.png){width="6.688889982502187in"
    height="2.2048567366579177in"}

[]{#_Toc91 .anchor}3.5.1 Select Exam type

To help search an exam, click the dropdown menu on the bottom of the
"Exams Browsing" window, and select a type, or "ALL" to visualize all
records.

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)

-   exam.EXA\_EXC\_ID\_A (foreign key referencing "examtype", exam type)

[]{#_Toc92 .anchor}3.5.2 New
Exam![](media/image88.png){width="2.8531780402449693in"
height="2.0080030621172353in"}

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

[]{#_Toc93 .anchor}3.5.3 Edit
Exam![](media/image89.png){width="2.8531780402449693in"
height="2.0404210411198602in"}

Select a row from "Exams Browsing" and click "Edit". An "Edit exam"
window opens; only the description and default result are editable. Once
changes have been made, click "OK" to confirm or "Cancel" to abort the
operation. If all data required are correct, the exam will be updated in
its database, else an error window is shown (see 3.5.2).

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)

-   exam.EXA\_DESC (exam name)

-   exam.EXA\_DEFAULT (default result)

[]{#_Toc94 .anchor}3.5.4 Delete Exam

Removes a exam from its database. Select a row from "Exams browsing" and
click "Delete". Click "OK" on the confirmation window, or "Cancel" to
abort the operation.

Data:

-   exam.EXA\_ID\_A (primary key, exam ID)

[]{#_Toc95 .anchor}3.5.5 Exam
result![](media/image90.png){width="2.6108978565179353in"
height="1.0736406386701662in"}

Every exam has a set of possible results (for example: positive /
negative). The outcome of an exam is reported in the "Laboratory
browsing" table, pictured left (see also chapter 6).

![](media/image91.png){width="3.8267749343832023in"
height="0.7237598425196851in"}

OH allows to manage the set of results for every recorded exam. Select a
row from the "Exam Browsing" window and click "Result". A new window
shows a table with all outcomes, each with a code and a description.
Here is an example of the "SUGAR" glucose exam (highlighted in the table
at chapter 3.5).![](media/image92.png){width="2.6108978565179353in"
height="1.629540682414698in"}

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

[]{#_Toc96 .anchor}3.5.6 Close Exams menu

Click "Close" on the "Exam Browsing" window to return to the main menu.

[]{#_Toc97 .anchor}3.6
Operation![](media/image93.jpeg){width="4.862378608923884in"
height="3.198293963254593in"}

The "Operations browser" table defines all operations recorded in the
"operation" database. Every row shows the operation code, the operation
type (3.1.9) and its description.

![](media/image94.png){width="3.7971205161854766in"
height="2.7200415573053367in"}

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)

-   operationtype.OCL\_ID\_A (foreign key referencing "operation",
    operation type)

-   operation.OPE\_DESC (operation name)

[]{#_Toc98 .anchor}3.6.1 Select operation type

To help search an operation, click the dropdown menu on the bottom of
the "Operations browser" window, and select a type, or "ALL" to
visualize all records.

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)

-   operationtype.OCL\_ID\_A (foreign key referencing "operation",
    operation type)

[]{#_Toc99 .anchor}3.6.2 New
Operation![](media/image95.png){width="4.089268372703412in"
height="1.4906692913385826in"}

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

[]{#_Toc100 .anchor}3.6.3 Edit
Operation![](media/image96.png){width="4.089268372703412in"
height="1.494284776902887in"}

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

[]{#_Toc101 .anchor}3.6.4 Delete Operation

Removes an operation from its database. Select a row from "Operations
browser" and click "Delete". Click "OK" on the confirmation window, or
"Cancel" to abort the deletion.

Data:

-   operation.OPE\_ID\_A (primary key, operation ID)

[]{#_Toc102 .anchor}3.6.5 Close Operation menu

Click Close" on the "Operations browsing" window to return to the main
menu.

[]{#_Toc103 .anchor}3.7
Vaccine![](media/image97.jpeg){width="4.598715004374453in"
height="3.023558617672791in"}

The "Vaccine browser" table defines all vaccines recorded in the
"vaccine" database. Every row shows the code ID, the vaccine type
(3.1.13) and its description.

![](media/image98.png){width="4.484686132983377in"
height="1.7183661417322835in"}

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)

-   vaccine.VAC\_VACT\_ID\_A (foreign key referencing "vaccinetype"
    database)

-   vaccine.VAC\_DESC (vaccine description)

[]{#_Toc104 .anchor}3.7.1 Select Vaccine Type

To help search a vaccine, click the dropdown menu on the bottom of the
"Operations browser" window, and select a type, or "ALL" to visualize
all records.

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)

-   vaccine.VAC\_VACT\_ID\_A (foreign key referencing "vaccinetype"
    database)

[]{#_Toc105 .anchor}3.7.2 New
Vaccine![](media/image99.png){width="2.8404833770778652in"
height="1.9973425196850394in"}

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

[]{#_Toc106 .anchor}3.7.3 Edit
Vaccine![](media/image100.png){width="2.8404833770778652in"
height="2.0219017935258092in"}

Select a row from "Vaccine Browser" and click "Edit". An "Editing
vaccine record" window opens; only the description field is editable.
Once changes have been made, click "OK" to confirm or "Cancel" to return
to close the window without saving changes. If data required are
correct, the operation will be updated in its database, else an error
window is shown (see 3.7.2).

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)

-   vaccine.VAC\_DESC (vaccine description)

[]{#_Toc107 .anchor}3.7.4 Delete Vaccine

Removes a vaccine from its database. Select a row from "Vaccine browser"
and click "Delete". Click "OK" on the confirmation window, or "Cancel"
to abort the deletion.

Data:

-   vaccine.VAC\_ID\_A (primary key, vaccine ID)

[]{#_Toc108 .anchor}3.7.5 Close Vaccine menu

Click "Close" on the "Vaccine browser" window to return to the main
menu.

[]{#_Toc109 .anchor}3.8 Prices
Lists![](media/image101.jpeg){width="4.734343832020997in"
height="4.021169072615923in"}

The "Price Lists" menu allows the administrator to manage pricing for
medicals, exams and operations, creating customized price lists for
different users. "The Prices Browser" window (below) shows all elements
for a single list, sorted in "Exams", "Operations", "Medicals" and
"Others" folders. Click on tre triangle next to each folder to expand
its content.

![](media/image102.png){width="3.066891951006124in"
height="0.9969772528433946in"}

Data (for every item of the list):

-   prices.PRC\_ID (primary key, item - price list
    pair)![](media/image103.png){width="3.066689632545932in"
    height="2.134620516185477in"}

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

[]{#_Toc110 .anchor}3.8.1 Choose
List![](media/image104.png){width="3.5002274715660544in"
height="0.9895297462817148in"}

The "Prices Browser" window has a dropdown menu on the top, to
choose![](media/image105.png){width="2.4881922572178476in"
height="1.2225229658792651in"} between the lists created with the
"Manage List" option (3.8.2). Every time the user switches to a
different list, a confirmation window (right) is shown. Click "OK" to
confirm, or Cancel to return to the current list.

Data:

-   pricelists.LST\_ID

-   pricelists.LST\_CODE

[]{#_Toc111 .anchor}3.8.2 Manage
Lists![](media/image106.png){width="2.3587390638670165in"
height="1.3025546806649169in"}

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

[]{#_Toc112 .anchor}3.8.2.1 New
List![](media/image107.png){width="2.1059273840769905in"
height="2.0028947944007in"}

Click "New" on the "List Browser" window. Enter the code, the name, the
description and the currency used in the list.

Click "OK" to confirm or "Cancel" to abort the operation. If all data
have been added, the list will be added to the "pricelists" database,
else a "Please insert a code/name/description/currency" is shown,
depending of the field(s) left empty. In this case, click "OK" to return
to the "New List" window.

Data: see chapter 3.8.2

[]{#_Toc113 .anchor}3.8.2.2 Copy
List![](media/image108.png){width="1.8149759405074366in"
height="0.756330927384077in"}

This option creates a copy of the list selected, with prices multiplied
by a given factor. Select the list from the "List Browser" table and
click "Copy". A sequence of 4 panels
opens.![](media/image109.png){width="1.8149562554680665in"
height="0.9728904199475066in"} Enter the name of the new list in the
first window. Click "OK" and enter the multiplying factor in the second
panel; Click "OK" and enter the rounding factor. Multiplied prices will
be rounding to the next higher multiple of the value inserted. After
clicking "OK", a "List Copied" message window is shown. Click "OK" to
close it, and the list will be added to the "priceslists"
database.![](media/image110.png){width="1.815223097112861in"
height="0.86918416447944in"}

Data:

see chapter 3.8.2

![](media/image111.png){width="1.8151049868766405in"
height="0.7295581802274715in"}

[]{#_Toc114 .anchor}3.8.2.3 Edit
List![](media/image112.png){width="2.21745406824147in"
height="2.051581364829396in"}

Select a row from "List browser" and click "Edit". The "Edit List"
window opens. All data are freely editable. Click "OK to confirm or
"Cancel" to abort the operation. If all data have been added, the list
will be updated, else an error window is shown (3.8.2.1).

Data :

see chapter 3.8.2

[]{#_Toc115 .anchor}3.8.2.4 Delete
List![](media/image113.png){width="3.5547911198600173in"
height="1.2541961942257218in"}

Removes a price list from its database. Select a row from "List browser"
and click "Delete". Click "OK" on the confirmation window (left), or
"Cancel" to abort the deletion.

Data:

-   pricelists.LST\_ID

[]{#_Toc116 .anchor}3.8.2.5 Close List Browser

Click "Close" on the "List Browser" window to return to OH's main menu.

[]{#_Toc117 .anchor}3.8.3 Save
List![](media/image114.png){width="2.620715223097113in"
height="1.1736329833770778in"}

After editing the items within a price list, changes must be saved
before closing the "Prices browser" window. Click the "SAVE" button and
then "OK" on the confirmation window (left). To discard changes, click
"Cancel".

[]{#_Toc118 .anchor}3.8.4 Print List

Generates a report containing the rows of the selected list. Click
"Print" on the "Prices Browser" window. The Jasper Viewer opens; it has
some buttons (below) to save in .PDF, print, update, scroll the pages,
fit the document to the computer screen and
zoom.![](media/image115.png){width="5.888888888888889in"
height="0.3888888888888889in"}

[]{#_Toc119 .anchor}3.8.5 Close Price Lists menu

Click "Close" on the "Prices Browser" menu to return to the main menu.

[]{#_Toc120 .anchor}3.9
Supplier![](media/image116.jpeg){width="4.420863954505687in"
height="3.5296806649168855in"}

The "Supplier Browser" menu tracks the list of the hospital's suppliers.
Every row shows the ID, the name, and some information about the
supplier (address, tax number, phone and fax numbers, e-mail address,
optional notes). The "Deleted" checkbox is ticked after a "Delete
Supplier" operation (see 3.9.3).

![](media/image117.png){width="6.688940288713911in"
height="1.0183005249343833in"}

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

![](media/image118.png){width="2.0897134733158356in"
height="2.3159372265966756in"}

[]{#_Toc121 .anchor}3.9.1 New Supplier

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

[]{#_Toc122 .anchor}3.9.2 Edit
Supplier![](media/image119.png){width="2.0897801837270342in"
height="2.3291229221347334in"}

Select a row from "Supplier browser" and click "Edit". The "Edit List"
window opens. All data except the ID, are freely editable. If the
"Deleted" checkbox has been previously ticked, the editing options
allows to undelete the supplier (see 3.9.3). If the name has been
inserted, the supplier will be updated, else a "Please insert a name"
window is shown. In this case, click "OK" to return to the "Edit
supplier" window.

Data:

see chapter 3.9

[]{#_Toc123 .anchor}3.9.3 Delete Supplier

Select a row from "Supplier browser" and click "Delete". This operation
is different from other deletion operations. The record is not removed
from the database, it will be unactive for the OH menus needing the
supplier DB. Click "Yes" on the confirmation window to virtually remove
the supplier, else "No" to abort the operation. If the "deletion" is
confirmed, the "Deleted" checkbox on the "Supplier browser" table is
checked. To undelete a supplier, select it and, click "Edit" and
deselect the checkbox
(3.9.2).![](media/image120.png){width="6.688889982502187in"
height="1.0053674540682416in"}

Data:

-   supplier.SUP\_ID

-   supplier.SUP\_DELETED

[]{#_Toc124 .anchor}3.9.4 Close Supplier menu

Click "Close" on the "Supplier Browser" window to return to the main
menu.

[]{#_Toc125 .anchor}3.10 SMS
Manager![](media/image121.jpeg){width="3.240926290463692in"
height="3.3229319772528436in"}

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
    time![](media/image122.png){width="3.984562554680665in"
    height="1.206169072615923in"} of the visit)

-   sms.SMS\_NUMBER (patient's phone number)

-   sms.SMS\_TEXT (SMS text)

-   sms.SMS\_USER (OH user which sent the message)

-   sms.SMS\_MOD (OH menu from which the SMS was sent)

-   sms.SMS\_MOD\_ID (patient ID - retained from patient.PAT\_ID - who
    receives the message)

[]{#_Toc126 .anchor}3.10.1 Select date
interval![](media/image123.png){width="3.5777766841644794in"
height="1.3521369203849518in"}

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

[]{#_Toc127 .anchor}3.10.2 New
SMS![](media/image124.png){width="2.466626202974628in"
height="1.665145450568679in"}

To send an SMS, click "New" on the "SMS Manager" window. Enter the
patient's scheduled date either by typing it in a DD/MM/YY format or by
clicking on the calendar icon (3.10.1).

![](media/image125.png){width="2.46662510936133in"
height="1.3315748031496062in"}

Then enter the scheduled time either by typing it in HH:MM format or by
clicking on the clock icon. Click on the hour and the minute on the new
window (right), then click "OK" to confirm and return to the "New SMS"
window.![](media/image126.png){width="3.952620297462817in"
height="2.49371719160105in"}

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

[]{#_Toc128 .anchor}3.10.3 Delete SMS

Select a row from "SMS manager" and click "Delete". Click "Yes" on the
confirmation window to remove the sms form the "sms" database, else "No"
to abort the operation.

Data:

-   sms.SMS\_ID

[]{#_Toc129 .anchor}3.10.4 Close SMS Manager menu

Click "Close" on the "SMS manager" window to return to the main menu.

[]{#_Toc130 .anchor}4. OPD (OutPatient
Department)![](media/image127.jpeg){width="3.6337893700787403in"
height="4.212944006999125in"}

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
    4.2)![](media/image128.png){width="5.079743000874891in"
    height="2.031056430446194in"}

[]{#_Toc131 .anchor}4.1 Search Patient

The left-side panel provides some tools that can be combined to help
search records:

Disease search: On the top of the window, there are two related dropdown
menus. Choose the disease type from the first one, or "All Type" for all
elements defined in the "General Data -\> Types -\>Disease Type". Then
select a disease from the second menu, or "All Disease". If a specific
type has been chosen, the menu shows only the elements belonging to that
type.

Date search: Type two dates in the "Date From" and "Date To" fields, in
a DD, MM, YYYY format, to seek records added in a determined date
interval. If "Date From" is greater than "Date To", a "Date from must be
lower than date to" window pops up. Click "OK" to return to the OPD
browser.

Age search: Type two values in the "Age From" and "Age To" fields to
seek records of patients in a determined age range. If "Age From" is
greater than "Age To", an "Age from must be lower than Age to" window
pops up. Click "OK" to return to the OPD browser. Default values are
both 0, meaning no patient age restriction.

Sex: Select between "All", "Male" and "Female" radio buttons, according
to patient sex.

OH Patient: Select between "All", "New attendance" and "Female" radio
buttons, according to the status. A new attending patient is making the
first visit for a certain diagnosis, while a re-attending patient
returns - once or multiple times - for the
same![](media/image129.png){width="4.922173009623797in"
height="2.0062543744531935in"} diagnosis, after being a "new" the first
time.

Once the filters have been selected, click "Search" to visualize the
results. The number of matching records is shown under the button.

Data:

see chapter 4.

[]{#_Toc132 .anchor}4.2 New OPD
registration![](media/image130.png){width="4.622826990376203in"
height="3.293765310586177in"}

Click "New" on the OPD browser. A "New OPD registration" window opens.
Select the patient status clicking on the buttons on the top of the
window (see chapter 4.1). In case of re-attendance, the last OPD's visit
is visible after selecting the patient.

![](media/image131.png){width="3.7846347331583554in"
height="0.6766141732283465in"}

Enter the patient's name clicking either on the magnifier icon or the
pencil icon. The former opens a dropdown menu with the list of
registered patients (left); choose one from this list. The latter opens
a "New Patient" window, if it's not recorded in OH (see chapter 8.1). To
help search an existing name, type a sub-string in the "Search" field,
then click the magnifier icon to choose the patient whose name contains
that sub-string.![](media/image132.png){width="2.7426126421697288in"
height="3.3676181102362204in"}

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

[]{#_Toc133 .anchor}4.3 Edit OPD
Registration![](media/image133.png){width="3.7997123797025374in"
height="2.7066765091863516in"}

Select a row from the OPD browser and click "Edit". An "Edit OPD
registration" window opens. All data except the OPD ID and patient data,
are editable. Once changes have been made, click "OK" to update or
"Cancel" to abort the operation.

Data:

same of chapter 4.2, except opd.OPD\_PAT\_ID, opd.USR\_ID\_A

[]{#_Toc134 .anchor}4.4 Delete OPD registration

Select a row from the OPD browser and click "Delete". Click "Yes" on the
confirmation window to remove the visit from its database, else "No" to
abort the operation.

Data:

opd.OPD\_PAT\_ID

[]{#_Toc135 .anchor}4.5 Close OPD menu

Click "Close" on the OPD browser to return to the main menu.

[]{#_Toc136 .anchor}5.
Pharmacy![](media/image134.png){width="4.634858923884514in"
height="5.195353237095363in"}

It is the hospital's pharmacy, where all medicals and other items are
managed. The "Pharmacy" menu has 3 sub-menus:

"Pharmaceuticals": shows the list of the hospital items.

"Pharmaceutical Stock": records all item movements between hospital and
suppliers, and between hospital and wards.

"Pharmaceutical Stock Ward": records all item movements between a
patient and the ward where he/she has been admitted in. This option is
active by default ("INTERNALPHARMACIES=yes" in the
rsc/generalData.properties).

[]{#_Toc137 .anchor}5.1
Pharmaceuticals![](media/image135.jpeg){width="6.0414479440069995in"
height="5.397685914260717in"}

Click "Pharmaceuticals" in the "Pharmacy" menu to open the
"Pharmaceutical Browsing" window. The table below shows all hospital
items recorded in the "medicaldsr" database. The columns in the table
include:![](media/image136.png){width="6.688889982502187in"
height="3.187895888013998in"}

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

[]{#_Toc138 .anchor}5.1.1 Select
Type![](media/image137.png){width="6.688889982502187in"
height="3.177400481189851in"}

Filters the "Pharmaceutical browsing" table by item type. Choose the
type from the dropdown menu on the bottom of the window, or "ALL" to
visualize the full list.

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A

-   medicaldsr.MDSR\_ID

[]{#_Toc139 .anchor}5.1.2 New
Pharmaceutical![](media/image138.png){width="3.5074431321084862in"
height="1.5891327646544182in"}

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
above.![](media/image139.png){width="6.688907480314961in"
height="0.8545177165354331in"}

Data:

-   medicaldsr.MDSR\_MDSRT\_ID\_A

-   medicaldsr.MDSR\_ID

-   medicaldsr.MDSR\_DESC

-   medicaldsr.MDSR\_CODE

-   medicaldsr.MDSR\_PCS\_X\_PCK

-   medicaldsr.MDSR\_MIN\_STOCK\_QTI

[]{#_Toc140 .anchor}5.1.3 Edit
Pharmaceutical![](media/image140.png){width="3.5075535870516186in"
height="1.5728838582677165in"}

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

[]{#_Toc141 .anchor}5.1.4 Delete
Pharmaceutical![](media/image141.png){width="3.530188101487314in"
height="1.4934514435695538in"}

Removes an item form the "medicaldsr" database, if it has no recorded
stock movements. Select a row from "Pharmaceutical Browsing" and click
"Delete". Click "Yes" on the confirmation window (left) to remove item
from its database, else "No" to abort the
operation.![](media/image142.png){width="3.5304779090113736in"
height="0.9303685476815398in"}

If there's at least one stock movement in the "medicaldsrstockmov"
database, containing the selected item, the deletion will be aborted and
an error window (left) opens.

Data:

-   medicaldsr.MDSR\_ID

-   medicaldsrstockmov.MMV\_MDSR\_ID (foreign key referenicing to the
    "medicaldsr" database)

[]{#_Toc142 .anchor}5.1.5
Export![](media/image143.png){width="2.45253280839895in"
height="1.8785826771653544in"}

Saves an .xls copy of the current "medicaldsr" database on the computer.
Click "Export" on the "Pharmaceutical browsing" window. A "Save" window
opens; enter the name of the file in the "Save As" field, and select the
folder where the file will be saved. To save the file in a non-existing
folder, click "New![](media/image144.png){width="2.4526826334208223in"
height="1.1798140857392825in"} Folder", enter the name in the new
window, and click "Create". The new folder appears in the "Save" window,
in the current visible path. Complete the operation clicking "Save" (or
"Cancel" to abort).

Data: see chapter 5.1

[]{#_Toc143 .anchor}5.1.6
STOCK![](media/image145.png){width="2.5863867016622923in"
height="3.8645483377077867in"}

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

[]{#_Toc144 .anchor}5.1.7
Order![](media/image146.png){width="2.6062073490813646in"
height="3.775463692038495in"}

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

[]{#_Toc145 .anchor}5.1.8
Expiring![](media/image147.png){width="1.996213910761155in"
height="1.1751902887139107in"}

This option generates a Jasper document (see 3.8.4 for .PDF export /
print / zoom / navigation operations), containing medical stocks expired
or close to due date. Click "Expiring" on the "Pharmaceutical Browsing"
window. Select the period on the new window (left). There are three
options: "Today",![](media/image148.png){width="2.008853893263342in"
height="0.9118689851268591in"} "This month" and "Other month" (opens a
window, pictured right, to choose the month and the year; click "OK" to
confirm). The document will report all medicals to order, depending on
the chosen period, each with the code, the description and the necessary
amount to reach the critical level.

[]{#_Toc146 .anchor}5.1.9 Close Pharmaceuticals menu

Click "Close" on the "Pharmaceutical Browsing" window to return to the
main menu.

[]{#_Toc147 .anchor}5.2 Pharmaceutical
Stock![](media/image149.jpeg){width="6.309174321959755in"
height="4.533752187226597in"}

This sub-menu of "Pharmacy" allows the administrator to track the
movements generated by hospital items, managing purchases form suppliers
("Charge") e and item assignation to the wards ("Discharge"). Pictured
below is the table after two charges (5.2.2) and a discharge
(5.2.3).![](media/image150.png){width="6.688889982502187in"
height="3.6888517060367456in"}

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

[]{#_Toc148 .anchor}5.2.1 Filter

The left side of the "Stock Movement Browser" window provides a
selection panel to help search stock movements. It has 4 main sections:

Pharmaceutical: Select an item from the "Description" dropdown, or "ALL"
to show all item's records.

Movement: Select a movement type (3.1.7) from the "Type" dropdown or
"ALL" to show all movement's records. Add dates, in DD / MM / YYYY
format, in the "From" and "To" fields format to filter by movement date.

Lot preparation date: enter values, in DD / MM / YYYY format, in the
"From" and "To" fields format to filter by lot preparation date.

Lot due date: enter values, in DD / MM / YYYY format, in the "From" and
"To" fields format to filter by lot due date.

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

[]{#_Toc149 .anchor}5.2.2
Charge![](media/image151.png){width="3.3444455380577427in"
height="1.3972747156605425in"}

Click "Charge" on the "Stock Movement Browser" window. A "Stock
Movement" window opens; charge information is shown on the top. Type the
reference number on the "Reference No." field, then choose the charge
type (3.1.7) and the supplier (3.9). Enter part of the name or of the
code on the "Type a code or a description and press ENTER". After
clicking the "Enter" button on the computer, select the medical among
the ones matching the string inserted and click
"Yes".![](media/image152.png){width="2.234051837270341in"
height="0.8936209536307962in"}

Once the medical has been selected, insert the quantity in the "Input"
window and click "OK" to confirm.

A "Lot informations" window opens. Assign the lot
number![](media/image153.png){width="3.3445308398950133in"
height="1.0753149606299213in"} (it will be assigned automatically if
"AUTOMATICLOT=yes" in the rsc/generalData.properties file) and enter the
lot preparation and due dates, in a DD/MM/YYYY format (see 3.10.1 for
the calendar icon). After clicking "OK", the "Stock Movement" window
(below) shows![](media/image154.png){width="4.469733158355206in"
height="1.678248031496063in"} the new charge.

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

[]{#_Toc150 .anchor}5.2.3
Discharge![](media/image155.png){width="3.242781058617673in"
height="1.1445122484689414in"}

Assigns an item ordered after a "Charge" operation. Click "Discharge" on
the "Stock Movement Browser" window. The "Stock Movement" panel is
similar to the one seen in chapter 5.2.2. The differences are in both
dropdown menus: the first includes all discharge types ("-" sign), the
second contains the hospital wards, to which the medical is discharged.
See 5.2.2 for reference number and medical
selection.![](media/image156.png){width="2.6875699912510935in"
height="1.14788823272091in"}

Once the medical has been selected, insert the quantity in the "Input"
window and click "OK" to confirm. Quantity must not exceed the "Lying in
stock" shown.

![](media/image157.png){width="3.032750437445319in"
height="1.4679538495188102in"}

After confirming the quantity, the "Lot informations" window opens.
Select the lot among those recorded in the database (the previously
created 012 in this example), then click "OK". Now the "Stock Movement"
window (below) shows the new discharge. Now the "Stock Movement" window
shows the new discharge. Click "Save" to save the
discharge,![](media/image158.png){width="4.9429013560804895in"
height="1.9464599737532808in"} else "Cancel" to discard.

If the data required have been inserted, the charge will be added to the
stock movement DB, else an error window is shown:

![](media/image159.png){width="2.234051837270341in"
height="1.1839774715660543in"}

-   "The inserted reference number already exists"

-   "Please select a ward"

-   "The quantity is not available" (right)

Click "OK" to return to the "Stock Movement" window. Picture below is
the movements browser after the charge and the discharge.

Data: see chapter
5.2.2![](media/image160.png){width="6.68900699912511in"
height="1.0104002624671915in"}

[]{#_Toc151 .anchor}5.2.4 Export

Saves an .xls copy of the current "medicaldsrstockmov" database on the
computer. Click "Export on excel" on the "Stock Movement Browser"
window. The function is identical to the pharmacy export seen in chapter
5.1.5.

[]{#_Toc152 .anchor}5.2.5 Close Pharmaceutical Stock menu

Click "Close" on the "Stock Movement Browser" window to return to the
main menu.

[]{#_Toc153 .anchor}5.3 Pharmaceutical Stock
Ward![](media/image161.jpeg){width="6.173018372703412in"
height="4.232291119860018in"}

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

[]{#_Toc154 .anchor}5.3.1 Ward Pharmacy

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
between:![](media/image162.png){width="4.560904418197725in"
height="2.5915529308836396in"}

![](media/image163.png){width="3.3555227471566056in"
height="0.6484973753280839in"}"Drugs": the table shown when opening the
P.S. Ward menu, records all available items in the selected ward.

"Incomings": shows all discharges from the main pharmacy (5.2.2).

"Outcomes": shows all movements from the main pharmacy to the ward
pharmacies. The buttons on the bottom of the window are referred to this
visualization.

Data:

see chapter 5.3

[]{#_Toc155 .anchor}5.3.2 New
Outcome![](media/image164.png){width="3.605744750656168in"
height="3.5115179352580927in"}

Click "New" on the "Ward Pharmacy" window to add a new movement. A
"New/Edit" window (left) opens. Select the destination clicking on the
"Patient" or the "Internal use" radio button. If the former is selected,
click "Pick Patient" to open the "Patient selection" window (or create a
new one, if not already registered in the "patient" DB, clicking on the
pencil icon; see chapter 8 "Admission/Patient").

Click on the magnifier icon to show the patient list (if a string has
been written in the "Search Patient" field, only rows containing that
string are visibile) Once selected the
row,![](media/image165.png){width="2.6982010061242345in"
height="1.0845067804024497in"} click "Select". If no weight data are
available, a "The selected patient has no weight defined" warning is
shown (left; see chapter 8.6 to add weight and other information). Click
"OK" to return to the "New/Edit" window. The "Pick Patient" buttons
becomes "Change Patient", and the nearby icon to delete the inserted
name, is enabled.![](media/image166.png){width="2.1933836395450568in"
height="1.5182261592300963in"}![](media/image167.png){width="2.381952099737533in"
height="1.1215890201224847in"}

Select the medical(s) to assign. Click "+ Medical" on the "New/Edit"
window. Pick an item from the dropdown menu (left) and click "OK".

Then enter the quantity (right) and click "OK". Quantity must not exceed
the available stock shown in the "Quantity"
window.![](media/image168.png){width="3.5540299650043745in"
height="3.4917880577427822in"}

Repeat the operation to add more medicals to the movement. To remove an
item, select it and click "X Remove Item". Pictured left is the
"New/Edit" window after inserting 3 units of Albendazole. Click "OK" to
add the record to the "Outcomes" table.

In case of items to assign to the ward (internal use), the record will
be shown in bold blue in the "Outcomes" browser. Pictured below is the
table after a record for a given patient of the children's ward, and a
record for internal use in that ward.

![](media/image169.png){width="5.0168700787401574in"
height="2.8309930008748907in"}

Data: see chapter 5.3

[]{#_Toc156 .anchor}5.3.3
Report![](media/image170.png){width="4.017420166229221in"
height="2.8645844269466316in"}

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

[]{#_Toc157
.anchor}5.3.4![](media/image171.png){width="3.2247965879265093in"
height="1.4669422572178479in"} Excel

Saves an .csv copy of the data shown in chapter 5.3.3. Click "Export" on
the "Ward Pharmacy" window. The function is identical to the pharmacy
export seen in chapter 5.1.5.

[]{#_Toc158 .anchor}5.3.5
Rectify![](media/image172.png){width="4.355122484689414in"
height="2.5345844269466316in"}

Click "Rectify" in "Ward Pharmacy". The "Rectify" window opens. It
allows the user to update the stock in the ward pharmacy, if the item is
damaged or stolen. Select an item form the dropdown menu and enter the
new actual quantity. Add the reason for the rectifying operation, if
necessary. Click "OK" to update or "Cancel" to abort.

[]{#_Toc159 .anchor}5.3.6 Close Pharmaceutical Stock Ward menu

Click "Close" on the "Ward Pharmacy" window, to return to the main menu.

[]{#_Toc160 .anchor}6.
Laboratory![](media/image173.jpeg){width="6.688889982502187in"
height="3.6038670166229223in"}

The "Laboratory browsing" window records all laboratory exams. It
provides a selection panel on the left side, and the lab table, where
every row shows the exam date, the patient examined, the exam type and
the exam result.![](media/image174.png){width="6.688889982502187in"
height="3.5700634295713036in"}

Data:

-   laboratory.LAB\_ID (primary key, exam ID, not shown in the table)

-   laboratory.LAB\_DATE (exam date)

-   laboratory.LAB\_PAT\_ID (foreign key referencing to the "patient"
    database)

-   laboratory.LAB\_EXA\_ID\_A (foreign key referencing to the "exam"
    DB, exam name)

-   laboratory.LAB\_RES (exam result)

[]{#_Toc161 .anchor}6.1 Search
Exam![](media/image175.png){width="4.464364610673666in"
height="2.511367016622922in"}

To help search exams, the selection panel allows to choose an exam type
from the dropdown menu and/or a date range, entering the dates, in
DD/MM/YYYY format, in the "Date From" and "Date To" fields. Then click
"Search" to visualize matching records.

Data:

see chapter 6

[]{#_Toc162 .anchor}6.2 New
Exam![](media/image176.png){width="3.580391513560805in"
height="1.93373687664042in"}

Click "New" while on "Laboratory Browsing". A "New Patient Exams" window
is shown. If necessary, change date and time typing in DD/MM/YYYY
HH:MM:SS format (default is the moment the window opens) or selecting
the date by clicking the calendar icon (3.10.1). Pick the patient as
seen in chapter 5.3.2. Check the
radio![](media/image177.png){width="2.013781714785652in"
height="1.1060553368328958in"} button to record the patient status
("OPD" if admitted, or "IP" if not admitted yet).

Add one or more exams clicking on "+ Exam". Select the element examined
(left) from the "Material" dropdown menu and click "OK".

![](media/image178.png){width="4.027563429571304in"
height="1.782594050743657in"}

Then select the exam (right), among those registered in the "exam" DB
and click "OK".

Finally, insert the exam result. Select the outcome from
the![](media/image179.png){width="1.989468503937008in"
height="1.5014873140857392in"} dropdown menu (3.5.5) and click "OK" to
return to the "New Patient Exams" window. Repeat these operations to add
more exams. To remove an exam, select it and click "X Remove". Add
optional notes in the "Notes" field on the bottom on the window. Once
data have been inserted, click "OK" to save the exam in the
database.![](media/image180.png){width="4.675108267716536in"
height="1.3357458442694663in"}

Pictured left is the "Lab browsing" table after adding the exam whose
steps have been shown in this page.

![](media/image181.png){width="3.3444444444444446in"
height="1.7729593175853018in"}

If something's missing in the "New Exam" operation, an error window
opens, showing one of the following messages:

-   "Please select a patient"

-   "Please insert a date"

-   "No exams
    inserted"![](media/image182.png){width="4.500387139107612in"
    height="1.0546992563429571in"}

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

[]{#_Toc163 .anchor}6.3 Edit
Exam![](media/image183.png){width="2.8660312773403325in"
height="3.4375174978127734in"}

Select a row from the "Laboratory browsing" window and click "Edit". An
"Edit Laboratory exam" window opens (left). All data, except patient's,
are editable. Click "OK" to update the record or "Cancel" to abort.

Data: see chapter 6.2

[]{#_Toc164 .anchor}6.4 Delete Exam

Select a row from the "Laboratory browsing" window and click "Delete".
Click "Yes" on the confirmation window to remove item from its database,
else "No" to abort the operation.

Data:

-   laboratory.LAB\_ID

[]{#_Toc165 .anchor}6.5 Print table

Generates a report with the current "exam" database. Click "Print table"
on the "Laboratory Browsing" window. The Jasper Viewer opens (see 3.8.4
for .PDF export / print / zoom / navigation operations).

[]{#_Toc166 .anchor}6.6 Close Laboratory menu

Click "Close" on the "Laboratory Browsing" menu to return to the main
menu.

[]{#_Toc167 .anchor}7.
Accounting![](media/image184.jpeg){width="4.788788276465442in"
height="5.382352362204724in"}![](media/image185.png){width="3.3444455380577427in"
height="4.189452099737533in"}

The "Accounting" menu manages payments and bills. It provides a submenu
with two options: "New Bill" to record a new payment, and "Bills
Manager", where all bills are stored.

[]{#_Toc168 .anchor}7.1 New
Bill![](media/image186.png){width="4.020869422572178in"
height="3.5609656605424322in"}

Click "New Bill" in the "Accounting" menu to open the "New Patient Bill"
window.

Date and time refer to when the window has been opened. If necessary,
enter a specific value, in DD/MM/YYYY - HH:MM:SS format, or select the
date by clicking on the calendar icon (3.10.1). If values are correct,
they will be shown in green, else in red. Then select the patient the
bill is assigned to, as seen in chapter 5.3.2. Select the pricing list
from the dropdown menu. Now add the items (medicals, operations, exam,
etc.) to the receipt, clicking on the buttons
on![](media/image187.png){width="2.6680194663167103in"
height="1.7130238407699037in"} the right side.

"+ Medical": adds a new medical (left). Select the item from the
"Medical" window and click "OK".

![](media/image188.png){width="2.6680194663167103in"
height="1.030660542432196in"}

Then enter the quantity and click "OK".

![](media/image189.png){width="4.273132108486439in"
height="2.346729002624672in"}

Pictured left is the bill with the selected medical, the quantity
entered, and the total money amount for that item (price of a single
unit \* quantity).

-   "+ Operation": adds a new operation (left). Select
    the![](media/image190.png){width="2.2865190288713912in"
    height="1.969712379702537in"} item from the "Operation" window and
    click "OK". Below is a detail of the bill after adding the
    operation.![](media/image191.png){width="4.142133639545057in"
    height="1.6412182852143482in"}

![](media/image192.png){width="4.2501727909011375in"
height="1.8233573928258968in"}

-   "+ Exam": adds a new exam (left). Select the item from the "Exam"
    window and click "OK". The exam is added to the "New Bill" window.

![](media/image193.png){width="2.561865704286964in"
height="1.3973818897637795in"}

-   "+ Other": used for medicals not recorded in OH's databases. Select
    the frequency (left; default: "Amount per day"), and click "OK".
    Then enter the![](media/image194.png){width="2.4387171916010497in"
    height="0.953989501312336in"} number of times the medical is
    required (below) and click "OK".

![](media/image195.png){width="2.5617694663167105in"
height="1.0566174540682414in"}

-   "+ Custom": used for items not recorded in OH's databases. Enter a
    description on the "Custom item" window (left) and click "OK". Then
    digit the price (below) and click
    "OK".![](media/image196.png){width="2.4386800087489062in"
    height="0.9828499562554681in"}

![](media/image197.png){width="4.220599300087489in"
height="3.675079833770779in"}The bill can contain more than one item of
the same type, just repeat the operations shown in this chapter.
Pictured left is the "New patient bill" window after the five steps
previously explained. The "TO PAY" row shows the total amount of the
bill, while the "BALANCE" row shows the money the patient owes the
hospital. No payments were recorded for now, so the balance equals the
value of the receipt. Before saving the bill in the database, it's
possible to remove an element. Select it and click "X Remove Item".

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
    quantity)![](media/image198.png){width="3.0641754155730534in"
    height="1.2155413385826772in"}

Once the items have been added to the receipt, record the payment adding
the total amount, the money the patient pays the hospital and the change
to give him/her if necessary. Use buttons on the right side, on the
bottom half of the
window.![](media/image199.png){width="3.3444455380577427in"
height="2.923027121609799in"}

-   "+ Payment": add the amount of a payment to the hospital. Enter the
    quantity and click for the "OK". The amount, the date and the time
    of the payment will be shown on the bottom table. In this case, the
    patient still owes one unit of currency, since "BALANCE" is 1.

-   "+ Refund": it's the opposite of "+ Payment". Enter the quantity as
    seen above and click "OK".

Repeat the operations shown to add more payments/refunds; to remove a
payment/refund, select it and click "X Remove Payment".

![](media/image200.png){width="4.912275809273841in"
height="4.329191819772529in"}Pictured left is the "New patient bill"
window after two payments and a refund.

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

[]{#_Toc169 .anchor}7.2 Bills
Manager![](media/image201.png){width="4.409873140857393in"
height="2.912544838145232in"}

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

[]{#_Toc170 .anchor}7.2.1 New Bill

See chapter 7.1.

[]{#_Toc171 .anchor}7.2.2 Edit
Bill![](media/image202.png){width="2.0112959317585304in"
height="1.0147626859142607in"}

Select a row from "Patients Bills Management" and click "Edit". The "New
Bill" window opens; you can add items, payments and refunds as seen in
chapter 7.1."X Remove Item" and "X Remove Payment" buttons are disabled,
while "Print Receipt" is enabled. Click on it, then click "Yes" on the
confirmation window (left). If the rsc/generalData.properties file shows
"RECEIPTPRINTER=yes" and the printer is connected to the computer, the
bill will be printed.

Data: attributes from "billitems" and "billpayments"

[]{#_Toc172 .anchor}7.2.3 Delete
Bill![](media/image203.png){width="4.2443011811023625in"
height="2.8052307524059494in"}

The function doesn't remove the bill from the "bills" database. It turns
its status to "D" (for Deleted); so it'll be visible only under the
"Bills" tab. "Deleted" rows are shown in red (left) and their amounts
won't be calculated in the reports. Select an open or close bill, and
click "Edit". Click "Yes" on the confirmation window, or "No" to abort
the operation.

Data:

-   bills.BLL\_ID

-   bills.BLL\_STATUS

[]{#_Toc173 .anchor}7.2.4 Receipt

Select a bill from "Patients Bills Management" and click "Receipt", to
print the bill and its items. The function is similar to the "Print
Receipt" button in "Edit Bill" (7.2.2).

[]{#_Toc174 .anchor}7.2.5
Report![](media/image204.png){width="2.6267366579177605in"
height="1.4136264216972878in"}

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
confirm.![](media/image205.png){width="2.626862423447069in"
height="1.069019028871391in"}

Once the time option is selected, if it's not "Today (closure)", a
"Report" window opens (left). Select between two options:

-   Short report: returns pending bills, and the total amount of the
    closed ones.

-   Full report: returns closed and pending bills in detail.

Click "OK" to confirm and generate the document
(below).![](media/image206.png){width="3.491453412073491in"
height="1.9334273840769904in"}

Data:

-   bills.BLL\_ID

-   bills.BLL\_DATE

-   bills.BLL\_PAT\_ID

-   bills.BLL\_USR\_ID\_A (user genersting the report, default "admin")

-   sum(bills.BLL\_AMOUNT) (sum of all amounts in the given period)

-   bills.BLL\_STATUS

[]{#_Toc175 .anchor}7.2.6 Close Bills Manager

Click "Close" on the "Patients Bill Management" window to return to OH's
main menu.

[]{#_Toc176 .anchor}8. Admission/Patient

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

[]{#_Toc177 .anchor}8.1 Search
Patient![](media/image207.jpeg){width="3.8170264654418196in"
height="2.2267508748906386in"}

To help search patient data, the browser provides some filter tools.
Options are intended with "ENHANCEDSEARCH=no" in the
rsc/generalData.properties file, meaning filters are automatically
applied according to the following selections:

Patient status: select from the dropdown menu ("All",
"Admitted",![](media/image208.png){width="5.163075240594925in"
height="1.5451935695538057in"} "Not Admitted").

Ward: tick the checkboxes to visualize records of patients admitted in a
given ward. If none are selected, no ward filter is applied.

Search Key: enter a substring to show only records matching either the
patient ID / name / city / address / telephone number / notes.

The number of matching records is shown under the "Ward" checkboxes.

Data: see chapter 8.

[]{#_Toc178 .anchor}8.2 New
Patient![](media/image209.jpeg){width="4.345698818897638in"
height="3.427564523184602in"}

Adds a new patient to the database. Click "New Patient" on the "Patients
Browser" window. A "New Patient" window opens. Add first name, second
name and select sex. Then enter the patients age, selecting the radio
button corresponding to the age format:

![](media/image210.png){width="5.249155730533683in"
height="3.3062445319335083in"}![](media/image211.png){width="2.1148589238845146in"
height="0.6748075240594925in"}

-   "Age": type the number of years, months and days in the three fields
    below.![](media/image212.png){width="2.1148589238845146in"
    height="0.6570439632545931in"}

-   "Birth date": enter the DD/MM/YYYY birthdate or select it clickcing
    on the calendar icon (3.10.1). To enter a different date, click on
    the basket icon and then enter the new
    value.![](media/image213.png){width="2.1148589238845146in"
    height="0.668568460192476in"}

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

-   Optional notes![](media/image214.png){width="1.5829352580927385in"
    height="2.51918416447944in"}![](media/image215.png){width="3.252049431321085in"
    height="2.4854516622922134in"}

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

[]{#_Toc179 .anchor}8.3 Edit
Patient![](media/image216.jpeg){width="3.920213254593176in"
height="2.9774015748031495in"}

![](media/image217.png){width="3.510324803149606in"
height="2.278314741907262in"}

Select a row from "Patients Browser" and click "Edit patient". All data
are editable (bottom right). If no photo was added, click "Load File" to
add a photo (8.2), else a red X is shown on the
photo![](media/image218.png){width="2.702587489063867in"
height="1.0704625984251968in"} to remove it. If the X is clicked, then
click "Yes" on the confirmation window (bottom left), else click "No" to
keep the current image.

Data: see chapter 8.2

[]{#_Toc180 .anchor}8.4 Delete
patient![](media/image219.jpeg){width="3.2539041994750657in"
height="1.5811384514435696in"}

Select a row from "Patients Browser" and click "Delete patient". Click
"Yes" on the confirmation window to remove the record, else "No" to
abort. If the patient is deleted, all foreign keys referencing the
patient will be removed.

Data: patient.PAT\_ID

[]{#_Toc181 .anchor}8.5
Admission![](media/image220.jpeg){width="5.103611111111111in"
height="5.194781277340333in"}

If the patient has not been admitted, the "Admission" buttons allows to
assign the patient a ward (8.5.1), else the button allows to edit
admission information (8.5.2).

[]{#_Toc182 .anchor}8.5.1 New Admission

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
related to the![](media/image221.png){width="6.688889982502187in"
height="3.2773950131233596in"} diagnosis. Click the "Delivery" tab to
add optional information about the delivery (for female patients). Click
on the "Notes" tab to add optional notes about the admission record.
Finally, click "Save" to save the admission data. If all required fields
(\*) have been filled, the admission record is saved, and the patient is
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

[]{#_Toc183 .anchor}8.5.2 Edit
admission![](media/image222.png){width="6.19771762904637in"
height="3.000949256342957in"}

Discharges an admitted patient. Select an "Admitted" row from "Patients
Browser", (the ones where the "Ward" column is not empty vuota) and
click "Admission". An "Edit Admission Record, window opens (below). All
data seen in chapter 8.5.1 are editable. Click "Save" to update
information. If all conditions previously explained have been respected,
the data will be updated.

Data: see chapter 8.5.1

[]{#_Toc184 .anchor}8.6
Examination![](media/image223.jpeg){width="4.562787620297462in"
height="3.5730424321959755in"}![](media/image224.png){width="3.8828576115485562in"
height="1.8832272528433947in"}

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
(0-100%).![](media/image225.png){width="4.0727723097112865in"
height="1.8096708223972005in"} Add optional notes in the "Complain"
textfield. Then click "Save" to save the data. Every time the window
referring to the same patient is opened, former measurements will be
visible (right), each with its date and time. Note 0, 0.0 and 0/0 values
mean those data were not collected (checkboxes not ticked).

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

[]{#_Toc185 .anchor}8.7 OPD

If "OPDEXTENDED=yes" in the rsc/generalData.properties file, you can
access to the OPD menu, by selecting a patient and clicking "OPD" (see
chapter 4).

[]{#_Toc186 .anchor}8.8 Bill

Select a patient and click "Bill" to access the "Accounting -\> New
Bill" to record a new bill for that patient (see chapter 7.1).

[]{#_Toc187 .anchor}8.9 Patient
Data![](media/image226.jpeg){width="5.465196850393701in"
height="4.120417760279965in"}![](media/image227.png){width="4.298902012248469in"
height="2.5173753280839897in"}

Select a patient from the browser and click "Data". The "Patient Data"
window opens (left). Admission history is reported on the right half.
Date, ward, admission diagnosis, discharge diagnosis and discharge date
are shown. Buttons on the bottom allow to manage these records and
update malnutrition control.

[]{#_Toc188 .anchor}8.9.1 Edit Patient Data

Select a row of "Patient Data" and click "Edit". The "Edit admission"
opens (8.5.2).

[]{#_Toc189 .anchor}8.9.2 Delete Patient Data

Select a row of "Patient Data" and click "Delete". Click "Yes" on the
confirmation window to remove the row, or "No" to abort.

[]{#_Toc190 .anchor}8.9.3 Malnutrition
Control![](media/image228.png){width="2.4760575240594926in"
height="1.0882436570428697in"}

Select a row of "Patient Data" (if the "Malnutrition control" checkbox
has previously been ticked; see chapter 8.5.1), then click "Malnutrition
control". A "Malnutrition Browser" window opens (left). It provides a
table with four columns: further date (date of the measurement),
approval date (date of next scheduled measurement), height and weight
(both referred to the current measurement. These data are completely
independent from those collected via the "Examination" menu (8.6).

[]{#_Toc191 .anchor}8.9.3.1 New Malnutrition Control
record![](media/image229.png){width="1.8418700787401574in"
height="1.1995100612423446in"}

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

[]{#_Toc192 .anchor}8.9.3.2 Edit Malnutrition Control record

Select a row of the malnutrition browser and click "Edit". An "Edit
Admission Record" window opens, where all data (8.9.3.1) are editable;
then click "OK" to confirm. If data are correct, the record will be
updated.

Data: see chapter 8.9.3.1

[]{#_Toc193 .anchor}8.9.3.3 Delete Malnutrition Control record

Select a row of the malnutrition browser and click "Delete". Click "Yes"
on the confirmation window to remove the row, or "No" to abort.

Data:

-   malnutritioncontrol.MLN\_ID

[]{#_Toc194 .anchor}8.9.3.4 Close Malnutrition Browser menu

Click "Close" on the "Malnutrition Browser" window to return to the
"Patient Data" window.

[]{#_Toc195 .anchor}8.9.4 Close Patient Data menu

Click "Close" on the "Patient Data" window to return to OH's main menu.

[]{#_Toc196 .anchor}8.10 Clinical
sheet![](media/image230.jpeg){width="3.8090376202974627in"
height="2.7308234908136484in"}

Select a patient from the browser and click "Clinical Sheet". A window
similar to "Patient Data" (8.9) opens (below), but it has different
buttons, aiming to generate Jasper Viewer reports (see 3.8.4 for .PDF
export / print / zoom / navigation operations) about the patient's OPD
history. If "DICOMMODULEENABLED=yes" in the rsc/generalData.properties,
you can access to the DICOM Viewer to analyze sonograms (8.10.5).

[]{#_Toc197 .anchor}8.10.1 OPD
Chart![](media/image231.png){width="4.521760717410324in"
height="2.5480489938757653in"}

Select a row from "Patient Data" where the column "Ward" is "OPD" (left)
and click "OPD Chart". This generates a report with a summary of the
visit. Information includes patient data and visit details (ID, date,
type, diagnosis, notes).

If there are no "OPD" records, a "Please select an OPD" window is shown.
Click "OK" to close
it.![](media/image232.png){width="3.543740157480315in"
height="2.3474267279090113in"}

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

[]{#_Toc198 .anchor}8.10.2 Admission
Chart![](media/image233.png){width="4.715706474190726in"
height="2.602788713910761in"}

Select a row from "Patient Data" where the column "Ward" has the name of
a ward (left). and click "Admission Chart". This generates a report with
a summary of the visit. Information includes patient data and admission
details (ID, date, type, admission diagnosis, notes, duration, discharge
diagnosis).

![](media/image234.png){width="3.576642607174103in"
height="2.4098162729658794in"}

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

[]{#_Toc199 .anchor}8.10.3 Discharge
Chart![](media/image235.png){width="4.490625546806649in"
height="2.493788276465442in"}

Select a row from "Patient Data" where the column "Ward" has the name of
a ward (left). and click "Discharge Chart". This generates the admission
chart seen in chapter 8.10.2, plus the discharge details.

Data: see chapter 8.10.2

![](media/image236.png){width="4.4437303149606295in"
height="3.078365048118985in"}

[]{#_Toc200 .anchor}8.10.4 Launch
Report![](media/image237.png){width="4.555494313210849in"
height="2.675667104111986in"}

Select a row from "Patient Data" and click "Discharge Chart". This
generates the admission chart (8.10.2), plus a report of the patient's
exams and their results.

Data:

-   all "patient" attributes used in 8.10.1

-   exam.EXA\_DESC

-   laboratory.LAB\_DATE

-   laboratory.LAB\_RESULT

![](media/image238.png){width="5.358883420822397in"
height="3.259339457567804in"}

[]{#_Toc201 .anchor}8.10.5
DICOM![](media/image239.png){width="6.688889982502187in"
height="3.7425929571303587in"}

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

[]{#_Toc202 .anchor}8.10.6 Close Clinical Sheet Menu

Click "Close" on the "Patient Data" window to return to the "Patients
browser" window.

[]{#_Toc203 .anchor}8.11
Therapy![](media/image240.jpeg){width="4.260418853893263in"
height="3.241270778652668in"}

Select a patient from the browser and click "Therapy". A new window
opens (left), showing the current calendar month. The user can add memos
of scheduled patient visits / therapies. To change the month and / or
year displayed, use the dropdown menu for the month and the selector for
the year, both on the left top corner of the window. Manage the
patient's calendar with the buttons on the right side, that will be
explained in the following
paragraphs.![](media/image241.png){width="4.745494313210848in"
height="2.600288713910761in"}

[]{#_Toc204 .anchor}8.11.1 Add
Therapy![](media/image242.png){width="4.260585083114611in"
height="2.3088473315835523in"}

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

[]{#_Toc205 .anchor}8.11.2 Edit
Therapy![](media/image243.png){width="4.531872265966754in"
height="2.5020800524934383in"}

Select a therapy stored in the calendar and click "Edit Therapy". All
data are editable. Click "OK" to update, or "Cancel" to abort.

Data: see chapter 8.11.1

[]{#_Toc206 .anchor}8.11.3 Remove Therapy

Select a therapy stored in the calendar and click "Remove Therapy". It
will be automatically deleted.

Data:

-   therapies.THR\_ID

[]{#_Toc207 .anchor}8.11.4 Check
Availability![](media/image244.png){width="2.721874453193351in"
height="1.2000153105861768in"}

Checks the availability of the medical for every stored therapy. When
the therapy is added, it is "NOT CHECKED". Select a therapy and click
"Check Availability". If the medical is available in the pharmacy the
icon shown under that button turns to "AVAILABLE", else a message window
opens as a warning to the user (left). To update the medical DB, see
chapter 5.1.

[]{#_Toc208 .anchor}8.11.5 Add visit

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

[]{#_Toc209 .anchor}8.11.6 Remove Visit

Select a visit stored in the calendar and click "Remove Visit". It will
be automatically deleted.

Data:

-   visits.VST\_ID

[]{#_Toc210 .anchor}8.11.7
SMS![](media/image245.png){width="2.9624267279090115in"
height="0.8985301837270341in"}

Select a visit / therapy and tick the "SMS" checkbox to send a text
notification, with the scheduled date and time, to the patient. If
the![](media/image246.png){width="2.183705161854768in"
height="0.8903871391076116in"} patient has no phone number recorded, a
message window (left) asks the user to add a number. If "OK" is clicked,
type the number on the new window (right), to add it to the "patient"
database.

Data:

-   visits.VST\_ID

-   visits.VST\_PAT\_ID

-   patient.PAT\_TELE

[]{#_Toc211 .anchor}8.11.8 Save![](media/image247.png){width="1.875in"
height="1.1458333333333333in"}

Saves data inserted / edited. Click "Save" and a confirmation window
(left) appears. Click "OK" to close it and return to the calendar. If
changes are not saved, the "Close" window (right) is shown. Click:

-   "Yes" (saves changes and closes the calendar window)

-   "No" (closes the calendar window without saving changes)

-   "Cancel" (back to the calendar).

[]{#_Toc212 .anchor}8.11.9 Close Therapy
calendar![](media/image248.png){width="1.967681539807524in"
height="1.0438571741032372in"}

Click "Close" on the calendar window to return to the "Admission /
Patient" menu. If changes have been made after the last saving, the
"Close" window opens; see 8.11.8 for options.

[]{#_Toc213 .anchor}8.12
Merge![](media/image249.jpeg){width="3.275515091863517in"
height="2.240178258967629in"}

The merging function is enabled if "MERGEFUNCTION=yes" in the
rsc/generalData.properties. It helps remove double registrations of the
same patient. To merge the data, both records must be "Not Admitted".
Select the two similar records and click "Merge". Click "Yes" on the
confirmation window (below), else "No" to abort the operation.

If the data are correct, the merger takes place and the old record (ID
510 in this example) will be automatically deleted;
else![](media/image250.png){width="3.263270997375328in"
height="1.2086187664041994in"} an error window is shown:

-   "Please select 2 patients"

-   "Cannot merge admitted patients"

Click "OK" to return to the former window. Pictured below are the
patient browser before the merger, and a detail of the browser after
this operation.![](media/image251.png){width="6.688889982502187in"
height="1.539963910761155in"}![](media/image252.png){width="6.688889982502187in"
height="0.5657895888013998in"}

Data:

two records from the "patient" database, where admission.ADM\_PAT\_ID is
null.

[]{#_Toc214 .anchor}9.
Vaccine![](media/image253.jpeg){width="4.918156167979003in"
height="4.150016404199475in"}![](media/image254.png){width="4.2468624234470695in"
height="2.4339326334208224in"}

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

[]{#_Toc215 .anchor}9.1 Search Vaccine

You can easily search records in the "Patient Vaccines Browser" window
thanks to a series of filters:

Vaccine type and name: Select the type from the first dropdown, or "All
type"; then choose the vaccine name from the second dropdown. The length
of this menu depends on the type choice (only the selected type, or all
recorded in OH).

Vaccination date: filter records by date entering DD/MM/YY dates or
choosing them clicking on the calendar icon (3.10.1).

Age: enter minimum and maximum age of the patients.

Sex: select between "All", "Male" and "Female" radio buttons.

Once the filters were selected, click "Search" to visualize only the
matching records, whose number is shown under that button.

Data: see chapter 9

[]{#_Toc216 .anchor}9.2 New Vaccine
Record![](media/image255.png){width="3.302470472440945in"
height="2.246447944006999in"}

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

"Please select a vaccine"

"Please select a patient"

Click "OK" to return to the former window.

Data:

see chapter 9

[]{#_Toc217 .anchor}9.3 Edit Vaccine
record![](media/image256.png){width="3.853545494313211in"
height="2.617017716535433in"}

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

[]{#_Toc218 .anchor}9.3 Delete vaccine record

Select a row of the "Patient Vaccine Browsing" and click "Delete". Click
"Yes" on the confirmation window to delete the record from the
"patientvaccine", or "No" to abort the operation.

Data:

-   patientvaccine.PAV\_ID

[]{#_Toc219 .anchor}9.4 Close Vaccine menu

Click "Close" on the "Patient Vaccine Browsing" window to return to OH's
main menu.

[]{#_Toc220 .anchor}10. Statistics

Generates reports of the hospital activity. After clicking "Statistics"
on the main menu, a "Report Launcher" window (below) opens. It has a
dropdown menu to select the data to report, two DD/MM/YYYY fields to
select the date range, and buttons to create reports, either in Jasper
or Excel format.

[]{#_Toc221 .anchor}10.1 Launch report

Select the data to report from the dropdown menu (above) and the
dat![](media/image257.jpeg){width="4.857653105861767in"
height="2.587029746281715in"}![](media/image258.png){width="6.688889982502187in"
height="0.9748031496062992in"}![](media/image259.png){width="2.9577766841644793in"
height="2.6321380139982504in"}![](media/image260.png){width="2.9577766841644793in"
height="1.5582163167104113in"}![](media/image261.png){width="3.575475721784777in"
height="1.8528160542432195in"}e interval, and click "Launch Report". A
Jasper Report document is generated (see 3.8.4 for .PDF export / print /
zoom / navigation operations).

Here are some example of data than can be reported:

-   number of registered patients (left)

-   number of admitted patients

-   numero of diagnoses of the admitted patients

-   laboratory inventory (bottom right)

-   epidemiology reports.

-   financial reports (bottom left).

-   etc.

[]{#_Toc222 .anchor}10.2 Excel

Same as 10.1, with data exported in .csv files, that can be read by
Microsoft Excel. See chapter 5.1.5 to save the generated file.

[]{#_Toc223 .anchor}10.3 Close Stats menu

Click "Close" on the "Report Launcher" window to return to OH's main
menu.

[]{#_Toc224 .anchor}11.
Printing![](media/image262.jpeg){width="6.435100612423447in"
height="2.352979002624672in"}

After clicking "Printing" on the main menu, a sub menu opens, with two
options "Exams List" and "Diseases list". According to the option
selected, a Jasper Viewer document opens, reporting respectively:

the list of exams recorded in OH and the set of results stored

the list of all diseases recorded in OH, sorted by type

See chapter 3.8.4 for .PDF export / print / zoom / navigation
operations.

[]{#_Toc225 .anchor}12.
Help![](media/image263.png){width="3.304818460192476in"
height="3.0600174978127734in"}

Click "Help" on the main menu to open OH's .pdf user manual, in a new
window (left).

[]{#_Toc226 .anchor}13. The OH database

The database running in OpenHospital is made of three functional
elements:

the login DB: manages the access to OpenHospital (13.1)

the main DB: links the main entities, such as patient, medicals, wards,
exams, operations, etc. (13.2)

the rest of the database: a series of independent tables for the
secondary functions (13.3)

[]{#_Toc440366455 .anchor}13.1 The login
DB![](media/image264.png){width="1.7335433070866142in"
height="3.6678116797900264in"}

[]{#_Toc440366456 .anchor}13.2 The main
DB![](media/image265.png){width="6.688889982502187in"
height="9.70440179352581in"}

[]{#_Toc229 .anchor}13.3 Other
tables![](media/image266.png){width="4.44748031496063in"
height="6.688889982502187in"}
