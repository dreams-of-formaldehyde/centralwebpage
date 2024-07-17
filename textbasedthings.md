- Stuff you likely dont need, and should not care about
Regarding the GTA 5 Source code leak, here is some info about the files:

IF THE HASHES DO NOT MATCH, DELETE THEM IMMEDIATELY.

GTAVSP.7z (more complete version):
Size: 4652367138 bytes (4436 MiB)
SHA1: ca39323730ed644fa534a2946506d4287f92a799
-

- Shh... Halo Custom Edition..
V1dDWFEtUUtRNFYtUVJXS1EtWURWR0otRkNSWUo=
RzlRSzItMjJLVjYtVEZYQ1ItVjNZOU0tMkNDQko=
UEdRVEctNFg0SjMtNjhNODctQjI4VFItSjJDQko=
TTRHSEYtTU1SV0stTVc5QkQtQjc2SkstNlA4TUo=
VzRXTVEtQlA3SjQtWVBWOEQtOUhZSzMtS1FUVlc=
UkdHRDktQllDQzQtNko2RlYtVlBKSlEtSENYSFc=
RzlRazItMjJLVjYtVEZYQ1ItVjNZOU0tMkNDQko=
Vjg0SDctSjYyWTQtSFRNSEstUktINlQtQkhYSFc=
VDM5UlgtSkg3WTItWFdUSkQtVkpYOFgtRzdNRDg=
RkNNMlQtM1E3RkctVFhLR1EtS1I0Q0QtRkNHVjM=
UFA2RDgtRjRNRjMtM1lUQ1EtWDhDS0gtMkZWUTg=
UVE0TUMtVDQ4QkMtQ0Q2OVQtUUtGOU0tVzNUVlc=
UU1XTTYtV1ZETUstODZRODYtQkZDOFgtSkhDQko=
VFJGMkItWTY3SzItR1Y3UlItSDREQ0ItUURDN1c=
VkhWRzItNkRHWEctR0NLSFEtVlgyWUgtNFE0WVE=
VzdWWTgtODZIS0ctNk1XRlgtN1BQSDgtNzMzS1Q=
WEJRRFgtR1JLQ0ItS1FWTVYtV1JSOVAtRjJDQko=
NDEyNDgtNzk0NTUtMzQ1NjUtODc5NDUtNjg3NDI=
RlJGVzctSEg0QjctQzk0NDQtVFI5NEYtUUhYSFk=
RzNUMzItMkhNSkotN0dUR1gtVlRSQlgtR1QyN1k=
SjM0SFYtWVlQTTYtTTNCSDYtNDYwMzctVlYzMzg=
S01DVDctMlFLVkYtNEtWMjctNlA4M0otVEhDQko=
SzlUR00tSzMzN1AtSlcyNFQtQjlWNzMtQzNUVlc=
OEQ2OUQtOEJGQjgtOTM5NDktNTg0NUYtRkg2ODY=
S1lLTUgtSldXWFEtWEcySEgtQ1BERkMtS1gyQko=
-

- Windows debloating stuff because i have early onset of dementia (not actually)
In a nutshell, there's a Powershell command that can remove all the UWP apps, and then (if you care to) reinstall the Windows Store so you can cherry pick. It also helps to disable animations (Ease of Access settings) and disable transparency (Ease of Access settings or Personalization settings)

Using either registry edits, doing it manually or using a third party tool called Ultimate Windows Tweaker (UWT) you can disable a lot of background and automatic processes ranging from Cortana, Update sharing, Data collection, Edge and UWP pre-loading as well as superfetch and prefetch which simply put, will pre-load some application files to make the related apps start up faster. Besides the ram boost, this is exceptionally useful for users with a mechanical hard drive as C:/

Windows 10 also carries over a feature from Vista (of all things) where it will automatically allocate ram to pre-load frequently accessed programs based on your maximum ram.

The same setup OP is sharing may run at 1.1GB of ram if they installed (say) 8GB of ram.

This is more noticeable at smaller maximum ram.

Lastly, if you have an ancient system or weak notebook, installing windows 10 32 bit can reduce ram usage. You loose the ability to run 64 bit programs (which isn't an issue if you're running mainstream popular big brand software) but gain some ram back as 32 bit programs require less ram due to shorter amounts of bits. This can make running a 2GB RAM Windows 10 system actually considerable.

