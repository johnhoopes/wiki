<!-- TITLE: Hackrf -->
<!-- SUBTITLE: A quick summary of Hackrf -->

# Libraries
libhackrf
hackrf-tools

# Commands
hackrf_info - Is it connected?  What version?
hackrf_transfer - transmit or recieve data  (can use to explore USB rates)  default is 20MB/second  (write to /dev/null... explore disk rates with other options)
 - a amp_enable - On/off... provides 14db gain (varies by freq).  If using osmocom, set to something > 10 to enable.
 - p antenna_enable - adds some dc to the antenna port.  usually off
 - l / -g / -x  - additional gain stages.
 - b - baseband_filter  Default Set filter lower than your sample rate.
 hackrf_spiflash - (reboot after flash)  make sure you update cpld (next step) every time you update firmware
  - w write file.bin
 hackrf_cpldjtag  (reboot after flash)
  -x hackrf_cpld_*.xsvf
	
	
	# My Chinesium HackRF Updates
	For some reason my chinese one has issues updating.  Followed this plus some:
	https://github.com/greatscottgadgets/hackrf/issues/456
	
	So.  In D:\Workspace\SDR\HackRF I have the chinese version mentioned above.  Links also here:
	http://www.mmdvm.club/index.php/h2.html
	
	Did the following.
	1.  Put the HackRF in DFU mode (down reset, down dfu, up reset, up dfu).
	2.  Shows up in windows as LHC device.
	3.  dfu_hackrf_one.bat
	
`	D:\Workspace\SDR\HackRF\ChineseCloneOf__mayhem_v1.3.1_FIRMWARE_WM8731\mayhem_v1.3.1_FIRMWARE_WM8731>dfu_hackrf_one.bat
*** Run HackRF firmware in RAM via LPC DFU ***`
	
 4.  HackRF shows up in Device Manager.
 5.  Then use older alternative fw:
`D:\Workspace\SDR\HackRF\ChineseCloneOf__mayhem_v1.3.1_FIRMWARE_WM8731\mayhem_v1.3.1_FIRMWARE_WM8731>flash_portapack_mayhem_8731.bat
*** Re-flash the HackRF with PortaPack wm8731 firmware from www.mmdvm.club***`

6.  Disconnect USB and it should come up in Mayhem.  (Hit center button from splash screen)
7.  Go to HackRF mode.
8.  Put on the most recent Mayhem.  1.5.4 was current when I worked this out.
`hackrf_update.exe 154_portapack-h1_h2-mayhem.bin`
### IMPORTANT
9.  Disconnect the USB
10.  Double click the rotational knob to save fw update (found that it needed to be powered off up in the github.  Reset will not save things).
11.  Seems to work now?