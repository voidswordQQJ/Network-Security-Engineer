# Getting Started

Before we actually stated to learned the network foundation staff, we need to set up our environment first, below is the requirement, also the external link will be include.

- Windows 10 Professional x64
  - VMware Workstation
    - Windows server 2003 and 2008
    - Windows client XP and 7
    - Centos version 7 or 8
    - Kali Linux
  - Scanner
    - OpenVAS or Nessus
    - AWVS Web Scanner

## Intro to IP Address

The IP address and its subnet mask is one pair, and the subnet mask divide network address and host address.

For example, if the subnet mask is `255.255.255.0`, then `255.255.255` is the network address and `0` is the host address.

> IPv4 Address: 192.168.1.1
>
> Subnet Mask: 255.255.255.0

If two host is required to communicate with each other, then they must have the same subnet mask, and a different IP.

Second, to avoid IP repeat problem, we must change the IPv4 address, so base on the network address and host address our subnet mask set, the first 3 part of the IPv4 address should be the same, and the last part we can change from 1 to 254.

You might think why the maximum is 254, it's because the base different, the IPv4 address are normally render as decimal, but it turn to binary when computer read it.

> 192.168.1.1 = 11000000 10101000 00000001 00000001
>
> 255.255.255.0 = 11111111 11111111 11111111 00000000
>
> IPv4 Address are made up with 32 digit binary number

In addition, we cannot use 0 and 255 in a IPv4 Address because they are take place in the subnet mask.

## Base Conversion

Base Conversion is simple, and the three main bases that we use nowadays are binary, decimal, and hex.

> Binary = 0, 1
>
> Decimal = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
>
> Hex = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F

In mathematics and digital electronics, a binary number is a number expressed in the base-2 numeral system or binary numeral system, which uses only two symbols: typically "0" (zero) and "1" (one).

The base-2 numeral system is a positional notation with a radix of 2. Each digit is referred to as a bit. Because of its straightforward implementation in digital electronic circuitry using logic gates, the binary system is used by almost all modern computers and computer-based devices.

Binary counting follows the same procedure, except that only the two symbols 0 and 1 are available. Thus, after a digit reaches 1 in binary, an increment resets it to 0 but also causes an increment of the next digit to the left:

> 0000,
>
> 0001, (rightmost digit starts over, and next digit is incremented)
>
> 0010, 0011, (rightmost two digits start over, and next digit is incremented)
>
> 0100, 0101, 0110, 0111, (rightmost three digits start over, and the next digit is incremented)
>
> 1000, 1001, 1010, 1011, 1100, 1101, 1110, 1111 ...

In mathematics and computing, hexadecimal (also base 16, or hex) is a positional system that represents numbers using a base of 16. Unlike the common way of representing numbers with ten symbols, it uses sixteen distinct symbols, most often the symbols "0"–"9" to represent values zero to nine, and "A"–"F" (or alternatively "a"–"f") to represent values ten to fifteen.

Most computers manipulate binary data, but it is difficult for humans to work with a large number of digits for even a relatively small binary number. Although most humans are familiar with the base 10 system, it is much easier to map binary to hexadecimal than to decimal because each hexadecimal digit maps to a whole number of bits.

With little practice, mapping 1111 to 0xF in one step becomes easy: see table in written representation. The advantage of using hexadecimal rather than decimal increases rapidly with the size of the number. When the number becomes large, conversion to decimal is very tedious. However, when mapping to hexadecimal, it is trivial to regard the binary string as 4-digit groups and map each to a single hexadecimal digit.

## Basic Dos Command

DOS, Disk Operate System, is a very old system we still using right now, for example CMD is a DOS. In this lesson, we are learning some simples DOS commands.

> Press Win + R to opened CMD in Windows

To locate drive, and access to a folder, use command `[Drive Letter]:` and `cd`.

```
C:\Users\Eleven\Documents>D:

D:\>cd D:\Study\A01 - Notebook\Testing

D:\Study\A01 - Notebook\Testing>
```

To create a file or folder, use command `mkdir` and `copy con [filename].txt` (After typing the content, use `CTRL + Z` and press `Enter` to save)

