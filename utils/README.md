Project-Specific Utilities Area
======================================================


UnityYAMLMerge Installation (`install-merge-tools`)
------------------------------------------
Here are notes on how to automate the installation on UnityYAMLmerge utility.

### 1) SourceTree Installation
`UnityYAMLMerge` is a small CLI application provided by Unity to help complex
merging situations within `.unity` and `.prefab` files. 

__Custom Diff Tool Example:__
- __Diff Command:__ `/Applications/Unity_5_5_3/Unity.app/Contents/Tools/UnityYAMLMerge`
- __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`

__Custom Merge Tool Example:__
- __Merge Command:__ `/Applications/Unity_5_5_3/Unity.app/Contents/Tools/UnityYAMLMerge`
- __Arguments:__   `merge -p $BASE $REMOTE $LOCAL $MERGED`



### 2) Define Fallback Merge Tool
`mergespecfile.txt` is located in the same directory as the `UnityYAMLMerge`
application and defines what diff tool the app will direct merging activity to
based on the file types being compared.

MacOS path example: `/Applications/Unity_5_5_3/Unity.app/Contents/Tools/mergespecfile.txt`

__Example using kdiff3 on MacOS:__
```bash
# Unity specific Diff Tool
unity use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
prefab use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto

# Fallback Diff Tool
* use "/usr/local/bin/kdiff3" "%r" "%b" "%l" -o "%d" --auto
```


Reference
------------------------------------------
- https://www.youtube.com/watch?v=EQB-N-ClO9g


Known Issues
------------------------------------------
- Can SourceTree honor a repo's local config for merge tool settings?
    - It seems SourceTree only uses/sets global config seetings for diff and merge tools
    - It seems that manually setting these config items do not take, after launching the
      SourceTree software (making automation impossible).
    - _https://community.atlassian.com/t5/Questions/Can-Does-SourceTree-use-local-git-config-for-Merge-and-Diff-tool/qaq-p/613626_
- Need to choose an "official" merge tool for the team (cross-platform, free)
    - diffMerge
    - meld (sorta supported on Mac)
    - kDiff
- Locating a user's global git config file is not completely straight forward
    - local: `git config --local --list --show-origin | grep "config" | awk '{print $1}' | sort -u | sed -e "s/^file://"` (however we can pretty much assume `.git/config`)
    - global: `git config --global --list --show-origin | grep ".gitconfig" | awk '{print $1}' | sort -u | sed -e "s/^file://"`

