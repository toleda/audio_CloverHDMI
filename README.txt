audio_cloverHDMI
============
OS X AMD/Nvidia/HD5K/HD4K/HD3K HDMI audio with Clover
Clover HDMI Audio - No Patching/Persistant

Clover HDMI audio enables HDMI, DP and DVI audio with patched or native Mavericks AppleHDA.kext. HDMI audio ACPI edits are enabled with dsdt edits, edited ssdts or Clover injection/dsdt patching.  Clover provides audio and graphic binary patching while preserving native kext installation.

Recommendation
  1. Achieve stable system before enabling HDMI audio:
     1. Boot from hard drive
     2. Recognized graphics
     3. Working onboard audio

Requirements
  1. Clover (2612 or newer)
  2. Mavericks (10.9 or newer)
  3. Patched RealtekALC or native Mavericks AppleHDA.kext
  4. Mavericks recognized and enabled graphics (Intel/AMD/Nvidia as installed)

Required Information (Select one from each category)
  1. Codec
	1. ALC885, 887, 888, 889, 892, 898, 1150
	2. Native AppleHDA,kext, no onboard audio
  2. Layout ID Support (Definitions, Note 1, below)
	1. HD4600/AMD/Nvidia
	2. HD4600/AMD/Nvidia
	3. HD4000/HD3000/AMD/Nvidia
  3. Graphics Connector Audio Support
	1. HD46000+ - HDMI, DP, DVI (max 2 audio, 3 video)
	2. HD4000/HD3000 - HDMI, DP (max 1 audio (Note 2, below), 2 video)
	3. AMD - HDMI, DP (max 6 DP, 1 HDMI)
	4. Nvidia - HDMI, DP, DVI (max Fermi: 2 audio/video, Kepler: 4 audio/video)
  4. HDMI Audio ACPI patching (Select 1, 2 or 3)
	1. Clover Injection
	   1. HD4600 - Not avialable
	   2. HD4000
	      1. Devices/InjectIntelHDMI/YES
	      2. Graphics/Intel/Yes
	      3. Graphics/ig-platform-id/0x0166000a
	   3. HD3000 - Not avialable
	   4. AMD (without Integrated Graphics)
	      1. ACPI/DSDT/Fixes/
		 1. NewWay_80000000/YES
		 2. AddHDMI_8000000/YES
	   5. Nvidia - TBA
	2. dsdt patches (Intel motherboard series/Intel graphics/discrete graphics)
	   1. 8series/HD4600/AMD/Nvidia - https://github.com/toleda/audio_hdmi_8series
	   2. 7series/HD4000/AMD/Nvidia - https://github.com/toleda/audio_hdmi_uefi
	   3. 6series/HD4000/AMD/Nvidia - https://github.com/toleda/audio_hdmi_hd4000
	   4. 7series/HD3000/AMD/Nvidia - https://github.com/toleda/audio_hdmi_hd3000
	   5. 6series/HD3000/AMD/Nvidia - https://github.com/toleda/audio_hdmi_hd3000
	   6. 5series/AMD/Nvidia - https://github.com/toleda/audio_hdmi_5series
	3. edited ssdts (Intel motherboard series/Intel graphics/discrete graphics)
	   1. 8series/HD4600/AMD/Nvidia (AMI UEFI)
	      - https://github.com/toleda/audio_hdmi_8series/tree/master/ssdt_8series
	   2. 7series/HD4000/AMD/Nvidia (AMI UEFI)
	      - https://github.com/toleda/audio_hdmi_uefi/tree/master/ssdt_7series
	   3. 6series/HD3000/AMD/Nvidia (AMI UEFI)
	      - https://github.com/toleda/audio_hdmi_uefi/tree/master/ssdt_6series
	   4. 6series/HD3000/AMD/Nvidia (AMI BIOS)
	      - https://github.com/toleda/audio_hdmi_hd3000/tree/master/ssdt_6series
  5. HDMI Audio framebuffer edits (kext edits, Note 3)
	1. Working Clover framebuffer edits
	   1. HD4600 - config-hdmi_hd4600-92.plist.zip
	   2. HD4600 - config-hdmi_hd4600-90.plist.zip
	   3. HD4000 - config-hdmi_hd4000-90.plist.zip
	   4. HD3000 - config-hdmi_hd3000-90.plist.zip
	   5. AMD/HD77750 - config-hdmi_hd7750-90.plist.zip
  6. Mavericks version
	1. 10.9.2(-92) works in 10.9.2 or newer, works in 10.9 and 10.9.1
	2. 10.9.1(-91) works in 10.9.1 or newer
	3. 10.9 (-90) works in 10.9 or newer