```
D:\Study\A01 - Notebook\Testing>mkdir Example

D:\Study\A01 - Notebook\Testing>cd Example

D:\Study\A01 - Notebook\Testing\Example>copy con example.txt
Here is Henry!
Here is Charlie!^Z
Copy         1 File

D:\Study\A01 - Notebook\Testing\Example>
```

To view all content in a folder, use command `dir`.

In addition, use command `dir /a` to view all file include system file.

```
D:\Study\A01 - Notebook\Testing>cd Example

D:\Study\A01 - Notebook\Testing\Example>dir
Volume in drive D is Database
Volume Serial Number is 7066-53F7

Directory of D:\Study\A01 - Notebook\Testing\Example

2020/09/15  09:45    <DIR>          .
2020/09/15  09:45    <DIR>          ..
2020/09/15  09:46                32 example.txt
         1 File(s)             32 bytes
         2 Dir(s)  198,072,438,784 bytes free

D:\Study\A01 - Notebook\Testing\Example>
```

To view the content in a file, use command `type [filename].txt` (Press `TAB` to auto fill filename)

```
D:\Study\A01 - Notebook\Testing\Example>type example.txt
Here is Henry!
Here is Charlie!
D:\Study\A01 - Notebook\Testing\Example>
```

To delete file, use command `del`.

- `del [filename].[suffix]` - deleted file
- `del *.[suffix]` - deleted all file with same suffix
- `del \*.\*` - deleted all file
- `del \*.\* /s /q` - forced to deleted all file

```
D:\Study\A01 - Notebook\Testing\Example>del example.txt

D:\Study\A01 - Notebook\Testing\Example>dir
Volume in drive D is Database
Volume Serial Number is 7066-53F7

Directory of D:\Study\A01 - Notebook\Testing\Example

2020/09/15  10:15    <DIR>          .
2020/09/15  10:15    <DIR>          ..
         0 File(s)              0 bytes
         2 Dir(s)  198,072,438,784 bytes free

D:\Study\A01 - Notebook\Testing\Example>
```

To contribute the property to file or folder, use command `attrib`.

- `attrib +h [filename]` - Hidden file
- `attrib +h +s +a [filename]` - Hidden file and turn it to a system file
  - h represent hidden
  - s represent system file
  - a represent only read

Create Empty file with custom data size, use command `fsutil file createnew c:\system.ini 409600000 `.

```
D:\Study\A01 - Notebook\Testing\Example>fsutil file createnew example.txt 20480000
File D:\Study\A01 - Notebook\Testing\Example\example.txt is created

D:\Study\A01 - Notebook\Testing\Example>dir
Volume in drive D is Database
Volume Serial Number is 7066-53F7

Directory of D:\Study\A01 - Notebook\Testing\Example

2020/09/15  10:43    <DIR>          .
2020/09/15  10:43    <DIR>          ..
2020/09/15  10:43        20,480,000 example.txt
         1 File(s)     20,480,000 bytes
         2 Dir(s)  198,051,954,688 bytes free

D:\Study\A01 - Notebook\Testing\Example>
```

To copy or move file from origin directory to target directory, use command `copy ` and `move`.

```
D:\Study\A01 - Notebook\Testing\Example>copy example.txt ..\
  1 file(s) copied.

D:\Study\A01 - Notebook\Testing\Example>cd ..

D:\Study\A01 - Notebook\Testing>dir
Volume in drive D is Database
Volume Serial Number is 7066-53F7

Directory of D:\Study\A01 - Notebook\Testing

2020/09/15  11:49    <DIR>          .
2020/09/15  11:49    <DIR>          ..
2020/09/15  10:43    <DIR>          Example
2020/09/15  10:43        20,480,000 example.txt
         1 File(s)     20,480,000 bytes
         3 Dir(s)  198,031,593,472 bytes free

D:\Study\A01 - Notebook\Testing>
```



## User and Group Management

### User Manage

User overview:

- After logging in to the operating system, each user has different permissions.
- Each account has its own unique SID (Security Identifier)
  - UID of Administrator account is 500
  - UID of User is started from 1000

Example of a SID below:

