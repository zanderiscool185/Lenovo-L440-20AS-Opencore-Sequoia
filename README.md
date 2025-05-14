# Lenovo-L440-20AS-Opencore-Sequoia
A EFI that's been updated to work with macOS 15 on the Thinkpad L440 
Woo! ive updated opencore to 1.0.4! its now ready to go! 
ive attached both a 7z and a self extracting ZIP file with the EFI, that way you can "drag and drop" and go
theres a PCI in the config thats disabled (has this symbol #), ONLY uncomment it IF you have the intel 7260 Wifi Card (Use it to get Opencore Legacy Patcher to give you an option for Modern Wireless Root Patch, alongside the Intel:Haswell Root Patch)
This EFI SUPPORTS WIRELESS IN RECOVERY MODE! WOO! So you can use the recovery to install macOS with Wifi AND ethernet 
little fun quirk, The WiFi password is stored in NVRAM, as its autoconnected in both macOS, and recovery on its own!
This is a followup and a update to my other repo: https://github.com/zanderiscool185/Lenovo-L440-20AS-Opencore-Sonoma
Much Love, and happy hacking.
PS. as much as i love this laptop, i think this genuinely might be the last macOS version to run on this, as its starting to take 20+ seconds to  boot (Vanilla install no apps,aka Fresh).
i hope this helps, also maybe this might address some of the come issues others mentioned, like No Displayport (STILL DOESNT WORK, Thats a Graphics Issue, you either get good graphics, or displayport, not both) and some issue with audio buzzing (havent tested)


How to use:
This is a two step process
1. Copy EFI folder to USB and Boot installer (50/50 on if wifi works in recovery mode)
2. Install macOS as normal
3. Download Opencore Legacy Patcher and Opencore Auxiliary Tools (OCAT)
4. Mount your EFI partition and Copy the folder to your EFI partiton on your SSD(PLEASE DONT USE HDDS!) Terminal Command: sudo diskutil mount /dev/diskXs1 (X = your disk! use diskutil list to find it!)
5. THIS IS THE WIFI PATCH PART AND ONLY APPLIES TO THIS SPECIFC WIFI MODEL!
6. copy the "Wifi Patch" into the EFI/OC/ and name it config.plist (GRAB THE CURRENT ONE AND RENAME TO configbak.plist)
7. reboot and run Opencore Legacy Patcher and click "Post Install Root Patch" and it now should say "Intel Graphics Patch" and NOW ALSO A "Modern Wifi Patch"
8. Run the patcher and let it finish, then reboot
9. rename the file thats currently "config.plist" to FixWifiAfterUpdate.plist, and the "configbak.plist" back to config.plist
10. Success! you should now have iMessage-Compatible Wifi Now!

PS. WHEN YOU UPDATE, Redo steps 5-9 BEFORE opencore patcher reminds you about it, if you accidentally patch, no worries! you can re-patch again, but have the Modern wifi patch added as well!

Sidenote, Updated perfectly fine from 15.4.1 to 15.5, other than the wifi patch, updated like normal, No Delta Updates tho (for those who dont know, delta updates are smaller updates, usually 1-2 GB, but when updating, it downloads a FULL OS IMAGE! so make sure you have the bandwidth!)
 
Ive added the EFI as well as pre-packaged, as not everyone has windows 11 and not everyone has 7z, the folder is the original, if you download the packages and they dont match the repo, DO NOT USE! (the folder names are different, but the files themselves will match)


CHANGES SINCE MY LAST REPO: EFI is now ALL IN ONE, Wifi (when not spoofed) should work in recovery, and macOS boot chime is now enabled

for the cybersecurity nuts who are curious as to what i packed it with, i used Keka for macOS: https://www.keka.io 
it provided a self extracting ZIP option, so i opted to try it out.

My repo couldnt have been done/created without the community, and the people whos EFI i forked off to make this one! 
macOS Monterey Source Repo: https://github.com/alerion921/Lenovo-Thinkpad-L440-20AS-OpenCore (shoutout this dude, as i forked off his repo, applied patches for Sonoma+ and updated opencore, rest was on him, and the Opencore Dev teams, as well as YOU! for keeping that tech alive "just a little longer")
