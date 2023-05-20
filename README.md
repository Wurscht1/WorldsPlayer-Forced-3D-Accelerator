# Requirements
Worlds 1922a10 (found here: https://files.worlio.com/files/WorldsPlayer/software/Worlds1922a10.exe (also make sure to check out Worlio's https://worlio.com/ beautiful webpage in order to gain support!!)
Ghidra https://github.com/NationalSecurityAgency/ghidra/releases (or any other Decompiler if you know what to do :) such as but not limited to: BinaryNinja, IDA64, ...)
HxD https://mh-nexus.de/en/hxd (or any other Hex Editor if you know what you're doing!)
# I don't wanna do it manually and totally trust your patched .DLL from the interwebs!
· Firstly thanks of all, I dont mean any harm, the already patched .DLL should be found here: URL
# Instruction
· First of all duplicate WorldsRenderer.dll (found in the root of your WorldsPlayer installation) and name it something like WorldsRenderer2.dll
· open up "WorldsRenderer2.dll" with your Hex editor of your liking, in my case HxD 
· start ghidraRun.bat
	· create an new non shared project (File -> New Project -> Non Shared Project -> Next -> change project folder and project name to your liking)
	· Finish -> click that green Dragon above your active project 
· File -> Import File -> import (the original, not your copy!) "WorldsRenderer.dll" (from your Worlds Installation folder!) -> OK 
· It should ask you to analyze the file, press "Yes", leave everything as it is and press "Analyze" 
· an "Import Results Summary" window should pop up, close it -> it shouldn't take long to load all in -> now on the left middle screen there should be an small "Symbol Tree" Window"
· enter "Acceleration" into its filter(slightly below it) (without quotes), ignore the ones from "Exports" and "Labels", only choose the ones from "Functions" 
· double click on "grGetHardwareAccelerationAvailable" -> then double click on the right the "return DAT_xxx" value [See Picture 1] 
· in my case "DAT_1000071BC" -> 100071BC might be your first offset, ignore the 1 at the beginning, read it as 0, so 000071BC! now go back to your Hex Editor, 
  goto that address and change it to "01"! 
· back Ghidra, double click "grGetHardwareAccelerationInUse" -> then double click its DAT_xxx (in my case DAT_1000071B8), Ignore the first number 1 again and r6ead it as 0 so 0000071b8 
  and it should be also "01" so change it[See Picture 2]!, now save it as a new file,
  dont overwrite your original WorldsRenderer.dll incase things go south! After saving it to e.g. WorldsRenderer2.dll (close your game if you haven't already), rename your (hopefully) 
  unmodified WorldsRenderer.dll to something like "WorldsRenderer.dll.backup",
  and your modified "WorldsRenderer2.dll" to "WorldsRenderer.dll" (without quotes..)
# Double Check..
If you've done everything correctly you can double check now in the game, press "Options", if you now see "Disable 3D Acceleration" you see that it worked!