# Penetration-Testing-Week-16


**Scenario**

In this assignment, you will work as a recently hired security analyst at Altoro Mutual, a banking service.


Concerned about their online presence and the security of their website demo.testfire.net, they have hired you to evaluate the security posture of their operations.


As a holder very sensitive customer and financial data, Altoro Mutual is worried malicious actors compromising their website anf gaining this information.


You are tasked with performing website enumeration, discovery, and vulnerability detection. Because this engagement is non-invasive, you will not try to hack into their system. Rather, you will discover any potential vulnerabilities or leaks that the company should be worried about.
Please note throughout this assignment, you will target a website named "Altoro Mutual" located at demo.testfire.net. Altoro Mutual was designed by IBM, a company that designs both hardware and software for computers. Their website demo.testfire.net was specifically designed to detect web application vulnerabilities.

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


**Instructions:**

-  As you complete the steps below, please record your answers in the Submission.md file. You will submit this file as your homework deliverable.

## Google Dorking

Altoro Mutual wants to ensure that private information that is unavailable on their public website cannot be found by searching the web.
    
A brief search on Google and short exploration of Altoro Mutual's `"about"` page revealed that a great deal of valuable information can be found by an attacker or potential threat actor. 


**About Page Results**

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Exec_Management%20Page.png)



**Google Search Results**

 
![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Google%20Search.png)



-  **How can this information be helpful to an attacker?**
    - The search results of the companies about page as well as the results of the google search are a hackers dream for comprising a       list of high level executive targets to send phishing attacks to via email.


## DNS and Domain Discovery

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


## Shodan.io

By running the DNS server for demo.testfire.net that was found using Google Dorking we were able to see the following open ports and services.

![TODO](https://github.com/Tamie13/Penetration-Testing-Week-16/blob/main/Images%20and%20Documents/Open%20Ports%20%26%20Services.png)


## Recon-ng

Altoro Mutual is also concerned about cross-site scripting attacks, which can cause havoc on their website. Verify whether or not Altoro Mutual is vulnerable to XSS by completing the following:

Install the Recon module xssed.
Set the source to demo.testfire.net.
Run the module.

Is Altoro Mutual vulnerable to XSS?

Step 5: Zenmap
Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:


Use Zenmap to run a service scan against the Metasploitable machine.


Bonus: In the same command, output the results into a new text file named zenmapscan.txt.



Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan.


Once you have identified this vulnerability, answer the following questions for your client:

What is the vulnerability?
Why is it dangerous?
What are your recommendations for the client to protect their server?




© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
