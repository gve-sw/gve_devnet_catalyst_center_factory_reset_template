# gve_devnet_catalyst_center_factory_reset_template

Sample workflow to reset an access point to factory default and remove it from the Catalyst Center inventory via an Apache Velocity template and Postman.


## Contacts
* Ramona Renner


## Solution Components
* Catalyst Center
* Postman
* Cisco Access Point (tested with a Cisco Catalyst 9136I Unified Access Point)
* Cisco Wireless Controller (tested with a Cisco Catalyst 9800 Wireless Controller)


## Prerequisites

**Catalyst Center Credentials**: In order to use the Catalyst Center APIs, you need to make note of the IP address, username, and password of your instance of Catalyst Center. Note these values to add to the Postman environment during the installation phase.

Furthermore, make sure that the REST API bundle of the Catalyst Center appliance is enabled. After enabling the REST API bundle, wait four minutes before attempting to issue a REST request to the Cisco Catalyst Center.


## Add Template to Catalyst Center

Follow the instructions in [Chapter: Create Templates to Automate Device Configuration Changes](https://www.cisco.com/c/en/us/td/docs/cloud-systems-management/network-automation-and-management/dna-center/2-3-5/user_guide/b_cisco_dna_center_ug_2_3_5/b_cisco_dna_center_ug_2_3_5_chapter_01000.html) to:

1. [Create a Project](https://www.cisco.com/c/en/us/td/docs/cloud-systems-management/network-automation-and-management/dna-center/2-3-5/user_guide/b_cisco_dna_center_ug_2_3_5/b_cisco_dna_center_ug_2_3_5_chapter_01000.html#create_projects) if not available yet.
2. [Import the Template](https://www.cisco.com/c/en/us/td/docs/cloud-systems-management/network-automation-and-management/dna-center/2-3-5/user_guide/b_cisco_dna_center_ug_2_3_5/b_cisco_dna_center_ug_2_3_5_chapter_01000.html#id_129885). Use the **clear_ap_template.json** file in this folder.
3. [Attach the Template to a Network Profile](https://www.cisco.com/c/en/us/td/docs/cloud-systems-management/network-automation-and-management/dna-center/2-3-5/user_guide/b_cisco_dna_center_ug_2_3_5/b_cisco_dna_center_ug_2_3_5_chapter_01000.html#Cisco_Task_in_List_GUI.dita_297c7d32-eadc-4020-a1f3-c18be8b2909e)


# Prepare Postman

Sign up or download Postman from https://www.postman.com/. Import the provided collection, **Catalyst Center Clean AP Worflow.postman_collection** from this folder, as described under [Importing data into Postman](https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/).

As a next step, create a new environment in Postman as described under [Creating environments](https://learning.postman.com/docs/sending-requests/managing-environments/#creating-environments). Add the following variables while doing so:

* **dnac** - IP of the Catalyst Center lab
* **username** - username of the Catalyst Center lab account with admin privileges 
* **password** - password of the Catalyst Center lab account with admin privileges
* **template_id** - ID of the Clear AP template in Catalyst Center. Use the **Helper - Get Template ID** request to retrieve the ID and other information about the available templates.
* **cisco_ap_name** - Catalyst Center name of the access point to reset (see Catalyst Center inventory view)
* **ap_id** - ID/UUID of the access point to reset. Use the **Helper - Get Device ID and Name** request to retrieve the ID and other information about the available devices.
* **wlc_id** - ID/UUID or the wireless controller to reset. Use the **Helper - Get Device ID and Name** request to retrieve the ID and other information about the available devices.
* **template_deployment_id** - ID of a template deployment. Result of the request: **3. Deploy AP Clear Template**
* **deletion_task_id** - ID of the deletion task. Result of request **6. Delete Cleared/Unreachable Device** 

The following field is automatically populated:
* **token** - Catalyst Center API token. Result of the request: **1. Authenticate / Get Token**

## Workflow

After setting up Catalyst Center and Postman, follow the workflow in its order to reset a Cisco Access Point to factory default and remove it from the Catalyst Center inventory. Therefore, make sure that the wireless controller and access point are available in the Catalyst Center inventory and reachable.

1. Authenticate / Get Token
2. (Optional) Preview AP Clear Template
3. Deploy AP Clear Template
4. (Optional) Get Status of Template Deployment
5. Check Device Reachability
6. Delete Cleared/Unreachable Device
7. (Optional) Get Status of Deletion Task


# Resources 
* API Documentation for Template Requests: https://developer.cisco.com/docs/dna-center/#!gets-all-the-versions-of-a-given-template
* Catalyst Center Templates: https://github.com/kebaldwi/DNAC-TEMPLATES/tree/master
* Apache Velocity Project: https://velocity.apache.org
* Using Advanced Velocity Templates in Cisco Catalyst Center – Part 3: https://blogs.cisco.com/developer/velocity-templates-in-dna-center-3


# Screenshots

![/IMAGES/screenshot.png](/IMAGES/screenshot.png)

### LICENSE

Provided under Cisco Sample Code License, for details see [LICENSE](LICENSE.md)

### CODE_OF_CONDUCT

Our code of conduct is available [here](CODE_OF_CONDUCT.md)

### CONTRIBUTING

See our contributing guidelines [here](CONTRIBUTING.md)

#### DISCLAIMER:
<b>Please note:</b> This script is meant for demo purposes only. All tools/ scripts in this repo are released for use "AS IS" without any warranties of any kind, including, but not limited to their installation, use, or performance. Any use of these scripts and tools is at your own risk. There is no guarantee that they have been through thorough testing in a comparable environment and we are not responsible for any damage or data loss incurred with their use.
You are responsible for reviewing and testing any scripts you run thoroughly before use in any non-testing environment.