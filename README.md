# Pegasus SpyWare Check for Iphone

<b> Back up The Iphone  </b>

Backup your iPhone with Itunes and encrypted is ON, with Password, just an example:  MyPassword123</b>

i just using the password during backup:  MyPassword123 

Check the result in 
/Users/ahmadrifky/Library/Application Support/MobileSync

We just move it to ~/Desktop

# Prepare the verification tools
<b> Pull Image from Docker </b>

https://docs.mvt.re/en/latest/docker/

git clone https://github.com/mvt-project/mvt.git

cd mvt

docker build -t mvt .

Just run this command in the same directory where the backup file is belong:
<b> docker run --rm -it -v "$PWD:/mnt/tmp" mvt </b>

# Usage

<b> Now start to Decrypt the Backup: </b>

root@ceac05f52f3f:/mnt/tmp# MVT_IOS_BACKUP_PASSWORD="MyPassword123" mvt-ios decrypt-backup -d /home/cases /mnt/tmp/Backup

<b> Make the output directory: </b>
mkdir /home/output

do the basic check:

mvt-ios check-backup --output /home/output/ /home/cases/

check in the /home/output is there any suspicious thing detected:

/home/output# ls -ltr|grep -i detect

***************************************

# Check the compromise
<b> download the STIX file </b>
mvt-ios download-iocs

<b> indicators "NSO Group Pegasus Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2

<b> indicators "Cytrox Predator Spyware Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-12-16_cytrox_cytrox.stix2

<b> indicators "RCS Lab Spyware Indicators of Compromise" to </b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_mvt-project_mvt-indicators_main_2022-06-23_rcs_lab_rcs.stix2

<b> indicators "Stalkerware Indicators of Compromise" to <b> 

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AssoEchap_stalkerware-indicators_master_generated_stalkerware.stix2
***************************************

Check one by one by fire these commands below: 
mvt-ios check-backup --output /home/output/ /home/cases/ --iocs   <full path name of the stix file>
