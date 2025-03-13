<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Network File Shares and Permissions </h1>
In this tutorial, I will explain how to create sample file shares with different permission levels, including Read and Read/Write. I will also guide you through the process of creating a security group, assigning specific permissions to it, and testing access to ensure everything works correctly. This step-by-step approach will help you efficiently manage file sharing and access controls.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)



<h1> Network File Shares and Permissions Lab </h1>

--------

![image](https://github.com/user-attachments/assets/9ed9c7bf-f0fa-42f2-b591-da1afb6d13ca)

---------

<h2> Step 1: Log into DC-1 as jane_admin -> go to file explorer (Windows key + E) -> Click on This PC ->  Choose the Windows C-Drive -> </h2>

----

![image](https://github.com/user-attachments/assets/570a22fd-d2b3-49c2-93bf-325a99735e18)


---------


<h2> Step 2: Create 4 folders (Control + Shift + N) Named: Read Access, Write Access, No Access, Accounting  </h2>

-------


![image](https://github.com/user-attachments/assets/05a63aa3-fbc2-4407-9ba5-5345ae26f094)


----------

<h2> Step 3: Next set the following permissions  </h2>

-----

- Right click the Read Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain users -> Click on Add -> Assign the Read Access folder  the Read Permission level -> Click on share -> done

------


![image](https://github.com/user-attachments/assets/c1a41fd5-ed7d-4bbc-83a2-9497ecaea3f5)



-----------

- Right-click the Write Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain users -> Click on Add -> Assign the Write Access folder the Read/Write permission level -> Click on share -> done

------

![image](https://github.com/user-attachments/assets/f48248f3-ab14-494d-9c7a-cfbbaa809578)


---------

- Right-click the No Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain admins -> Click on Add -> Assign the No Access folder the Read/Write permission level -> Click on share -> done

---------


![image](https://github.com/user-attachments/assets/3e2c3a69-9a82-421d-81e8-ef05db9cdb20)


-------


<h2> Step 4: Log into Client-1 as fas.tacos  </h2>

------

![image](https://github.com/user-attachments/assets/1c6fcd2c-33da-4945-8328-e97ca2a07da2)


--------

- Search for the Shared Files

---------


- Open file explorer (Windows key + E) -> In the search bar Type: \ \DC-1 ->


---------

![image](https://github.com/user-attachments/assets/c4d15ca0-c877-4593-97d5-20519961e458)


--------

- Try to access and open the folders -> Attempt to create a text file and write something in it -> Save

-------

- Domain Admins only have Access to the No Access Folder, Domain Users Can't access the No Access Folder

--------

- No access folder

-------

![image](https://github.com/user-attachments/assets/dd3afc6d-c101-4a68-917b-5e6db5ac96f8)



--------

- Read Access folder

---------

- Domain Users only have Read Access to the Read Access Folder, they are not able to edit Files

---------

- Try to Create a Text Document

---------

![image](https://github.com/user-attachments/assets/a9056554-ae0c-46ca-8767-d4b1a3d1c288)



-------

- Write Access Folder

-------

- Domain Users are able to Access and edit in the Write Access Folder


---------

- Try to Create a Text Document

---------

![image](https://github.com/user-attachments/assets/7209e057-d071-46e6-ba98-779b369c11c6)



----------

![image](https://github.com/user-attachments/assets/895571e4-e92d-428f-a011-90eaa69b2a2a)



-------

- Edit Text document

----------


![image](https://github.com/user-attachments/assets/3b2ece54-58a2-4d08-8663-0dffe5fb6264)


--------


<h2> Step 5: Create a Security Group Called Accountants </h2>

----------

- Create An OU Called _GROUPS

----------


- Click the Start menu -> go to Windows Administrative Tools -> choose Active Directory Users and Computers -> Create a new OU called _GROUPS -> Right Click Mydomain.com-> New -> Organizational Unit -> Name it: _GROUPS

---------


![image](https://github.com/user-attachments/assets/51489071-d5b9-412d-b827-48b34b296481)



----------

- Create A Security Group called Accountants

-----------

- Right click on the OU _Groups -> New -> Group ->

----------

![image](https://github.com/user-attachments/assets/071fc2f3-2521-45ec-a12f-6e8c8e7e05b7)


------------

- Name the Group Accountants ->

----------

![image](https://github.com/user-attachments/assets/b1cb4bdf-579e-47ca-bea1-141638086b87)


---------

- Add the Security Group Accountants to the Accountants folder and Assign the Accountants folder the Read/Write permission level

----------

- Next go to File Explorer -> C-Drive -> Right-click the Accounting Folder -> Properties -> Sharing -> Share -> Type: Accountants -> Click on Add -> Assign the permission level (read/write) -> share -> done

-----------


![image](https://github.com/user-attachments/assets/e057b2a7-07a5-42ca-89b3-d822d1769aff)


---------

<h2> Step 6: Within Client-1 you should be able to see the Accounting folder </h2>

----------

![image](https://github.com/user-attachments/assets/a3829b7a-9e0f-4a5c-8999-477b0d43372e)

-----------

- Attempt to log into the Accounting folder as fas.tacos

----------

![image](https://github.com/user-attachments/assets/61d14601-172c-443b-a4a8-0a1f5dcfe501)


---------

<h2> Step 7: Sign out of Client-1 as fas.tacos. Add fas.tacos as a member of the Security Group Accountants  </h2>

---------

- Within DC-1 -> go to Active Directory Users and Computers and click on the OU _GROUPS   ->  double click on the Accountants group -> Go to members -> click on Add -> Type: fas.tacos -> click on Check Names -> ok -> apply -> ok

-----------

![image](https://github.com/user-attachments/assets/31cd11d1-83c4-4a89-bd47-a7a6beed4159)


---------

<h2> Step 8: Log into Client-1 with the user fas.tacos </h2>


-----------

![image](https://github.com/user-attachments/assets/f23a8427-b98b-4ad1-9625-c12529642785)


-------

![image](https://github.com/user-attachments/assets/6ccba3cf-e9be-4ee9-a4a7-878c573115a0)

------------

- Open file explorer (Windows key + E) -> In the search bar Type: \ \DC-1 -> Attempt to log into the Accounting folder as fas.tacos -> Create a Text Document

------------

![image](https://github.com/user-attachments/assets/c45d4911-cf5b-476f-a5d1-6fd7526a0f7c)





