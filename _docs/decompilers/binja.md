---
title: Binary Ninja
permalink: /docs/binja/
---

## Extra Install Steps 

### If you don't plan on developing BinSync
If you are using Binary Ninja, and you don't plan on developing BinSync, it's recommended to install it through the Binary Ninja plugin manager, which allows you to skip these install steps.

1. Click `Plugins->Manage Plugins` and search for and install BinSync
2. Continue setting up BinSync by [setting up access to your BinSync repo](/docs/install/#set-up-access-to-your-binsync-repo)

### If you installed manually or via the install script
Since Binja may be running a custom Python interpreter, please manually set or verify that your Python
for Binja is set to the same python as `python3` in your terminal. To do that:
1. Open Binja
2. Click `Edit->Settings->User` and search for Python
3. Select the correct Python interpreter for `Python Interpreter`
4. Restart Binja

## Usage Notes
BinSync also works when you open .bndb files (or .hex files with identical contents) in place of the binary file used when creating the project. 

## Support Progress

| Operations&nbsp;&nbsp;&nbsp;&nbsp; | Function Headers&nbsp;&nbsp;&nbsp;&nbsp; | Stack Vars&nbsp;&nbsp;&nbsp;&nbsp; | Global Vars&nbsp;&nbsp;&nbsp;&nbsp; | Structs&nbsp;&nbsp;&nbsp;&nbsp; | Enums&nbsp;&nbsp;&nbsp;&nbsp; | Comments&nbsp;&nbsp;&nbsp;&nbsp; |
|------------------------------------|------------------------------------------|------------------------------------|-------------------------------------|---------------------------------|-------------------------------|----------------------------------|
| Symbols   	                        | :heavy_check_mark: 	                     | :heavy_check_mark:    	            | :heavy_check_mark: 					            | :heavy_check_mark:   					      | :heavy_check_mark: 					      | :heavy_check_mark: 	             |
| Types     	                        | :heavy_check_mark: 	                     | :heavy_check_mark:    	            | :heavy_check_mark: 					            | :heavy_check_mark:   					      | :heavy_check_mark: 					      | :heavy_check_mark: 	             |
| Pull      	                        | :heavy_check_mark: 	                     | :heavy_check_mark:    	            | :heavy_check_mark: 					            | :heavy_check_mark:   					      | :heavy_check_mark: 					      | :heavy_check_mark: 	             |
| Push      	                        | :heavy_check_mark:                       | :heavy_check_mark:		               | :heavy_check_mark:					             | :heavy_check_mark:			           | :heavy_check_mark: 					      | :heavy_check_mark: 					         |
| Auto Push 	                        | :heavy_check_mark:                       | :heavy_check_mark:		               | :heavy_check_mark:					             | :heavy_check_mark:			           | :heavy_check_mark: 					      | :heavy_check_mark: 					         |
