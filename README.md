Practical 2:

Search EC2 > Launch Instance> Name > Windows Server > Create Key Pair > other all same > Lauch instance >> Select instance > Connect> RDP Client> Download Remote Desktop File > Get Password > Upload Private key > Decrypt Password > Copy password > Open rdp file > Connect > Username : Administrator > Password : (Decrypted password) > Windows EC2 Desktop opens >> Amazon Linux > Launch instance > Connect > Linux Terminal opens > commands : ls , ls -la, whoami >> Red Hat > Launch Instance > Connect > SSH Client > Copy command  and Run it in cmd 

Practical 3:

Create basic index.html > Create ZIP file >> AWS Amplify > Create New App > Deploy without Git > Drag and Drop > Save and Deploy >> GitHub Repository > Push local project using Git commands >> git init | git add . | git commit -m "Initial commit" | git branch -M main | git remote add | origin <repo_url> | git push -u origin main >> AWS Amplify > Create New App > GitHub > Select repository > Save and Deploy

Practical 4:

Lambda > Create Function > Author from Scratch > Name > Runtime: Python 3.x > Enable > Architecture: x86_64 > Create Function >> import json   | import logging | logger = logging.getLogger() | logger.setLevel(logging.INFO) | def lambda_handler(event, context): |     length = event['length'] |     breadth = event['breadth'] |     area = calculate_area(length, breadth |    print("Area is:", area) |     logger.info(f"CloudWatch Log Group: | {context.log_group_name}") |     data = { "area": area } | return json.dumps(data)
def calculate_area(length, breadth): |    return length * breadth >> Deploy > Create test event > Invoke Test >> { "length": 23, |  "breadth": 40 }

Practical 5: 

Vpc | subnet | route table | internet gateway | > Make vcp  10.0.0.0/16 > Make public subnet  10.0.1.0/24  > Make private subnet  10.0.0.0/24 > Public and private Route table > Now make association of route table to subnet, publicpublic , privateprivate > Make internet gateway > Attach it to your vpc (right-click)> Create a NAT Gateway > Public Route Table with Internet Gateway:  Route public route table    edit route  internet gateway , destination 0.0.0.0> Private Route Table with Nat Gateway : Route public route table    edit route  nat gateway , destination 0.0.0.0> Make private and public security group > Make a key pair > Make an iam role  create role  aws service  usecase: ec2  give access : AmazonS3FullAccess  create> Make an ec2 in public subnet  ubuntu  auto-assign ip : enable  select exisiting security grp  public sg , IAM : create-s3 > Make an ec2 in private subnet  ubuntu  auto-assign ip : enable  select exisiting security grp  private sg , IAM : create-s3  > Add inbound rule to allow ssh from local computer into public SG  checkup.amazonaws.com  copy ip ,  go in edit inbound ssh , ip paste , > Add inbound rule to make private SG to allow ssh from public  copy ip of public ec2  private ip address , (public ec2 ka private private mai) > Now ssh into public : connect public ec2  ssh client , copy the example line , now open an cmd where your downloaded pem file is , write :1) ssh  execute , 2) now paste the example, execute , > ubuntu will open  write commands  1) sudo apt-get update 2) sudo snap install aws-cli --classic   3) aws s3 ls> NOW a new cmd of same path  write command > scp -i "C:\Users\user-5\vpc-key-pair.pem" "C:\Users\user-5\vpc-key-pair.pem" ubuntu@100.29.184.101:/home/ubuntu/> here there is file path 2 times , the ip is public ec2 public ip then :/home/ubuntu > now in old cmd do  sudo su > you will be taken into home/ubuntu , now do ls , 2 things should be there (snap and pem file) > now here paste the private ec2’s example line , but change the ip to private ip , > the ip will be of public ip , you have to change just the ip to its private ip address . 

Practical 6:

Run command : java -jar jenkins.war > jaihind , jaihind  >> Manage Jenkins > Security >  Users > Create two users. >> Manage Jenkins > Security > Project-based Authorization > Add users > Assign permissions. Signout > Login as second user > Create basic python file > New Item > Freestyle Project >> Build Steps >> Execute Windows Batch Command Command: python -V >> Workspace path: C:\Users\<username>\.jenkins\workspace\pythontest > Copy > new.py >> Configure > Build Steps >> python new.py >> Build Now

Practical 7:

conf > server.xml > line 70: 8081>> bin > cmd: startup.bat >> open Jenkins >> new item > pipeline > html file make > pipeline script : node {    stage('Dev')   stage('QA')    {      input 'QA Deploy'    }    stage('deploy TO PROD'){        bat 'xcopy "C:\\Users\\arydo\\Downloads\\jenkins" "C:\\apache-tomcat-11.0.18\\webapps\\ROOT" /E /I /Y'    }} > build now > proceed > local host /index.html

Practical 8: 
Ec2 ubuntu >> connect >> sudo apt update > sudo apt install ansible -y > ansible –version > nano install_nginx.yml > code: 

---
- name: Install and Start Nginx
  hosts: localhost
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
    - name: Start Nginx Service
      service:
        name: nginx
        state: started
    - name: Create file
      file:
        path: /home/ubuntu/demo.txt
        state: touch
Unbuntu > commands: ls > ansible-playbook -i hosts install_nginx.yml



