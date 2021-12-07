---
description: Instructions for merging new webflow exports
---

# Merging webflow exports

1. Obtain the latest Webflow export from [here](changelog/)
2. Unzip it into a temporary folder `unzip webflow.zip`
3. Use `rsync` to copy the new files across `rsync -avz /path/to/unzipped/file/* /path/to/wazimap-ng-ui/src`
4. The `rsync` command will bring about a bunch of changes and it is important to note what changes are needed.&#x20;
5. Add `<script src="js/index.js"></script>` after the last script tag in src/index.html.

**Example:**

Command: `rsync -avz unzipped/* /home/warachi/Documents/OpenUp/wazimap-ng-ui/src`

A lot of changes are made by the above command and in this case, the files marked `M` for modified and the ones that are desired.

![](<../.gitbook/assets/Screenshot from 2021-06-29 15-27-34.png>)
