<!-- TITLE: Btswork -->
<!-- SUBTITLE: A quick summary of Btswork -->


# The various codes for different countries and providers
http://www.mcc-mnc.com/



# Yate - May only be bladerf compatible (nice web interface that I want)
The following build instructions mostly worked.

https://www.evilsocket.net/2016/03/31/how-to-build-your-own-rogue-gsm-bts-for-fun-and-profit/

On 12/17/2019 - I was able to build using the below patch with current pull of yate / yatebts only to discover that they only support bladerf (as of 2018 sometime)
The version that comes with evilsocket



Patch to fix gcc version issues (look like ostream type stuff:
http://yate.null.ro/mantis/view.php?id=416

How to apply the patch
https://nuand.com/forums/viewtopic.php?t=4113



Pulling current code via svn
```
apt install subversion
svn co http://voip.null.ro/svn/yate/trunk yate
svn co http://voip.null.ro/svn/yatebts/trunk/ yatebts
```

# OpenBTS
```
```

# UHD
```
apt install uhd-host libuhd-dev
```

Trying to build from source:

```
sudo apt-get install libboost-all-dev libusb-1.0-0-dev python-mako doxygen python-docutils cmake build-essential
git clone git://github.com/EttusResearch/uhd.git
```

