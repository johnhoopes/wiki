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
	