# Ironsworn with AI
- [Ironsworn with AI](#ironsworn-with-ai)
  - [Introduction](#introduction)
    - [Premise](#premise)
    - [What is this repo ?](#what-is-this-repo-)
    - [Preview and features](#preview-and-features)
  - [Requirements](#requirements)
    - [Mandatory](#mandatory)
    - [Optionnal](#optionnal)
    - [Opinionated](#opinionated)
  - [Installation](#installation)
    - [Extensions](#extensions)
    - [Mandatory](#mandatory-1)
    - [Optional](#optional)
    - [Opinionated](#opinionated-1)
    - [Settings](#settings)
      - [SillyTavern](#sillytavern)
      - [Multihog D\&D Framework](#multihog-dd-framework)
      - [Chat setup](#chat-setup)
      - [Databank](#databank)
      - [Expression+ Fork (if you installed it)](#expression-fork-if-you-installed-it)
      - [Auto music (if installed)](#auto-music-if-installed)
      - [TTS (if you installed Dialogue Voices)](#tts-if-you-installed-dialogue-voices)
      - [Ikarus Auto image](#ikarus-auto-image)
  - [Creating your character and campaign](#creating-your-character-and-campaign)
    - [Create you character](#create-you-character)
      - [(Easy) From Sillytavern using the UI](#easy-from-sillytavern-using-the-ui)
      - [(Hard-Legacy) Manually in a text editor](#hard-legacy-manually-in-a-text-editor)
        - [TIME](#time)
        - [CHARACTER](#character)
        - [MOMENTUM](#momentum)
        - [VOWS](#vows)
        - [INVENTORY](#inventory)
        - [COMPANIONS and ASSETS](#companions-and-assets)
        - [BONDS](#bonds)
  - [Done !](#done-)
  - [Disclaimer](#disclaimer)
  - [Credit \& thanks](#credit--thanks)

## Introduction
### Premise
In the Ironsworn tabletop roleplaying game, you are a hero sworn to undertake perilous quests in the dark fantasy setting of the Ironlands.
Others live out their lives hardly venturing beyond the walls of their village or steading, but you are different. You will explore untracked wilds, fight desperate battles, forge bonds with isolated communities, and reveal the secrets of this harsh land.
### What is this repo ?
[Ironsworn](https://tomkinpress.com/pages/ironsworn) is lightweight TTRPG meant to be played solo or in a small group. While the author did an incredible job giving you all the tools be your own GM, you might prefer someone to create the story for you. And maybe you can't find that someone.
That is why i decided to use Sillytavern, as well at some of its extension to try and recreate the experience from behind your screen.

### Preview and features
TODO

## Requirements
Note that the installation section will guide you into setting up each of them.
### Mandatory
- [SillyTavern](https://github.com/SillyTavern/SillyTavern)
- [MultihogDnDFramework](https://github.com/MultihogAurelius/SillyTavern-MultihogDnDFramework)
- [IronswornRoll](github.com/HijackHornet/SillyTavern-IronswornRoll)
- Files from this repo
### Optionnal
- [Expression-plus (fork)](https://github.com/HijackHornet/expressions-plus) to have companions sprites on the right
- [Auto-Music](https://github.com/virgilianshailer/AutoMusic) to generate music and SFX (requires comfyui)
- [Ikarus-auto-image](https://github.com/IkarusV/IkarusAutoImage) for its prompt post processing allowing you to define the tags of each character even with multihog

### Opinionated
For TTS i've spent weeks trying different providers and setup and i ended up using the following options. However if you have another prefered TTS provider just skip this section as its very much what I consider best (opensource, running on CPU, no VRAM, faster output than play time, but also good voice cloning).
- [Webui-TTS](https://ttswebui.com/) + [PocketTTS addon](https://github.com/HijackHornet/tts_webui_extension.pocket_tts)
- [Dialogue Voice](https://github.com/HijackHornet/TTS-DialogueVoices) this a vibecoded addon i did that will only work with WebUI-TTS and let you define a different voice per character

## Installation
### Extensions
Open SillyTavern and open the **Extensions** menu. Click **Install Extension**, paste each repository URL below, and install it. Refresh SillyTavern after installing the extensions.

### Mandatory
- [MultihogDnDFramework](https://github.com/MultihogAurelius/SillyTavern-MultihogDnDFramework)
- [IronswornRoll](https://github.com/HijackHornet/SillyTavern-IronswornRoll)

### Optional
- [Expression-plus (fork)](https://github.com/HijackHornet/expressions-plus)
- [Auto-Music](https://github.com/virgilianshailer/AutoMusic)
- [Ikarus-auto-image](https://github.com/IkarusV/IkarusAutoImage)

**Expression-plus** replaces the built-in Expressions extension, so disable the built-in **Expressions** extension after installing it. 
**Auto-Music** also requires ComfyUI and its required models/workflows. 
**Ikarus-auto-image** requires an image-generation API configured in SillyTavern.

The Dialogue Voice extension mentioned above is not required for the suite and is not included in this installation guide because its repository link is not available yet.
### Opinionated
The following guide if for installing the very good PocketTTS model using WebUI TTS.
Its quite a long install so i'm not recommending this to everyone. Expect at least 20min here.
Install [WebTTS UI](https://ttswebui.com/installation/) and then install the [PocketTTS extension](https://github.com/HijackHornet/tts_webui_extension.pocket_tts) (by me). Launch it and test it into the [Gradio page](http://localhost:7770/).
If you want to use custom voices, YOU NEED to open the voice cloning setup and follow the instructions. Its a legal requirement that we cant go around.
![alt text](GuideImages/firefox_EnKVmYPa58.jpg)
Once it works, you can either use it as is in sillytavern or also install the sillytavern extension [Dialogue Voices](https://github.com/HijackHornet/TTS-DialogueVoices) that allow splitting voices per character using regex. (See settings further down this guide)
### Settings
#### SillyTavern
**Important**: MultihogDnDFramework requires the use of ChatCompletion.

**Recommanded model**: DeepSeekV4 Flash 0731 (cheap, fast and knows the rules already)
If you want to use another model just try and test it by asking questions like "In ironsworn i am in a battle with a wolf. At what point do i win the combat ?" If the model says something like "when you complete the track you win" then it doesnt know the rules well enought to be a GM. Sure the tools provided here will guide it, and i included most of those rules into its prompt, but still its better if it already knows the basics. FYI in Ironsworn you progress on the battle track and at any point you can choose to try and roll for completing the battle, and your roll is compared to the track progress. So you dont (and usually shouldnt) have to fill the track to win.

- Enable function calling in **AI Response Configuration**. This is required for the IronswornRoll and Multihog tools.
- Use a context size of at least `18000` tokens. Recommanded `30000`
- Set the response length at `7000` tokens or higher.


#### Multihog D&D Framework
Open **Multihog D&D Framework**  under the magic wand icon then open the settings :
![alt text](GuideImages/firefox_WHSLkfwaaR.jpg)

The cartridge supplies the Ironsworn game system, prompts, modules, and tracker configuration. In the Multihog settings, open Game Systems > Game Cartridges > Import  and use [this file](Cartridge\multihog_cartridge_ironsworn_1788811796501.json), and activate the imported **Ironsworn** profile.

Disable the following :
- World Progression > **DISABLED**
- Persistant Map > Map Updater > **DISABLED**
- Persistant Map > Map Evolution > **DISABLED**

#### Chat setup
- Create a new character called "Narrator" or "Game master" and dont put ANY description in it. Multihog probably asked you to create one already.
- Create a personna with your Character name and an empty description as well (multihog will make its own)
- Open a new chat with the Narrator character
#### Databank
Open SillyTavern's **Data Bank** and import all seven PDF files from this repository's [`Databank`](Databank) folder:

- `1-The Basics_Ironsworn-Rulebook.pdf`
- `2-Your Character_Ironsworn-Rulebook.pdf`
- `3-Moves_Ironsworn-Rulebook.pdf`
- `4-Your World_Ironsworn-Rulebook.pdf`
- `5-Foes_Ironsworn-Rulebook.pdf`
- `6-Oracle_Ironsworn-Rulebook.pdf`
- `7-Gameplay_Ironsworn-Rulebook.pdf`

Import them into the global Data Bank so they are available to the campaign. Do not import the Delve rulebook; this suite is intended for the free Ironsworn base game. The above files have been trimed from example play that might confuse the AI.

In Silly tavern Extension menu, open **Vector Storage**, choose **Local**, and use the following settings.
![alt text](GuideImages/firefox_NoUPyDkWw9.jpg) Don't forget **[✓]Enable for files** !
#### Expression+ Fork (if you installed it)
Open the settings and go to "Scenario".
Set the following settings
![alt text](GuideImages/firefox_KCcMS30pNe.jpg)
The custom pattern is :
`<font\b[^>]*\bname=["']([^"']+)["'][^>]*>` with flag `gim`
#### Auto music (if installed)
In the settings uncheck `Library: Auto-play next on end`
For `Analyze every X message(s)` i chose 2 or 4. Dont put lower than 2 as the tool calls split every messages into 2 message already. Else music will generate twice per message. 
In advance settings select for both music and SFX `Èngine : Stable audio 3` and checkpoint `stable_audio_3_medium.safetensors`. Check `Loop` and i recommend using 20sec for SFX and 90sec for Music.

In comfyui you should find the workflow already in the templates. 
![alt text](GuideImages/firefox_mcOtfBVABG.jpg)
But really you only need to have the following models downloaded :
- text_encoders
  - [qwen3.5_2b_bf16.safetensors](https://huggingface.co/Comfy-Org/Qwen3.5/resolve/main/text_encoders/qwen3.5_2b_bf16.safetensors)
  - [t5gemma_b_b_ul2.safetensors](https://huggingface.co/Comfy-Org/stable-audio-3/resolve/main/text_encoders/t5gemma_b_b_ul2.safetensors)
- checkpoints
  - [stable_audio_3_medium.safetensors](https://huggingface.co/Comfy-Org/stable-audio-3/resolve/main/checkpoints/stable_audio_3_medium.safetensors)
#### TTS (if you installed Dialogue Voices)
For this to work you need to have WebUI TTS and to install the PocketTTS addon. 
If you use anything else just skip this part.
Use the following settins
![alt text](GuideImages/firefox_GBtoNrT6mQ.jpg)
![alt text](GuideImages/firefox_wBpazCvJft.jpg) Speaker detection pattern `<font\b[^>]*\bname=["']([^"']+)["'][^>]*>([^<]+)<\/font>`
Name to voice map is where you set the voice for each of the character of your story. Else they will default to the narrator voice. 
Available voices `Alba Mackenna (EN),Anna (EN),Azelma (EN),Bill Boerst (EN),Caro Davy (EN),Charles (EN),Cosette (EN),Eponine (EN),Eve (EN),Fantine (EN),George (EN),Jane (EN),Jean (EN),Javert (EN),Marius (EN),Mary (EN),Michael (EN),Paul (EN),Peter Yearsley (EN),Stuart Bell (EN),Vera (EN)`
![alt text](GuideImages/firefox_Vw0x7XdV3H.jpg)

To add custom voices to PocketTTS, add the voice sample (10-20sec) in `WebUITTS\voices`
Then add it without extension (`Alice` if file is `Alice.ogg`) in the available voices setting above. Then click reload.
#### Ikarus Auto image
Deactivate `Enable Prompt Injection`
Scroll to replacement and filters. Here you can implement logics that will modify prompts sent to ComfyUI. I wont go into detail here but you can put a filter that would say : If the prompt contain the name of my character, then prepend the prompt with a custom lora. Remember than multihog use a Narrator card so normal "character prefix" would not work and thats why i recommend this extension.
## Creating your character and campaign
### Create you character
#### (Easy) From Sillytavern using the UI
Now that you are in the new empty chat, its time to create your world and character ! Don't worry I made it easy for you. 

Type `/ironsworn-init` and enter.

**Step 1 :** Choose how you world is. You are given 3 options per topic, or you can write your own. Those responses will be loaded at all time in the context so the ai knows about your world. For reference look at the "Your world" section of the offical rules.

**Step 2 :** Create your character. Think about who you want to be and choose the matching stats. For reference look at [Your Character](Databank\2-Your Character_Ironsworn-Rulebook.pdf)

**Step 3 :** Pick three assets (ability or companions) to help on your journey. Only the first of its three abilities will be activated at first. You can upgrade them later by consuming XP.

**Step 4 :** Choose your bonds (friends, familly, places that own you for helping them etc)

**Step 5 :** Choose your vows. This is probably the most complicated one so i urge you to read page 191 of the official rulebook. But in summary you want to choose a mid term and a long term quest. The first one will take 20h or so to complete while the second one might take you the entire campaign, or you might not even complete it.

**Step 6 :** Copy the code of the tracker into multihog by clicking the 3 bar icon and pasting it there.![alt text](GuideImages/firefox_u8VRvOCGmf.jpg)

**Step 7:** Activate the new lorebook. To see it refresh the page then open lorebook and you should have a new entry to activate. Keep it always active 

#### (Hard-Legacy) Manually in a text editor
Not recommanded, but i'm leaving this here for reference and understand how the character tracker is built.

Start by opening [`TrackerTemplates/CharacterTemplate.txt`](TrackerTemplates/CharacterTemplate.txt) and filling in a copy of it. The template follows the character sheet and character-creation rules from the Ironsworn rulebook. You can compare your result with [`TrackerTemplates/ExampleCharacter.txt`](TrackerTemplates/ExampleCharacter.txt).

When you are finished, copy the completed template into the Multihog character or state tracker area where you want to use it. Keep the section names and formatting markers such as `[CHARACTER]`, `((SLOTS))`, and `((PILL))`, because Multihog uses them to display and maintain the tracker.

##### TIME
```text
[TIME]
Current Time: 08:00, Day 1
[/TIME]
```

Set the current in-world time and day. This is the starting clock for the campaign. You can change it to fit your opening scene, but keep the `[TIME]` block in the template.

##### CHARACTER
Choose your character's name and assign the five starting stat bonuses. Ironsworn starts with these bonuses, arranged in any order:

- Edge: quickness, agility, and ranged combat
- Heart: courage, willpower, empathy, and loyalty
- Iron: strength, endurance, and close combat
- Shadow: stealth, deception, and cunning
- Wits: knowledge, expertise, and observation

Use the values `3, 2, 2, 1, 1` exactly once each. For example, the provided character uses Edge `+3`, Heart `+2`, Iron `+1`, Shadow `+2`, and Wits `+1`.

Set the starting tracks as follows:

- HP: `5/5`
- Supply: `5/5`
- Spirit: `5/5`
- Experience: `0 XP`

Health, Supply, and Spirit normally range from 0 to 5. Supply represents the shared mundane equipment and provisions of the party, so you do not need to list every ration or arrow.

##### MOMENTUM
Start with `+2/10` momentum. The standard maximum is `+10`, and the reset value is `+2`. The tracker will update momentum as moves and consequences occur. Do not add debilities when creating the character.

##### VOWS
Create exactly two starting vows:

1. An **inciting vow**, which is the immediate problem that begins the campaign. Give it a rank, usually `Troublesome`, `Dangerous`, or `Formidable`.
2. A **long-term or background vow**, which is an important personal goal. Give it a rank of `Extreme` or `Epic`.

Write each vow as a short name followed by a clear description. The description is included in prompts, so keep it specific and easy to understand. Set both progress tracks to `0/10` at the start and leave the milestone marker as `? (No milestone yet)`. The example uses **Bring peace** as its inciting vow and **Clear our names** as its long-term vow.

##### INVENTORY
Items are optional. Add only important equipment, quest items, or resources that you want to establish in the fiction. Ordinary travel gear, food, ammunition, and similar necessities are already represented by Supply. Items do not grant mechanical bonuses unless an official asset says that they do.

##### COMPANIONS and ASSETS
You need exactly **three assets total**. Use the official Ironsworn assets from the [Ironsworn Printable Asset Cards](https://tomkinpress.com/collections/free-downloads/products/ironsworn-printable-asset-cards). The four official asset types are companions, paths, combat talents, and rituals.

A companion is simply an asset with an NPC name, role, type, and its own HP track. It counts as one of your three assets. Copy the companion's three abilities from the official card, mark the first ability as active with `((PILLS))`, and mark the remaining two abilities with `🔒`. Start a companion at `5/5` HP unless the asset specifies otherwise. In the example, Alice is the companion asset, while Infiltrator and Cutthroat are the other two assets.

For each non-companion asset, copy its name, asset type, and all three abilities from the official card. Put the first selected ability after `((PILLS))` and prefix locked abilities with `🔒`. At character creation, choose the three assets that best fit the character and their story. Additional assets can be gained later through experience during play.

##### BONDS
Add exactly **three starting bonds** with people, communities, or other meaningful groups. Mark the bonds progress track with three ticks, shown in the template as `0.75/10`. Give each bond a name and type, such as `NPC`, `Community`, or `Place`. The example includes a blacksmith, a village, and an overseer.
## Done !
You are done ! Thank you for reading this far. I hope your aventure will run smoothly and i'm open to suggestion for improvements.

## Disclaimer
This set of tools is meant to play Ironsworn without the [Delves](https://tomkinpress.com/pages/ironsworn-delve) extension. If you want to use the extension, you must buy it, adapt the prompts to it, and **MAKE SURE YOUR AI PROVIDER COMMIT TO NOT TRAIN ON PROMPTS**. If you feed AI with paid rulebooks you are destroying the author livelyhood. So don't be that guy... I'd say stick to the base game that is free and that AI already know the rules of. Then if you love it, buy the extension or the sequel rulebook and play without AI.
## Credit & thanks
Based on [Ironsworn](https://tomkinpress.com/pages/ironsworn) by Shawn Tomkin.
Thanks to him for making such a great game !
