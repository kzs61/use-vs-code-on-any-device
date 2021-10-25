# Deploying `code-server` on AWS ec2 server

This is the cloudFormation template is creating an Ubuntu EC2 instance and deploy code-server in the browser. You can use <a align="left"> </a> <a href="https://code.visualstudio.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/visualstudio_code/visualstudio_code-icon.svg" alt="vscode" width="15" height="15"/> </a>   [VS Code](https://code.visualstudio.com) any machine including your ipad, iphone, android mobile devices, computer, etc.

<br></br>

## Steps

<br></br>

## 1. Select the desired AWS region where you want to create your ec2 server

![Selecting_desired_AWS_Region.png](img/Selecting_desired_AWS_Region.png?raw=true)


_You will have to use an existing `key pair`. If you don't have one already, create a new key pair after selecting your desired AWS Region._
<br></br>

## 2. Create CloudFromation stack with new resources

![Create_a_CloudFromation_Stack](img/Create_a_CloudFromation_Stack.png?raw=true)
<br></br>

## 3. Upload the CloudFromation template

![Upload_the_CloudFormation_Template](img/Upload_the_CloudFormation_Template.png?raw=true)
<br></br>

## 4. Specify stack details
![Specify_stack_details_stackName_KeyPairName](img/Specify_stack_details_stackName_KeyPairName.png?raw=true)
<br></br>

_Name your new stack. You must have an existing `key pair` you have already created before. 
Instance name will be the stack name you give. Please refer the template for instance properties/Tags._
<br></br>

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

<br></br>
_Click_ `Next` _to move all the way the last step_ `Review` _without making any other change_ 
<br></br>


## 5. Review and create stack

![Review_and_create_stack](img/Review_and_create_stack.png?raw=true)
<br></br>

_After stack creation is complete check your ec2 console for your_ `vscode-server`
<br></br>

![Stack_created](img/Stack_created.png?raw=true)
<br></br>

![Ec2_instance_created](img/Ec2_instance_created.png?raw=true)
<br></br>


## 6. Navigate the server

_Once your instance starts, you can simply navigate to the public IP address and get forwarded to a secure version of code-server, which will be proxied behind your GitHub account (the first one you log in with). Login to your GitHub account. For information on how this works, see_ [code-server](https://github.com/cdr/code-server#cloud-program-%EF%B8%8F)
<br></br>

![Navigate_the_server](img/Navigate_the_server.png?raw=true)
<br></br>

## 7. Select a theme and open folder

![Select_themes_and_open_folder](img/Select_themes_and_open_folder.png?raw=true)

<br></br>

# Using VS Code on iPad

![installing_extensions](caption/Installing_extensions.mp4?raw=true)

![clone_repo](caption/Clone_repo_from_github.mp4?raw=true)


<br></br>

## Reference

See the original code and more information for [deploying on AWS](https://github.com/cdr/deploy-code-server/blob/main/guides/aws-ec2.md)

Some additional lines added to user data in this CloudFromation template which is slightly different than the [original user data](https://github.com/cdr/deploy-code-server/blob/main/deploy-vm/launch-code-server.sh).

See the [troubleshooting guide](../deploy-vm#troubleshooting) if you are unable to connect after some time.

[Deploying code-server on various cloud platforms](https://github.com/cdr/deploy-code-server)



## 
<br>

<a align="left"> </a> <a href="https://code.visualstudio.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/visualstudio_code/visualstudio_code-icon.svg" alt="vscode" width="40" height="40"/> </a> 

<a href="https://aws.amazon.com/cloudformation/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/amazon_cloudformation/amazon_cloudformation-icon.svg" alt="aws" width="40" height="40"/> </a> 

<a href="https://www.gnu.org/software/bash/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/></a> 
