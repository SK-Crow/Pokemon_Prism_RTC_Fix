# Pokemon Prism RTC Fix

## What is it?
[Pokemon Prism](https://rainbowdevs.com/title/prism/) is a popular Pokemon Crystal romhack that is compatible with original hardware.

## What is there to fix?
Placeholder

## Who needs this patch?
If your copy of Pokemon Prism changes to a random time every time you save, or re-launch the system, you may benefit from this patch.  I have only been able to test this on the black PCB flash cartridges sold by Xiame Tuiwan Electronic Technology Co., Ltd. on Alibaba.com.  I am in no way affiliated, I just bought these cartridges over the other options because I thought black would make a cooler cartridge.  This will likely fix Pokemon Prism for both unsupported cartridges, as well as emulators with said symptoms.  See the images section below for pictures of the supported cartridge.

## How do I apply the fix?
1. Go to the [Rainbowdevs website](https://rainbowdevs.com/prism-setup/) and follow the instructions to patch a 0.95.0254 Prism ROM onto a "Pokemon - Crystal Version (USA, Europe) (Rev 1).gbc" ROM (MD5 301899b8087289a6436b0a241fbbb474).
2. Go to [Marcrobledo's rompatcher.js](https://www.marcrobledo.com/RomPatcher.js/) upload your freshly patched Pokemon Prism 0.95.0254 ROM, then upload the Pokemon_Prism_0.95.0254_RTC_Fix.bps as the patach file.  Click "Apply patch, and download "pokeprism (patched).gbc".

Your patched ROM's MD5 will be **cee3a490c52381e7dc822f9abc7fd467**.  If you get a different result, you missed a step, used a different base ROM, or applied the wrong version of Pokemon Prism.

You'll know it works if:
1. The real time clock increments while the system is offline.
2. The real time clock is consistent every time you power-cycle your console.
3. The real time clock is consistent when you load your game.
4. The real time clock is consistent when you save your game, then re-check the time.

If this patch does not fix your cartridge, please open an [issue](https://github.com/SK-Crow/Pokemon_Prism_RTC_Fix/issues) and I'll do what I can to help.  When in doubt, ask Claude or Grok - both have a good understanding of these things, and can apply patches for you.

## Images
See a list of supported cartridge types below.  There's only one at the moment - please submit a picture of yours if it works for you.

![Supported Cartridge 1](https://raw.githubusercontent.com/SK-Crow/Pokemon_Prism_RTC_Fix/refs/heads/master/Images/cartridge.jpg)
