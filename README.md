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
