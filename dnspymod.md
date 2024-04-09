---
title: Using DNSpy to modify a dll
description: 
published: true
date: 2024-04-09T20:29:26.949Z
tags: 
editor: markdown
dateCreated: 2024-04-09T20:28:35.522Z
---

# Borrowed from Pirate Bay

1. Install \<PRODUCT> and get the latest updates during setup. When it restarts and asks for activation, close the window
2. Download dnSpy-net###.zip from:
softpedia dot com/get/Programming/Debuggers-Decompilers-Dissasemblers/dnSpy dot shtml

3. Extract dnSpy-net###.zip to a folder and run dnSpy.exe as administrator! (If you don't, it will not work)
4. In the dnSpy program, click on File -> Open. Navigate to "C:\Program Files (x86)\<PRODUCT>" and click on "product.dll" and click Open
5. The file will open and be highlighted in the left pane. Click on the arrow next to the file name in the left pane to expand the item. A purple item will show, click on the arrow to expand the menu
6. Find the yellow item labeled "PRODUCT.Activation" and click on it. A green item called "ProductActivationService" will show, click on it
7. A bunch of orange names will now show. Find the one called "IsProductActivationRequired() : bool" and right click on it. Click on the option that says "Edit Method (C#) ..."
8. A window with code will open. Within the code, delete lines 13-30 so that the method only shows

public bool IsProductActivationRequired()
{

return true;
}

9. In the code thats left, change "return true" to "return false"

10. At the bottom of the window, click "Compile" and the window will close
11. In the main window of dnSpy, click on File -> Save Module. A window will open, click on "OK"
12. Close the dnSpy program and run PRODUCT. Your product is now "Activated"