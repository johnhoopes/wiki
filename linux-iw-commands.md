---
title: Information About Adapters in Linux
description: mostly IW command reference
published: true
date: 2024-06-10T03:41:20.412Z
tags: 
editor: markdown
dateCreated: 2024-06-10T03:41:20.412Z
---

# IW Dev

```
root@dragon-VirtualBox:~# iw dev                                                                                                                    
phy#1                                                                                                                                               
        Interface wlx00c0ca47a92b                                                                                                                   
                ifindex 5                                                                                                                           
                wdev 0x100000001                                                                                                                    
                addr 00:c0:ca:47:a9:2b                                                                                                              
                type managed                                                                                                                        
                txpower 20.00 dBm                                                                                                                   
                multicast TXQ:                                                                                                                      
                        qsz-byt qsz-pkt flows   drops   marks   overlmt hashcol tx-bytes        tx-packets                                          
                        0       0       0       0       0       0       0       0               0 
```
    
# IW PHY
```
root@dragon-VirtualBox:~# iw phy                                                                                                                    
Wiphy phy1                                                                                                                                          
        wiphy index: 1                                                                                                                              
        max # scan SSIDs: 4                                                                                                                         
        max scan IEs length: 2257 bytes                                                                                                             
        max # sched scan SSIDs: 0                                                                                                                   
        max # match sets: 0                                                                                                                         
        Retry short long limit: 2                                                                                                                   
        Coverage class: 0 (up to 0m)                                                                                                                
        Device supports RSN-IBSS.                                                                                                                   
        Supported Ciphers:                                                                                                                          
                * WEP40 (00-0f-ac:1)                                                          <REDACTED>
             Available Antennas: TX 0 RX 0                                                                                                               
        Supported interface modes:                                                                                                                  
                 * IBSS                                                                                                                             
                 * managed                                                                                                                          
                 * AP                                                                                                                               
                 * AP/VLAN                                                                                                                          
                 * monitor                                                                                                                          
                 * mesh point                                                                                                                          
```

# IW SCAN
```
root@dragon-VirtualBox:~# iw dev wlx00c0ca47a92b scan | more                                                                                        
BSS 04:18:d6:93:8b:b1(on wlx00c0ca47a92b)                                                                                                           
        TSF: 860113383905 usec (9d, 22:55:13)                                                                                                       
        freq: 2412                                                                                                                                  
        beacon interval: 100 TUs                                                                                                                    
        capability: ESS Privacy ShortPreamble (0x0031)                                                                                              
        signal: -39.00 dBm                                                                                                                          
        last seen: 0 ms ago                                                                                                                         
        Information elements from Probe Response frame:                                                                                             
        SSID: hoopeslan2                                                                                                                            
        Supported rates: 1.0* 2.0* 5.5* 11.0* 6.0 9.0 12.0 18.0                                                                                     
        DS Parameter set: channel 1                                                                                                                 
        ERP: Use_Protection                                                                                                                         
        Extended supported rates: 24.0 36.0 48.0 54.0                                                                                               
        BSS Load:                                                                                                                                   
```
