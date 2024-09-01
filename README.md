# Router Configuration for Secure Communication
Project Overview

This project involves configuring routers to ensure secure communication between PCs on different LANs. Key security measures include enforcing password policies, implementing user authentication, configuring SSH, enabling AAA authentication, and applying encryption.
Key Configurations
1. Password and Encryption

    Minimum Password Length: Enforced a minimum password length of 10 characters for all passwords on the routers.
    Privileged EXEC Password: Assigned and encrypted with a secure password (cisco12345).
    Password Encryption: Enabled encryption for all passwords using the service password-encryption command.

2. User Authentication

    Local User Accounts: Added users with privilege levels:
        Router R1: admin01 with privilege level 15, password admin01pass.
        Router R2: admin02 with privilege level 15, password admin02pass.
    AAA Configuration: Enabled AAA (Authentication, Authorization, and Accounting) with local database authentication and case-sensitive username authentication. Implemented enhanced login settings to block access for 3 minutes after 4 failed login attempts within 2 minutes.

3. SSH Configuration

    SSH for Secure Remote Access: Configured SSH on routers with RSA key generation (1024 bits) for encryption, set SSH timeouts to 90 seconds, and limited authentication retries to 2.
    VTY Line Configuration: Restricted access to SSH only for VTY lines with the transport input ssh command.

4. Routing and ACL Configuration

    IP Addressing:
        Router R1: IP address 172.16.1.1, Loopback interfaces 172.16.4.1 and 172.17.5.1.
        Router R3: IP address 172.16.1.2, Loopback interfaces 10.10.10.3, 10.20.20.3, and 10.30.30.3.
    Routing: Configured static routes for default routing.
        Router R1: ip route 0.0.0.0 0.0.0.0 172.16.1.2
        Router R3: ip route 0.0.0.0 0.0.0.0 172.16.1.1
    Access Control Lists (ACLs):
        Telnet ACL: Allowed Telnet connections from Router R1's Loopback10 to Router R3's Loopback20 and Loopback30.
        Ping ACL: Allowed ping requests from Router R1's Loopback20 to Router R3's Loopback10.

Testing

    SSH Access: Verified SSH connectivity from PC0 to Router R1 and PC1 to Router R2.
    ACL Testing: Tested Telnet and ping ACL configurations to ensure correct access control.

Summary

The project ensures secure communication between PCs on different LANs by applying advanced security measures on routers. These measures include enforcing strong password policies, encrypting passwords, implementing user authentication, configuring SSH with enhanced security settings, and applying proper routing and ACL configurations.
