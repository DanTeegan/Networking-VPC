# Networking

## Region & Availability zones

- Region is a close cluster of data centres.
- Within the region we have availability zone, which are logically connected but physically segregated data centres inside a region.

## Creating the VPC
#### 1) Search for VPC in the AWS dashboard and click VPC

![](images/vpc1.png)

##### 2) Click on “Your VPC” on the left and then “Create VPC”
![](images/vpc2.png)

##### 3) Give the VPC a name tag and IPv4 CIDR block and click create
![](images/vpc3.png)

## Creating the Internet Gateway IG

##### 1) Click on Internet gateways on the left hand side
![](images/vpc4.png)

##### 2) Add a name tag remember to use correct naming conventions. In the tag options add a new tag with a key of name and value of the nametag. I have added IGW in the name. Then click on create internet gateway
![](images/vpc5.png)

##### 3) Next click on actions in the top right and then attach to VPC

![](images/vpc6.png)

##### 4) Then attach the VPC that you created previously. And click on attach internet gateway. This will succesfully create the internet gateway

![](images/vpc7.png)

## Creating a Subnet

##### 1) Click on Subnets located in the left hand side toolbar

![](images/vpc8.png)

##### 2) Then click on create subnet

![](images/vpc9.png)

##### 3) Creating public subnet! Fill in the information for the subnet. Remember correct naming conventions. I selected the VPC I recently created and used the same CIDR block IP. Once added click on create

![](images/vpc10.png)

##### 4) Click create subnet to be taken back to this page. Creating private subnet! Add the same information for the public subnet however the CIDR block IP changes slightly as seen below

![](images/vpc11.png)

## Creating a Route Table

##### 1) On the left hand toolbar click on route table

![](images/vpc12.png)

##### 2) Have the public route selected and click actions and edit routes

![](images/vpc13.png)

##### 3) Then add a destination and target. The target I used was the internet gateway created earlier. Then click save routes.

![](images/vpc14.png)

##### 4) One the public route click on subnet associations and then edit subnet associations.

![](images/vpc15.png)

##### 5) Select the public subnet and click on save.

![](images/vpc16.png)

## Creating a Network ACL

##### 1) On the left hand side toolbar under security click on Network ACLs and then click create network ACL.

![](images/vpc17.png)

##### 2) Enter a name tag. Remember naming conventions I added NACL into this nametag. I selected the VPC created previously and clicked on create.

![](images/vpc18.png)

##### 3) I then clicked edit inbound rules of the NACL just created and added the following:

![](images/vpc19.png)

##### 4) I then clicked on edit outbound rules and added the following. I allowed all traffic out. I then clicked save.

![](images/vpc20.png)

##### 5) Then click on subnet associations and edit subnet associations.

![](images/vpc21.png)

##### 6) In the subnet associations select the public subnet created earlier and select edit 

![](images/vpc22.png)

## Creating a new EC2 Instance to check the VPC is working

##### 1) I created a new EC2 Instance and went through the configuration. One the page below remember to add the VPC and subnet previously created.

![](images/vpc23.png)

##### 2) Once the EC2 instance has been created I then SSH into the VM using the VM IP address
```python
ssh -i ~/.ssh/DevOpsStudents.pem ubuntu@VM_IP_ADRESS
```

![](images/vpc24.png)

##### 3) I went into root using ```sudo su``` and then installed Nginx on the VM using ``` apt-get install nginx```

![](images/vpc25.png)

##### 4) sing the EC2 instances IP address we can see Nginx has installed succesfully. This means our VM has access to the internet

![](images/vpc26.png)