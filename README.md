# Pokemon Prism RTC Fix

## What is it?
[Pokemon Prism](https://rainbowdevs.com/title/prism/) is a popular Pokemon Crystal romhack that is compatible with original hardware.  This patch fixes the real time clock functionality for *some* unsupported cartridge types.

## Who needs this patch?
If your copy of Pokemon Prism changes to a random time every time you save, or re-launch the system, you may benefit from this patch.  I have only been able to test this on the black PCB flash cartridges sold by Xiame Tuiwan Electronic Technology Co., Ltd. on Alibaba.com.  I am in no way affiliated, I just bought these cartridges over the other options because I thought black would make a cooler cartridge.  This will likely fix Pokemon Prism for both unsupported cartridges, and may fix Prism for emulators with said symptoms.  See the images section below for pictures of the supported cartridge.

## What is there to fix?
Unlike Pokemon Crystal, Pokemon Prism rewrites the cartridge's real time clock every time you save.  Pokemon Crystal only reads the clock, then adds a saved offset to it, thus accurately keeping the date and time.  Prism keeps that same offset, but it folds the current time into the offset and writes zeros to the cartridge's clock to start counting again from 0.  This has the benefit of fixing a bug with Pokemon Crystal in which the RTC counter cannot count greater than 512 days, however it has an unintended side effect of breaking some cheap third party flash cartridges.

That works on a genuine cartridge, however the cartridge that I used keeps accurate time, but appears to ignores the reset writes from Prism.  This causes Prism to count the same elapsed minutes twice (once in the new offset and again in the clock that was never reset).  The result is the clock jumping to seemingly a random time on every save or re-launch.  The clock itself is fine, just incompatible with Prism's saving routine.

This patch stops Prism from writing to the clock:
- The routine that 0's and writes the clock now only reads it.
- The save routine no longer replaces the offset with the current time, but it still copies the offset into your save.
- The two routines that wrote to the clock to clear the halt and carry flags are disabled.
- The date calculation that runs when you set the clock on a new game assumed that the clock had been reset to zero.  It now subtracts the clock's day count properly.

Side effects:
- The clock's day counter overflows after about 512 days.  If this happens, you may be able to reset the in-game clock with FlashGBX or similar, then set the time again via the Time Machine item.  This is untested, but may fix it for another 512 days.
- Resetting or rewriting the clock outside the game (FlashGBX or similar) will revert the in-game time by that amount.  You must set the clock again afterwards.
- Existing saves have a wrong stored offset (if they were made on a cartridge with this problem).  I don't know what will happen if you set the clock again other than with New Game.  Backup your save before messing with this.
- Prism no longer clears the clock's halt flag.  If your clock was ever halted (dead battery for example), Prism won't start it again.

I have only tested this on one cartridge type.  A genuine MBC3 cartridge does NOT need the patch, and I haven't tested it on them or other clones.

## How do I apply the fix?
1. Go to the [Rainbowdevs website](https://rainbowdevs.com/prism-setup/) and follow the instructions to patch a 0.95.0254 Prism ROM onto a "Pokemon - Crystal Version (USA, Europe) (Rev 1).gbc" ROM (MD5 301899b8087289a6436b0a241fbbb474).
2. Go to [Marcrobledo's rompatcher.js](https://www.marcrobledo.com/RomPatcher.js/) upload your freshly patched Pokemon Prism 0.95.0254 ROM (MD5 7777fe98c1985ed73d024e2518a3a83b), then upload the Pokemon_Prism_0.95.0254_RTC_Fix.bps as the patch file.  Click "Apply patch" and download "pokeprism (patched).gbc".

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
