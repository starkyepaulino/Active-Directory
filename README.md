# Active-Directory
Active Directory---This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.

<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Table of Contents</h2>

- Step 1: Setup the Azure Enviorment
- Step 2: Create the Active Directory domain controller VM
- Step 3: Connect to the domain controller virtual machine
- Step 4: configure the domain controller
- Step 5: Join Windows 10 to your domain
- Step 6: Test the Active Directory enviorment

<h2>Deployment and Configuration Steps</h2>

![Screenshot (75)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/2144731a-b67a-46bd-aa41-21aef3e2d15d)

<p>
<div>
  <h3>Step 1: Set up the Azure environment:</h3>
  <ol>
    <li>Sign in to the Azure portal at <a href="https://portal.azure.com">portal.azure.com</a>.</li>
    <li>Create a new resource group for your virtual network and virtual machines.</li>
  </ol>
</div>
</p>
<br />


![Screenshot (77)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/d6562cf9-527d-4f2f-ad50-1b40b9bd4792)
![Screenshot (78)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/01eb921b-8ce7-474e-a1f6-6ea2af8e908c)
![Screenshot (79)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/b988a1b0-3598-4fb6-bdfc-f490fc361102)
![Screenshot (82)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/3cdc39d4-8fa1-4746-ae64-6c5af809e0f6)

<p>
<div>
  <h3>Step 2: Create the Active Directory domain controller virtual machine:</h3>
  <ol>
    <li>Select "Create a resource" from the Azure portal's left-hand menu.</li>
    <li>Search for "Windows Server" and choose the appropriate version.</li>
    <li>Configure the virtual machine settings, such as name, resource group, size, and region.</li>
    <li>Specify the virtual network and subnet you created in step 1.</li>
    <li>Choose a username and password for the domain controller's administrator account.</li>
    <li>Configure additional settings like disk type, networking, and management options.</li>
    <li>Review and create the virtual machine.</li>
  </ol>
</div>
</p>
<br />

![Screenshot (83)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/1249b639-600c-482e-9ef1-6570b9deefa9)
![Screenshot (84)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/b01a5495-5d99-441f-b672-ab3f4d481a19)

<p>
<div>
  <h3>Step 3: Connect to the domain controller virtual machine:</h3>
  <ol>
    <li>Once the virtual machine is created, search Virtual Machines & select the VM created in Azure portal.</li>
    <li>Copy the public ip address to paste in remote desktop client.</li>
    <li>Login with the credentials you created in step 2.</li>
</div>
</p>
<br />

![Screenshot (86)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/405d6538-58eb-48a1-a8ad-d52f0da58eae)
![Screenshot (87)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/fda28150-b786-4723-98db-8011e5f587d8)
![Screenshot (88)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/3fc9b988-a4bc-4ad4-8333-163346c1019d)
![Screenshot (89)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/0aae2f2e-6dab-42b5-a33b-1367c47ccbaa)
![Screenshot (90)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/e934ded3-499e-4204-aa05-f64bc6f171db)
![Screenshot (91)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/f88dac86-a493-4337-add0-0cd312eb1d15)


<p>
<div>
  <h3>Step 4: Configure the domain controller:</h3>
  <ol>
    <li>On the domain controller virtual machine, open the Server Manager.</li>
    <li>Select "Add roles and features" and proceed through the wizard.</li>
    <li>Choose the "Active Directory Domain Services" role and install it.</li>
    <li>After installation, promote the server to a domain controller.</li>
    <li>Specify the desired Active Directory domain name and set the domain controller options.</li>
    <li>Set the Directory Services Restore Mode (DSRM) password.</li>
    <li>Complete the wizard and let the server restart.</li>
  </ol>
</div>
</p>
<br />

![Screenshot (103)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/119964b1-15fe-4e61-b3ab-02353732b305)
![Screenshot (99)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/163ceda3-9a6f-40cf-8e42-7c1bc762803b)
![Screenshot (101)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/517887eb-db21-4be8-89ec-5b57ee37a0f3)
![Screenshot (106)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/f20a111b-2f01-49a2-b2a3-707c7550647e)

<p>
<div>
  <h3>Step 5: Join Windows 10 to your domain (mydomain.com)<h3/>
  <ol>
    <li>From the Azure Portal, set Windows10’s DNS settings to the windows server’s Private IP address</li>
    <li>From the Azure Portal, restart windows 10 VM</li>
    <li>Login to Windows 10 (Remote Desktop) as the original local admin and join it to the domain (computer will restart)</li>
     <li>Open the System properties,go to rename this PC (advance), go to the "Computer Name" tab, and click on "Change".</li>
    <li>Select "Domain" and enter the Active Directory domain name configured in step 4.</li>
    <li>Provide the credentials of an account with sufficient permissions to join the domain.</li>
    <li>Login to the windows server (Remote Desktop) and verify the VM shows up in Active Directory Users and Computers (ADUC) inside the "Computers" container on the root of the domain</li>
  </ol>

</div>
</p>
<br />

![Screenshot (107)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/879e32c1-3d2d-4a6d-92b7-d51f764af9af)
![Screenshot (108)](https://github.com/DaAvionBrock/ActiveDirectory/assets/118222338/60ef7ddd-5a11-4205-9356-7431213a734e)

<p>
<div>
  <h3>Step 6: Test the Active Directory environment:</h3>
  <ol>
    <li>Log in to the domain-joined virtual machines using domain user accounts.</li>
    <li>Verify that the domain users can authenticate successfully.</li>
    <li>Test Active Directory services like Group Policy, user authentication, and directory access.</li>
  </ol>
</div>
</p>
<br />
