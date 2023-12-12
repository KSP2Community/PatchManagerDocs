# Getting Started With Patch Manager

## Setting Up Your KSP2 Installation
Before doing anything with Patch Manager, Patch Manager must first be installed into KSP2, the recommended way to do this
is using CKAN, but manual installation is still possible.

<tabs>
    <tab title="Installation via CKAN">
        <procedure id="install-via-ckan">
            <p>If you already have CKAN installed and set up you can skip to step 7</p>
            <step>
                <p>Download and install CKAN from <a href="https://github.com/KSP-CKAN/CKAN/releases/latest">its GitHub Releases page</a></p>
            </step>
            <step>
                <p>Open CKAN</p>
            </step>
            <step>
                <p>At the top of the window select <code>File</code>-><code>Manage Game Instances</code></p>
            </step>
            <step>
                <p>Then select <code>New game instance</code>-><code>Add instance to CKAN</code></p>
            </step>
            <step>
                <p>Then browse for the <code>KSP2_x64.exe</code> file of your KSP2 installation and select that</p>
            </step>
            <step>
                <p>If the game instance doesn't automatically get selected, follow the previous steps up to step 4 and select the instance</p>
            </step>
            <step>
                <p>Search for "PatchManager" in the search bar</p>
            </step>
            <step>
                <p>Check the <code>Installed</code> checkbox</p>
            </step>
            <step>
                <p>Press the <code>Apply Changes</code> button at the top, and let CKAN do the rest</p>
            </step>
        </procedure>
    </tab>
    <tab title="Manual Installation">
        <procedure id="manual-install">
            <p>If you already have SpaceWarp and UITK set up, you can skip to step 5</p>
            <step>
                <p>Download UITKForKSP2 from <a href="https://spacedock.info/mod/3363/UITK%20for%20KSP%202">Spacedock</a></p>
            </step>
            <step>
                <p>Extract the contents of the downloaded zip file for UITK For KSP2 into the root directory of your KSP2 Installation</p>
            </step>
            <step>
                <p>Download SpaceWarp+BepInEX from <a href="https://spacedock.info/mod/3277/Space%20Warp%20+%20BepInEx">Spacedock</a></p>
            </step>
            <step>
                <p>Extract the contents of the downloaded zip file for SpaceWarp+BepInEx into the root directory of your KSP2 installation</p>
            </step>
            <step>
                <p>Download PatchManager from <a href="https://spacedock.info/mod/3482/Patch%20Manager">Spacedock</a></p>
            </step>
            <step>
                <p>Extract the contents of the downloaded zip file for PatchManager into the root directory of your KSP2 installation</p>
            </step>
            <chapter title="Help" collapsible="true" default-state="collapsed">
                <deflist>
                    <def>
                        <title>Root Directory</title>
                        <p>The root directory of your KSP2 installation is the folder that contains <code>KSP2_x64.exe</code></p>
                    </def>
                </deflist>
            </chapter>
        </procedure>
    </tab>
</tabs>

## Setting Up the Settings for Patch Manager inside KSP2

Once you have installed Patch Manager and all the necessary prerequisites for it, since you are going to be doing development
while having it installed, you will want to enable the `Always Invalidate Cache Option` from within the game.

To do this:

1. Launch KSP 2
2. Press `Settings` once you get to the main menu
3. Press `Mods`
4. Scroll down until you see `Patch Manager`
5. Toggle `Always Invalidate Cache` to `Yes`
6. Close KSP 2

## Setting Up a Modding Environment to Develop Patch Manager Patches

### (Optional) Installing Visual Studio Code and the Patch Manager Language Extension for it
A very useful tool when it comes to writing Patch Manager patches is the Patch Manager syntax highlighting extension for
visual studio code. This should definitely be a part of your environment if you are using VSCode or want to use VSCode.

First, if you don't already have VSCode, then you can download and install it [here](https://code.visualstudio.com/).

Then, once you have VSCode, you can add the Syntax Highlighting extension by searching "Patcher Language Server" and
installing the one by "Sinon".

### Setting up Your Mod

First off, decide here what you want your mod is going to do:

A) is it only going to add patches?

B) is it going to add patches and new parts?

C) is it going to add patches and code?

D) is it going to do all of the above?

