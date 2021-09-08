

AZ: us-east-1 ---- region: us-east
##################################
US-EAST-1: ---> region o AZ?
vpc-6be79616 
s-g:   sg-2ee31030

US-EAST-2:
vpc-787a1613



IAM ROLE S3 READ-ONLY:
	ec2-for-s3-read-only



-	Configure aws account
-	Login on cli
-	Add ssh key to ec2
-	Create ssh security group
-	Create webserver security group
-	Create ec2 instance
-	Launch ec2 with custom user-data and the 2 security groups
-	Create s3 bucket
-	Upload file
-	Have ec2 user-data read ONLY s3 bucket for crap


aws ec2 run-instances --image-id ami-0443305dabd4be2bc --instance-type t2.micro --key-name ubuntu-wsl  --security-group-ids sg-0fa377428b332c12b sg-099152f90bf8223cc --subnet-id subnet-b20fcdcf --user-data file://webservers.txt



aws ec2 run-instances --image-id ami-0443305dabd4be2bc --instance-type t2.micro --key-name notebook-laburo  --security-group-ids sg-0fa377428b332c12b sg-099152f90bf8223cc --subnet-id subnet-b20fcdcf --user-data file://userdata-webservers.txt

# run instance with access to s3 and a sample image from the static bucket 
aws ec2 run-instances --image-id ami-0443305dabd4be2bc --instance-type t2.micro --key-name notebook-laburo  --security-group-ids sg-0fa377428b332c12b sg-099152f90bf8223cc --subnet-id subnet-b20fcdcf --user-data file://userdata-webservers-and-s3.txt --iam-instance-profile Name="ec2-for-s3-read-only"


