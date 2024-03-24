---
layout: post
author: Mikami
title: Assets not found in binary app
---

When you double-click an application(binary app) to run it on macOS, the application's working directory is set to the user's home directory by default, not the directory where the application resides. This behavior contrasts with running the application from the command line (CLI), where the working directory is typically the directory from which you run the command, which can lead to issues.


<br/>
Solution:


<br/>
Create a Wrapper Script:

Another solution is to create a script that sets the working directory correctly and then launches the application. This script can then be converted to an application bundle (.app) that users can double-click.

bash:

```
#!/bin/bash
cd "$(dirname "$0")"  # Change directory to the script's directory
exec ./YourExecutableName  # Replace with your executable's name
```

After creating this script, you can use tools like Platypus or Script Editor to create a .app bundle that runs your script, packaging your actual executable and resources as needed.