## FATMKDIR.G4B v0.1 (20241007)

<pre><code>Function: front-end for Grubutil 'FAT', function 'mkdir'
FATMKDIR.G4B [--mdbase=sector] [DEVICE][/]PATH[/] switches
FATMKDIR.G4B /? (this text)
Make full path on DEVICE - if DEVICE is omitted: on ROOT
On hidden FAT partitions too!
Default: short 8+3 directory names, Long File Names with library ATTRIBFT.LLL
--mdbase=sector: changes (md)startsector in use. Default: 0x3000 *
* Except: 0x0-0x21F, 0x228-0x2FF, 0x30x-0x2FFF, 0x4000-0xD460, 0x12000-0x12FFF
DEVICE = (fd#), (hd#,#), (0x#) and (#): on FAT devices only
[/]PATH[/] = directories between '/' - first '/' and last '/' optional

Switches: /q /sfn[[:]@] /lfn[:case]|/lfn[:]@ /t
/q = quiet mode: error messages only
/sfn = convert Long File Name(s) in PATH to Short File Name(s) **
/sfn[:]@ = make file(s) containing Long File Name with '#' instead '~' in SFN
/lfn = make Long File Name directories in PATH 3*
/lfn:case = make Long File Names of Short File Names IF not all uppercase 3*
/lfn[:]@ = make Long File Names of saved Long File Names on disk (with '#') 3*
/t = trial mode: recognizes existing directories/ first Short File Name (/lfn)
** SFN's in Windows 9x-style: truncated with (max 6 chars of) NAME~number[.EXT]
** Spaces: double-quotes "[DEVICE][/]P A T H[/]" or escaped spaces: P\ A\ T\ H
** '=' sign: double-quotes "[DEVICE][/]P=A=T=H[/]" or escaped '=': P\=A\=T\=H
3* needed: Loosely Linked Library ATTRIBFT.LLL, in same folder as FATMKDIR.G4B

Remarks:
Order of switches and lowercase/ uppercase free ('/lfn[:case]' will make case)
Exports variable 'result=1' if success, 'result=0' if not (for use with '/q')
FAT needed, searched: %~dp0, ROOT, (bd) and /, /grub/, /grubutil/, /g4dll/
File versions: Grubutil FAT 15/02/2015 and Grub4Dos 0.4.6a/ Grub4dos for UEFI
 Grub4dos for UEFI soon ' out of malloc memory' (last version 20240901)
 Found not compatible with Grub4Dos 0.4.5b / Grub4Dos 0.4.5c
More convenient: insmod DEVICE/PATH/FATMKDIR.G4B MKDIR or MD (insmod FAT too)

Example FATMKDIR.G4B (hd0,0)/SOMEDIR (same as 'FAT mkdir (hd0,0)/SOMEDIR')
Example FATMKDIR.G4B (hd0,0)/SUBDIR1/SUBDIR2/SUBDIR3
Example FATMKDIR.G4B "(hd0,0)/Program Files" /sfn /t
Example FATMKDIR.G4B "(hd0,0)/Program Files" /sfn
Example FATMKDIR.G4B "(hd0,0)/Program Files" /sfn:@ /q
Example FATMKDIR.G4B "(hd0,0)/Program Files" /lfn /t
Example FATMKDIR.G4B "(hd0,0)/Program Files" /lfn
Example FATMKDIR.G4B (hd0,0)/Program\ Files /lfn 
Example FATMKDIR.G4B (hd0,0)/Programs /lfn:case /q
Example FATMKDIR.G4B (hd0,0)/Progra~1 /lfn:@</code></pre>

#### ATTRIBFT.LLL

Concept of 'Loosely Linked Library' is courtesy of Wonko the Sane (Jaclaz)  
More information and download:
https://github.com/deomsh/ATTRIBFT.LLL

### HISTORY

Version 0.1  
First published version

### SCREENSHOTS

Basic functions compared with function 'mkdir' of grubutil FAT: making more than one directory at once and making a Long File Name with switch /lfn. Switch /t for testing first (no '>')

![FAT mkdir compared with FATMKDIR G4B making more than one directory at once and Long File Name with -l I](https://github.com/user-attachments/assets/95adec4e-57ac-4ee9-b0d5-3b69e4b80de0)

FATMKDIR.G4B making case in Short File Names as Long File Name with switch /lfn:case

![FATMKDIR G4B making Long File Name as case of Short File Names with -lfn=case II](https://github.com/user-attachments/assets/7cf8865e-b556-4bbc-9b69-2ff5870967b4)

Special Feature 1: with switch /sfn@ make Short File Name directories from Long File Names and store LFN's as external attribute in xxxxxx#1 files. FATLSDIR.G4B reads tem out with swithches /sfn@ and /s

![FATMKDIR make SFN directories from LFN's and LFN's stored in #-files with switch -sfn@ and FATLSDIR -sfn@ -s shows them II](https://github.com/user-attachments/assets/9c5e4c45-3101-4ef9-8509-831b296e08da)

Special Feature 2: with switch /lfn@ make Long File Names from stored LFN's as external attribute in xxxxxx#1 files. FATLSDIR.G4B reads tem out with swithches /lfn and /s

![FATMKDIR make LFN's to SFN directories from LFN's stored in #-files with switch -lfn@ and FATLSDIR -lfn -s shows them III](https://github.com/user-attachments/assets/2d68d9a1-16fa-4b22-a0de-8f8940b778b6)

