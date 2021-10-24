# Deploying `code-server` on AWS ec2 server

This is the cloudFormation template is creating an Ubuntu EC2 instance and deploy code-server (VSCode) in the browser. You can code any machine including your ipad, iphone, android mobile devices, computer, etc.



## Steps:

## 1. Select the desired AWS region where you want to create your ec2 server

![Selecting_desired_AWS_Region.png](docs/Selecting_desired_AWS_Region.png?raw=true)


_You will have to use an existing `key pair`. If you don't have one already, create a new key pair after selecting your desired AWS Region._


## 2. Create CloudFromation stack with new resources

![Create_a_CloudFromation_Stack](docs/Create_a_CloudFromation_Stack.png?raw=true)


## 3. Upload the CloudFromation template

![Upload_the_CloudFormation_Template](docs/Upload_the_CloudFormation_Template.png?raw=true)

## 4. Specify stack details

![Specify_stack_details_stackName_KeyPairName](docs/Specify_stack_details_stackName_KeyPairName.png?raw=true)

_Name your new stack. You must have an existing `key pair` you have already created before. 
Instance name will be the stack name you give. Please refer the template for instance properties/Tags._
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

_Click_ `Next` _to move all the way the last step_ `Review` _without making any other change_ 


## 5. Review and create stack

![Review_and_create_stack](docs/Review_and_create_stack.png?raw=true)


_After stack creation is complete check your ec2 console for your_ `vscode-server`

![Stack_created](docs/Stack_created.png?raw=true)

<br></br>

![Ec2_instance_created](docs/Ec2_instance_created.png?raw=true)


## 6. Navigate the server

_Once your instance starts, you can simply navigate to the public IP address and get forwarded to a secure version of code-server, which will be proxied behind your GitHub account (the first one you log in with). Login to your GitHub account. For information on how this works, see_ [code-server](https://github.com/cdr/code-server#cloud-program-%EF%B8%8F)


![Navigate_the_server](docs/Navigate_the_server.png?raw=true)


## 7. Select a theme and open folder
![Select_themes_and_open_folder](docs/Select_themes_and_open_folder.png?raw=true)


<br></br>

## Reference

See the original code and more information for [deploying on AWS](https://github.com/cdr/deploy-code-server/blob/main/guides/aws-ec2.md)

Some additional lines added to user data in this CloudFromation template which is slightly different than the [original user data](https://github.com/cdr/deploy-code-server/blob/main/deploy-vm/launch-code-server.sh).

See the [troubleshooting guide](../deploy-vm#troubleshooting) if you are unable to connect after some time.

[Deploying code-server on various cloud platforms](https://github.com/cdr/deploy-code-server)



## 
<br>

<a align="left"> </a> <a href="https://code.visualstudio.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/visualstudio_code/visualstudio_code-icon.svg" alt="vscode" width="100" height="100"/> </a> 

<a href="https://aws.amazon.com/cloudformation/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/amazon_cloudformation/amazon_cloudformation-icon.svg" alt="aws" width="100" height="100"/> </a> 

<a href="https://www.gnu.org/software/bash/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="100" height="100"/></a> 
