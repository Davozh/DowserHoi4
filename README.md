# 🛠️ HOI4 Dowser Launcher Fix (Windows 11)

This project provides a workaround for an issue with the **Hearts of Iron IV (HOI4)** launcher (`dowser.exe`) on **Windows 11** (24H2 in my case).  
While other Paradox games (EU4, CK3, etc.) can be fixed by adding the `--in-process-gpu` launch option, HOI4 uses its own **dedicated dowser** instead of the shared Paradox launcher, which breaks this method.

👉 With this fix, you can **launch HOI4 with the official launcher, mods, and Steam features** working properly.

---

## ⚡ Tested Requirements

- 💻 **CPU:** Intel i7 6700k  
- 🎮 **GPU:** NVIDIA GTX 1060  
- 🖥️ **OS:** Windows 11 24H2  
- ⚠️ The issue may also happen on other hardware with Windows 11  

---

## 📖 Step-by-step guide

### 1. Backup the original dowser
1. Navigate to your HOI4 installation folder (usually:  
   `C:\Program Files (x86)\Steam\steamapps\common\Hearts of Iron IV\`)
2. Rename `dowser.exe` → `dowser_original.exe`  
   This keeps a safe backup in case you need to restore it.

---

### 2. Use the custom replacement dowser
1. Download the provided **replacement `dowser.exe`** from this repository (compiled with Inno Setup).  
2. Place it inside the HOI4 installation folder (next to `hoi4.exe`).  
3. This replacement simply forwards the command with the required parameter:
--in-process-gpu


ensuring the launcher opens correctly.

---

### 3. Launch the game via Steam
- Run HOI4 normally from Steam.  
- The custom dowser will start, pass the correct flags, and load the launcher with **mods and online features** enabled. 🎉

---

## ⚠️ Disclaimer

- This project is an **unofficial workaround**.  
- **Use at your own risk.** I am not responsible for any damage, corruption, or bans (although it is highly unlikely as this only replaces the local launcher).  
- Always **keep a backup** of the original `dowser.exe` (`dowser_original.exe`).  

---

## ❓ FAQ

**Q: Why not just skip the launcher?**  
A: Skipping works, but you lose **mods and online features**. This fix keeps them functional.

**Q: Can this break multiplayer compatibility?**  
A: No. The game executable (`hoi4.exe`) is untouched. Only the launcher call is adjusted.

**Q: Does this affect achievements?**  
A: No. Since Steam integration is preserved, achievements should work as normal.

**Q: What if I want to restore the original launcher?**  
A: Delete the custom `dowser.exe` and rename `dowser_original.exe` back to `dowser.exe`.

**Q: Can this help on other Paradox games?**  
A: Probably not needed — EU4, CK3, and others already work with the `--in-process-gpu` parameter directly. HOI4 is the odd one out.

---

## 📝 Notes

This workaround was tested on my system with a **GTX 1060** and **i7 6700k** running **Windows 11 24H2**.  
It should work on similar setups, but feedback is welcome if you try it on other configurations!

---
