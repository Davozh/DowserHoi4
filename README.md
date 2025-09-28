# DowserHoi4
Fix to run HOI4 launcher with mods on Windows 11 using custom compiled exe


Install steps (summary)

Locate HOI4 game folder:

Steam: Right-click HOI4 → Manage → Browse local files

Backup original:

dowser.exe → dowser_backup.exe (or dowser_original.exe)

Put your wrapper dowser.exe (compiled from Inno or C#) in the same folder.

Run Steam as Administrator (recommended) and launch HOI4.

If it works, the Paradox launcher should open and mods/Steam features should be available.

Rollback / restore original files

Exit Steam.

Delete the wrapper dowser.exe.

Rename dowser_backup.exe or dowser_original.exe back to dowser.exe.

Run Steam and launch the game.

Troubleshooting & tips

Antivirus warnings: Some AVs may flag unsigned exes. If so, compile locally and whitelist the file. Don’t run binaries from untrusted sources.

Permissions: If launcher still fails, try running Steam as Administrator.

Compatibility flags: In Windows: right-click dowser.exe → Properties → Compatibility → check Disable fullscreen optimizations.

GPU preference: Windows Settings → System → Display → Graphics settings → add dowser.exe and select High performance (dedicated GPU).

If the launcher still crashes: Collect logs from:

%LocalAppData%\Paradox Interactive\launcher-v2\

%LocalAppData%\Paradox Interactive\launcher-v2\chromium-data

If you experience Steam/online problems afterwards: Remove wrapper and restore original dowser.exe.

Logs & diagnostics to collect (if submitting to Paradox)

C:\Users\<yourname>\AppData\Local\Paradox Interactive\launcher-v2\ (all .log)

C:\Users\<yourname>\Documents\Paradox Interactive\Hearts of Iron IV\logs\ (system.log, error.log, exceptions.log)

Output of dxdiag (dxdiag /t dxdiag.txt)

pdx_settings.txt and settings.txt from your Documents folder for HOI4.

FAQ

Q: Is this safe?
A: Replacing an exe is non-standard and unsupported. It worked for me and several testers, but proceed with caution and backup files.

Q: Can I upload the compiled wrapper here?
A: You can, but many people prefer to compile on their own machine to avoid AV and trust issues. If you publish a binary, sign it and provide source.

Q: Why not just use Steam launch options?
A: Steam often calls dowser.exe and does not reliably forward launch args to the launcher, so this wrapper approach ensures required flags are passed.
