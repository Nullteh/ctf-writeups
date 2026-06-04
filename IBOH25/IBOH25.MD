# IBOH25 Write-up \- Whiteberry

# 

# Forensic

## **Bloom**

![](IBOH25/images_IBOH25/0.png)

Crack IKE hash with hashcat  
![](IBOH25/images_IBOH25/1.png)  
We got **bloom25**  
So the password for the encrypted zip will be **bloom25\_boh25** as stated by the http packet

Decrypt **espoused-key.zip** with **bloom25\_boh25**, which lets us read **inbound-outbound.txt**  
**![](IBOH25/images_IBOH25/2.png)**  
Head to Wireshark \-\> Edit \-\> Preference \-\> Protocol \-\> ESP \-\> ESP SAs **Edit…**  
Insert the info from the txt file into ESP SAs  
![](IBOH25/images_IBOH25/3.png)

The ESP packet now visible and we find the flag at packet 197 from /api-keys.txt  
![](IBOH25/images_IBOH25/4.png)

## **Hive**

Load **NTUSER.DAT** into RegistryExplorer  
Found **evil** in ROOT\Software\Microsoft\Windows\CurrentVersion\Run  
![](IBOH25/images_IBOH25/5.png)  
![](IBOH25/images_IBOH25/6.png)

Decode value from **Base64**  
![](IBOH25/images_IBOH25/7.png)

## **Dumps**

Manually read through the **strings** inside the app.exe.dmp  
![](IBOH25/images_IBOH25/8.png)

Found point of interest  
![](IBOH25/images_IBOH25/9.png)

Decode it through vigenere  
![](IBOH25/images_IBOH25/10.png)

## 

## **Now I'm here, now I'm not**

Load **memory.raw** with MemProcFS with **\-Forensic 2** (for file retrieval)  
![](IBOH25/images_IBOH25/11.png)

Found encrypted pdf  
![](IBOH25/images_IBOH25/12.png)

Generate hash with pdf2john and crack with john  
![](IBOH25/images_IBOH25/13.png)  
Password is **pumpkinpie**

Edit with adobe acrobat  
![](IBOH25/images_IBOH25/14.png)  
Flag is behind the large text block  
![](IBOH25/images_IBOH25/15.png)

# Misc

## **Bleep Bloop**

Decode the sound with **RX-SSTV**  
![](IBOH25/images_IBOH25/16.png)
