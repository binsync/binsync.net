---
title: Install
permalink: /docs/install/
---

Installing BinSync can be as simple as using pip in combination with our Python-based installer:
```bash
pip3 install binsync && binsync --install 
```

If you are using Binary Ninja, and you don't plan on developing BinSync, it's recommended to install it through the 
Binary Ninja plugin manager, which allows you to skip these install steps. 

Installation is a two-step process because we need to first install the BinSync core library into your Python install,
then we need to copy the plugin code to your respective decompiler. Using the above command is the simplest solution
since it will open an assistant prompt that asks for decompiler paths. It looks something like:
```
$ binsync --install

 _____ _     _____
| __  |_|___|   __|_ _ ___ ___
| __ -| |   |__   | | |   |  _|
|_____|_|_|_|_____|_  |_|_|___|
                  |___|
Now installing BinSync...
Please input decompiler/debugger install paths as prompted. Enter nothing to either use
the default install path if one exist, or to skip.

IDA Plugins Path:
...
``` 

If you are not able to find the `binsync` command, you might be able to access it with `python3 -m binsync`. 
**NOTE: you must pip install binsync to the python interpreter used in your decompiler**. If even that fails,
please jump to the [Manual Install](#manual-install) section.

After you are done with that, if you are using one of the following decompilers, please go to the link
and follow the extra setup instructions:
- [Ghidra](../ghidra)

## Manual Install

If you were able to use the built-in Python script, skip this. 

If you are unable to install using the earlier method, you are probably on Windows. In that case, installing
BinSync is a two-step process: 
1. Install the core with the Python version associated with your decompiler: `pip3 install binsync`
2. Install the decompiler stub directly into your decompilers `plugin` folder.

For step 2, you copy (or link) the file associated with your decompiler in the `decompiler_stubs` folder. As an example, for IDA you would copy only
the `decompiler_stubs/ida_binsync.py` file, but for angr you would copy the entire `decompiler_stubs/angr_binsync` folder. 

After you are done with that, if you are using one of the following decompilers, please go to the link
and follow the extra setup instructions:
- [Ghidra](../ghidra)

## Unlocking your SSH Key
If you plan on using BinSync to pull and push to a BinSync repo, you need a SSH key that is associated with that repo. If you plan 
on only reading from the repo, you don't need one. Since BinSync relies on Git for its headless-server and database, you must unlock
your SSH key when BinSync is in use.

## Install Validation and Usage
After you are done installing BinSync with the steps above, you should validate that the install works by syncing data from an example repo we have setup. 
You can find a tutorial to validate this install, with some basic usage, in the [Install Validation](/docs/install-validation) section.

After validating your installation, it's **highly** recommended that you read the [Usage Guide](/docs/fundamentals), since BinSync can be rather complicated to 
use on your very first look at it. 
