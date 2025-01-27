# FortiGate Firewall – High Availability (Active-Active) LAB

## Objective

This lab provides practical experience for network administrators and engineers in deploying and managing high-availability networks using FortiGate firewalls simulating, configuring, and testing an environment where multiple FortiGate firewalls are set up in an Active-Active HA mode. The goal is to understand how the FortiGate devices work together to enhance network reliability, performance, and redundancy.

### Skills Learned

- FortiGate Firewall Administration
- High Availability (HA) Configuration
- Load Balancing and Traffic Optimization
- Network Redundancy and Reliability

### Tools Used

- FortiGate VM: A virtual appliance used in virtualized environments, such as VMware or Hyper-V
- FortiOS Web Interface (GUI)
- FortiOS Command Line Interface (CLI)
- FortiView Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- FTP/HTTP/HTTPS Servers: For uploading firmware or serving configurations during the lab.
- Traffic Generation Tools
- GNS3 for simulated network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
![image](https://github.com/user-attachments/assets/34008658-3107-4640-b70d-9a794ff8acb8)
 

Before Enabling HA we should review Those Recommendations:

- we need to have the same FortiOS version (Firmware) in the units.

- we need to have the same hardware Model. 

- the interfaces should not be on DHCP.

 
* On FortiGate we have two modes of HA 

Active-Active (a-a): in a-a mode the traffic start load balancing between the cluster members when we have a policy with a security profile enabled or when our unite reach the maximum sessions supported.

Active-Passive (a-p): in a-p mode the traffic get handled by one member of the cluster while the other member stay on standby waiting for the active unite to fall.
![image](https://github.com/user-attachments/assets/8c28dda5-6342-4b2c-8460-b836bf7c4356)


## STEPS


# Changing the cluster member role
in order to make a member role as primary you need to:

1)	Use this following command from CLI:
![image](https://github.com/user-attachments/assets/4d750af4-b839-4b56-bc7b-3a84d09717ac)
 


2)	2) Disconnect and Reconnect cable from the interface which is being monitored on the primary.

# HA Configuration
![image](https://github.com/user-attachments/assets/bccd7d55-a996-4d1f-aeb3-9b16fcbd7e71)
![image](https://github.com/user-attachments/assets/3536f9b1-a3f5-4250-b34e-d59a26fcad17)
![image](https://github.com/user-attachments/assets/7a7a7672-d411-40b8-b1a4-898f685fb1ac)


# Get HA Status
![image](https://github.com/user-attachments/assets/1c1e5595-aa32-474c-ae49-69f7ce66d0ad)
![image](https://github.com/user-attachments/assets/9141e7e5-761c-42b1-af6c-b0cc14256c1a)
 
 
We will see that our FortiGate cluster members are synchronized now that mean that the

configuration of our FortiGate 1 which is the primary replicated to our FortiGate 2.
![image](https://github.com/user-attachments/assets/91c7a3e2-1ffe-451d-8f52-b168a9b0e7e5)
![image](https://github.com/user-attachments/assets/687a7df9-be3a-44b0-aadc-2b6ce97b8319)

 
## Access from Primary unit to the secondary ##

# Set MGMT IP To HA Clusters
![image](https://github.com/user-attachments/assets/f7cd948a-6165-46a2-b073-9f7a837ee7e1)


* We have the same IP of our primary FortiGate, so we can only now see our primary.

 


# Please Note That in a-a mode the replication of the configuration is from the two members (Primary to Secondary and Secondary to Primary)
