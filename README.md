# Flask on Cloud VM
HHA504 Assignment 2: Cloud Foundations for Health Informatics

## Student Info
- Name: Angel Huang
- Cloud Provider: Google Cloud Platform (GCP)

## Video recording: 
- Zoom video: https://drive.google.com/file/d/1sac5CZZTq29bMdtDAJHk1PVnjPVZI-rt/view?usp=sharing

## Steps
### 1. VM Creation
### Create/Start VM
1. Go to [google cloud](https://console.cloud.google.com) and sign in
2. Make sure you created and selected a project
3. Click Create a VM
4. Give it a name under " Name* "
5. Chose a " Region* " and " Zone* " of your chose, better if it's a region near you
6. Scroll down and choose a Machine type
- In this case E2 (smallest available/free-eligible) and scroll down more and pick e2-micro
7. Then click " OS and storage "
8. Click " Change "
9. Under " Operating system ", click " Ubuntu " and then click " Select "
10. Go to " Networking "
11. Check the boxes " Allow HTTP traffic " and : Allow HTTPS traffic "
12. Click " Create "
- Once you see a green circle with a check next to the name of your VM, it is up and running
![screenshot](images/gcp/gcp_step21.png)

### 2. Networking (Port 5003 Open)
1. Once VM is running, click " Set up firewall rules" and then " Create firewall rules
2. Give it a name and discription
3. Check the box " TCP " and type in "5003" under it
4. Scroll up and click "Targets" and change it to "All instances in the network"
5. Type " 0.0.0.0/0 " under Source IPv4 ranges "
6. Click " Create " and it should show up in the list now
![screenshot](images/gcp/gcp_step21.png)

### 3. OS Update + Python Install
1.  Click the arrow back on your browser to go back to seeing the VM you just created
2. Click " SSH " and " Authorize "
3. Update OS by using the code:
 ```bash
   sudo apt update && sudo apt upgrade -y
   ``` 
4. Install Git, Python 3 + pip using the code:
 ```bash
   sudo apt install git python3 python3-pip python3.13-venv -y
   ```
5. Clone the Flash templete by Professor Hants:
 ```bash
   git clone https://github.com/hantswilliams/HHA-504-2025-FlaskStarter.git
    cd flask_template
   ```
6. Create new virutal environment using the code:
 ```bash
    python3 -m venv venv
   ```
7. Then activate virtual environment using the code::
 ```bash
    source venv/bin/activate
   ```
8. Install using the code:
 ```bash
    pip install requirements.txt
   ```
9. Run the app on port 5003 using the code:
 ```bash
    python3 app.py
   ```
![commands + screenshot](images/gcp/gcp_step21.png)

### 4. Flask App Running
1. Exit the SSH and back to looking at your VM
2. Copy the IP under "External IP"
3. Open a new browser and paste your IP into this: 
http://<PUBLIC_IP>:5003
4. Click enter
![screenshot of terminal + browser](images/gcp/gcp_step21.png)

### 5. Public IP Access
URL: http://104.196.212.141:5003
**NOTE: URL is not running anymore after VM is deleted**
![screenshot](images/gcp/gcp_step21.png)