> S-1-5-21-1180699209-877415012-3182924384-1004
>
> In this case, the user UID is 1004

The SAM file is a database include the username and the password.

When we log in to the operating system, the system will automatically check with the SAM in the Config. If the password and username are found to be consistent with the encrypted data in the SAM file, you will successfully log in. If there is an error, you will not be able to log in.

Example of a SAM file content below:

> Administrator:500:611D6F6E763B902934544489FCC9192B:B71ED1E7F2B60ED5A2EDD28379D45C91:::

Built-in user:

> User Account
>
> 1. administrator - high permissions
> 2. guest - low permissions
>
> System Account
>
> 1. system - very high permissions
> 2. local services - low permissions
> 3. network services - low permissions

Every user has there owned a config file (Home Directory), it automatically generates when the user first logs in to the system.

> In windows 7 and 10, it locate at C:\Users\

User manage commands:

> net user [username] - view user information
>
> net user [username] [password] - changed user password
>
> net user [username] [password] /add - add a new user

### Group Manage

 Group overview:

- The role of groups is to simplify the assignment of permissions
- Permissions can direct assign to a user, but easier to assign as a group.

Built-in group:

> 1. administrators - high permissions
> 2. guests - low permissions
> 3. users - medium permissions
> 4. network - network config
> 5. print - printer
> 6. Remote Desktop - remote connect

Group manage commands:

> net localgroup - view group list
>
> net localgroup [group name] - view members in group list
>
> net localgroup [group name] /add - add a new group
>
> net localgroup [group name] [username] /add - assign a user to a group
>
> net localgroup [group name] [username] /del - remove a user from a group
>
> net localgroup [group name] /del - delete a group

## Remote Connect

### Microsoft Terminal Services

In Windows 10 or later, you can configure your PC for remote access with a few easy steps.

> 1. On the device you want to connect to, select Start and then click the Settings icon on the left.
> 2. Select the System group followed by the Remote Desktop item.
> 3. Use the slider to enable Remote Desktop.
> 4. It is also recommended to keep the PC awake and discoverable to facilitate connections. Click Show settings to enable.
> 5. As needed, add users who can connect remotely by clicking Select users that can remotely access this PC.
>    Members of the Administrators group automatically have access.
> 6. Make note of the name of this PC under How to connect to this PC. You'll need this to configure the clients.

