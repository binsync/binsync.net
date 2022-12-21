---
title: Install Validation
permalink: /docs/install-validation/
---

Although every decompiler has a slightly different implementation for BinSync, the instructions below should work almost the same for all decompilers.
This is because we use a unified GUI made to work in a variety of QT versions. 

In this tutorial, you will validate your BinSync install can:
1. Use Git to connect to a BinSync project
2. Read data from the remote BinSync project
3. Set the read data into your decompiler. 

For this tutorial, we will use the example binsync repo that is a part of the BinSync project. 

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
   1. You can hit `Ctrl+Shift+B` or `Ctrl+Alt+Shift+B` to open it, OR
   2. You can click your decompiler menu: `Edit -> Plugins -> Binsync: Configure...`. On Binja it's under `Plugins`. On Ghidra under `Tools`

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
// This is a large function comment.
// Thanks for using BinSync!
// 
// <3 mahaloz
// ***
__int64 __fastcall mahaloz_main(int a1, char **a2, char **a3)
{
  int ret_val; // [rsp+1Ch] [rbp-24h] BYREF
  mahaloz_struct special_var; // [rsp+20h] [rbp-20h] BYREF
  char buf[16]; // [rsp+30h] [rbp-10h] BYREF

  buf[8] = 0;
  LOBYTE(special_var.field_8) = 0;
  puts("Username: ");   // probs some username thing!
  read(0, buf, 8uLL);
  read(0, &ret_val, 1uLL);
  puts("Password: ");
  read(0, &special_var, 8uLL);
  read(0, &ret_val, 1uLL);
  ret_val = sub_400664(buf, &special_var);
  if ( !ret_val )
    sub_4006FD(buf);
  return sub_4006ED(buf);
}
```

Take note of the variable names & types, and the comments. This will look different per-decompiler, but the symbols and
types should line up for the most part.

For more general use, tips, and advice, see our [Use Guide](../fundamentals) for full help.
