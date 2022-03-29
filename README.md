# Penetration-Testing-Week-16

Unit 16 HW Submission File: Penetration Testing

**Scenario**

-  In this assignment, you will work as a recently hired security analyst at Altoro Mutual, a banking service.
-  Concerned about their online presence and the security of their website demo.testfire.net, they have hired you to evaluate the        security posture of their operations.
-  As a holder very sensitive customer and financial data, Altoro Mutual is worried malicious actors compromising their website anf      gaining this information.
-  You are tasked with performing website enumeration, discovery, and vulnerability detection. Because this engagement is non-          invasive, you will not try to hack into their system. Rather, you will discover any potential vulnerabilities or leaks that the      company should be worried about.
-  Please note throughout this assignment, you will target a website named "Altoro Mutual" located at demo.testfire.net. Altoro          Mutual was designed by IBM, a company that designs both hardware and software for computers. Their website demo.testfire.net was      specifically designed to detect web application vulnerabilities.


**Topics Covered in This Assignment**

-  Website enumeration
-  Google Dorking
-  OSINT Recon
-  Shodan
-  Recon-NG
-  Installing modules
-  Zenmap
-  nmap's scripting engine


-  Lab Environment
   - You will use Azure online VMs to complete the homework.
     To start the labs, log into Azure and launch the Penetration Security machine.
     Once you are connected to that machine, launch the Pen Testing Hyper-V machine 
     and start it to boot up Kali Linux.


**Kali credentials:**

-  `Username: root`

-  `Password: toor`


**Metasploitable credentials:**

-  `Username: msfadmin`

-  `Password: msfadmin`


Note: Your Kali machine will act as the attacker machine, and the Metasploitable machine will act as the victims machine.
Please note throughout this assignment, you will target a website named "Altoro Mutual" located at demo.testfire.net. Altoro Mutual was designed by IBM, a company that designs both hardware and software for computers. Their website demo.testfire.net was specifically designed to detect web application vulnerabilities.


## Test 1: Google Dorking

Altoro Mutual wants to ensure that private information that is unavailable on their public website cannot be found by searching the web.
    
A brief search on Google and short exploration of Altoro Mutual's `"about"` page revealed that a great deal of valuable information is not private and can be found by an attacker or potential threat actor easily.


**About Page Results**

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Exec_Management%20Page.png)



**Google Search Results**

 
![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Google%20Search.png)



-  **How can this information be helpful to an attacker?**
    - A short exploration of the companies about page as well as a brief search of google yielded a wealth of information that could       be used by a hackers or potential threat actor to target high level executive with phishing attacks via email.


## Step 2: DNS and Domain Discovery

The reconnaissance phase of a penetration test is possibly the most important phase of the engagement. Without a clear understanding of your client's assets, vulnerabilities can go unnoticed and later exploited.


Using `centralops.net` the following information was revealed by running demo.testfire.net in `Domain Dossier.`


-  The company location:
    - `Sunnyvale, CA 94085 - USA`


-  Their NetRange IP address:
    - `65.61.137.64 - 65.61.137.127`

-  Who they use to store their infrastructure:

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Server%20Host.png)

-  The IP address of the DNS server:
    - `65.61.137.117`


## Test 3: Shodan.io

-  What open ports and running services did Shodan find?
    - Port 80 - Apache Tomcat/Coyote - HTTP
    - Port 443 - Apache Tomcat/Coyote - HTTPS
    - Port 8080 - Apache Tomcat/Coyote - HTTP

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Open%20Ports%20%26%20Services.png)


## Test 4: Recon-ng

*Altoro Mutual is also concerned about cross-site scripting attacks, which can cause havoc on their website. Verify whether or not Altoro Mutual is vulnerable to XSS by completing the following:*

Install the Recon module `xssed`
Set the source to `demo.testfire.net`
Run the module.

*`Is Altoro Mutual vulnerable to XSS?`*

**Yes, see image below.**

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Recon-ng%20Vulnerability.png)


## Test 5: Zenmap

-  Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:
-  Use Zenmap to run a service scan against the Metasploitable machine.
-  Bonus: In the same command, output the results into a new text file named zenmapscan.txt.
-  Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan.
-  Once you have identified this vulnerability, answer the following questions for your client:

**Zenmap Scan**

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/zenmap%20scan%20one.png)


**Vulnerability Level**

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Vulnerability%20Info.png)


**What is the vulnerability?**
    
`CVE-2007-2447`

**Why is it dangerous?**

"The MS-RPC functionality in smbd in Samba 3.0.0 through 3.0.25rc3 allows remote attackers to execute arbitrary commands via shell metacharacters involving the (1) SamrChangePassword function, when the "username map script" smb.conf option is enabled, and allows remote authenticated users to execute commands via shell metacharacters involving other MS-RPC functions in the (2) remote printer and (3) file share management."
 
    
**What are your recommendations for the client to protect their server?**

Vulnerabilities on both SMB Ports 139/445 creates a severe risk combination to the transport layer.  If these vulnerabilities are found on a clients server they should be mitigated immediately. Recommendations made by the `National Cyber Awareness System` for
[SMB Security Best Practices](https://www.cisa.gov/uscert/ncas/current-activity/2017/01/16/SMB-Security-Best-Practices) to mitigate risk include:

-  disabling SMBv1 and
-  blocking all versions of SMB at the network boundary by blocking TCP port 445 with related protocols on UDP ports      137-138 and TCP port 139, for all boundary devices.




© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
