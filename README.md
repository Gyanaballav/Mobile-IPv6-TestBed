# Testbed Setup for Mobile IPv6

## Overview
This README provides step-by-step instructions for setting up a testbed environment for Mobile IPv6 using Fedora virtual machines in Oracle VirtualBox. The testbed will consist of four virtual machines: Fedora - HA, Fedora - MN, Fedora - Router, and Fedora - CN.

## Prerequisites
- Oracle VirtualBox: Download and install Oracle VirtualBox from [Oracle's official website](https://www.virtualbox.org/).
- Fedora OS: Download the Fedora ISO image from [Fedora's official website](https://getfedora.org/).

## Setup Instructions
### Virtual Machine Setup
#### Virtual Machine Creation: 
Create four virtual machines in Oracle VirtualBox and name them accordingly:
   - Fedora - HA
   - Fedora - MN
   - Fedora - Router
   - Fedora - CN

#### Network Configuration:
   - Set up the network interfaces of the virtual machines to use an internal network type within VirtualBox. This is done to ensure isolation and control over the network environment, which is crucial for testing purposes.

   - Name the network interface as mip-h (Home Network), mip-r (Router Network), mip-f (Foreign Network).

   - Fedora - HA : mip-h, mip - r (2 Interface)
   - Fedora - Router : mip-r, mip - f (2 Interface)
   - Fedora - CN : mip-f (1 Interface)
   - Fedora - MN : mip-h, mip - f (1 Interface)

#### Network Interface Configuration Commands:
   - Use the following commands to configure the network interface:
     ```
     nmcli c
     nmcli c edit $uuid
     ```
     Replace `$uuid` with the UUID of the network connection you wish to configure. This will open up the NetworkManager editor for the selected connection, allowing you to modify its settings.

    ```
     nmcli c
     nmcli c edit $uuid
     ```

## Why Internal Network Type?
Using an internal network type in VirtualBox for the testbed offers several advantages:
- **Isolation**: Internal network type ensures that the virtual machines can communicate only with each other within the internal network, keeping the test environment isolated from external networks.
- **Control**: It provides greater control over the network environment, allowing precise configuration and monitoring of network traffic between the virtual machines.
- **Security**: Since the internal network is isolated from external networks, it reduces the risk of unauthorized access or interference during testing.

## Conclusion
Following these instructions will help you set up a testbed environment for Mobile IPv6 using Fedora virtual machines in Oracle VirtualBox. Ensure to follow each step carefully to achieve the desired configuration.
