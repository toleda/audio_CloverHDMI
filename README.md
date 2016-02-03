Clover HDMI Audio AppleHDA [Guides]_v1.0  
![alt text](https://github.com/toleda/audio_RealtekALC/blob/master/sound.jpeg)
#audio_cloverHDMI

**OS X Intel HD Graphics/AMD/Nvidia HDMI audio with Clover**  
Clover HDMI Audio - No kext patching/Persistant

**Updates**  
**1/15/16 - El Capitan support, cloverHDMI script**  
12/2/14 - Yosemite, 9series support   
Credit: TimeWalker/10.10+/HD4600 codec patch

Clover HDMI audio enables HDMI, DP and DVI audio with patched or native OS X AppleHDA.kext. HDMI audio ACPI edits are enabled with dsdt edits, edited ssdts or Clover injection/dsdt patching.  Clover provides audio and graphic binary patching while preserving native kext installation.  Supports Intel HD Graphics and/or AMD or Nvidia HDMI audio.

cloverHDMI detects and installs the correct ssdt(s) and patches the Intel framebuffer for the connected display(s) enabling OS X HDMI audio.

Repo downloads: select link, select View Raw

**cloverHDMI**  
Beta  

1. Download: [audio_cloverHDMI-...command](https://github.com/toleda/audio_CloverHDMI/blob/master/audio_cloverHDMI-110.command.zip) (select View Raw)
2. Installs HDMI audio ssdt(s) and edited config.plist
	1. Intel/AMD/Nvidia: HDMI audio **ssdt** (EFI/CLOVER/ACPI/patched/)
	2. Intel: DP2HDMI framebuffer edits (EFI/CLOVER/**config.plist**/KernelAndKextPatches/)
3. Test Drive
	1. Set audio_cloverHDMI-xxx.command/gDebug=1
	2. Copy config.plist to Desktop
	3. Continue with 4. Installation/Step 3
4. Installation (performs all steps in Installation, below) 
	1. Mount EFI
	2. SIP enabled, OK
	3. For Intel, HDMI displays only, unplug DP displays
	4. Double click Downloads/audio_cloverHDMI-...command
	5. Answer y/n questions
	6. Password
	7. Restart
5. Terminal/Shell/Export Text As...
	1. [cloverHDMI-Intel with AMD or Nvidia](https://github.com/toleda/audio_CloverHDMI/blob/master/cloverHDMI-Intel%26AMD:Nvidia)
	2. [cloverHDMI-Intel](https://github.com/toleda/audio_CloverHDMI/blob/master/cloverHDMI-Intel)
	3. [cloverHDMI-AMD or Nvidia](https://github.com/toleda/audio_CloverHDMI/blob/master/cloverHDMI-AMD:Nvidia)
6. Support
	1. OS X: 10.11, 10.10, 10.9, 10.8
	2. Intel/desktop series: 9, 8, 7, 6, 5
	3. Intel/desktop/graphics hd (native GPU Power Management)
		1. Desktop: HD6200, HD4600+, HD4000, HD3000
		2. BRIX/NUC: HD6100, HD6000, HD5500, HD5200, HD5000, HD4000
	4. AMD/default framebuffer (ATY,AMD,RadeonFramebuffer)
		1. R7/R9 3xx, R7/R9 2xx, 7xxx, 6xxx, 5xxx  
		2. Except: GCN 1.1/Hawaii/Bonaire/AMD8000Controller.kext
	5. Nvidia (750, 9xx require Nvidia web drivers)
		1. 9xx, 7xx, 6xx, 5xx, 4xx  
		2. Except: 550, 560, 450 

**Additional Clover HDMI Audio Installation Methods**  

1. [ssdt/dsdt/bootloader methods](https://github.com/toleda/audio_hdmi_guides)

**HDMI Audio/Details**
 
1. [README/HDMI Audio Details](https://github.com/toleda/audio_hdmi_guides)


**Additional Information**

1.	[HDMI audio](https://github.com/toleda/audio_hdmi_guides)  
2.	[HDEF audio](https://github.com/toleda/audio_ALC_guides)

[Problem Reporting](https://github.com/toleda/audio_ALC_guides/blob/master/Problem%20Reporting.md)  

1.	Problem Reporting/Post to: 
2.	Problem Reporting/Attached requested files

Credit  
[TimeWalker75a Post #118](http://www.insanelymac.com/  forum/topic/290783-intel-hd-graphics-4600-haswell-working-displayport/page-6#entry1949558)  
[PikeRAlpha](https://pikeralpha.wordpress.com/2013/09/19/haswell-hdau-solution/)  
[bcc9 Post #11](http://www.insanelymac.com/forum/topic/290783-intel-hd-graphics-4600-haswell-working-displayport/?p=1934889)

toleda
https://github.com/toleda/audio_cloverHDMI