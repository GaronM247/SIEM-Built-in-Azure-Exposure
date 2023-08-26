

<h2>Description</h2>
  In this lab session, I will lead you through the intricacies of configuring Azure Sentinel (SIEM) and establishing a connection with a dynamic virtual machine, simulating a honey pot. Collaboratively, we will witness real-time instances of RDP Brute Force attacks originating from diverse global locations. Our analytical approach will be elevated through the utilization of a meticulously crafted PowerShell script, enabling the extraction of geolocation data pertaining to the attacker's. This data will be adeptly visualized on the Azure Sentinel Map, culminating in a dynamic and informative experience. Join me on this captivating expedition of knowledge and exploration.

  
 <h2>Environments & Utilities Used:</h2>
 
- <b>PowerShell ISE</b>
- <b>Windows Event Viewer</b>
- <b>Windows 10 </b>
- <b>Azure VM </b>
- <b>Security Center</b>
- <b>Azure Sentinel/Map </b>
- <b>Log Analytics Workspace</b>

 <h2>Project walk-through:</h2>

## Preparation

### Azure Subscription Setup

1. Ensure you have an Azure subscription and access to the Azure portal.
2. If you're new to Azure, follow the provided prompts to set up your subscription.
3. Remember your username and password, as you'll need them later.

- Free Azure Subscription: [Azure Free](https://azure.microsoft.com/en-us/free/)
- Azure Portal Login: [Azure Portal](https://portal.azure.com)

### Obtain an API Key

1. Obtain an API key from [ipgeolocation.io](https://ipgeolocation.io/) in your web browser.
2. Sign up for an account and follow the on-screen instructions.
3. Keep the unique API key secure for later use.

## Setting up the Honey Pot with Virtual Machine

### Create a Virtual Machine (VM)

1. Open the Azure Portal.
2. In the main search bar, type "Virtual Machine" and select the relevant option.
3. On the left side, click the "Create" button.

### Set up Resource Group

1. Choose to create a new resource group.
2. Name the resource group "Honey Pot VM" for identification.
   
<p align="center">
<img src="https://i.imgur.com/EmV9yH8.png" height="85%" width="85%" alt="Image"/>
</p> 


### Specify Location

1. During the prompts, choose "West US2" as the location for the data center.

### Provide Username and Password

1. Enter the required username and password details for the VM.

### Access Advanced Network Settings

1. Navigate to the "/nik network group/" section.

### Create a Fresh Firewall Rule

1. Clear any default rules.

### Craft a New Rule for All Traffic

1. Create a rule that allows all traffic.
2. In the destination port field, use a "Star for anything."
3. Set protocol action to "allow."
4. Set priority to "low" (100).
5. Name the rule "danger."

### Review and Creation

1. Proceed to the review and creation step.
2. Wait for the setup to complete.

## Setting up a Log Analysis Workspace

### Access Log Analysis Workspace

1. Begin by accessing the Log Analysis Workspace through the main search bar.

### Customized Event Logs and Geolocation

1. This step is essential to create customized event logs and configure geolocation settings.
2. Azure SIEM will integrate with this workspace.

### Navigate to Workspace Creation

1. Navigate to the creation of the Log Analysis Workspace.

### Choose Resource Group

1. When choosing the resource group, you may find certain details already populated from previous inputs.
2. Opt for "Honey Pot lab."

### Assign Workspace Name

1. Assign the name "La Honey Pot 1" to the Log Analysis Workspace.

### Select Region

1. Select the region – "West US 2."

### Complete the Process

1. Complete the process by clicking on "View and Create," similar to the previous steps.

## Security Center Logs Configuration

### Search for "Security Center

1. Use the main search bar to search for "Security Center."

### Enable Log Gathering

1. Enable the capability to gather logs from virtual machines.
2. Direct the logs to the Log Analysis Workspace.

### Access Pricing and Settings

1. Within the Security Center interface, navigate to the left-hand side.
2. Locate and click on "Pricing" and "Settings."

### Choose Log Analysis Workspace

1. Click on the "Log Analysis Workspace" option.

### Configure Defender and SQL Servers

1. Within Log Analysis Workspace, enable Defender.
2. Simultaneously, turn off SQL Servers as shown in the image.
   
  <p align="center">
<img src="https://i.imgur.com/pDcjDe8.png" height="85%" width="85%" alt="Image "/>
</p> 

### Save Changes

1. Click the "Save" button to apply the Defender and SQL Servers configuration changes.

### Access Data Collection

1. On the left-hand side, click on "Data Collection."

### Choose Collect All Events

1. Within "Data Collection," select the option "Collect All Events."
2. Click the "Save" button at the top of the interface to confirm the "Collect All Events" configuration.

## Connect Logs Analytics to VM

### Access Log Analytics Workspace

1. Get back to the Log Analytics Workspace through the main search bar.

### Navigate to Workspace

1. On the left side, click on "Workspace."

### Select VM

1. Again, on the left side, find and click on "VM."

### Click "Connect"

1. Within the VM section, locate your "virtual machine" that was set up earlier.
2. Click on "Connect," which should be under the prompt.

### Continue to Next Step

1. While the connection process is underway, keep moving forward to the next step in a new window.
2. Onward and upward!

## Setting up Azure Sentinel

### Access Azure Portal

1. Begin by opening the Azure portal.
2. Navigate to Azure Sentinel within the portal.

### Initiate Setup

1. Click on the "Create" option to initiate the setup process.

### Establish Log Analytics Workspace

1. Follow the prompts to create a new Sentinel Log Analytics workspace.
2. Incorporate this workspace into the configuration.

### Wait for Setup

1. Allow some time for the setup process to take place.

### Check Virtual Machine Tab

1. During the waiting period, consider navigating back to the Virtual Machine tab.
2. Check if the setup process on the Virtual Machine has concluded.

### Log In to Virtual Machine

1. Once the setup is verified as complete, log in to the Virtual Machine instance.

### Click on Virtual Machine Instance

1. Click on the Virtual Machine instance.

### Confirm and Proceed

1. Confirm your actions by clicking "OK."

### Click on IP Address

1. Move on to the next crucial step by clicking on the "IP address."
2. This step is a pivotal point in the ongoing process.

## Accessing the VM via Remote Desktop

### Copy the IP Address

1. Click on the "IP address."
2. Copy the IP address as you prepare to log in remotely and explore.

### Initiate Remote Desktop Connection

1. Click on your desktop's "Start menu."
2. Locate the "Remote Desktop" application.
3. Launch the application.
   
   <p align="center">
<img src="https://i.imgur.com/DYP9Sck.png" height="85%" width="85%" alt="Image RDP"/>
</p> 

### Paste the IP Address

1. Within the remote desktop application, paste the IP address you copied earlier to establish the connection.

### Customize Display Settings

1. Customize your display settings to match your preferences before clicking "Connect."

### Use Different Account (if prompted)

1. After clicking "Connect," you might see "More Choices."
2. If so, select the option to use a different account.
3. Input your Virtual Machine's designated username and password for smoother login.

### Proceed Despite Certificate Warning

1. In case of a certificate warning, proceed despite the warning.

### Log In with Incorrect Credentials

1. Log in using intentionally incorrect credentials.
2. This generates a "failed login attempt" scenario for future reference.

### Navigate VM Interface

1. As your Virtual Machine's interface unfolds, answer "No" to each query presented.

### Locate the "Start Menu"

1. After completing the login, find the "Start Menu" on the Virtual Machine.

### Microsoft Edge Setup

1. Upon setup, "Microsoft Edge" will appear.
2. When prompted, choose to proceed without signing in.

## Navigating Event Viewer in a Virtual Machine

### Access Event Viewer

1. Return to the "Start Menu" on the Virtual Machine.
2. Initiate a search for "Event Viewer," a tool for examining logs.

### Navigate Within Event Viewer

1. After accessing the "Event Viewer," follow these steps:
   - Click on "Windows logs."
   - Further navigate to "Security."

### Focus on Event ID 4625

1. In the "Security" section, focus on "Event ID: 4625."
2. Double-click on it to reveal a wealth of event information.
3. Details include an unfamiliar username, the individual's identity attempting the login, and the reason behind the event.

### Check for IP Address

1. Verify whether an "IP address" is present in this event information.
2. If the IP address is absent, follow the steps outlined in the guide.

## Disabling Windows Firewall on the Virtual Machine

### Access Firewall Settings

1. Go to the "Start Menu" on the Virtual Machine.
2. In the search bar, type "wf.msc" to quickly access the Firewall settings.
3. Open the Firewall interface.

### Access the "Domains" Section

1. Inside the "Windows Defender Firewall Properties," navigate to the "Domains" section.

### Disable Firewall for All Settings

1. In the "Domains" section, disable the firewall for all settings, including both private and public configurations.

### Apply Changes

1. After making the necessary adjustments to firewall settings, ensure that you apply the changes by selecting the "Apply" option.

### Refer to Accompanying Image

1. For additional guidance, you can refer to the accompanying image provided.

### Return to Desktop Environment

1. Now that you have configured the firewall settings, return to your desktop environment.

### Initiate Ping Test via Command Line

1. From the desktop environment, open the command line.
2. Initiate a ping test to confirm proper functionality.

### Confirm Ping Test Functionality

1. Verify that the ping test functions as expected, indicating successful connectivity.
2. Once you have confirmed the ping test, transition back to the Virtual Machine.

## Custom PowerShell Script for Retrieving Geolocation Information

### Develop or Source the Script

1. Craft a custom PowerShell script or locate one on GitHub for retrieving geolocation information linked to IP addresses used by potential attackers.

### Obtain the GitHub Script

1. Search for a script named "custom security log exporter" on GitHub.
2. Once found, copy the script to your clipboard.

### Open PowerShell ISE on VM

1. Launch "PowerShell ISE" on your virtual machine.

### Insert the Script

1. Paste the copied script from GitHub into the PowerShell ISE window.

### Update with New API Key

1. Utilize the API key created earlier for this task.
2. Replace the existing API key in the script with the new one you generated.

### Execute the Script

1. Run the modified script within PowerShell ISE.

### Save the Script

1. After successful execution, save the script on your virtual machine's desktop with the filename "Log Exporter."

### Output Location

1. The script will organize the output logs into a folder within the "C program" directory.
2. You might need to manually locate this folder.

### Identify Failed Login Attempts

1. Look for any entries highlighted in "purple" within the output logs.
2. Explore sample files that came with the script to understand the data structure.

### Process Overview

1. Understand the process: Failed event logs related to user activity are sent to the Geolocation API website.
2. The script generates a dedicated folder on your virtual machine containing detailed information about these failed login attempts.

### Future Use

1. This information will be essential for training the analyst workspace and enhancing security measures.

## Creating a Custom Log in the Log Analysis Workspace

### Navigate to Azure

1. Return to Azure's main screen and locate the "Log Analysis" feature.

### Access Your Workspace

1. Within the left-hand menu, find and select your designated workspace labeled as "Honeypot."

### Add a Custom Log

1. Proceed to "Custom logs" within the workspace options and click "Add."

### Specify the Log File

1. Input the log file created on your virtual machine (VM).
2. Retrieve the file labeled "C program data."

### Transfer and Prepare the Log Data

1. Open the copied file and extract all the contained information.
2. Minimize the VM and return to your PC.

### Paste into Notepad

1. Open "Notepad" and paste the extracted information into it.

### Save the Log File

1. Save the file on your PC's desktop as "Failed Rdp.Log."
2. This file will serve as the basis for training log analysis to identify specific patterns.

### Locate and Input the File

1. Locate the saved "Failed Rdp.Log" file on your PC's desktop.
2. Input this file in the corresponding prompt during the customization process.

### Progress through the Setup

1. Click "Next" to proceed.
2. A preview of the log file will appear on the screen. Review it for accuracy.

### Configure the Collection Path

1. Input the correct collection path: "c program data failed_rdp.log."
2. Ensuring accuracy is crucial to successful log collection.

### Double-check and Move Forward

1. Verify all input details are accurate before advancing. If necessary, cross-check on the VM.
2. Click "Next."

### Add Name and Details

1. Under "Details," provide a name for the custom log, such as "failed rdp with geo."
2. The system will automatically append "cl" at the end.

### Confirm and Create

1. Proceed by clicking "Next" followed by "Create Custom Log."
2. Allow some time for synchronization.

### Verification and Utilization

1. To verify, access "Logs" and start typing to see the custom log appear in the dropdown menu.
2. Click on it to initiate its execution.
3. This will open up a display containing logs and events.

## Access Security Event Logs

1. Go to the "security event" section.
2. Enter the filter: "security event id equals 4625".
3. Run the filter to display failed RDP logs.
4. Explore the logs for IP addresses and more details.
   
<p align="center">
<img src="https://i.imgur.com/VNdfCEa.png" height="85%" width="85%" alt="Image"/>
</p> 



## Extract Files from Logs

1. Wait briefly for logs to load, take a coffee break.
2. Click "run" to display all logs.
3. Identify the date field to extract.

## Extract Specific Fields

1. Click on a log to expand it.
2. Tap the three dots on the side.
3. Choose "extract fields."
4. Access "raw data logging" view.
5. Zoom in if necessary to view all fields.
6. Highlight the field, e.g., "Longitude."
7. Name the field, select "numeric", click "extract."
8. Verify the extraction process for accuracy.
9. Ensure correct values are highlighted.
10. If correct, "save extraction."
11. Repeat for other fields: longitude, destination host, username, source host, state, country, lab (country dash IP address), and timestamp/daytime.

## Review and Edit Extractions

1. If issues arise, edit the extraction process to match.
2. Return to "custom logs" on the left-hand side.
3. Confirm the presence of the custom log created earlier.
4. Click "custom fields" to see all extractions.
5. Edit extractions to improve training.

## Query for New Logs

1. Run a query to check for new logs.
2. Wait patiently for new logs to populate.

## Step 13: Validating Extracted Information

### Transition to PC for Testing

1. Return to your PC for a comprehensive validation test on the extracted data.

### Revisit "Remote Login" Section

1. Go back to the "remote login" section as part of the evaluation.

### Simulate Password Failure

1. Enter the designated "VM IP address."
2. Deliberately input an incorrect password to simulate a "password failure."
3. Gracefully exit the process after the simulation.

### Examine "C Program Files" Folder

1. Navigate to the "c program file" folder on the VM's desktop.
2. Thoroughly examine it to confirm the successful registration of the earlier attempt.

### Delving into Extracted Log Analysis

### Enter "Log Analysis" Domain

1. Access the "Log Analysis" domain within Azure's interface.

### Execute Subsequent Query

1. Initiate another query execution to retrieve the most up-to-date logs.

### Comprehensive Log Scrutiny

1. Engage in a meticulous examination of the logs.
2. Align the log content with the previously extracted data.

### Validate Key Field Accuracy

1. Methodically verify the accuracy and coherence of key fields, such as country and state.

### Interlude for Log Generation

1. Allow Time for Fresh Logs
2. Dedicate a short interval to allow the accumulation of new logs.

### Indulge in a Coffee Break

1. Utilize this time for a well-deserved coffee break.

### Await New Log Entries

1. During the break, patiently wait for new log entries to appear.

## Set-up Map Visualization in Sentinel

1.) Open a new browser tab and navigate to "portal.azure.com".
2.) In the search bar at the top of the portal, type "Sentinel" and press Enter.

### In Azure Sentinel:

1. Locate and select "Law-honeypot1," the instance we previously set up.
2. Click on the "Overview" section to access general setup information and basic dashboard elements.

### Investigate Logs

1. Click on the "failed rdp" icon to view details related to failed Remote Desktop Protocol attempts.
2. Explore "security event" to access event logs specific to the virtual machine.

### Access Workbook

1. On the left-hand side menu, find and select "workbook."
2. Click on "add a workbook" to start creating a new workbook.

### Customize Workbook

1. In the upper left corner of the workbook, click on "edit."
2. Remove any default widgets that may be present in the workbook.

### Add Query

1. Within the workbook, click on "add a query."
2. Paste the following Query:

FAILED_RDP_WITH_GEO_CL | summarize event_court=count() by sourcehost_CF, latitude _CF, longitude _CF, country_CF, label _CF, destinationhost _CF | where destinationhost _CF != "samplehost" | where source host_CF  !=  ""

3. Verify the accuracy of the query by clicking "Run Query."

### Configure Visualization

1. Navigate to the "Visualization" option within the workbook.
2. Choose "map" to create a map visualization.

### Adjust Map Settings

1. Open the map visualization, which appears at the bottom of the screen.

### Access Map Settings

1. Locate the "Map settings" on the right-hand side of the screen.

### Customize Appearance and Functionality

1. Customize the map settings to achieve the desired appearance and functionality. 

### Plotting Locations

1. Plot locations using the "longitude_CF" field for longitude and the "latitude_CF" field for latitude. These locations are obtained from Geolocation data.

### Size by Prompt Input

1. In the side prompts, select the choices related to "event_count" for size. Click "Apply" to confirm.

### Metric Labels

1. In the prompt, label the metric as "metric_CF" and click "Apply."

### Metric Value

1. Input "event_count" as the metric value. Click "Apply" to apply the changes.

### Handling Plotting Issues

1. If there's an issue with plotting longitude and latitude, use "country_CF" as the country field.

### Save Configuration

1. Save the configuration with the name "Failed RDP World Map."
2. Save it in the "West US2" location.

### Finalize and Refresh

1. Click "Save" and then "Done Editing."
2. Wait a few days for the visualization to gather data.

### Refreshing Data

1. Periodically refresh the visualization by clicking "Refresh" or enabling "Auto refresh." Set a refresh time, e.g., every 5 minutes.

### Monitor PowerShell Script

1. Ensure the PowerShell script for the map is still running, as it's essential for the map to function.

### Data Visualization

1. After a few days, you should see the map populated with data points, along with relevant information at the bottom of the screen.

### Analyze Data

1. Review the data in the VM PowerShell script to gain insights into attacks and their patterns.

   
  <p align="center">
<img src="https://i.imgur.com/JWnqI1C.png" height="85%" width="85%" alt="Image Map"/>
</p> 



### Long-Term Observation

1. Allow the setup to run for a couple of days to gather sufficient activities for analysis.

### End

At the end of this lab, go back to Azure and delete all the resource groups to avoid incurring additional costs in your subscription.

1. Go to Azure > Resource Groups.
2. Find the resource group we were using and "Delete it."

This ensures that you don't continue to be charged for resources you no longer need.