Installation
  1. Kext Binary Patching (framebuffer, audio controller)
     1. Clover (Use Clover Configurator, Xcode, Property List Editor, etc.)
	1. Downloads/audio_CloverALC-master/config-hdmi_.....plist
	2. EFI/Clover/config.plist/Add
	  1. KernelAndKextsPatches/KextsToPatch/hdmi... (hdmi audio patch(es))
	  2. Devices/Audio/Inject/Layout (1, 2 or 3)  
	  3. Save
  2. HDMI Audio ACPI Patching (Select 1, 2 or 3)
     1. Clover injection (See above, Requirements/4. HDMI Audio ACPI patching/1.)
	1. Clover/config.plist	
     2. dsdt injection
	1. Clover/config.plist
	   1. ACPI/DSDT/Name/DSDT.aml
	2.HDMI audio edited dsdt
	   1. Install EFI/Clover/ACPI/patched/dsdt.aml
     3. ssdt injection
	1. Clover/config.plist
	   1. ACPI/SSDT/DropTables/SaSsdt 
	2. HDMI audio edited ssdt
	   1. Installation EFI/Clover/ACPI/patched/SSDT-1.aml (-1 as appropriate)
  3. Restart
  4. Verify HDMI Audio
     1. System Preferences/Sound/Output/select HDMI

Issues
  1. Clover 2565 and newer - AMD HDMI audio w/HD4000 may not work
  2. Clover 2570 and newer - HD4000/HDMI audio ssdt may not work
     1. Fix: w/ssdt, use HDMI Audio ACPI patching/Clover Injection/HD4000 (above)

Notes
  1. Layout Definitions
	1 - 3/5/6 audio port analog audio
	2 - 3 audio port analog audio
	3 - HD3000/HD4000 HDMI audio and analog audio
  2. HD4000/HD3000 HDMI audio
	1. Limited to one display w/patched AppleHDA.kext
	2. Supports 2 displays
	   1. Native AppleHDA.kext
	   2. AppleHDA.kext customization, see https://github.com/toleda/audio_ALCInjection/blob/master/M-Realtek_ALC_AppleHDA_Customization.pdf.zip
  3. Framebuffer kext edits
	1. Intel HD Graphics - see https://github.com/toleda/graphics_Intel_framebuffers
	   1. Intel HD4600 - AppleIntelFramebufferAzul.kext
	   2. Intel HD4000 - AppleIntelFramebufferCapri.kext
	   3. Intel HD3000 - AppleIntelSNBGraphicsFB.kext
	2. AMD framebuffer edits - likely specific to particular graphics card
	   1. Edit Guides
	      1. http://www.insanelymac.com/forum/topic/291117-how-to-make-radeon-desktop-or-mobility-be-working-by-using-clover/
	      2. http://www.insanelymac.com/forum/topic/249642-editing-custom-personalities-for-ati-radeon-hd45xxx/
	   2. Kexts
  	      1. AMD R9/R7/HD7xxx - AMD7000Controller.kext
	      2. AMD HD6xxx - AMD6000Controller.kext
	      3. AMD HD5xxx - AMD5000Controller.kext
	3. Nvidia/GT/GTS/GTX 4xx/5xx/6xx/7xx - Not applicable
  4. Clover/config.plist 
	1. plist Editors
	   1. Clover Configurator (1 window)
	   2. Xcode/Property List Editor/PlistEdit Pro  (multiple windows)
	   3. TextEdit, TextWrangler
	2. Instructions
	   1. Copy specific patch from config-hdmi...plist
	   2. Paste patch to same property in EFI/Clover/config.plist
	   3. Save
  5. Do not boot config-hdmi_....plist, graphics support only

Tools:
  1. Clover Configurator - http://www.osx86.net/files/file/49-clover-configurator/
  2. Clover Wiki - http://clover-wiki.zetam.org/Home
  3. Property List Editor - Xcode, Property List Editor, PlistEdit Pro, TextEdit, etc.
  4. IOReg (View Raw) - https://github.com/toleda/audio_ALCInjection/blob/master/IORegistryExplorer_v2.1.zip

Problem Reporting (include the following information)
  1. Description of HDMI audio problem
	1. OS X version/motherboard model/BIOS version/processor/graphics
	2. Procedure/Guide Used
	4. Copy of IOReg - IOReg_v2.1/File/Save a Copy As…, verify file (not
           ioreg.txt)
	5. EFI/Clover/config.plist
	6. EFI/Clover/misc/debug.log (Set config.plist/Boot/Debug/YES)
	7. EFI/Clover/ACPI/Patched/dsdt.aml (if installed)
	8. EFI/Clover/ACPI/Patched/ssdt.aml (if installed)
  2. Post to:
	1. http://www.tonymacx86.com/hdmi-audio/112469-mavericks-hdmi-audio-applehda.html
	2. http://www.insanelymac.com/forum/topic/292999-mavericks-applehda-hdmi-audio/

Credit:
PikeRAlpha https://pikeralpha.wordpress.com/2013/09/19/haswell-hdau-solution/
bcc9 Post #11 - http://www.insanelymac.com/forum/topic/290783-intel-hd-graphics-4600-haswell-working-displayport/?p=1934889

toleda
https://github.com/toleda/audio_cloverHDMI