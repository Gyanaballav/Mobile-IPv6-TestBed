# Testbed Setup for Mobile IPv6

## Overview
This README provides step-by-step instructions for setting up a testbed environment for Mobile IPv6 using Fedora virtual machines in Oracle VirtualBox. The testbed will consist of four virtual machines: Fedora - HA, Fedora - MN, Fedora - Router, and Fedora - CN.

## Prerequisites
- Oracle VirtualBox: Download and install Oracle VirtualBox from [Oracle's official website](https://www.virtualbox.org/wiki/Downloads).
- Fedora OS: Download the Fedora ISO image from [Fedora's official website](https://fedoraproject.org/workstation/download).

## Setup Instructions
### Virtual Machine Setup
#### Virtual Machine Creation: 
Create four virtual machines in Oracle VirtualBox and name them accordingly:
   - Fedora - HA
   - Fedora - MN
   - Fedora - Router
   - Fedora - CN

#### Network Interface Setup:
1. Set up the network interfaces of the virtual machines to use an internal network type within VirtualBox. This is done to ensure isolation and control over the network environment, which is crucial for testing purposes.

2. Name the network interface as mip-h (Home Network), mip-r (Router Network), mip-f (Foreign Network).

3. Assign the following network interface to the following Virtual Machine:
-   Fedora - HA : mip-h, mip - r (2 Interface)
-   Fedora - Router : mip-r, mip - f (2 Interface)
-   Fedora - CN : mip-f (1 Interface)
-   Fedora - MN : mip-h, mip - f (1 Interface)

#### Network Interface Configuration Commands (Only for Router and Home Agent):
1. Use the following commands to configure the network interface:
     ```
     nmcli c
     nmcli c edit $uuid
     ```
2. Replace `$uuid` with the UUID of the network connection you wish to configure. This will open up the NetworkManager editor for the selected connection, allowing you to modify its settings. Then the `nmcli>` interface will appear.

3. To save it use:
    ```
    save persistent

    ```
    in the `nmcli>` interface.

4. A file is formed at `/etc/NetworkManager/systemconnection/` named as Wired Connection 1.

5. Open the file and do the following changes:
-   **Home Agent Interface 1:**
    ```
    address1=2001:db8:aaaa:2::1/64
    method=manual
    ```
-   **Home Agent Interface 2:**
    ```
    address1=2001:db8:aaaa:2::1/64
    method=manual
    route1=2001:db8:aaaa:3::/64,2001:db8:aaaa:2::2
    ```
-   **Router Interface 1:**
    ```
    address1=2001:db8:aaaa:2::1/64
    method=manual
    route1=2001:db8:aaaa:3::/64,2001:db8:aaaa:2::2
    ```
-   **Router Interface 2:**
    ```
    address1=2001:db8:aaaa:2::1/64
    method=manual
    ```

   

## Why Internal Network Type?
Using an internal network type in VirtualBox for the testbed offers several advantages:
- **Isolation**: Internal network type ensures that the virtual machines can communicate only with each other within the internal network, keeping the test environment isolated from external networks.
- **Control**: It provides greater control over the network environment, allowing precise configuration and monitoring of network traffic between the virtual machines.
- **Security**: Since the internal network is isolated from external networks, it reduces the risk of unauthorized access or interference during testing.

## Conclusion
Following these instructions will help you set up a testbed environment for Mobile IPv6 using Fedora virtual machines in Oracle VirtualBox. Ensure to follow each step carefully to achieve the desired configuration.