There's a few more tricks and details, but maybe I'll post a guide with more in depth ways to trim windows 10, besides for ram. I set up a lot of PC's as a hobby, and usually work on laptop revival and restoring DDR2 era desktops to run efficiently for modern use. Some weaker systems boasting Athlon 64 and Pentium 4 CPUs with 2,3, or 4GB or RAM can run Windows 10 decently once the fat is trimmed, and paired with even a 5 dollar GPU, LGA 775 and AM2+ machines can actually hold up, even with high end design or gaming tasks, especially once the excess bloat of Windows 10 is removed.

It's true what they said when 10 launched: If your machine can run Windows 7, it can run 10 (baring the one exception that 7 can run on a processor that does not have the NX function while 10 requires it) Once all the Microsoft marketing nonsense is removed, Windows 10 preforms much like a clean install of 7 would in terms of raw performance.
-

- Extra stuff you might need idfk
If anyone wants them, these are the PowerShell commands I use. This will remove all UWP apps including ones you have elected to download from the Windows Store, and the Windows Store itself. They will have to be redownloaded and re-logged into. This includes some hidden apps such as the Windows 10 Game Bar.

The following apps are unaffected for what I assume are obvious reasons:
Settings, Windows Security, Edge

When running PowerShell (in the highest bit supported by your OS (64 bit in most cases)) in Admin mode you can use this command to remove all UWP apps. This will take some time, and PowerShell will turn teal, black, and red:

Get-AppxPackage -AllUsers | Remove-AppxPackage

This command essentially calls for a list of all UWP apps. The second half of it tells the PC to remove all retrieved apps in the list, ergo all of them.

To restore Windows Store and thus cherry pick what UWP apps you want, use this command:

Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

It reinstalls the Windows Store

Do note that some apps include other apps or other removed background apps, such as reinstalling Microsoft Photos will always reinstall Video Editor.
-

- Java 8 parameters, some may be placebo (gotta weed em out)
-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:-PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -XX:+UseFastAccessorMethods -XX:+OptimizeStringConcat -XX:+AggressiveOpts -XX:UseAVX=3 -Dgraal.SpectrePHTBarriers=None -Dgraal.CompilerConfiguration=enterprise -XX:UseSSE=99 -XX:+UseSSE42Intrinsics -XX:+UseStringDeduplication -XX:+UseAESIntrinsics -XX:+UseAES
-

- Java 17 parameters, should be about the same, just a few things removed
-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:-PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -XX:+OptimizeStringConcat -Dgraal.SpectrePHTBarriers=None -Dgraal.CompilerConfiguration=enterprise -XX:UseAVX=3 -XX:AVX3Threshold=0 -XX:+UseSSE42Intrinsics -XX:+UseStringDeduplication -XX:+UseAESIntrinsics -XX:+UseAES
-

- Java options are highlighted here too, check them out!
https://chriswhocodes.com/vm-options-explorer.html
-

- PCPP list for a budget build i may make
https://pcpartpicker.com/list/z7MFvj
-

- Katana archlinux packages (-mtune=tigerlake -O3 -march=tigerlake | might not run on other systems without AVX-512 support, but atleast theyre prebuilt!)
https://cdn.discordapp.com/attachments/1200232726607958026/1252517806394576907/katie-git-4.14.0.r8318.b7f240178-1-x86_64.pkg.tar.zst
https://cdn.discordapp.com/attachments/1200232726607958026/1252517919951163422/ariya-icons-4.24.0.r26.cccd0224-1-any.pkg.tar.zst
https://cdn.discordapp.com/attachments/1200232726607958026/1252517932857163808/katana-extraapps-4.24.0.r1782.6999d07f-1-x86_64.pkg.tar.zst
https://cdn.discordapp.com/attachments/1200232726607958026/1252517960602484776/katanalibs-4.24.0.r5536.508ad0d2-1-x86_64.pkg.tar.zst
https://cdn.discordapp.com/attachments/1200232726607958026/1252517996979552377/katana-workspace-4.24.0.r3812.960bf5ff-1-x86_64.pkg.tar.zst
-

- PluginRepo for Aliucord
https://cdn.discordapp.com/attachments/1199871459070320741/1252843988214349884/PluginRepo.zip
-

- Must have grub kernel parameters (put them in /etc/default/grub if on EndeavourOS)
mitigations=off split_lock_detect=off
- free performance tbh
enable_guc=3 i915.enable_fbc=1
- Intel exclusive, it helps with gaming performance, not just power usage too !!READ!!ENABLE_GUC=3 REQUIRREESSS GEN12 iGPUS AND NEWER!!READ!!
