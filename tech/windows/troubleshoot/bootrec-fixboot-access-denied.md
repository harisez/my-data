bootrec /fixboot access denied issue

https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/windows-10-bootrec-fixboot-access-is-denied/747c4180-7ff3-4bc2-b6cc-81e572d546df

Windows 10 Installation Media:

Insert the Media (DVD/USB) in your PC and restart.
Boot from the media.
Select Repair Your Computer.
Select Troubleshoot.

Choose Command Prompt from the menu:
Type in the command:

Diskpart

Type in the command:

List disk            (Note which disk is your Boot drive number mine is 0)

Type in the command:

Sel disk 0

Type in the command:

List vol               (Note which volume is the EFI partition mine is 4)

Type in the command:

Sel vol 4

Type in the command:

assign letter=V:

Type in the command:

Exit

Type in the command:

V:

After you have assigned a drive letter Using Diskpart You can format the EFI partition:

Example: if you assigned a letter V to the partition the command would be:

format V: /FS:FAT32

After the format you need to recreate the EFI directory structure with the command:

Type in the command:

bcdboot C:\windows /s V: /f UEFI      (This replaces the above crossed out lines and works in Win 10 1709)
