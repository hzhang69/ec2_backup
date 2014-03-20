Ec2_Backup
==========
Authors:  
Nick Noga		<nnoga@stevens.edu>  
Eli Davis		<edavis1@stevens.edu>  
Paul-Anthony Dudzinski	<pdudzins@stevens.edu>  


INPUT
ec2backup takes as input the volume from amazon, in order to error check this the script will check to see if the volume starts with 'vol-' and has between 8-20 alphanumeric charachers on the assumption that amazon will continue to name thier volumes this way but they might get longer.
