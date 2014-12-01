audio_cloverHDMI
============
OS X AMD/Nvidia/Iris Pro/HD5000/HD4600/HD4000/HD3000 HDMI audio with Clover
Clover HDMI Audio - No Patching/Persistant

Update: v3 - Yosemite, 9series support

Clover HDMI audio enables HDMI, DP and DVI audio with patched or native Mavericks AppleHDA.kext. HDMI audio ACPI edits are enabled with dsdt edits, edited ssdts or Clover injection/dsdt patching.  Clover provides audio and graphic binary patching while preserving native kext installation.

Credit: 10.10/HD4600 TimeWalker

Installation
  A. Kext Binary Patching (framebuffer, audio controller)
	1. Clover (Use Clover Configurator, Xcode, Property List Editor, etc.)
	   a. Downloads/audio_CloverALC-master/config-hdmi_.....plist
	   b. EFI/Clover/config.plist/Add
	      i.   KernelAndKextsPatches/KextsToPatch/hdmi... 
	      ii.  Devices/Audio/Inject/Layout (1, 2 or 3)  
	      iii. Save
  B. HDMI Audio ACPI Patching (Select 1, 2 or 3)
	1. Clover injection
	   a. Clover/config.plist	
	2. dsdt injection
	   a. Clover/config.plist
	      i. ACPI/DSDT/Name/DSDT.aml
	   b.HDMI audio edited dsdt
	      i. Install EFI/Clover/ACPI/patched/dsdt.aml
	3. ssdt injection
	   a. Clover/config.plist
	      i. ACPI/SSDT/DropTables/SaSsdt 
	   b. HDMI audio edited ssdt
	      i. Installation EFI/Clover/ACPI/patched/SSDT-1.aml (-1 as 	      appropriate)
  C. Restart
  D. Verify HDMI Audio
	1. System Preferences/Sound/Output/select HDMI

Recommendation
  A. Achieve stable system before enabling HDMI audio:
     1. Boot from hard drive
     2. Recognized graphics
     3. Working onboard audio

Issues
  A. Clover 2565 and newer - AMD HDMI audio w/HD4000 may not work
  B. Clover 2570 and newer - HD4000/HDMI audio ssdt may not work
     1. Fix: w/ssdt, use HDMI Audio ACPI patching/Clover Injection/HD4000

Requirements
  A. Clover (2612 or newer)
  B. Mavericks (10.9 or newer)
  C. Patched RealtekALC or native Mavericks AppleHDA.kext
  D. Mavericks recognized and enabled graphics (Intel/AMD/Nvidia as installed)

Required Information (Select one from each category)
  A. Codec
	1. ALC885, 887, 888, 889, 892, 898, 1150
	2. Native AppleHDA,kext, no onboard audio
  B. Layout ID Support (Definitions, Note A, below)
	1. HD4600/AMD/Nvidia
	2. HD4600/AMD/Nvidia
	3. HD4000/HD3000/AMD/Nvidia
  C. Graphics Connector Audio Support
	1. HD46000+ - HDMI, DP, DVI (max 2 audio, 3 video)
	2. HD4000/HD3000 - HDMI, DP (max 1 audio (Note B, below), 2 video)
	3. AMD - HDMI, DP (max 6 DP, 1 HDMI)
	4. Nvidia - HDMI, DP, DVI
	   a. Fermi: 2 audio/video
	   b. Kepler: 4 audio/video
	   c. Maxwell: 4 audio/video
  D. HDMI Audio ACPI patching (Select 1, 2 or 3)
	1. Clover Injection
	   a. HD4600 - Not available
	   b. HD4000
	      i.   Devices/InjectIntelHDMI/YES
	      ii.  Graphics/Intel/Yes
	      iii. Graphics/ig-platform-id/0x0166000a
	   c. HD3000 - Not available
	   d. AMD (without Integrated Graphics)
	      i.   ACPI/DSDT/Fixes/
		 1. NewWay_80000000/YES
		 2. AddHDMI_8000000/YES
	   e. Nvidia - TBA
	2. dsdt patches
	   a. 9series/HD4600/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_9series
	   b. 8series/HD4600/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_8series
	   c. 7series/HD4000/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_hd4000
	   d. 6series/HD4000/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_hd4000
	   e. 7series/HD3000/AMD/Nvidia -
	https://github.com/toleda/audio_hdmi_hd3000
	   f. 6series/HD3000/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_hd3000
	   g. 5series/AMD/Nvidia - 
	https://github.com/toleda/audio_hdmi_5series
	3. edited ssdts
	   a. 9series/HD4600/AMD/Nvidia (AMI UEFI) - 
        https://github.com/toleda/audio_hdmi_8series/tree/master/ssdt_9series
	   b. 8series/HD4600/AMD/Nvidia (AMI UEFI)- 
	https://github.com/toleda/audio_hdmi_8series/tree/master/ssdt_8series
	   c. 7series/HD4000/AMD/Nvidia (AMI UEFI) - 
	https://github.com/toleda/audio_hdmi_uefi/tree/master/ssdt_7series
	   d. 6series/HD3000/AMD/Nvidia (AMI UEFI) - 
	https://github.com/toleda/audio_hdmi_uefi/tree/master/ssdt_6series
	   e. 6series/HD3000/AMD/Nvidia (AMI BIOS) - 
        https://github.com/toleda/audio_hdmi_hd3000/tree/master/ssdt_6series
  E. HDMI Audio framebuffer edits (kext edits, Note C)
	1. Working Clover framebuffer edits (Yosemite)
	   a. HD4600 - config-hdmi_hd4600-100.plist.zip
	   b. HD4000 - config-hdmi_hd4000-100.plist.zip
	   c. HD3000 - config-hdmi_hd3000-100.plist.zip
	   d. AMD/HD77750 - config-hdmi_hd7750-100.plist.zip
	2. Working Clover framebuffer edits (Mavericks)
	   a. HD4600 - config-hdmi_hd4600-92.plist.zip
	   b. HD4600 - config-hdmi_hd4600-90.plist.zip
	   c. HD4000 - config-hdmi_hd4000-90.plist.zip
	   d. HD3000 - config-hdmi_hd3000-90.plist.zip
	   e. AMD/HD77750 - config-hdmi_hd7750-90.plist.zip
  F. OS X version
	1. Yosemite version
	   a. 10.10 (-100) works in 10.10 or newer
	2. Mavericks version
	   a. 10.9.2(-92) works in 10.9.2 or newer, works in 10.9 and 10.9.1
	   b. 10.9.1(-91) works in 10.9.1 or newer
	   c. 10.9 (-90) works in 10.9 or newer

