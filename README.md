This repository documents the completion of Task 4 for the cybersecurity internship, which involved configuring the Windows Defender Firewall.
## Deliverables

This submission includes this README.md file and the required screenshots demonstrating the applied firewall rules.

*Screenshot 1: New Inbound Rule for Port 23*
<img width="1283" height="975" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/9e8c408f-0837-4060-b37a-2b9312076ba0" />


*Screenshot 2: PowerShell Test Result*
<img width="1479" height="765" alt="Screenshot (12)" src="https://github.com/user-attachments/assets/7fafcaeb-a65f-45d7-b509-dad08f30b016" />

## Documentation of Task Implementation (8 Steps)

The following sections detail the 8 steps outlined in the task guide.

### 1. Open Firewall Configuration Tool

To begin, I accessed the advanced firewall configuration tool.
* *Action:* I used the Windows Start Menu to search for and open *"Windows Defender Firewall with Advanced Security"*.
* *Reason:* This tool provides granular control over firewall rules, unlike the basic "Windows Defender Firewall" panel. It allows for specifying rules based on ports, protocols, and programs for different network profiles.

### 2. List Current Firewall Rules

Once in the tool, I inspected the existing configuration.
* *Action:* I clicked on the *"Inbound Rules"* tab in the left-hand pane.
* *Observation:* This displayed a comprehensive list of all rules that control traffic coming into the computer from the network. Each rule has properties like its name, a "Block" or "Allow" action, the program, and the ports it applies to.
* 
### 3. Add a Rule to Block Inbound Traffic on Port 23

The core of the task was to create a new rule to block Telnet traffic.
* *Action:* I right-clicked on "Inbound Rules" and selected "New Rule...", which launched a configuration wizard. I proceeded through the following 5 steps:

    1.  *Rule Type:* I selected *Port*.This was chosen because the task required blocking a specific port (23), rather than an entire application (which would be 'Program').
    <img width="911" height="747" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/2cf45418-4b11-4c62-868d-91db0d5ad302" />

    2.  *Protocol and Ports:* I specified *TCP* and, in "Specific local ports," I entered *23*. [span_6](start_span)Telnet is a protocol that uses TCP (Transmission Control Protocol) for its communication, and it          traditionally operates on port 23.
    <img width="903" height="770" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/28b98270-7681-47c8-bd5d-4d8d07363b18" />

    3.  *Action:* I selected *Block the connection*. This instructs the firewall to drop any inbound connection attempt that matches the criteria (TCP on port 23), effectively preventing access.
    <img width="1257" height="762" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/7eb2fc99-1b20-43ca-9b99-0d528f5ffc85" />

    4.  *Profile:* I left all three profiles (*Domain, **Private, **Public*) checked. This is crucial as it ensures the block is active regardless of the network type the computer is connected to (e.g., corporate          domain, home private network, or public Wi-Fi).
    <img width="1260" height="759" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/a2c1ca5e-9e11-4226-8784-b6a835d150da" />

    5.  *Name:* I named the rule Task 4 - Block Telnet (Port 23) and added a description. A clear name is essential for future auditing and management.
  
### 5. Add Rule to Allow SSH (Linux)

This step was noted as being for Linux users.
 *Action:* As I am on a Windows machine, this step was not applicable. The Windows equivalent for remote access is typically RDP (Port 3389), which already has its own set of rules.

### 6. Remove the Test Block Rule

To complete the task, I restored the system to its original state.
* *Action:* I went back to the "Windows Defender Firewall with Advanced Security" window, located the Task 4 - Block Telnet (Port 23) rule in the "Inbound Rules" list, right-clicked it, and selected *"Delete"*.
* *Reason:* Leaving unnecessary block rules (especially for testing) can cause future connectivity issues, so cleanup is good practice.
### 7. Document Commands or GUI Steps Used

This README.md file serves as the official documentation for the task. It records all GUI steps taken to create and remove the rule, as well as the specific PowerShell command used for testing.

### 8. Summarize How Firewall Filters Traffic

This task demonstrated how a firewall filters network traffic.
*Summary:* A firewall acts as a digital gatekeeper for a computer or network. It constantly monitors all *inbound* (incoming) and *outbound* (outgoing) network traffic. It inspects each piece of data (packet) and compares it against a set of security rules.
* Based on these rules—which can define specific *ports* (like port 23), *protocols* (like TCP), or *applications—the firewall makes a simple decision: **Allow* the traffic to pass, or *Block* it.
* Windows Firewall is a *stateful* firewall, which means it not only checks rules for individual packets but also tracks the state of active connections, offering more robust security than a stateless firewall (which treats every packet in isolation).By blocking unused ports like 23 (Telnet), which is insecure, the firewall significantly reduces the "attack surface" available to hackers.
