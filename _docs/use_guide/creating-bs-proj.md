---
title: Creating a BS Project
permalink: /docs/creating-bs-proj/
---

Like in the [validation](/docs/install-validation) section, you can create your own repo for a BinSync project. BinSync
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
