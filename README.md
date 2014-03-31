Ec2_Backup
==========
Authors:  
Nick Noga		<nnoga@stevens.edu>  
Eli Davis		<edavis1@stevens.edu>  
Paul-Anthony Dudzinski	<pdudzins@stevens.edu>  


Input
==========
ec2backup takes as input the volume from amazon, in order to error check this the script will check to see if the volume starts with 'vol-' and has between 8-20 alphanumeric charachers on the assumption that amazon will continue to name thier volumes this way but they might get longer.

Volume Creation
==========
ec2backup calculates the size of the volume to be twice the size of the directory to backed up except when the file is less than 1 GB. In the smallest case (> 1 GB) ec2backup creates a volume of 2GB in size in order to make the volume more reusable. This assumption is contingent on the tendency for file size to grow and the overall growth of filesize as programs and users generate more data.

Key Pair and Security Group
==========
The Keypair and the Security Group are to come from the AWS_EC2_BACKUP_FLAGS, if these two do not exist the program will error and exit. Only the "security-groups" and "key-name" parameters may be used to pass these two variables. After these variables are checked for existence they are also checked against the users list of available keys and groups. If they do not exist in the list the program will exit. Finally these variables can still cause the program to exit at instance creation time if they are incorrectly configured. One particular case that will cause the program to exit are incorrectly configured ports, ec2_backup does not check for port configuration but will exit if an ssh connection cannot be established.

SSH KEY
==========
ec2_backup always uses the default ssh key pair configured on the system. The program was built to be key agnostic in the sense that it can be passed any ssh keypair via EC2_BACKUP_FLAGS_SSH (using the -i option) but does not check to see that the pair supplied in the flags matches the ssh key baked into the instance at creation time. If there is a key mismatch the program will exit gracefully and print the error output of SSH to STDERR along with a message prefix.
