---
description: Instructions for merging new webflow exports
---

# Merging webflow exports

1. Obtain the latest Webflow export from [here](changelog/)
2. Run [`import-webflow`](https://www.npmjs.com/package/import-webflow-export) `path-to-webflow-export.zip`
3. Check that everything works as expected
   1. Start the local dev server and try it
   2. Run automated tests
4. Add all the changes to git, commit and push to your branch.

## Fixing conflicts

If you have conflicts with webflow-controlled files, importing the latest webflow export ought to fix that.

This only works when the latest webflow export is safe to import, which should always be the case, by versioning components with breaking changes.

```
$ git checkout master 
Switched to branch 'master'
Your branch is behind 'origin/master' by 28 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)


$ git pull
Updating 5cb0775..d586c13
Fast-forward
...
  src/index.html         |    20 +-
...


$ git checkout feature-branch
Switched to branch 'feature-branch'


git merge master 
Auto-merging src/index.html
CONFLICT (content): Merge conflict in src/index.html
Automatic merge failed; fix conflicts and then commit the result.


import-webflow ~/Downloads/wazimap-ng.webflow\ \(latest-export-10032022\).zip 
Extracting to temporary directory /tmp/tmp-296926-8rNUgOwtcaJs
Copying css to src/css
Copying js to src/js
Copying images to src/images
Looking for files matching index.html in /tmp/tmp-296926-8rNUgOwtcaJs
Reading /tmp/tmp-296926-8rNUgOwtcaJs/index.html
Transforming using ./src/js/webflow/import.js
Looking for files matching {401,about}.html in /tmp/tmp-296926-8rNUgOwtcaJs
Reading /tmp/tmp-296926-8rNUgOwtcaJs/401.html
No DOM transformation provided
Writing src/401.html
Reading /tmp/tmp-296926-8rNUgOwtcaJs/about.html
No DOM transformation provided
Writing src/about.html
Writing src/index.html
Cleaning up temporary directory /tmp/tmp-296926-8rNUgOwtcaJs



$ git status
On branch no-style-tags-in-body
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        ...
	new file:   __tests__/gui/...
        ...
        
Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   src/index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   src/401.html
	modified:   src/about.html
	modified:   src/css/wazimap-ng.webflow.css
	modified:   src/js/webflow.js


$ git add src/

$ git commit
[feature-branch 32ecbac] Merge branch 'master' into feature-branch
```
