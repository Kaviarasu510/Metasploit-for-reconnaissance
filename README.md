# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find out the ip address of the attackers system

## OUTPUT:

![5 1](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/b5c203a9-7fed-49ec-82a8-bf0a167f58c7)

Invoke msfconsole:

## OUTPUT:
![5 2](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/db83856f-b3c5-416f-9481-2f3c6a7ea8ac)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![5 3](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/ce184097-fb86-493a-be88-79288657146b)

## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).

msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![5 4](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/0def96f2-3db9-430a-8f16-e060d7c195c2)

## step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.

msf > db_nmap 192.168.181.0/24

## OUTPUT:

![5 5](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/7ae30b1a-a148-4509-8aff-afffdebf12fe)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.

cd /usr/share /metasploit-framework/modules/auxiliary

kali > ls -l

## OUTPUT:

![5 6](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/f6c5e5f7-a851-4e9b-84c9-4c2ab0c3554f)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 

msf >search name:Microsoft type:exploit

![5 7](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/5e33fd3c-3904-4da5-892e-a1003d78cc5b)

The info command provides information regarding a module or platform,

![5 8](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/590f9fcd-e659-4b32-94a4-ccb5c2da42f7)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:

systemctl start postgresql

msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.

db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![5 9](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/47bc0380-728d-4d43-b63e-b0208ccf58e0)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.

search type:auxiliary mysql

![5 10](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/3de584a4-8c6b-486a-a3d2-a3c57c9a7dd3)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.

use 11

Or:

use auxiliary/scanner/mysql/mysql_version

![5 11](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/4a6169be-8122-49a1-bbe8-2ec865dc58ce)

Use the set rhosts command to set the parameter and run the module, as follows:

![5 12](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/c18da853-c48e-4d56-84b3-66c7556199cc)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![5 13](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/f52afec1-d40f-49e4-9246-8c654a0fc9a2)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:

set PASS_FILE /usr/share/wordlistss/rockyou.txt

Then, specify the IP address of the target machine with the RHOSTS command.

set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

set BLANK_PASSWORDS true

![5 14](https://github.com/Kaviarasu510/Metasploit-for-reconnaissance/assets/119392695/364009d3-4b49-49a9-bfb3-5afb0ccfba45)

## RESULT:

The Metasploit framework for reconnaissance is  examined successfully
