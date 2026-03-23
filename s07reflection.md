#Session 07 Reflection

Why Lists Beat Variables at Scale

Using a List to manage 100 IP addresses is fundamentally superior to using 100 separate variables because it enables the creation of an "efficiency engine" to automate repetitive network checks across multiple hosts
. As outlined in The Automation Forge: Python Network Auditing Session (2026), the objective is to build a tool that programmatically audits targets rather than performing manual checks
. If an analyst used separate variables, they would be forced to write the socket connection logic—specifically the s.connect_ex((ip, port)) function—100 individual times, which significantly increases the risk of SyntaxErrors


By using a single List, the analyst can utilize a for loop to iterate through every target found in the target_intel.txt file
. This approach ensures the code follows the "Law of White Space," defining the logical "room" for the scan only once and allowing the socket library to verify if a port is open or closed based on a return of 0
. This streamlined method utilizes data types as evidence (Strings for IPs and Integers for Ports) to maintain a secure and scalable auditing process


References
Python Security Scripting and Port Auditing Lab. (2026). Student Instructions.
The Automation Forge: Python Network Auditing Session. (2026). Mission Parameters.
