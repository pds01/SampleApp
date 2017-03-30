# Requirements
- Create the server (can be local VM or AWS based)
- Configure an OS image (your choice) appropriately.
- Deploy the provided application.
- Make the application available on port 80.
- Ensure that the server is locked down and secure.

# Additional Requiremts
- Allow for scaling of the application
- Build resiliancy 
- Ease of update

# Aproach
- Setup an Autoscaling group for resiliancy and scalability
- Use Code Deploy to publish and update the application on the fly 
- Create an AWS Cloud Fromation template to deploy the solution 

# Components
- 1 x Virtual Private Cloud
- 2 x Subnets
- 1 x Route Table
- 1 x Internet Gateway
- 2 x Security Groups
- 1 x Loadbalancer
- 1 x Lauch Config
- 1 x Autoscaling Group
- 2 x EC2 Redhat Instances
- 1 x Code Deploy Deployment Group
- 1 x Code Deploy Deployment

# Security Considerations
- SeLinux is in place
- Web application runs as non root user
- Web application is proxied across by Apache
- Ports are not open to the world

# Instalation Instructions
- Update the templates SSH key element ""KeyName": "Phil AWS"" with a key thats alreay in your account
- Create a stack on Cloudformation using template_part_1.json
- Ensure status checks are green on the instances
- Update the stack on Cloudformation using template_part_2.json  
- The template outputs the DNS name of the loadbalancer that can be used to view the application

# Updating Sample App Code
- Updated code will need to commied to a GIT repo
- Update the REA2DeploymentGroup element in template_part_2.json with the repo id and commit id
- Use CloudFormation to deploy the new template
- Manual creation of a deployment via CodeDeploy is also possible

# New Learnings
- Cloud Formation
- Ruby Apps
- Passenger (played withit but didnt end up using it)

# Further Improvments Required
Combine templates into one. This requires wait conditions to be setup, but I have been having issues getting the aws tools working on the redhat AMI.
https://forums.aws.amazon.com/thread.jspa?messageID=412308
http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-helper-scripts-reference.html
http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-waitcondition.html
http://cloudacademy.com/blog/working-with-waitcondition-on-awss-cloudformation/

Setup rules for autoscaling


