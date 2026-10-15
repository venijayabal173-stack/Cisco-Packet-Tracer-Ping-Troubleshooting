# Answer Key: Cisco Packet Tracer Ping Troubleshooting

## 1. Aim

To identify and troubleshoot network connectivity failures in Cisco Packet Tracer by analyzing physical connections, IP addressing, subnet masks, default gateways, ARP resolution, and ICMP ping results.

## 2. Software Required

- Cisco Packet Tracer
- Two PCs
- One Cisco 2960 switch
- Copper Straight-Through cables

## 3. Common Ping Errors and Troubleshooting

| Error Scenario | Typical Result | Possible Cause | Troubleshooting Action |
|---|---|---|---|
| Mismatched subnet | Request timed out or destination unreachable | PCs belong to different subnets without a router | Check IP addresses and subnet masks using `ipconfig` |
| Wrong default gateway | Remote network cannot be reached | Gateway is missing or incorrect | Verify the gateway using `ipconfig` |
| Duplicate IP address | Intermittent connectivity | Two devices use the same IP address | Assign a unique IP address to each device |
| Amber link indicators | Initial ping may fail | Switch ports are converging through STP | Wait until the links turn green |
| Wrong cable or disconnected link | Ping fails | Physical connection is incorrect | Check cables, ports, and link indicators |
| ARP resolution delay | First ping may time out | Destination MAC address is not yet resolved | Repeat ping and inspect `arp -a` |

## 4. Systematic Troubleshooting Procedure

### Step 1: Check Physical Connections

1. Open Cisco Packet Tracer.
2. Inspect the connections between the PCs and switch.
3. Confirm that the correct cables are connected to the appropriate ports.
4. Check the link indicators.

**Expected Result:** The links should become green when the connections are active.

### Step 2: Test the Loopback Address

1. Click PC0.
2. Navigate to **Desktop → Command Prompt**.
3. Enter the command:

   `ping 127.0.0.1`

4. Press Enter and observe the output.

**Expected Result:** Successful replies indicate that the local TCP/IP stack is responding.

### Step 3: Test the PC's Own IP Address

1. In PC0's Command Prompt, enter:

   `ping 192.168.10.25`

2. Press Enter.
3. Check whether replies are received.

**Expected Result:** Successful replies indicate that the PC responds to its assigned IPv4 address.

### Step 4: Verify IP Configuration

1. Open Command Prompt on PC0 and PC1.
2. Run the following command on each PC:

   `ipconfig`

3. Compare the IPv4 addresses and subnet masks.
4. Ensure that each PC has a unique IP address.

Example configuration:

| Device | IPv4 Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.10.25 | 255.255.255.0 |
| PC1 | 192.168.10.26 | 255.255.255.0 |

Both PCs belong to the network `192.168.10.0/24`.

### Step 5: Test Connectivity Between PCs

1. Open PC0 → **Desktop → Command Prompt**.
2. Enter:

   `ping 192.168.10.26`

3. Press Enter.
4. Observe the replies from PC1.

**Expected Result:** Successful replies indicate that PC0 can communicate with PC1.

If the ping fails, verify the cables, IP addresses, subnet masks, and link status.

### Step 6: Inspect the ARP Table

1. In PC0's Command Prompt, enter:

   `arp -a`

2. Press Enter.
3. Look for the IP address `192.168.10.26`.
4. Check whether a corresponding physical (MAC) address is listed.

**Expected Result:** An entry for PC1 indicates that PC0 has resolved PC1's IPv4 address to its MAC address.

### Step 7: Use Simulation Mode

1. Switch from **Realtime** to **Simulation** mode.
2. Open the event filters and enable **ARP** and **ICMP**, if available.
3. Run the ping command again.
4. Use **Capture/Forward** to inspect packet movement.
5. Examine packet details to identify where communication fails.
<img width="1312" height="1199" alt="image" src="https://github.com/user-attachments/assets/e5f76362-0687-4508-9a49-66aec08649b3" />

**Expected Result:** The simulation helps identify whether the failure occurs during ARP resolution or ICMP communication.

## 5. Testing Results

| Test | Expected Result |
|---|---|
| Physical link check | Links become green |
| Loopback ping | Successful |
| Own IP ping | Successful |
| IP configuration check | Correct and unique IP addresses |
| PC0-to-PC1 ping | Successful when configuration is correct |
| ARP table inspection | PC1's IP-to-MAC mapping appears after communication |
| Simulation mode | Packet events can be inspected |

## 6. Result

Network connectivity troubleshooting procedures were studied and applied in Cisco Packet Tracer. Physical connections, IP addressing, subnet masks, default gateways, ARP resolution, and ICMP ping tests were examined to identify common causes of network communication failures.

## 7. Conclusion

This lab demonstrates a systematic approach to network troubleshooting using the OSI model. Checking physical links first, followed by IP configuration, ARP resolution, and ping tests, helps identify and resolve common LAN connectivity problems.
## 👩‍💻 Author

**Krishnaveni**

**Course:** B.Tech – Computer Science and Business Systems

---

## ⭐ Project Status

**Completed**
