<!-- TITLE: Mount S3 -->
<!-- SUBTITLE: Mounting S3 Drives -->

From: https://tuttlem.github.io

```text
sudo apt-get install s3fs
echo MYIDENTITY:MYCREDENTIAL >  ~/.passwd-s3fs
chmod 600  ~/.passwd-s3fs
s3fs your-bucket-name /your/local/folder -o passwd_file=/home/michael/.passwd-s3fs

```
