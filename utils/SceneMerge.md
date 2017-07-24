Unity Scene Merge Setup
======================================================

KDiff3 Installation
------------------------------------------
This diff application is free, robust and supported across all major platforms.
It should allow easy file merging when dealing with any files handled within
your git environment. 

Please follow the installation instructions provided here:
http://kdiff3.sourceforge.net/



UnityYAMLMerge Installation (`install-merge-tools`)
------------------------------------------
Here are notes on how to automate the installation on UnityYAMLmerge utility.

### 1) SourceTree Installation
`UnityYAMLMerge` is a small CLI application provided by Unity to help complex
merging situations within `.unity` and `.prefab` files.  We must tell
SourceTree to route all merge operations through this app to insure these files
are merged properly.

#### Custom Diff & Merge Tool Examples
__Windows:__
- __Diff Command:__ `C:\Program Files\Unity\Editor\Tools\UnityYAMLMerge`
- __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`

__MacOS:__
- __Command:__ `/Applications/Unity_5_5_3/Unity.app/Contents/Tools/UnityYAMLMerge`
- __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`



### 2) Define Fallback Merge Tool (kdiff3)
`mergespecfile.txt` is located in the same directory as the `UnityYAMLMerge`
application.  This file defines what diff tool will be used for merging activity
both for Unity files, or any other file.

#### Example using kdiff3 on MacOS
The code below can be pasted at the top of the file.

File path: `/Applications/Unity_5_5_3/Unity.app/Contents/Tools/mergespecfile.txt`

```bash
# Unity specific Diff Tool
unity use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
prefab use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto

# Fallback Diff Tool
* use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
```

> _Note:_ Application path and variables may need to be adjusted, depending on
installation location and OS.

> _Tip:_ It is a good idea to backup the original `mergespecfile.txt` file, in case
problems occur during editing.



Reference
------------------------------------------
Use this great [video](https://www.youtube.com/watch?v=EQB-N-ClO9g) as a guide.  It uses Meld as it's diff tool, but otherwise is exactly the workflow we will use.



Known Issues
------------------------------------------
- Can SourceTree honor a repo's local config for merge tool settings?
    - It seems SourceTree only uses/sets global config seetings for diff and merge tools
    - It seems that manually setting these config items do not take, after launching the
      SourceTree software (making automation impossible).
    - _https://community.atlassian.com/t5/Questions/Can-Does-SourceTree-use-local-git-config-for-Merge-and-Diff-tool/qaq-p/613626_
