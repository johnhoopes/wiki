<!-- TITLE: Extractfrompfx -->
<!-- SUBTITLE: A quick summary of Extractfrompfx -->

#  Extracting Certificate and Private Key Files from a .pfx File
(from https://wiki.cac.washington.edu/display/infra/Extracting+Certificate+and+Private+Key+Files+from+a+.pfx+File)

Skip to end of metadata

    Created by Michael Brogan, last modified on Nov 04, 2013

Go to start of metadata
Purpose

Customers sometimes have a need to export a certificate and private key from a Windows computer to separate certificate and key files for use elsewhere. Windows doesn't provide the means to complete this process.

Exporting Certificates from the Windows Certificate Store describes how to export a certificate and private key into a single .pfx file. Follow the procedure below to extract separate certificate and private key files from the .pfx file.
Procedure

    Take the file you exported (e.g. certname.pfx) and copy it to a system where you have OpenSSL installed. Note: the *.pfx file is in PKCS#12 format and includes both the certificate and the private key.
    Run the following command to export the private key: openssl pkcs12 -in certname.pfx -nocerts -out key.pem -nodes
    Run the following command to export the certificate: openssl pkcs12 -in certname.pfx -nokeys -out cert.pem
    Run the following command to remove the passphrase from the private key: openssl rsa -in key.pem -out server.key 