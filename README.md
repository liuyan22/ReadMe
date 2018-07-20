# ReadMe
# **THIS IS THE README FILE FOR THE DATA SCIENCE TOOLKIT**
This README file documents a detailed outline of the steps required to configure your own Jupyter Data Science Notebook Server on Amazon Web Services.

# **STEPS**
# **Step 1:**  
Create SSH using command *ssh-keygen -t rsa * and *ssh-keygen -t rsa -f ~/.ssh/newname.pub*
# **Step 2:** 
Create a Amazon EC2 account
# **Step 3:** 
Add security group where the security group added are: 
            HTTP TCP 80
            PostgreSQL TCP 5432
            SSH TCP 22
            Custom TCP Rule TCP 27016
            HTTPS TCP 443
# **Step 4:** 
Launch Amazon EC2 instance. First choose ubuntu AMI, because AMI works well for Docker. Using the security group set up in the above step and add 20G storage
# **Step 5:** 
Install Docker. In git bash, using command *curl -sSl https://get.docker.com | sh* to get docker, then using 
 command *sudo usermod -aG docker ubuntu*, reconnect/SSH to AWS using command *Docker -v*
# **Step 6:** 
Use command *Docker pull jupyter/datascience-notebook* to obtain the correct image
# **Step 7:** 
Run data science notebook in the securied security environment using command *docker run -p 80:8888 -v /home/ubuntu:/home/jovyan jupyter/datascience-notebook* and then copy and paste token to ip:443 to open jupyter
# **Step 8:** 
Security: notebook uses token to authenticate requests
 
# **Diagram:** 
Local (my machine): create id_rsa - local SSH keypair --(SSH)--> AWS: id_rsa.pub - id_rsa(remote SSH Keypair) 
 --(SSH)--> GitHub
# **Budget for 3 different kinds EC2 instances:** 
 Tier:             t2.micro  t2.small  t2.medium
 RAM:              1G        2G        4G
 CPU credits/Hour: 6         12        24
 Price/3month:     25.41     48.12     101.61
