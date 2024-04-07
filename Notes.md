# QUESTION 1 : 
How to change the default profile from the aws command line interface ?
Solution : 
 1. Go to iam create user.
 2. Goto security credential and creta access keys
 3. Download the access keys 
 4. Download the latest version aws cli
 5. Install it
 6. Run aws configure to access aws cli by adding credentilas that is security accessid and keys.
 7. Now you take help and access all the things that ou were doing with the console.
 8. aws ec2 help
 9. aws ec2 describe-instances

 ## HANDLING  MULTIPLE AWS ACCOUNTS 
     1.Create multiple profile from different aws accounts
     2. To create profiles use commands : aws configure --profile account1  ------> add the credentials of the user with that aws accounts.
     3. Repeat same steps for multiple aws accounts.
     4. By default the first aws account is set default 

  ## Solution -------> Configure the changes in /.aws/coonfig ------> edit the default part and define the profile you want to make it default.

