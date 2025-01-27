# Starting a Nexus Program

Nexus Repository Manager needs to be hosted on a machine, which can either be a virtual machine (VM) or a locally hosted system. To set up Nexus, a properly configured machine is required, along with the correct Sonatype program installed or executed on it. In this guide, I will demonstrate how to set up Nexus on a locally hosted machine using Vagrant.

---

## Requirements
1. **A Virtual Machine**:
   - Hosted either on the cloud or locally.
2. **System Specifications**:
   - The machine should have at least **4GB of RAM**.
3. **Nexus Program**:
   - The official Sonatype Nexus Repository Manager.

---

## Steps to Set Up Nexus

### 1. Create a Dedicated User for Nexus
It is recommended to create a separate user for Nexus to configure granular access control. This ensures better management and security.

- Delete any existing user with the same name, if applicable:
  ```bash
  sudo userdel -r username
