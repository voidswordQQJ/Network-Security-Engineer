# Network Security Engineer

This note is an English version of [【Qianfeng Education】Network Security Engineer](https://www.bilibili.com/video/BV1i7411G7vm), and it will contain all information need and review from the video.

1. (1-122P): network foundation, switching routing technology, advanced network technology.

2. (122-158P): Linux security operation and maintenance, comprehensive project combat.

3. (158-200P): front-end, database, back-end code security, python security application development, code audit.

4. (200P--): Introduction, intelligence collection, weak passwords, common vulnerabilities attack and defense, penetration testing, privilege escalation, and post penetration.

## 1. Getting Started

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

### 1.1 Intro to IP Address

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

### 1.2 Base Conversion

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

### 1.3 Basic Dos Command

DOS, Disk Operate System, is a very old system we still using right now, for example CMD is a DOS. In this lesson, we are learning some simples DOS commands.

> Press Win + R to opened CMD in Windows

To locate drive, and access to a folder, use command `[Drive Letter]:` and `cd`.

> C:\Users\Eleven\Documents>D:
>
> D:\>cd D:\Study\A01 - Notebook\Testing
>
> D:\Study\A01 - Notebook\Testing>

To create a file or folder, use command `mkdir` and `copy con [filename].txt` (After typing the content, use `CTRL + Z` and press `Enter` to save)

> D:\Study\A01 - Notebook\Testing>mkdir Example
>
> D:\Study\A01 - Notebook\Testing>cd Example
>
> D:\Study\A01 - Notebook\Testing\Example>copy con example.txt
> Here is Henry!
> Here is Charlie!^Z
> Copy         1 File
>
> D:\Study\A01 - Notebook\Testing\Example>

To view all content in a folder, use command `dir`.

In addition, use command `dir /a` to view all file include system file.

> D:\Study\A01 - Notebook\Testing>cd Example
>
> D:\Study\A01 - Notebook\Testing\Example>dir
>  Volume in drive D is Database
>  Volume Serial Number is 7066-53F7
>
>  Directory of D:\Study\A01 - Notebook\Testing\Example
>
> 2020/09/15  09:45    \<DIR>          .
> 2020/09/15  09:45    \<DIR>          ..
> 2020/09/15  09:46                32 example.txt
>                1 File(s)             32 bytes
>                2 Dir(s)  198,072,438,784 bytes free
>
> D:\Study\A01 - Notebook\Testing\Example>

To view the content in a file, use command `type [filename].txt` (Press `TAB` to auto fill filename)

> D:\Study\A01 - Notebook\Testing\Example>type example.txt
> Here is Henry!
> Here is Charlie!
> D:\Study\A01 - Notebook\Testing\Example>

To delete file, use command `del`.

- `del [filename].[suffix]` - deleted file
- `del *.[suffix]` - deleted all file with same suffix
- `del \*.\*` - deleted all file
- `del \*.\* /s /q` - forced to deleted all file

> D:\Study\A01 - Notebook\Testing\Example>del example.txt
>
> D:\Study\A01 - Notebook\Testing\Example>dir
>  Volume in drive D is Database
>  Volume Serial Number is 7066-53F7
>
>  Directory of D:\Study\A01 - Notebook\Testing\Example
>
> 2020/09/15  10:15    \<DIR>          .
> 2020/09/15  10:15    \<DIR>          ..
>                0 File(s)              0 bytes
>                2 Dir(s)  198,072,438,784 bytes free
>
> D:\Study\A01 - Notebook\Testing\Example>

To contribute the property to file or folder, use command `attrib`.

- `attrib +h [filename]` - Hidden file
- `attrib +h +s +a [filename]` - Hidden file and turn it to a system file
  - h represent hidden
  - s represent system file
  - a represent only read

Create Empty file with custom data size, use command `fsutil file createnew c:\system.ini 409600000 `.

> D:\Study\A01 - Notebook\Testing\Example>fsutil file createnew example.txt 20480000
> File D:\Study\A01 - Notebook\Testing\Example\example.txt is created
>
> D:\Study\A01 - Notebook\Testing\Example>dir
>  Volume in drive D is Database
>  Volume Serial Number is 7066-53F7
>
>  Directory of D:\Study\A01 - Notebook\Testing\Example
>
> 2020/09/15  10:43    \<DIR>          .
> 2020/09/15  10:43    \<DIR>          ..
> 2020/09/15  10:43        20,480,000 example.txt
>                1 File(s)     20,480,000 bytes
>                2 Dir(s)  198,051,954,688 bytes free
>
> D:\Study\A01 - Notebook\Testing\Example>

To copy or move file from origin directory to target directory, use command `copy ` and `move`.

> D:\Study\A01 - Notebook\Testing\Example>copy example.txt ..\
>         1 file(s) copied.
>
> D:\Study\A01 - Notebook\Testing\Example>cd ..
>
> D:\Study\A01 - Notebook\Testing>dir
>  Volume in drive D is Database
>  Volume Serial Number is 7066-53F7
>
>  Directory of D:\Study\A01 - Notebook\Testing
>
> 2020/09/15  11:49    \<DIR>          .
> 2020/09/15  11:49    \<DIR>          ..
> 2020/09/15  10:43    \<DIR>          Example
> 2020/09/15  10:43        20,480,000 example.txt
>                1 File(s)     20,480,000 bytes
>                3 Dir(s)  198,031,593,472 bytes free
>
> D:\Study\A01 - Notebook\Testing>

### 1.4 User and Group Management

#### 1.4.1 User Manage

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
>2. guest - low permissions
> 
>System Account
> 
>1. system - very high permissions
> 2. local services - low permissions
>3. network services - low permissions

Every user has there owned a config file (Home Directory), it automatically generates when the user first logs in to the system.

> In windows 7 and 10, it locate at C:\Users\

User manage commands:

> net user [username] - view user information
>
> net user [username] [password] - changed user password
>
> net user [username] [password] /add - add a new user

#### 1.4.2 Group Manage

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

### 1.5 Remote Connect

#### 1.5.1 Microsoft Terminal Services

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

#### 1.5.2 Telnet Services

In Windows 2008 or later, you can configure your PC for telnet access with a few easy steps.

> 1. Start Server Manager. Click Start, right-click Computer, and then click Manage.
> 2. If the User Account Control dialog box appears, confirm that the action it displays is what you want, and then click Continue.
> 3. In the Features Summary section, click Add features.
> 4. On the Select Features page, select Telnet Server. You can also select Telnet Client if you want.
> 5. Click Next, and then on the Confirm Installation Options page, click Install.
> 6. On the Installation Results page, click Close.
> 7. Close Server Manager.

To connect to a Telnet Server, by press `Win + R` and enter `cmd` in the test bar, then use command `telnet [hostname]`.

#### 1.5.3 SSH Services

Right now, we are not using SSH for learning, but it will include in the future when we talk about Linux Security, so the only thing to reminder now is the SSH port is 22.

### 1.6 NTFS Security Permissions

