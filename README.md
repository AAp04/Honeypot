# Week 9 Project: Honeypot

Time spent: 15 hours spent in total

### Project summery 

In this project we stand up a basic honeypot and demonstarte its effectiveans at detecting and collecting data about an attack. The project requires to use a well-supported open source honeypot, which is Modern Honey Network(MHN). MHN is a centralized server for management and data collection of honeypots.

### Milestone 0 : Google Cloude Set Up

To accomplish this project we required to set up Google Cloud Platforms(GCP) Free Tier or alternative one Cloud Platforms. After setting up the platform we initialized the zone and region.

### Milestone 1 : Create MHN Admin VM 

Since GCP require to create the firewall rules seperatley and then apply them to the VM we require to use the following attrubutes.

- Ubuntu 14.04(trusty)
- HTTP traffic allowed(port 80)
- TCP ports 3000 and 100000

Command used 
gcloud beta compute firewall-rules create mhn-allow-admin --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:3000,tcp:10000 --source-ranges=0.0.0.0/0 --target-tags=mhn-admin

Result 

<img src="https://i.imgflip.com/27zs1q.gif" title="made at imgflip.com"/>

### Milestone 2 : Install the MHN Admin Application 

In this step we install the server and login to server using our"superuser"

### Milestone 3 : Create a MHN Honeypot VM 

In this step we deploy Dionaea over HTTP

Dionaea is "meant to be a nepenthes successor , embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls"

### Milestone 4 : Install the Honeypot Application

In this step we install honeypot application into the VM and wire it to connect back to the admin server.

The wget command executed inside the honeypot VM to install the Dionae sorftware .

wget "http://35.184.8.8/api/script/?text=true&script_id=4" -O deploy.sh && sudo bash deploy.sh http://35.184.8.8 yYw8AEVE

<img src="https://i.imgflip.com/27zt00.gif" title="made at imgflip.com"/>

<img src="https://i.imgflip.com/27zt7p.gif" title="made at imgflip.com"/>

### Milestone 5 : Attack!

In this step we can make sure everything is set up correctly and working by using nmap command.

<img src="https://i.imgflip.com/27zth7.gif" title="made at imgflip.com"/>


<img src="https://i.imgflip.com/27ztnb.gif" title="made at imgflip.com"/>

### Exporting Data

Attempted to download file 

gcloud compute scp mhn-admin:~/session.json ./session.json
ERROR: (gcloud.compute.scp) Underspecified resource [mhn-admin]. Specify the [--zone] flag.

sudo gcloud compute scp mhn-admin:~/session.json ./session.json --zone us-central1-c     
ERROR: (gcloud.compute.scp) Could not fetch resource:
Insufficient Permission

<img src="https://i.imgflip.com/27zvyd.gif" title="made at imgflip.com"/>
