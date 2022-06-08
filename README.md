# Cisco SecureX June 2022 Webinar

This workflow fetches Cisco Secure Firewall incidents and conducts automated enrichment to see if additional data can be found about the event.

The public IPv4 or domain name is searched in Umbrella database, if the IP or domain is malicious is added to an Umbrella destination list.

The source of the event is searched in Cisco Secure Endpoint and if a matching endpoint is found, an Orbital live query is performed and a forensic analysis is created.

A casebook and sighting are created and a message is sent to a configured Cisco Webex teams space

Steps:
* Sets Required Variables -  Configure the required variables for the workflow:
	- Cisco Secure Endpoint cloud: nam, eu, apjc
	- Cisco Webex Bot Token: Token of Webex Bot used to push messages
	- Cisco Webex Room ID: ID of the Webex room to publish messages
	- Umbrella Investigate access token: Token used by Umbrella investigate

* Generate an access token for Threat Response
* Fetch incidents for the past hour
* Loop through each new incident
*> Search for each processed/past incidents in the past 60 minutes: Task to avoid processing multiple times the same incident
*>> If incident was processed already finish execution of incident
*>> Purge incidents older than 60 minutes
* Get the incident's relationships
* Loop through each relationship
* For each observable:
*> Identify if is Public IPv4 or Domain
*> Investigate category in Umbrella Investigate
*> If is malicious add IP or domain to Umbrella destination list
*> Search Cisco Secure Endpoint using the IP
*> If found computer, get GUID
*> Query the endpoint using Orbital
* Build the casebook description and create casebook
* Build Cisco Webex Teams description and post message
* Record incident in processed incident table

This workflow was created by Cisco employee for the delivery of Orchestration workflow webinar and is provided as is and for demo purposes.

More Information: https://github.com/jponcedo/SecureX_June2022_Webinar
