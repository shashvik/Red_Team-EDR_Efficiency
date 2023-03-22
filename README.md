# Red_Team-EDR_Efficiency
This Repository describes the methods with which you can test out your EDRs efficiency.

Describes the overall test case design, implementation, and 
execution of the CrowdStrike efficiency analysis.

Objectives: The main objective of this analysis is to identify the potential gaps in an EDR tool and 
to mitigate them.

We have divided the analysis into 3 main sections
1. Events captured by the EDR tool: What are the various logging events that are captured by 
the sensor( Windows, Linux, MacBook, Containers) they include items like below:\
    Command line activities\
    Logon, logoff activities\
    File access and modifications\
    DNS Network and port events\
    Registry changes\
    File downloads\

2. Known malicious files: Download set of known malicious hashes to identify what is blocked 
by Crowdstrike

3. Red Team Emulation: Identify various TTP mapped on to MITTRE that are correctly identified 
and prevented by the EDR tool.

Procedure:
1. We will require 1 C2 server where we will be hosting MITTRE Caldera.
2. We will have Windows, Linux, containers, and MacBook with Crowdstrike.
3. Using Caldera emulation tool, a TCP reverse proxy will be setup from the individual hosts.
4. We will run MITTRE TTP using atomic tests on these individual servers via C2.
5. Individual tests for the various event types will be conducted locally on each server and will 
be observed via events portal on the EDR tool.
6. Samples of malware will be obtained via Malwarebazaar: bazaar.abuse.ch and loaded on to 
test server and Crowdstrike findings will be observed.



Known malicious files:
This test is to identify the efficiency of CrowdStrike to identify known malicious files by only their 
hashes.
Procedure:
1. We downloaded 15 malware samples with multiple hits on virustotal onto a test windows 
server and unzipped the folder.
2. Identify if the file was auto quarantined by the EDR and wait for an alert for the same.


Red Team Emulation Tests:
The below set of tests was to emulate an entire chain of events from initial access, execution all the 
way to impact testing out the various tactics and techniques in the MITTRE framework and 
determine what all are correctly identified by Crowdstrike and prevented and what all are not.
Test Case Identify Agent Communication to C2:
1. The first set of tests involve the correct identification of a malware which will be used to 
connect back to the C2 server.
2. This was conducted in two different ways 
a. Pre Crowdstrike installation: To identify if the malware sample or beaconing activity 
is correctly identified once Crowdstrike is installed at a later stage.
b. Post Crowdstrike: To identify if the malware sample or beaconing activity is correctly 
identified by Crowdstrike during initial payload drop.

The red team emulation tests were conducted with MITRE Caldera: a red team emulation tool designed with atomic test cases built into it.
https://caldera.mitre.org/#:~:text=A%20Scalable%2C%20Automated%20Adversary%20Emulation,energy%20through%20automated%20security%20assessments.

https://github.com/mitre/caldera

https://www.mitre.org/our-impact/intellectual-property/caldera

The Emulation campaigns for windows and linux are in the yaml files.

