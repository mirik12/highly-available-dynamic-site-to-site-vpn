To save time later in the DEMO we should populate this before configuring the ONPREM environment.
There are two VPN connections ... one between AWS and ONPREM ROUTER1 and one between AWS and ONPREM ROUTER2
For each of those there are two tunnels ... AWS Endpoint A -> ONPREMROUTER
and AWS endpointB -> ONPREMROUTER

Those are the details we will populate

SHARED VALUES
ROUTER1_PRIVATE_IP = 192.168.12.127
ROUTER2_PRIVATE_IP = 192.168.12.94
ONPREM BGP ASN = 65016
AWS BGP ASN = 64512

CONNECTION1 - AWS => ON PREM ROUTER1
CONN1_TUNNEL1_PresharedKey = JBB1.ENZny3TMXyilAZfc1uzhc47leVw
CONN1_TUNNEL1_ONPREM_OUTSIDE_IP = 44.209.44.14
CONN1_TUNNEL1_AWS_OUTSIDE_IP = 3.33.253.137
CONN1_TUNNEL1_ONPREM_INSIDE_IP = 169.254.30.2/30
CONN1_TUNNEL1_AWS_INSIDE_IP = 169.254.30.1/30
CONN1_TUNNEL1_AWS_BGP_IP = 169.254.30.1

CONN1_TUNNEL2_PresharedKey = P4qmdJYP55dzEI6x636pDGsTWE9juXgd
CONN1_TUNNEL2_ONPREM_OUTSIDE_IP = 44.209.44.14
CONN1_TUNNEL2_AWS_OUTSIDE_IP = 13.248.155.75
CONN1_TUNNEL2_ONPREM_INSIDE_IP = 169.254.204.158/30
CONN1_TUNNEL2_AWS_INSIDE_IP = 169.254.204.157/30
CONN1_TUNNEL2_AWS_BGP_IP = 169.254.204.157

CONNECTION2 - AWS => ON PREM ROUTER2
CONN2_TUNNEL1_PresharedKey = jgbIVy.km7_oz67uVvQ2.iomMrPzyflC
CONN2_TUNNEL1_ONPREM_OUTSIDE_IP = 3.221.11.6
CONN2_TUNNEL1_AWS_OUTSIDE_IP = 75.2.112.0
CONN2_TUNNEL1_ONPREM_INSIDE_IP = 169.254.177.118/30
CONN2_TUNNEL1_AWS_INSIDE_IP = 169.254.177.117/30
CONN2_TUNNEL1_AWS_BGP_IP = 169.254.177.117

CONN2_TUNNEL2_PresharedKey = 6_DUORiOvHk4e6s.u8m69lDT8QM8oc4b
CONN2_TUNNEL2_ONPREM_OUTSIDE_IP = 3.221.11.6
CONN2_TUNNEL2_AWS_OUTSIDE_IP = 99.83.254.62
CONN2_TUNNEL2_ONPREM_INSIDE_IP = 169.254.43.154/30
CONN2_TUNNEL2_AWS_INSIDE_IP = 169.254.43.153/30
CONN2_TUNNEL2_AWS_BGP_IP = 169.254.43.153

INSTRUCTIONS ON GETTING THE VALUES
We will be locating values for a specific connection CONN1 or CONN2 and a specific tunnel .. TUNNEL1 or TUNNEL2

For anything starting with CONN1 .. Look in the CONNECTION1CONFIG.TXT file
For anything starting with CONN2 .. Look in the CONNECTION2CONFIG.TXT file
In each of the above files, for anything showing TUNNEL1 fine the section IPSec Tunnel #1 in the above files (THE TOP HALF)
In each of the above files, for anything showing TUNNEL2 fine the section IPSec Tunnel #2 in the above files (THE BOTTOM HALF)

For ROUTER1_PRIVATE_IP its the 192.168.12.SOMETHING Private IPv4 Address for ROUTER1 - Check the Outputs of the ONPREM CFN Stack for Private IP of Router1
For ROUTER2_PRIVATE_IP its the 192.168.12.SOMETHING Private IPv4 Address for ROUTER2 - Check the Outputs of the ONPREM CFN Stack for Private IP of Router2

For CONN1_TUNNEL1_PresharedKey open CONNECTION1CONFIG.TXT, Locate IPSec Tunnel #1, Locate - Pre-Shared Key Your key is there
For CONN1_TUNNEL2_PresharedKey open CONNECTION1CONFIG.TXT, Locate IPSec Tunnel #2, Locate - Pre-Shared Key Your key is there
For CONN2_TUNNEL1_PresharedKey open CONNECTION2CONFIG.TXT, Locate IPSec Tunnel #1, Locate - Pre-Shared Key Your key is there
For CONN2_TUNNEL2_PresharedKey open CONNECTION2CONFIG.TXT, Locate IPSec Tunnel #2, Locate - Pre-Shared Key Your key is there

For CONN1_TUNNEL1_ONPREM_OUTSIDE_IP its the PublicIPv4 Address of ROUTER1
CONN1_TUNNEL2_ONPREM_OUTSIDE_IP its the PublicIPv4 Address of ROUTER1
CONN2_TUNNEL1_ONPREM_OUTSIDE_IP its the PublicIPv4 Address of ROUTER2
CONN2_TUNNEL2_ONPREM_OUTSIDE_IP its the PublicIPv4 Address of ROUTER2

For CONN1_TUNNEL1_AWS_OUTSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Outside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN1_TUNNEL2_AWS_OUTSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Outside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN2_TUNNEL1_AWS_OUTSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Outside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN2_TUNNEL2_AWS_OUTSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Outside IP Addresses:, locate - Virtual Private Gateway the value is there

For CONN1_TUNNEL1_ONPREM_INSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Customer Gateway the value is there
For CONN1_TUNNEL2_ONPREM_INSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Customer Gateway the value is there
For CONN2_TUNNEL1_ONPREM_INSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Customer Gateway the value is there
For CONN2_TUNNEL2_ONPREM_INSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Customer Gateway the value is there

For CONN1_TUNNEL1_AWS_INSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN1_TUNNEL2_AWS_INSIDE_IP open CONNECTION1CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN2_TUNNEL1_AWS_INSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #1, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Virtual Private Gateway the value is there
For CONN2_TUNNEL2_AWS_INSIDE_IP open CONNECTION2CONFIG.TXT, locate IPSec Tunnel #2, locate #3: Tunnel Interface Configuration, locate Inside IP Addresses:, locate - Virtual Private Gateway the value is there

For CONN1_TUNNEL1_AWS_BGP_IP the value is the same as CONN1_TUNNEL1_AWS_INSIDE_IP (without the /30)
For CONN1_TUNNEL2_AWS_BGP_IP the value is the same as CONN1_TUNNEL2_AWS_INSIDE_IP (without the /30)
For CONN2_TUNNEL1_AWS_BGP_IP the value is the same as CONN2_TUNNEL1_AWS_INSIDE_IP (without the /30)
For CONN2_TUNNEL2_AWS_BGP_IP the value is the same as CONN2_TUNNEL2_AWS_INSIDE_IP (without the /30)