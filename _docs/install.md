---
title: Install
permalink: /docs/install/
---

Installing BinSync can be as simple as using pip in combination with our Python-based installer:
```bash
pip3 install binsync && binsync --install 
```

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
2. Install the decompiler plugin directly into your decompilers `plugin` folder.

For step 2, you copy all files (and folders) found under the plugin folder in BinSync. As an example, for IDA,
you would copy everything in `plugins/ida_binsync/*` to the plugins folder.

After you are done with that, if you are using one of the following decompilers, please go to the link
and follow the extra setup instructions:
- [Ghidra](../ghidra)


## Install Validation
Although BinSync supports various decompilers, which may have large differences, a lot of the way you interact
with BinSync is standard across all versions. In each decompiler we use the same UI regardless of QT version.

For decompiler specific intricacies, please see our supported decompilers usage manual in our [Wiki](https://github.com/angr/binsync/wiki).
Before attempting to use the BinSync for its pushing features, **assure you have an unlocked (non-password protected) ssh key 
associated with the repo you plan on editing**.

After validating your install below, it is very helpful to read our user [Manual](https://github.com/angr/binsync/wiki/Manual) in our [Wiki](https://github.com/angr/binsync/wiki).

### Sync Validation 
1. Copy down a local version of the testing repo and grab the `fauxware` binary
```bash
git clone git@github.com:mahaloz/binsync_example_repo.git
cp binsync_example_repo/fauxware .
```

2. Open the fauxware binary in your decompiler, verify it has loaded in the decompiler terminal
```
[BinSync] 2.9.1 loaded
```
Or check your plugin menu. For example, if you are using IDA, you should see this option:

   <img src="/assets/img/binsync_idaplugin.png" width="50%" height="50%">

If neither does not show, it means the plugin is not in the plugins folder.

3. Open the BinSync Config Pane
   1. You can hit `Ctrl+Shift+B` to open it, OR
   2. You can click your decompiler menu: `Edit -> Plugins -> Binsync: settings`. On Binja it's under `Tools`.

4. Give a username and find the example_repo from earlier, click ok
   <img src="/assets/img/demo1.png" width="50%" height="50%">

The Git repo refers to the local path of the BinSync repo. If you do not create a BinSync repo locally, you should leave it blank. In this exmaple, you should copy the git URL (`git@github.com:mahaloz/binsync_example_repo.git`) to "Remote URL".

5. Verify your terminal says (with your username):
```bash
[BinSync]: Client has connected to sync repo with user: <username>.
```

6. You should now see an Info Panel. Click on `Activity`, you can see other user's activities. You should also notice
   your username on the bottom right of the panel to be green (online).
   <img src="/assets/img/demo2.png" width="50%" height="50%">

Congrats, your BinSync seems to connect to a repo, and recognize you as a user.
Let's test pulling to verify you can actually do stuff with your install.

7. In your decompiler, click anywhere in the function `main` once. After a second or two you should notice on the
   Info Panel that the words on the bottom left say `main@0x40071d`. This is your context.

8. Now click on the `Context` tab, and right click on the user `mahaloz`. Click the `Sync` popup.
   <img src="/assets/img/demo3.png" width="50%" height="50%">

9. If everything works out, your decompilation should've changed for `main`. Now the function should be named
   `mahaloz_main`, and it should look something like:

```c
// ***
// This is a function comment:
//
// Thanks for using BinSync <3
//
// - mahaloz
// ***
int __cdecl mahaloz_main(int argc, const char **argv, const char **envp)
{
  int buf;
  mahalo_struct special_stack_var;
  char username[16];

  username[8] = 0;
  LOBYTE(special_stack_var.field_8) = 0;
  puts("Username: ");
  read(0, username, 8uLL);
  read(0, &buf, 1uLL);
  puts("Password: ");                           // totally a password
  read(0, &special_stack_var, 8uLL);
  read(0, &buf, 1uLL);
  buf = authenticate(username, &special_stack_var);
  if ( !buf )
    rejected(username);
  return accepted(username);
}
```

Take note of the variable names & types, and the comments. This will look different per-decompiler, but the symbols and
types should line up for the most part.

For more general use, tips, and advice, see our [Wiki Manual](https://github.com/angr/binsync/wiki/Manual) for full help.

### Making your own BinSync Repo

Like in the [validation](#validation) section above, you can create your own repo for a BinSync project. BinSync
will work with any git url, but for this tutorial we will only show how to do it on GitHub.

1. Make a GitHub repo; it does not matter if you init it or add a README
<img src="/assets/img/demo4.png" width="50%" height="50%">

2. Copy the SSH url from the next page; It would look something like: `git@github.com:mahaloz/my_binsync_project.git`

3. Open a binary in your decompiler of choice; we will use `fauxware` again from the example above

4. Configure BinSync in your decompiler and fill in the remote url and user. You can put nothing in the git repo
   section as it will default to putting the repo next to the binary you have open.

   <img src="/assets/img/demo5.png" width="50%" height="50%">

You should now be connected to your new remote repo. The remote on GitHub will also show 2 new branches now:
- your first user
- the `binsync/__root__` repo

Now all your friends can connect their clients to your repo like in the example above :).
