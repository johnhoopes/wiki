

<!-- TITLE: Msfconsole -->
<!-- SUBTITLE: A quick summary of Msfconsole -->


Running with a resource file:
msfconsole -r resourcefile.rc

Sound effects:
load sounds

If you've already got a payload handler running
set DisablePayloadHandler true

setg will carry into multiple exploits
LHOST, LPORT etc.


Finding all exploits with RPORT == X
This question comes up quite a bit in the IRC channel: How can I see all exploits for a given port? You can do it easily with IRB

msf > irb >> framework.exploits.each_module { |n,e| x=e.new; print_good("#{e.fullname}: #{x.datastore['RPORT']}") if x.datastore['RPORT'].to_i == 445 }; nil

Just replace 445 with the port you are looking for. If you want aux modules, you may replace framework.exploits with framework.auxiliary. 

