# Pegasus SpyWare Check for Iphone

<b> Back up The Iphone  </b>

Backup your iPhone with Itunes and encrypted is ON, with Password YOUR_PASSWORD</b>

i just using the password during backup:  YOUR_PASSWORD  

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
docker run --rm -it -v "$PWD:/mnt/tmp" mvt

# Usage

<b> Now start to Decrypt the Backup: </b>

root@ceac05f52f3f:/mnt/tmp# MVT_IOS_BACKUP_PASSWORD="YOUR_PASSWORD" mvt-ios decrypt-backup -d /home/cases /mnt/tmp/Backup

<b> Make the output directory: </b>
mkdir /home/output

do the basic check:

mvt-ios check-backup --output /home/output/ /home/cases/

check in the /home/output is there any suspicious thing detected:

/home/output# ls -ltr|grep -i detect

***************************************

# Check the compromise
<b> indicators "NSO Group Pegasus Indicators of Compromise" to </b>

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2

indicators "Cytrox Predator Spyware Indicators of Compromise" to

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-12-16_cytrox_cytrox.stix2

indicators "RCS Lab Spyware Indicators of Compromise" to

/root/.local/share/mvt/indicators/raw.githubusercontent.com_mvt-project_mvt-indicators_main_2022-06-23_rcs_lab_rcs.stix2

indicators "Stalkerware Indicators of Compromise" to

/root/.local/share/mvt/indicators/raw.githubusercontent.com_AssoEchap_stalkerware-indicators_master_generated_stalkerware.stix2
***************************************


mvt-ios check-backup --output /home/output/ /home/cases/ --iocs   /root/.local/share/mvt/indicators/raw.githubusercontent.com_AmnestyTech_investigations_master_2021-07-18_nso_pegasus.stix2
