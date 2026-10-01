# Pokemon Prism RTC Fix

## What is it?
[Pokemon Prism](https://rainbowdevs.com/title/prism/) is a popular Pokemon Crystal romhack that is compatible with original hardware.

## What is there to fix?
Unlike Pokemon Crystal, Pokemon Prism 

## Who needs this patch?
If your copy of Pokemon Prism changes to a random time every time you save, or re-launch the system, you may benefit from this patch.  I have only been able to test this on the black PCB flash cartridges sold by Xiame Tuiwan Electronic Technology Co., Ltd. on Alibaba.com.  I am in no way affiliated, I just bought these cartridges over the other options because I thought black would make a cooler cartridge.  This will likely fix Pokemon Prism for both unsupported cartridges, as well as emulators with said symptoms.  See the images section below for pictures of the supported cartridge.

## How do I apply the fix?
Go to [the Rainbowdevs BSP patcher](https://rainbowdevs.com/patcher_unified.htm), upload your freshly patched Pokemon Prism 0.95.0254 ROM, then upload the Pokemon_Prism_0.95.0254_RTC_Fix.bps, and click "Begin patching".  Download the patched ROM, clear the ROM from your flash cart, then flash the newly patched ROM.  

You'll know it works if:
1. The real time clock increments while the system is offline.
2. The real time clock is consistent every time you power-cycle your console.
3. The real time clock is consistent when you load your game.
4. The real time clock is consistent when you save your game, then re-check the time.

If this patch does not fix your cartridge, please open an [issue](https://github.com/SK-Crow/Pokemon_Prism_RTC_Fix/issues) and I'll do what I can to help.  When in doubt, ask Claude or Grok - both have a good understanding of these things, and can apply patches for you.

## Images
placeholder
