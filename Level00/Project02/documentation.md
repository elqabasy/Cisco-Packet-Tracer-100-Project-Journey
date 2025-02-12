**# Multi-Department Network Setup Documentation**

## **1. Overview**
This project involves designing and configuring a multi-department Local Area Network (LAN) using **Cisco Packet Tracer**. The network consists of three departments: **IT, Sales, and HR**, each having its own subnet and connected via a central router. The primary goal is to establish inter-department communication while maintaining logical separation.

## **2. Objectives**
- Design a scalable and well-structured network topology.
- Implement subnetting for logical separation.
- Configure static IP addressing and subnet masks for all devices.
- Establish inter-department communication using a central router.
- Ensure connectivity using `ping` and other network diagnostic tools.
- Document the configuration and troubleshooting steps.

## **3. Network Topology**
The network consists of:
- **One central router** for inter-subnet communication.
- **Three switches**, each representing a department (IT, Sales, HR).
- **Multiple PCs** connected to respective departmental switches.
- **Gigabit and Fast Ethernet links** to ensure high-speed data transfer.

### **Subnet Details:**
| Department  | Network Address | Subnet Mask  | Default Gateway  |
|------------|---------------|-------------|----------------|
| IT         | 192.168.1.0   | 255.255.255.0 | 192.168.1.1    |
| Sales      | 192.168.3.0   | 255.255.255.0 | 192.168.3.1    |
| HR         | 192.168.4.0   | 255.255.255.0 | 192.168.4.1    |

## **4. Configuration Steps**

### **Router Configuration:**
1. Assign IP addresses to the router interfaces.
```bash
Router(config)# interface fa0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# interface fa0/1
Router(config-if)# ip address 192.168.3.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# interface fa0/2
Router(config-if)# ip address 192.168.4.1 255.255.255.0
Router(config-if)# no shutdown
```

### **PC Configuration:**
Each PC is manually assigned an IP address within its respective subnet. For example, for a PC in the IT Department:
```bash
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

### **Switch Configuration:**
Each switch is configured with basic settings:
```bash
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.X.2 255.255.255.0
Switch(config-if)# no shutdown
```

## **5. Testing and Verification**
To ensure proper connectivity:
1. **Test PC-to-PC communication** within the same department using the `ping` command.
2. **Test inter-department communication** by pinging PCs in different subnets.
3. **Verify routing table on the router** using:
```bash
Router# show ip route
```
4. **Check switch interfaces** to confirm proper connections:
```bash
Switch# show interfaces status
```

## **6. Troubleshooting Steps**
- **Issue: No connectivity between subnets**
  - Check if the router interfaces are up (`show ip interface brief`).
  - Verify IP configurations on PCs (`ipconfig` for Windows or `ifconfig` for Linux).
  - Ensure subnet masks and gateways are correctly assigned.

- **Issue: PCs within the same department cannot communicate**
  - Check if all PCs are in the same subnet.
  - Verify switch ports are active (`show interfaces status`).
  - Test with a different cable or port.

## **7. Expected Outcomes**
- Each department's PCs should communicate seamlessly within their subnet.
- The router should successfully route traffic between departments.
- Connectivity tests (`ping`, `traceroute`) should confirm successful configuration.
- The project provides a foundational understanding of subnetting, routing, and troubleshooting.

## **8. Conclusion**
This project demonstrates the ability to design and configure a basic enterprise network using subnetting and static routing. The knowledge gained is fundamental for handling larger-scale networks and VLAN implementations in real-world scenarios.

---

**Project Completed: ✅**  
*#CPT 100-Project Journey*

