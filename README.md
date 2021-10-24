# Deploying code-server on AWS EC2

This is the cloudFormation template is creating an Ubuntu EC2 instance and deploy code-server in the browser. You can code any machine including your ipad, iphone, android mobile devices, computer, etc.
<br></br>

**Steps:**


**1. Select the desired AWS Region where you want to create your ec2 server**

![Selecting_desired_AWS_Region.png](docs/Selecting_desired_AWS_Region.png?raw=true)

> You will have to use an existing key pair. If you don't have one already, create a new key pair after selecting your desired AWS Region.

**2. Create CloudFromation stack with new resources**

![Create_a_CloudFromation_Stack](docs/Create_a_CloudFromation_Stack.png?raw=true)

**3. Upload the CloudFromation template**

![Upload_the_CloudFormation_Template](docs/Upload_the_CloudFormation_Template.png?raw=true)


**4. Specify stack details**

![Specify_stack_details_stackName_KeyPairName](docs/Specify_stack_details_stackName_KeyPairName.png?raw=true)

> You can give any Stack name you like. However, you must have an existing key pair you have already created before. 

> Instance name will be "stackName" in this case it will be vscode-server. Please refer the template for instance properties/Tags.
```
CodeServer:
    Type: AWS::EC2::Instance
    Properties:
      # Ubuntu
      ImageId: ami-09e67e426f25ce0d7
      InstanceType: t2.micro
      KeyName: !Ref KeyPairName
      IamInstanceProfile: !Ref CodeServerEC2Profile
      SecurityGroupIds:
        - !GetAtt CodeServerSecurityGroup.GroupId
      Tags:
        - Key: Name
          Value: !Sub ${AWS::StackName}
        - Key: server
          Value: vscode
```

> Click next to move all the way the last step "Review" without making any other change 

**5. Review and create stack**

![Review_and_create_stack](docs/Review_and_create_stack.png?raw=true)
<br></br>

> After stack creation is complete check your ec2 console for your vscode-server

![Stack_created](docs/Stack_created.png?raw=true)
<br></br>

>ec2 console

![Ec2_instance_created](docs/Ec2_instance_created.png?raw=true)
<br></br>

**6. Navigate the server**

Once your instance starts, you can simply navigate to the public IP address and get forwarded to a secure version of code-server, which will be proxied behind your GitHub account (the first one you log in with). Login to your GitHub account. For information on how this works, see [code-server --link](https://github.com/cdr/code-server#cloud-program-%EF%B8%8F).**


![Navigate_the_server](docs/Navigate_the_server.png?raw=true)
<br></br>

**7. Select theme and open folder**

![Select_themes_and_open_folder](docs/Select_themes_and_open_folder.png?raw=true)


- ### Original code and more information for deploying on AWS can be found here

    <https://github.com/cdr/deploy-code-server/blob/main/guides/aws-ec2.md>


* ### Deploying code-server to various cloud hosting platforms

    <https://github.com/cdr/deploy-code-server>


- ### Original code and more information for deploying on AWS can be found here:

    <https://github.com/cdr/code-server>