Depending on your answer to the prior question, there are multiple ways to set up your modding environment

<tabs>
    <tab title="Patch Only Mod">
        <p>Setting up a patch only mod is quite simple, you only need to create a mod folder with a certain structure, and fill in the values of one file</p>
        <chapter title="Folder Structure" collapsible="true" default-state="expanded">
            <code-block>
            ModFolder/
                swinfo.json
                patches/
                    libraries/
            </code-block>
        </chapter>
        <chapter title="swinfo.json setup" collapsible="true" default-state="expanded">
            <p>The aforementioned <code>swinfo.json</code> file in that above file structure has to be formatted a certain way</p>
            <p>If you want to write it manually, you can follow the <a href="https://docs.spacewarp.org/en/latest/pages/swinfo.json.html">SpaceWarp documentation</a></p>
            <code-block lang="json">
            {
                "spec": "2.0",
                "mod_id": "YourModId", 
                "author": "You",
                "name": "Your Mod",
                "description": "Does something",
                "source": "your/source/link",
                "version": "1.0.0",
                "ksp2_version": {
                    "min": "0.1.5",
                    "max": "*"
                },
                "dependencies": [
                    {
                        "id": "com.github.x606.spacewarp",
                        "version": {
                            "min": "1.5.0",
                            "max": "*"
                        }
                    },
                    {
                        "id": "PatchManager",
                        "version": {
                            "min": "0.4.0",
                            "max": "*"
                        }
                    }
                ]
            }
            </code-block>
            <p>When you copy this though, the following fields need to be changed</p>
            <deflist>
            <def title="mod_id">
                <p>This is the ID of your mod, it's usually your mod name but CamelCase and with an optional prefix of your username in CamelCase to the front with a <code>.</code> </p>
            </def>
            <def title="author">
                <p>This is your (user)name or the (user)names of the people working on the project</p>
            </def>
            <def title="name">
                <p>This is quite self-explanatory, it is the name of your mod</p>
            </def>
            <def title="description">
                <p>This is a short description of what your mod does to the game</p>
            </def>
            <def title="source">
                <p>If you are hosting your mods source code on GitHub or something, this field should point there, otherwise this field should be deleted</p>
            </def>
            <def title="version">
                <p>This is the version of your mod, change this when you change anything about your mod, should follow <a href="https://semver.org">semantic versioning rules</a></p>
            </def>
            </deflist>
        </chapter>
        <p>After you have set this up, anything referring to your mod folder in the future refers to the top level folder you made</p>
    </tab>
    <tab title="Patch + Parts Mod">
        <p>For a patch + parts mod, first you need to set up unity according to the <a href="https://wiki.spacewarp.org/wiki/Setting_up_Unity">wiki</a>, and follow the instructions at the end about building a full mod from unity</p>
        <p>After you have done that, there should be a <code>plugin_template</code> folder within unity, if there isn't, then make one, this is your "mod folder" from now on</p>
        <p>Under your mod folder you should create 2 more folders <code>patches</code> and <code>libraries</code> as a sub-folder of <code>patches</code> to store your patch files and patch libraries</p>
        <p>After all that is done, you have set up your environment</p>
    </tab>
    <tab title="Patch + Code Mod">
        <p>For a patch + code mod, first you should set up a VS/Rider project using the <a href="https://github.com/SpaceWarpDev/SpaceWarp.Template">SpaceWarp Template</a></p>
        <p>After you have done that, there should be a <code>plugin_template</code> folder inside the generated project, this is your "mod folder" from now on</p>
        <p>After all that is done, you have set up your environment</p>
    </tab>
    <tab title="Patch + Code + Parts Mod">
        <p>For a patch + code parts mod, first you should set up a VS/Rider project using the <a href="https://github.com/SpaceWarpDev/SpaceWarp.Template">SpaceWarp Template</a></p>
        <p>After you have done that, there should be a <code>plugin_template</code> folder inside the generated project, this is your "mod folder" from now on</p>
        <p>After all that is done, you now need to set up unity according to the <a href="https://wiki.spacewarp.org/wiki/Setting_up_Unity">wiki</a>, and follow the instructions at the end about copying assets (or addressables) only</p>
        <p>Now you have set up your environment</p>
    </tab>
</tabs>

You are now ready to start writing patches with %product%