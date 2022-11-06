---
title: Ghidra
permalink: /docs/ghidra/
---

## Extra Install Steps
After following the setps in the [Install](../install) page, you will need to do the following:
1. Start Ghidra
2. On the Project Window, click the tab `File->Install Extensions...`
![](./data/readme_0.png)

3. Search in the filter for "binsync", and enable it by clickng on the box
	- If you don't see the binsync plugin, download the latest release from [here](https://github.com/angr/binsync/releases/latest/download/binsync-ghidra-plugin.zip) and add it manually to the Extensions/Ghidra folder in your install.

4. Restart Ghidra
5. Open a binary, now click `File->Configure...` tab and enable `binsync` plugin.

You are done! Now you should be able to hit `Ctrl+Shift+B` to start the BinSync config. 
You can also find it in the `Tools` tab when you have a binary open.  