# Red_Team-EDR_Efficiency
This Repository describes the methods with which you can test out your EDRs efficiency.

Describes the overall test case design, implementation, and 
execution of the CrowdStrike efficiency analysis.

Objectives: The main objective of this analysis is to identify the potential gaps in an EDR tool and 
to mitigate them.

We have divided the analysis into 3 main sections
1. Events captured by the EDR tool: What are the various logging events that are captured by 
the sensor( Windows, Linux, MacBook, Containers) they include items like below:
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
