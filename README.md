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

![image](https://github.com/user-attachments/assets/cf103185-4baf-4c5d-80aa-4fa7002b7692)

---------


<h2> Step 2: Create 4 folders (Control + Shift + N) Named: Read Access, Write Access, No Access, Accounting  </h2>

-------


![image](https://github.com/user-attachments/assets/8f36e3e0-b21a-4955-9266-e0addca2d596)

----------

<h2> Step 3: Next set the following permissions  </h2>

-----

- Right click the Read Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain users -> Click on Add -> Assign the Read Access folder  the Read Permission -> Click on share -> done

------


![image](https://github.com/user-attachments/assets/79b0f039-66cf-4c64-a900-2ad295005996)


-----------

- Right-click the Write Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain users -> Click on Add -> Assign the Write Access folder the Read/Write permission level -> Click on share -> done

------

![image](https://github.com/user-attachments/assets/8b3463e6-b605-47a4-a3d3-e0b57a23c04f)

---------

- Right-click the No Access folder -> Click on properties -> Click on sharing -> Share -> Type: domain admins -> Click on Add -> Assign the No Access folder the Read/Write permission level -> Click on share -> done

---------


![image](https://github.com/user-attachments/assets/82e526ed-7ffb-4193-ad18-eae7c114ac65)

-------


<h2> Step 4: Log into Client-1 as fas.tacos  </h2>

------

![image](https://github.com/user-attachments/assets/1c6fcd2c-33da-4945-8328-e97ca2a07da2)


--------

- Open file explorer (Windows key + E) -> In the search bar Type: \ \DC-1 ->


---------

![image](https://github.com/user-attachments/assets/3fe0b988-2776-4755-a4ca-9e86c06eb366)

--------

- Try to access and open the folders -> Attempt to create a text file and write something in it -> Save

--------

- No access folder

-------

![image](https://github.com/user-attachments/assets/cf081e90-06de-4336-85b1-8ef29fba0b71)


--------

- Read Access folder

---------

- Try to Create a Text Document

---------

![image](https://github.com/user-attachments/assets/759b69f3-726a-4cb3-819f-ef082d78af69)


-------

- Write Access Folder


---------

- Try to Create a Text Document

---------

![image](https://github.com/user-attachments/assets/f29eb3ab-311f-4399-9abf-2620cb817861)


----------

![image](https://github.com/user-attachments/assets/f3fce59d-8162-4ef6-8c32-b168df3debe1)


-------

- Edit Text document

----------



![image](https://github.com/user-attachments/assets/c732a985-4351-4a04-88ba-362219ed5cb4)

--------


<h2> Step 5: Create a Security Group Called Accountants </h2>

----------

- Click the Start menu -> go to Windows Administrative Tools -> choose Active Directory Users and Computers -> Create a new OU called _GROUPS -> Right Click Mydomain.com-> New -> Organizational Unit ->

---------

![image](https://github.com/user-attachments/assets/d82afce3-fb1d-4d16-aafb-ab938df2c34f)


----------

- Right click on the OU _Groups -> New -> Group ->

----------

![image](https://github.com/user-attachments/assets/4b6b2e07-a076-41b0-876f-93bf3c39f8fe)

------------

- Name the Group Accountants ->

----------

![image](https://github.com/user-attachments/assets/71a617f0-1f13-4d2b-af5e-16a253e56b2f)


---------

- Next go to File Explorer -> C-Drive -> Right-click the Accounting Folder -> Properties -> Sharing -> Share -> Type: Accountants -> Click on Add -> Assign the permission level (read/write) -> share -> done

-----------


![image](https://github.com/user-attachments/assets/58a0d105-e719-438d-9a05-951c55002824)



---------

<h2> Step 6: Within Client-1 you should be able to see the Accounting folder </h2>

----------

![image](https://github.com/user-attachments/assets/cad9b41f-d9b8-4523-be2f-6d06786b2405)

-----------

- Attempt to log into the Accounting folder as fas.tacos

----------

![image](https://github.com/user-attachments/assets/62c501c9-238f-4120-af4a-1b830386b866)

---------

<h2> Step 7: Sign out of Client-1 as fas.tacos. Add fas.tacos as part of the Security Group Accountants  </h2>

---------

- Within DC-1 -> go to Active Directory Users and Computers and click on the OU _GROUPS   ->  double click on the Accountants group -> Go to members -> click on Add -> Type: fas.tacos -> click on Check Names -> ok -> apply -> ok

-----------

![image](https://github.com/user-attachments/assets/1a8727c6-7744-4aa5-81e6-f846db9d73ee)


---------

<h2> Step 8: Log into Client-1 with the user fas.tacos </h2>


-----------

![image](https://github.com/user-attachments/assets/33f7683c-e3d4-4e3d-b3d1-8adb74570f75)

-------

![image](https://github.com/user-attachments/assets/6ccba3cf-e9be-4ee9-a4a7-878c573115a0)

------------

- Open file explorer (Windows key + E) -> In the search bar Type: \\DC-1 -> Attempt to log into the Accounting folder as fas.tacos -> Create a Text Document

------------

![image](https://github.com/user-attachments/assets/28ed5cfa-2113-4aaf-8d9a-cd7c1f454237)




