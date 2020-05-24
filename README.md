## Network and Security Testing Tools for SD-WAN, iBGP, and ADVPN.
    
### Here is a repo for some useful tools to test SD-WAN implementations (tested on Ubuntu 18.04 and 20.04*): 
   * **Ekiga Softphone for failover testing between Hubs and Branches.**
   * **iperf3 for Load Balance testing.**
   * **FIT for application steering testing.** 

   ### 1. Ekiga Softphone Quick Install Steps (*currently not supported on Ubuntu 20.04):
        sudo apt update
        sudo apt-get install ekiga -y
   - ##### Using RDP or console from ESXi or KVM, connect to both branch Ubuntu VMs, let's use branch1 and branch2 as an example.  
   - ##### Launch the Ekiga Softphone on both and enter the IP of branch2 on branch1. 
   - ##### Click the green phone icon to call and establish a session.  
   - ##### Go to branch2 console and accept the call if the auto answer feature is not enabled.

   ### 2. iperf3 Quick Install Steps:
        sudo apt update
        sudo apt-get install iperf3 -y
            
   - #### In order to generate 4 simultaneous streams using iperf3 between two Ubuntu VMs
                
      - ##### SSH into the Hub Ubuntu instance and issue:
            » iperf3 -s -p 6001 -i 1
      - ##### From the the Branch Ubuntu instance SSH session issue:
            » iperf3 -c <ip address of Hub> -p 6001 -u -i 1 -t 600 -b 1M -l 1360 -P 4
      - ##### This should initiate 4 streams from the Branch to Hub, and from here you can run SLA load balance and failover testing.
    
            - More information can be found here on iperf3 command syntax: [https://iperf.fr/iperf-doc.php](https://iperf.fr/iperf-doc.php).
         
   ### 3. Firewall Inspection Tester Install Steps, Go here:
   * [Firewall Internet Tester](https://github.com/gahlberg/fit.git) - FIT Author: Alex Harvey
