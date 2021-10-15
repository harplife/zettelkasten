---
alias: [Reasons why Linux sucks, Linux flaws]
tags: [experience, opinion, thought, linux, ubuntu]
status: ongoing
edited: 2021-10-15
---

# Reasons why Linux sucks
It's just my experience with using Ubuntu at home, since the start of 2021.
The laptop I was using (HP Elite) initially had Windows 10 but it started acting out after updating it. So I replaced with Ubuntu 20.04. Then, issues came up again, and so I installed Ubuntu 18.04, which proved to be a lot more stable.

As far as using Linux for hosting website and such goes, I still prefer Linux.

I listed issues I've experienced, organized by categories.

## Graphics
- Linux isn't quite compatible with laptops with Dual GPUs (like HP Elite series).
- Most of Steam games crashes.
- Screen tearing is QUITE noticeable (it didn't happen on Windows 10).
- QT library has issues; GUI programs that has dependency all crashed. Horribly.

## Firmware
- Turns out Linux is not compatible with many devices. Wacom is one. Even if the driver is provided by the company (that made the device), it's rather difficult to install it.

## Softwares
- So many dependencies, so many missing. It's nearly impossible to figure out which dependencies are missing. On hindsight, [[appimage|AppImage]] might be the solution for that.
- Some programs I have to build myself, and chances are, it won't run.

## Notifications
- A program could be installing without any indication (no GUI, no terminal).
- A program could fail to install/run without any indication (no GUI, no terminal).

## Language Compatibility
- Some programs do not allow typing Korean.
- Setting right ALT key as language switch button doesn't work right sometimes.
- Korean words break sometimes, and won't form a character completely. (e.g. ㅅㅡㄴㅣㅁ)

## Conclusion
Some of these problems are not entirely the fault of the OS itself, but rather the fault of the GNOME desktop, or the program. I can't say for sure that other Linux based operating systems share the same problems that Ubuntu has - but as far as I know, Ubuntu is the most developed one for home use, and most of the systems use GNOME desktop all the same.

The laptop already had some issues to begin with, and it might've worsen the problems in Linux, especially the Graphics. I had fixed the problem with the Audio (on Windows 10), so I guess that's a plus.

HP does some things to the laptop at BIOS level, so I think it might've messed with the Linux. Next time I try Linux, it might be better to use a FreeDOS laptop, or a laptop that is made for Linux.

I looked more into the screen tear issue, and that seems to be a prevalent issue that is acknoledged across the linux community - the problem has been around for a while.