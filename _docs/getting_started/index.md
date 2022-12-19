---
title: Introduction
permalink: /docs/home/
redirect_from: /docs/index.html
---

<p align="center">
   <img src="https://i.imgur.com/qdesKpg.png" style="width: 30%;" alt="BinSync Logo"/>
</p>

BinSync is a decompiler collaboration tool built on the Git versioning system to enable fined-grained reverse
engineering collaboration regardless of decompiler. BinSync is built by [mahaloz](https://github.com/mahaloz), 
the [SEFCOM](https://sefcom.asu.edu) research lab, and various members of [Shellphish](https://shellphish.net). 

All good decompilers share common objects called Reverse Engineering Artifacts (REAs). These REAs are the
center of BinSync's syncing ability. Here are the supported REAs:
- Function headers (symbol, args, type)
- Stack Variables (symbol, type)
- Structs
- Comments

Note: all types support user-created types like structs. In short, with BinSync you can track, manage, and sync 
changes you make in your decompiler with any decompiler supported by BinSync. 

For synchronous help, or a more vocal discussion, join our discord:
[![Discord](https://img.shields.io/discord/900841083532087347?label=Discord&style=plastic)](https://discord.gg/wZSCeXnEvR)

## Supported Platforms
- IDA Pro: **>= 7.3**
- Binary Ninja: **>= 2.4**
- angr-management: **>= 9.0**
- Ghidra: **>= 10.1**

All versions require **Python >= 3.6** and **Git** installed on your system. Ghidra support is still very much in early stage, so only expect the minimal features.

