# Source Engine Strike 

Information from [wikipedia](https://wikipedia.org/wiki/Source_(game_engine)):

Source is a 3D game engine developed by Valve.
It debuted as the successor to GoldSrc with Half-Life: Source in June 2004,
followed by Counter-Strike: Source and Half-Life 2 later that year.
Source does not have a concise version numbering scheme; instead, it was released in incremental versions

Source code is based on TF2 2018 leak. Don't use it for commercial purposes.

This project is using waf buildsystem. If you have waf-related questions look https://waf.io/book

# Features:
- Android, OSX, FreeBSD, Windows, Linux support
- Arm support (except windows)
- 64bit support
- Modern toolchains support
- Fixed many undefined behaviours
- Touch support
- VTF 7.5 support
- PBR support
- bsp v19-v21 support
- mdl v46-49 support
- Removed useless/unnecessary dependencies
- Fixed many bugs
- Server Browser and Achievements working without steam

# Current tasks
- Should fix texts
- Fix fov makes the viewmodel invisible

# Cooking Book for Windows
1. Download Python 3 and Git if necessary
2. Clone the repo via git clone --recursive or just download as a zip if you want to
3. Open a command prompt inside the folder
4. Type **waf configure -T release --prefix=cstrike --build-games=cstrike --disable-warns**
   * You can add some additional parameters for example:
   * **--enable-opus** / activates voice chat, did'nt tested.
   * **--32-bits** / compiles 32-bit binaries
   * You can change the build type by just changing **-T release** with **-T debug**
5. Wait until the command finishes
6. Type **waf build -p -v** and wait until compiling process being finished
   * Tooks about 15-20 minutes but it depends on your specs
7. When everythings done, just enter **waf install** to obtain the game binaries
   * All the files should be in a folder called "cstrike", inside of the root
8. Acquire CS:S files and put it into **source-engine-strike\cstrike** except bin files
9. Download HL2 Pre-anniversary branch and copy the files inside hl2 folder that starts with <b>hl2_misc_***.vpk</b>
10. Put that files into **source-engine-strike\cstrike\hl2**
11. Copy **gameinfo.txt** from **cstrike** and paste into **hl2**
12. Start the game, and have fun!

## Creating Solution for VS2022
- Creating a solution is more easier than you think, heres the steps to reproduce:
1. Open a command prompt inside the repository folder
2. Type **waf msvs** and wait till you get a success message.
3. Enter the solution named **source-engine.sln**
4. Set Startup Project as **hl2_launcher** project
5. Go into Properties of it
6. Enter **Debugging** tab and change Command to **$(ProjectDir)\..\cstrike\hl2_launcher.exe**
   * You can also add launch parameters through the properties.

### Developing
- Make sure everytime when you editing the code, you need to type **waf install** to the command prompt to apply the changes.