Notes
  A. Layout Definitions
	1 - 3/5/6 audio port analog audio
	2 - 3 audio port analog audio
	3 - HD3000/HD4000 HDMI audio and analog audio
  B. HD4000/HD3000 HDMI audio
	1. Limited to one display w/patched AppleHDA.kext
	2. Supports 2 displays
	   a. Native AppleHDA.kext
	   b. AppleHDA.kext customization - 
https://github.com/toleda/audio_ALCInjection/blob/master/M-Realtek_ALC_AppleHDA_Customization.pdf.zip

  C. Framebuffer kext edits
	1. Intel HD Graphics -
	   https://github.com/toleda/graphics_Intel_framebuffers
	   a. Intel HD4600 - AppleIntelFramebufferAzul.kext
	   b. Intel HD4000 - AppleIntelFramebufferCapri.kext
	   c. Intel HD3000 - AppleIntelSNBGraphicsFB.kext
	2. AMD framebuffer edits - likely specific to particular graphics card
	   a. Edit Guides
	      i.   http://www.insanelymac.com/forum/topic/291117-how-to-make-radeon-desktop-or-mobility-be-working-by-using-clover/
	      ii.   http://www.insanelymac.com/forum/topic/249642-editing-custom-personalities-for-ati-radeon-hd45xxx/

	   b. Kexts
  	      i.   AMD R9/R7/HD7xxx - AMD7000Controller.kext
	      ii.  AMD HD6xxx - AMD6000Controller.kext
	      iii. AMD HD5xxx - AMD5000Controller.kext
	3. Nvidia/GT/GTS/GTX 4xx/5xx/6xx/7xx - Not applicable
  D. Clover/config.plist 
	1. plist Editors
	   a. Clover Configurator (1 window)
	   b. Xcode/Property List Editor/PlistEdit Pro  (multiple windows)
	   c. TextEdit, TextWrangler
	2. Instructions
	   a. Copy specific patch from config-hdmi...plist
	   b. Paste patch to same property in EFI/Clover/config.plist
	   c. Save
  E. HD4600 includes Iris Pro, HD5000 and HD4600
  F. Do not boot config-hdmi_....plist, graphics support only

Tools
  A. Clover Configurator - http://www.osx86.net/files/file/49-clover-configurator/

  B. Clover Wiki - http://clover-wiki.zetam.org/Home

  C. Property List Editor - Xcode, Property List Editor, PlistEdit Pro, TextEdit, etc.

  D. IOReg (Download/Select View Raw) - https://github.com/toleda/audio_ALCInjection/blob/master/IORegistryExplorer_v2.1.zip

  E. DPCIManger - http://sourceforge.net/projects/dpcimanager/

Problem Reporting (include the following information)
  A. Description of HDMI audio problem
	1. OS X version/motherboard model/BIOS version/processor/graphics
	2. Procedure/Guide Used
	4. Copy of IOReg - IOReg_v2.1/File/Save a Copy As…, verify file (not
           ioreg.txt)
	5. EFI/Clover/config.plist
	6. EFI/Clover/misc/debug.log (Set config.plist/Boot/Debug/YES)
	7. EFI/Clover/ACPI/Patched/dsdt.aml (if installed)
	8. EFI/Clover/ACPI/Patched/ssdt.aml (if installed)
  B. Post to
	1. http://www.tonymacx86.com/hdmi-audio/112469-mavericks-hdmi-audio-applehda.html

	2. http://www.insanelymac.com/forum/topic/292999-mavericks-applehda-hdmi-audio/

Credit
TimeWalker75a Post #118, http://www.insanelymac.com/forum/topic/290783-intel-hd-graphics-4600-haswell-working-displayport/page-6#entry1949558
PikeRAlpha https://pikeralpha.wordpress.com/2013/09/19/haswell-hdau-solution/
bcc9 Post #11 - http://www.insanelymac.com/forum/topic/290783-intel-hd-graphics-4600-haswell-working-displayport/?p=1934889

toleda
https://github.com/toleda/audio_cloverHDMI