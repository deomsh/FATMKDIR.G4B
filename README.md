## FATMKDIR.G4B v0.1 (20241002)

<pre><code>echo Function: front-end for Grubutil 'FAT', function 'mkdir'
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

###HISTORY

Version 0.1
First published version

###SCREENSHOTS

