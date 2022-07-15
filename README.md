#Taiwu_mods
#The Scroll of Taiwu game Mod
Google-translated to English

[![Build Status](https://travis-ci.com/phorcys/Taiwu_mods.svg?branch=master)](https://travis-ci.com/phorcys/Taiwu_mods)

****
## compile dependencies
*Visual Studio 2017/2019
*.NET Framework 3.5/4.x
* Game body
* Modify *genvsproj.cmd*, set the **STEAMDIR** inside to the local **Taiwu painting volume** installation directory
* If there is no cmake, install the latest version of cmake (to support VS2019, please download cmake 3.14.3 or later) and add cmake to the environment variable *PATH*
* Run genvsproj.cmd on the command line, it will automatically download the dependent dlls, and generate the Visual Studio solution *Taiwu_Mods.sln* to the build directory
* The .cs in the mod directory will be automatically added to the project, the .dll will be automatically used as a dependency, and other files such as .md, .txt, etc. will be automatically copied to the mod path of the game (if you don't want to copy, add ignore in .modignore)
* cmake will automatically add a post build event to the project. After the build is successful, if there is a folder with the same name as mod in the game mod directory, it will automatically copy the dll to the corresponding mod directory in the game mods directory.

****
## New Mod Process

1. Create a new directory and put your mod's .cs file into it
2. Put the **Info.json** (pay attention to the case, the encoding is *utf8 with bom*) file in this directory, the format is similar:
````json
{
    "Id": "HerbRecipes",
    "DisplayName": "Instruction on Refining Materials of Medicine Induction Cooking Recipe",
    "Author": "phorcys",
    "Version": "2.3.0",
    "AssemblyName": "HerbRecipes.dll",
    "EntryMethod": "HerbRecipes.Main.Load",
    "Requirements": ["BaseResourceMod"]
}
````
3. Except the last line of Requirements, other fields are required
4. In the Mods folder under the Taiwu game path, create a new folder to store your mods, such as: *E:/SteamLibrary/steamapps/common/The Scroll Of Taiwu/Mods/HerbRecipes/*
5. Run genvsproj.cmd to generate the project and start mod development
6. Windows supports .modignore files, which are used to ignore some files when copying files to the mod directory (the default includes .cs .dll .modignore, these three do not need to be added) (only * and ? matching are supported, ** matching is not supported )

## Precautions 

##Mods development aids repo:

https://github.com/phorcys/Taiwu_Mods_Tools.git