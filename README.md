# CHFI
**Operating System Forensic**

****Challenges to Forensics from Anti-Forensics****
- accessing and evaluating encrypted data without the relevant decryption keys
- Attackers securely delete data from the evidence source or overwrite crucial text and metadata
- Attackers hide crucial data by renaming files and file extensions
- Misleading evidence decreases the integrity and accuracy of findings by introducing falsified evidence
- Attackers obfuscate executable code using program packers to avoid detection using antimalware solutions. Other methods such as hiding files within files or utilizing encrypted containers.
- Attacker modifies the timestamps on the servers while launching an attack, server logging is eliminated.
- Because anti-forensic techniques such as IP spoofing and onion routing keep the attacker’s identity anonymous
- Attackers intentionally corrupt critical data to weaken the integrity and reliability of digital evidence
- 
Given below are the various types of anti-forensic techniques: 

1. Data/file deletion
   - Forensic investigators can use data-recovery tools such as Autopsy, Recover My Files, Ease US Data Recovery Wizard, and R-Studio to scan hard drives and analyze file systems for successful data recovery.
   - In the FAT file system, the OS replaces the first letter of a deleted file name with the hex byte code E5h. E5h is a special tag indicating a deleted file.
   - The clusters allocated to the deleted file are marked as free in the $BitMap ($BitMap file, which is a record of all the used and unused clusters).
   - The Windows OS assigns one specific space on each hard disk partition to store files in the Recycle Bin.
   - The system does not store larger items in the Recycle Bin; instead, it permanently deletes them.
   - When a user deletes a file or folder, Windows 10 and its later versions create two new files in the Recycle Bin for every deleted file. The first file is ‘$R’ which is followed by any random string and contains the main contents that were deleted. On the other hand, the second file created is ‘$I’, which contains the metadata of that deleted file including the original file name, file size, path, etc.
   - The OS uses this information to restore the deleted file to its original location. And these ‘$R’ and ‘$I’ files are located at C:\$Recycle.Bin\<USER SID> (command to get USER SID: wmic useraccount get name,sid)
   - The OS uses this information to restore the deleted file to its original location. And these ‘$R’ and ‘$I’ files are located at C:\$Recycle.Bin\<USER SID>
   - Recycle Bin on Windows 11 is generally located in the user's profile folder inside "C:\Users<Username>$Recycle.Bin.

     **File Carving Techniques and Ways to Recover Evidence from Deleted Partitions**
     It helps
     - to recover deleted/lost files and fragments of files from a hard disk when file system metadata are missing.
     - extract valuable artifacts related to a case of cybercrime for further examination.
     - investigators extract data from a storage medium without any support from the file system used for file creation in case A perpetrator may also attempt to delete an entire partition from the hard disk, and then merge the unallocated space of the deleted partition with the primary partition of the system to prevent the investigator from identifying the lost partition.
     - Investigators can analyze file headers to verify the file format using tools such as 010 Editor, CI Hex Viewer, Hexinator, Hex Editor Neo, and WinHex.
     - In TRIM-disabled SSD’s, a forensic investigator can perform file carving to recover lost data from the drive.
   **SSD File Carving on Windows File System**
Forensic Workstation: Windows 11
   - When Autopsy is employed to perform file carving on an evidence file, the software lists the file names (which can be seen in the screenshot); however, the deleted data cannot be recovered.
