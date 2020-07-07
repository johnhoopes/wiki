<!-- TITLE: Tclxlroot -->
<!-- SUBTITLE: A quick summary of Tclxlroot -->

	# From https://forum.xda-developers.com/android/development/amazing-temp-root-mediatek-armv8-t3922213
	
	Note that the mtk-su binary says it's for Arm8, uname says arm7, but it worked :)
	

```text
	Get mtk-su
	
	adb push path/to/mtk-su /data/local/tmp/
	adb shell
	cd /data/local/tmp
	chmod 755 mtk-sh
	./mtk-sh
	(cross fingers and then get uid 0)
	

```
	