# Patch Management and Vulnerability Remediation using WSUS

## Intro
This project focuses on learning the fundamentals of patch management and vulnerability remediation using Windows Server Update Services (WSUS). WSUS enables administrators to centrally manage the distribution of Microsoft updates across a corporate network. By the end of this project, we will have the skills to deploy WSUS, configure client systems, approve and distribute updates, and monitor update status.

## Prerequisites
- Basic knowledge of Windows Server and client management
- A Windows Server 2016 or later system. In this project, I use the 2022 server
- Windows client devices (Windows 10) for testing purposes
## Lab Environment and Tools
- Windows Server 2022 or later with WSUS role installed
- Windows client machines
- Active Directory for domain-joined machines (optional but recommended)

## Tasks

### Task 1: Installing and Configuring WSUS

**Steps:**

1. Open Server Manager on the Windows Server.
2. Click "Manage" > "Add Roles and Features".
3. Follow the installation wizard to add the WSUS role:
    - Select "Windows Server Update Services".
    - Choose the required services and proceed with the installation.
4. Once installed, launch the WSUS Configuration Wizard:
    - Configure the update source.
    - Choose the classifications and products you want to update.
    - Set up synchronization schedule.
    - Complete the wizard to finalize the setup..

**Result:**
- WSUS is installed and configured with initial settings applied

### Task 2: Configuring Group Policies for WSUS

**Steps:**

1. Open the Group Policy Management Console (GPMC) on the Windows Server.
2. Create a new Group Policy Object (GPO) or modify an existing one.
3. Navigate to "Computer Configuration" > "Policies" > "Administrative Templates" > "Windows Components" > "Windows Update".
4. Configure the following policies:
    - "Specify Intranet Microsoft update service location": Set it to the WSUS server URL (e.g., `http://wsusserver`).
    - "Configure Automatic Updates": Set it to auto-download and schedule the install.
5. Link the GPO to the organizational unit (OU) containing the target client machines.

**Result:**
- Group policies are configured to direct client devices to use the WSUS server for updates.

### Task 3: Approving and Deploying Updates

**Steps:**

1. Open the WSUS management console on the server.
2. Navigate to "Updates" > "All Updates".
3. Select the updates to be approved for installation.
4. Right-click the selected updates and choose "Approve".
5. Assign the updates to the appropriate computer groups.

**Result:**
- The selected updates are approved for deployment to designated device groups.

### Task 4: Checking Update Status on Client Devices

**Steps:**

1. On a client machine, open Command Prompt with administrative privileges
2. Execute the following command to trigger an update check:
    ```bash
    wuauclt /detectnow
    ```
3. Open Windows Update from the Control Panel or Settings and check for available updates.
4. Confirm that the updates approved in WSUS are listed and begin installation.

**Result:**
- The client machine detects and installs updates as configured by WSUS

### Task 5: Generating and Reviewing WSUS Reports

**Steps:**

1. Access the WSUS console on the server.
2. Navigate to the "Reports" section and select the desired report type (e.g., Update Status Summary).
3. Define the necessary parameters and generate the report.
4. Analyze the report to assess update compliance and identify any issues.

**Result:**
- A detailed report providing insights into update status and compliance across client devices, helping to detect pending or failed updates.


**Summary:**

By completing these exercises, participants will gain hands-on experience in using WSUS for patch management and vulnerability remediation, including server configuration, client setup, update deployment, and compliance monitoring.
