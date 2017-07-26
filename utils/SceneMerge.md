Unity Scene Merge Setup
======================================================

Unity development within a team requires special handling to ensure edited
files are merged properly without unneeded conflict.  The instructions below
will guide you to setup a solid method to do so using the follwing tools:

- SourceTree
- KDiff3
- UnityYAMLMerge



Getting Started
------------------------------------------
First off... watch this [video](https://www.youtube.com/watch?v=EQB-N-ClO9g).

We have modified some of the process below, mainly to use the application
"KDiff" instead of "Meld", but otherwise is the workflow we have choosen to
use.


KDiff3 Installation
------------------------------------------
This diff application is free, robust and supported across all major platforms.
It should allow easy file merging when dealing with any files handled within
your git environment. 

Please follow the installation instructions provided here:
http://kdiff3.sourceforge.net/



UnityYAMLMerge Installation
------------------------------------------
`UnityYAMLMerge` is a small CLI application provided by Unity to help complex
merging situations within `.unity` and `.prefab` files.  



### 1) Git Client Installation

#### a) SourceTree
We must tell SourceTree to route all merge operations through this app to
insure these files are merged properly.

This process must be done manually in the SourceTree's preferences UI.

_Preferences/Options > Diff > External Diff/Merge_

> _Windows Example:_
> - __Diff Command:__ `C:\Program Files\Unity\Editor\Tools\UnityYAMLMerge`
> - __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`
> 
> _MacOS Example:_
> - __Command:__ `/Applications/Unity/Unity.app/Contents/Tools/UnityYAMLMerge`
> - __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`

#### b) Git CLI
For those power-users out there... you can also install settings for your CLI
to direct merge operations properly.

Please try running `./utils/install-merge-tools` from the repo's root directory
to automate this process.



### 2) Define Fallback Merge Tool
To ensure that any other files are merged normally by Git, you must instruct
`UnityYAMLMerge` how you want other files to be handled.

The setting file `mergespecfile.txt` is located in the same directory as the
`UnityYAMLMerge` application installed above.  This file defines what diff tool
will be used for merging activity both for Unity files, or any other file.


#### Installation
Copy and paste the code below, at the top of your `mergespecfile.txt` file.

_The KDiff3 application path ("/usr/local/bin/kdiff3") may require editing,
based on installation location_

```bash
# Unity-Specific Diff Tool
unity use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
prefab use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto

# Fallback Diff Tool
* use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
```

> _Tip:_ It is a good idea to backup the original `mergespecfile.txt` file, in case
problems occur during editing.

> _Note:_ It is possible to use an alternative diff tool, but will require its own
custom application paths and input variables.  (See instructions within file for
more details).



Known Issues
------------------------------------------
- Can SourceTree honor a repo's local config for merge tool settings?
    - It seems SourceTree only uses/sets global config seetings for diff and merge tools
    - It seems that manually setting these config items do not take, after launching the
      SourceTree software (making automation impossible).
    - _https://community.atlassian.com/t5/Questions/Can-Does-SourceTree-use-local-git-config-for-Merge-and-Diff-tool/qaq-p/613626_
