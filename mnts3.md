<!-- TITLE: Mnts 3 -->
<!-- SUBTITLE: A quick summary of Mnts 3 -->

From: https://tuttlem.github.io

```text
sudo apt-get install s3fs
echo MYIDENTITY:MYCREDENTIAL >  ~/.passwd-s3fs
chmod 600  ~/.passwd-s3fs
s3fs your-bucket-name /your/local/folder -o passwd_file=/home/michael/.passwd-s3fs

```