**HDD File Carving on Windows File System**
     - The forensic image file is acquired using tools such as FTK Imager and DD utility and examined using Autopsy.
     - **EaseUS Data Recovery Wizard** software is used to recover lost data due to deletion, formatting, partition loss, unbootable or crashed systems, virus attacks, etc., from Recycle Bin, HDD, SSD, SD card, USB drive, cameras, music players, video players, RAID, ZIP drives, and other devices under Windows 11 and Windows Server 2022/2019. It can recover deleted documents, images, videos, emails, and other files. This tool specializes in disk partition recovery. It has the latest file-repair features that can be used to repair corrupt photos, videos, and documents.
     - below are some additional tools for file recovery in Windows:
     - ▪ DiskDigger (https://diskdigger.org) ▪ Handy Recovery (https://www.handyrecovery.com) ▪ Active@ File Recovery (https://www.file-recovery.com) ▪ Stellar Data Recovery for Windows (https://www.stellarinfo.com) ▪ PhotoRec (https://www.cgsecurity.org)
     - **File Carving on Linux**
     - Forensic investigators can use third-party tools, such as the Kernel for Linux Data Recovery, R-Studio for Linux, and Foremost, to recover deleted data from the disk.
     - if an executable erases itself, its contents can be retrieved from a /proc memory image. The command cp /proc/$PID/exe /tmp/<file name> file creates a copy of a file in /tmp.
     - In contrast to Windows, Linux can access and retrieve data from various machines. The Linux kernel supports many file systems, including VxFS, UFS, HFS, NTFS, and FAT. Some file systems are not readable in a Windows environment, and users can easily recover such files using a bootable Linux Distro such as Knoppix.
       **SD File Carving on Linux File System**
       - The forensically acquired image from a TRIM-disabled SSD should be examined using file-carving tools such as Autopsy and R-Studio for Linux.
     - **Tools for file recovery in Linux-based systems**: ▪ R-Studio for Linux (https://www.r-studio.com) ▪ Recoverit (https://recoverit.wondershare.com) ▪ UFS Explorer (https://www.ufsexplorer.com) ▪ TestDisk (https://www.cgsecurity.org) ▪ GNU ddrescue (https://www.gnu.org)
     - **File Carving on macOS**
     - Investigators can use sophisticated tools, such as PhotoRec, UFS Explorer Standard Recovery, and TestDisk to work only with raw data associated with media that are not linked to the file system structure. These tools allow investigators to identify the storage medium from which they can restore files, including a hard drive, SSD, USB drive, memory card, or any other storage device.
     - R-Studio - Forensically acquire the disk image of the Apple File Systems (APFS) from a TRIM-disabled SSD.
     - iBoysoft - Forensic investigators can use this tool to recover recently deleted files, permanently deleted files, and lost data from unreadable external disks on Mac. It allows investigators to recover lost files by not mounting an external hard drive on a Mac, as well as restoring files from formatted or corrupted removable or portable storage devices such as HDD, SSD, SD cards, and USB drives. Additionally, iBoysoft supports Mac APFS-formatted disks encrypted by Secure Enclave technology of T2 Security chip or Apple Silicon M1, M2, by APFS encryption, or by FileVault 2.
     - **Recovering Deleted Files from USB on Mac Machine** - Disk Drill is a Mac data recovery software that helps forensic investigators recover deleted, lost, or damaged data, personal or business documents, music, photos, videos, and other files from internal, external, and virtual hard drives, memory cards, iPhones, iPads, Android devices, RAID arrays, and other data sources. Additionally, Disk Drill can scan the USB flash drive/pen drive and locate the deleted files.
     - **File Recovery Tools: macOS**: Some tools for file recovery in macOS-based systems are ▪ Data Rescue 6 (https://www.prosofteng.com) ▪ Stellar Data Recovery for Mac (https://www.stellarinfo.com) ▪ AnyRecover for Mac (https://www.anyrecover.com) ▪ DM Disk Editor and Data Recovery Software (https://dmde.com) ▪ Cisdem Data Recovery for Mac (https://www.cisdem.com)
     - **Custom File Carving Signatures** Some data-recovery tools that provide custom-carving features for file recovery like Belkasoft X, Active@File Recovery etc.
     - **Recovering Deleted Partitions** The investigator should use automated tools, such as R-Studio, to retrieve the lost partition data. R-Studio is a data recovery tool for Windows, Linux, and macOS partitions, even if the partitions are deleted, damaged, or formatted.
     - **Partition Recovery Tools**  Some of the tools for partition recovery: ▪ EaseUS Data Recovery Wizard (https://www.easeus.com) ▪ Stellar Data Recovery Professional (https://www.stellarinfo.com) ▪ Hetman Partition Recovery (https://hetmanrecovery.com) ▪ Remo Recover (https://www.remorecover.com) ▪ MiniTool® Data Recovery Software (https://www.minitool.com)
     - **Recovering ReFS Volumes Using ReFSUtil** ReFSUtil is a command-line tool available on Windows and Windows Servers to diagnose and investigate heavily damaged ReFS volumes, such as identifying the remaining files and copying those files to another volume. The primary function of this tool is to perform ReFS salvage, which can help investigators recover data from volumes shown as RAW in disk management.
     - **RAID Recovery Tools**  Some tools that can be used for this purpose include ▪ DiskInternals RAID Recovery, ▪ R-Studio (https://www.r-studio.com) ▪ RAID Reconstructor (https://www.runtime.org) ▪ Stellar Data Recovery Technician (https://www.stellarinfo.com) ▪ Klennet Recovery (https://www.klennet.com) ▪ UFS Explorer (https://www.ufsexplorer.com)
2. Password protection
    **Explore Password Cracking/Bypassing Techniques**
   - Computing devices can store and transmit passwords as cleartext, obfuscated, and hashed passwords, of which only hashed passwords require cracking, whereas other password types can assist in the cracking phase.
   - **Tools to Extract the Password Hashes** pwdump7, ▪ Mimikatz (https://github.com) ▪ PyCrack (https://github.com) ▪ DSInternals PowerShell (https://github.com) ▪ hashcat (https://hashcat.net)
   - **Password Cracking Tools**  Passware Kit Forensic Source: https://www.passware.com, ▪ John the Ripper (https://www.openwall.com) ▪ THC-Hydra (https://github.com) ▪ hashcat (https://hashcat.net) ▪ Secure Shell Bruteforcer (https://github.com) ▪ DataProtectionDecryptor (https://www.nirsoft.net)
   - **Bypassing Passwords on Powered-off Computer** Bypassing BIOS Passwords. In the BIOS setup, there are three types of passwords: ▪ System password ▪ Admin password ▪ HDD password. Resetting CMOS Using Jumpers. Bypassing BIOS Passwords by Removing CMOS Battery.
   - **Tool to Reset Admin and Local User Password: PassFab 4WinKey**
   - **Bypassing Windows User Password by Booting Live USB.** CAINE, Guymager, an imaging tool
   - **Application Password Cracking Tools**
   - **Office Password Cracking Tools** Some of the office password cracking tools are listed below: ▪ Online Password Remover (https://www.password-find.com) ▪ Advanced Office Password Recovery (https://www.elcomsoft.com) ▪ PassFab for Office (https://www.passfab.com) ▪ Passper for Excel (https://passper.imyfone.com) ▪ Office Password Genius (https://www.isunshare.com)
   - **PDF Cracking Tools** Some of the PDF cracking tools are listed below: ▪ PDF Password Recovery (https://www.top-password.com) ▪ PDF Password Genius (https://www.isunshare.com) ▪ PassFab for PDF (https://www.passfab.com) ▪ Guaranteed PDF Decryptor (http://www.guapdf.com) ▪ Passper for PDF (https://passper.imyfone.com)
   - **ZIP Password Cracking Tools** Some of the ZIP password-cracking tools are listed below: ▪ Accent ZIP Password Recovery (https://passwordrecoverytools.com) ▪ ZIP Password Genius (https://www.isunshare.com) ▪ PassFab for ZIP (https://www.passfab.com) ▪ ZIP Password Recovery (https://www.top-password.com) ▪ Passper for ZIP (https://passper.imyfone.com)
   - **RAR Cracking Tools** Some of the RAR cracking tools are listed below: ▪ Accent RAR Password Recovery (https://passwordrecoverytools.com) ▪ RAR Password Genius (https://www.isunshare.com) ▪ cRARk (http://www.crark.net) ▪ PassFab for RAR (https://www.passfab.com) ▪ Passper for RAR (https://passper.imyfone.com)
4. Steganography (masks the data within images and audio files)
   - In addition to the anti-forensic technique(s) discussed previously, attackers may also use the following methods: 1. Steganography, 2. Hiding data in file system structures, 3. Trial obfuscation, 4. File extension mismatch
6. Data hiding in file system structures (by renaming files and file extensions)
7. Trail obfuscation
8. Artifact wiping
9. Overwriting data/metadata
10. Encryption
11. Program packers
12. Minimizing footprint (modifies the timestamps on the servers,  such as IP spoofing and onion routing keep)
