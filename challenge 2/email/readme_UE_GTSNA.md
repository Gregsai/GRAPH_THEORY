## Dataset 

`dataset_UE_GTSNA.csv` (270 MB) encodes emails exchanged during the period 4 to 19 March 2019 in a consulting firm. 

The file has been compressed and splitted with `rar` in order to upload it to Moodle where files can't exceed 30 MB.

To extract the multi-part rars,   please use `unrar x dataset_UE_GTSNA.part01.rar` (Linux), or simply double-click (works also with Linux ;-))

### Lines

~~~
GroupName1 | MessSize | MessDate | Subject | Id_Direction | PartnerTypeName | Id_Recipient | Id_Regroup | Partner_Name | Recipient_Display | Recipient_Name
Senior | 0,0477132797241211 | 03/04/2019 00:03 | 4bb26edab1c7a7bd212a86e4308d128af11e117c | 2 | Internal | 719 | 772 | f0ea57ffa0ffbe9ee2ee743dd0b3a739abe3c8d7 | 031c2220cade22cd67b6ec200668e1c86f570889 | 665751c47b55cb0f3c4fc9376db0c3c7109f8d99
Manager | 0,0353221893310547 | 03/04/2019 00:03 | 4bb26edab1c7a7bd212a86e4308d128af11e117c | 1 | Internal | 772 | 719 | f0ea57ffa0ffbe9ee2ee743dd0b3a739abe3c8d7 | 	665751c47b55cb0f3c4fc9376db0c3c7109f8d99 | 031c2220cade22cd67b6ec200668e1c86f570889
~~~

1174928 lines in `dataset_UE_GTSNA.csv` 

Each line describes what a collaborator sent or received at MessDate. S/he sent (Id_Direction is equal to 1) or received an email from a contact (Id_Direction is equal to 2).

The interlocutor can be interne/externe/unidentified (PartnerTypeName).

The interaction involving the collaborator is defined by:

- GroupName1 : Post/Title of the collaborator

- RecipientName : The collaborator

- MessSize : message size in Mégabytes

- MessDate : Date+Hour

- Id_Direction : 1 for a sent email, 2 for a received email

- PartnerTypeName : the interlocutor may be either: 

	- Interne
	- Internet (external interlocutor)
	- Unidentified local address (applications or server or cloud mail address)

- PartnerName : domain name if external interlocutor

- Recipient_Display : the interlocutor

### Mails

A line IS NOT an email, just the point of view of 1 **collaborator** from the **company**.

The dataset contains 509954 mails (uniques pairs ["Subject",'MessDate']). An email can be described by several lines.

 If Id_Direction = 2, Recipient_Display is the sender of the message and "ReciptientName" refers to the target. If Recipient_Display is not a colleague (PartnerTypeName = internet), the mail is described by 1 unique line : the point of view of the receiver. But if the sender is a colleague frome the company, there will be 2 lines for the same email : one line for the sender AND one line for the receiver.


Example1: if A and B are two internal colleagues, there will be 1 line dedicated to A and 1 line dedicated to B for the same message 
~~~
Manager | 04/03/2019 00:03 | 1 | B | A | 4bb26edab1c7a7bd212a86e4308d128af11e117c
Senior  | 04/03/2019 00:03 | 2 | A | B | 4bb26edab1c7a7bd212a86e4308d128af11e117c
~~~

Example2: if A, B, C are 3 colleagues and they all receive the same message from an external partner, there will be 3 lines with same (subject,date) with id_Direction = 2.

~~~
Manager | 04/03/2019 00:03 | 2 | D | A | 4bb26edab1c7a7bd212a86e4308d128af11e117c
Staff   | 04/03/2019 00:03 | 2 | D | B | 4bb26edab1c7a7bd212a86e4308d128af11e117c
Senior  | 04/03/2019 00:03 | 2 | D | C | 4bb26edab1c7a7bd212a86e4308d128af11e117c
~~~



