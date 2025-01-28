# Hosting Nexus on a Linux Machine

## Overview
Nexus can be hosted on a machine, which can either be a virtual machine or a locally hosted machine. To successfully host Nexus, you need a properly configured machine and the appropriate Sonatype program installed and running.

This guide demonstrates hosting Nexus on a locally hosted machine using Vagrant.

---

## Prerequisites

1. **Machine Requirements:**
   - A virtual machine hosted locally or on the cloud.
   - Minimum 4GB RAM.

2. **Nexus Program:**
   - The Nexus software must be downloaded and installed.

---

## Step 1: Create a User for Nexus

It is advisable to create a dedicated user for running Nexus to ensure granular access control.

1. **Create a user named `nexus`:**
   ```bash
   sudo adduser nexus
   ```

   This command creates a new user named `nexus`.

2. **Grant `sudo` privileges to the `nexus` user:**
   ```bash
   sudo usermod -aG sudo nexus
   ```

   This command adds the `nexus` user to the `sudo` group, allowing it to execute commands requiring root privileges using the `sudo` command.

---

## Step 2: Download Nexus Program

Download the Nexus program from the official Sonatype website:

```bash
wget https://download.sonatype.com/nexus/3/nexus-3.52.0-01-unix.tar.gz 
```

---

## Step 3: Extract the Nexus Program

Extract the downloaded archive:

```bash
tar -xzvf latest-unix.tar.gz
```

The extraction will produce two directories:
- `nexus-3.52.0-01`
- `sonatype-work`

---

## Step 4: Change Ownership of Extracted Files

Change the ownership of the extracted files to the `nexus` user:

```bash
sudo chown -R nexus:nexus nexus-3.52.0-01
sudo chown -R nexus:nexus sonatype-work
```

Replace `<version>` with the specific version of the Nexus software.

---

## Step 5: Configure Nexus

Navigate to the `bin` directory inside the extracted Nexus folder:

```bash
cd nexus-<version>/bin
```

Edit the `nexus.rc` file using a text editor:

```bash
sudo nano nexus.rc
```

Modify the file to include the following line:

```bash
run_as_user="nexus"
```

Save and exit the file.

---

## Step 6: Start Nexus

Start Nexus from the `bin` directory:

```bash
./nexus start
```

To verify that Nexus is running, execute the following command:

```bash
ps aux | grep nexus
```

This will display the running Nexus process if it has started successfully.

---

## Conclusion
By following this guide, you can set up and host Nexus on a Linux machine, ensuring that it is properly configured and running. This setup provides a robust platform for managing repositories and supporting development workflows.