In Windows 7 and early version of Windows 10, to configure your PC for remote access, download and run the [Microsoft Remote Desktop Assistant](https://www.microsoft.com/download/details.aspx?id=50042). This assistant updates your system settings to enable remote access, ensures your computer is awake for connections, and checks that your firewall allows Remote Desktop connections.

To connect to a Microsoft Terminal Server, by press `Win + R` and enter `mstsc` in the text bar to open the client.

### Telnet Services

In Windows 2008 or later, you can configure your PC for telnet access with a few easy steps.

> 1. Start Server Manager. Click Start, right-click Computer, and then click Manage.
> 2. If the User Account Control dialog box appears, confirm that the action it displays is what you want, and then click Continue.
> 3. In the Features Summary section, click Add features.
> 4. On the Select Features page, select Telnet Server. You can also select Telnet Client if you want.
> 5. Click Next, and then on the Confirm Installation Options page, click Install.
> 6. On the Installation Results page, click Close.
> 7. Close Server Manager.

To connect to a Telnet Server, by press `Win + R` and enter `cmd` in the test bar, then use command `telnet [hostname]`.

### SSH Services

Right now, we are not using SSH for learning, but it will include in the future when we talk about Linux Security, so the only thing to reminder now is the SSH port is 22.

## NTFS Security Permissions

By setting NTFS permissions, different users have different permissions, and users can access only after setting the correct access permissions.

The reason to set up NTFS permissions is simple, prevent resources from being modified or deleted without authorization.

### File System

File system is a method of organizing files on storage devices.

Here is the common file system we have nowadays:

> - Fat - Windows
> - NTFS - Windows
> - EXT - Linux

### Features of NTFS

1. Improve disk read and write performance
2. Reliability
   - Encrypted file
   - Security Permissions
3. Good disk utilization
4. Support single file more than 4G

### Edit NTFS Permissions

To start to edit NTFS permissions, the first things we need to know file inheritance. The file inheritance is a setting helpful when you are editing multiple files permissions. It can pass down the permissions you edit until there is no file to pass down, and you can also disable it to set multiples files into the different permits. [Here](https://winaero.com/blog/enable-disable-inherited-permissions-windows-10/) is guide to enable or disable the file inheritance.

| File Permission     | Permission Description                                       |
| ------------------- | ------------------------------------------------------------ |
| Full control        | Permissions to read, write, and execute, also include the special permissions |
| Modify              | Permissions to read, write, and execute                      |
| Read & execute      | Permissions to read and write                                |
| Read                | Permission to read                                           |
| Write               | Permission to write                                          |
| Special permissions | Permission to change the permission                          |

| Folder Permission    | Permission Description                                       |
| -------------------- | ------------------------------------------------------------ |
| Full control         | Permissions to read, write, and delete the file and folder, also include the special permission |
| Modify               | Permissions to read, write, and delete the file and folder   |
| Read & execute       | Permissions to download, read, and execute the file in folder |
| List folder contents | Permission to list file content include in the folder        |
| Read                 | Permission to download and read the file in folder           |
| Write                | Permission to create the file in folder                      |
| Special permissions  | Permission to change the permission                          |

### Permission Accumulation

When a user are in multiple group, the permission is accumulate.

For example, user Charly is in the IT and HR group, and the IT group has permissions to read, the HR group has permissions to write, then the final permissions Charly has is read and write.

When user permission is accumulating, then deny permission is a priority to effect.

### Permission Inheritance

File and folder ownership can be change by the administrator, [here](https://www.laptopmag.com/articles/take-ownership-folder-windows-10-using-file-explorer) is a guide of how to change it.

Permission Inheritance can also force to effect, [here](https://www.tenforums.com/tutorials/88305-enable-disable-inherited-permissions-objects-windows.html) is a guide of how to force it.

When you copy a file to the target folder, the origin file permission will then replaced by the target folder.

## File Share Server

File Share System provides file share service by the network, offer download, and upload services. (Similar to FTP Server)

### Create Share Server

To create a file share and share the folder with specific users:

1. Create a local folder on your server computer. For example, create a folder called Share on the C:\ drive.
2. Right click the folder, and then click Properties.
3. Click the Sharing tab, and then click Share.
4. Enter the name of your Windows user, and click Add.

> Make a note of the network path shown in the confirmation screen as you use this later during setup of your shared persistence storage folders. The network path will be in the following format: \server-name\Share

Things to mention, when you log in local, then you are only affected by the NTFS permissions. However, when you log in remote, then you are both affected by the NTFS permissions and share permissions, and take the intersection. Therefore, the recommended settings for share permissions are full control for everyone, then set up the detail in NTFS permissions.

### Share Server Command

All commands are practicing in CMD, and no third party applications are required.

Use the command `net share` to list all running sharing.

```
C:\Users\Eleven>net share

Share name   Resource                        Remark

-------------------------------------------------------------------------------
C$           C:\                             默认共享
IPC$                                         远程 IPC
D$           D:\                             默认共享
E$           E:\                             默认共享
F$           F:\                             默认共享
ADMIN$       C:\Windows                      远程管理
C02 - SMB    D:\Daily\C02 - SMB
The command completed successfully.
```

Use the command `net share [Share name] /del` to delete sharing.

```
C:\Windows\system32>net share C$ /del
C$ was deleted successfully.
```

Use the command `net share [Share name]=[Resource]` to create sharing.

```
C:\Windows\system32>net share C$=C:\
C$ was shared successfully.
```

### Disable Share Server (Disable Port 445)

To modify the ports and programs permitted by Windows Firewall:

1. On the computer that runs Windows Firewall, open Control Panel.
2. Right-click Windows Firewall, and then click Open.
3. Configure any required exceptions and any custom programs and ports that you require.

Although I didn't give an actual method about how to disable the port, instead I want you to try to learn firewall controls for Windows by yourself, and it's simple.