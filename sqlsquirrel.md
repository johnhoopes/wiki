<!-- TITLE: Sqlsquirrel -->
<!-- SUBTITLE: A quick summary of Sqlsquirrel -->

[Back to Tools](/tools)

Website: http://squirrel-sql.sourceforge.net/

# Summary
SQL Squirrel is like downloading the development tools for various sql servers.  It connects using the user id and password and allows sql requests to be sent.  It also presents the results in table form.  Ideally we'd have command line clients for all database, but to my knowlege no such collection of clients exists.
# Installation
The hardest part of installation is getting the jdbc drivers for each sql server.  As I collect them I will put attach them to this document.

# Training
Decent Introduction Video:
https://www.youtube.com/watch?v=NldYgRAANOo


# Drivers
Access - http://ucanaccess.sourceforge.net/site.html#clients

Import the .jar file in the main directory created by opening the .zip plus all of the .jars in the lib directory
Class name is net.ucanaccess.jdbc.UcanaccessDriver

Example URL:   jdbc:ucanaccess:///home/gord/Documents/Database1.accdb;showSchema=true
(I used it successfully to open an mdb file)

