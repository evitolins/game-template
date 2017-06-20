__game-{add project name here}__
===============================================================================

This document should contain important info on how to get started with this
game project.


Basic Usage
---------------------------------------

### a) Documentation

Store all documenation for the game within `/docs/`.  This includes meeting notes, schedules, planning and game design files.


### b) Asset Development

Store working files and output for official game assets within `/assets/`.
Depending on the project, certain asset types and workflows will be needed.

This area is for source files such as _Maya, Photoshop, Modo, Zbrush, etc..._
which are responsible for generating final assets for the game.

Below are a few common __asset types__ and corresponding __file structures__ to
consider:

- **Character** (deforming rig)

        /assets/char/Minion_A/
        /assets/char/Minion_A/Animation/
        /assets/char/Minion_A/Artwork/
        /assets/char/Minion_A/Exports/
        /assets/char/Minion_A/Geometry/
        /assets/char/Minion_A/Texture/
        /assets/char/Minion_A/Reference/
        /assets/char/Minion_A/Rig/


- **Prop** (non-deforming rig)

        /assets/prop/Sword_Worldslayer/
        /assets/prop/Sword_Worldslayer/Animation/
        /assets/prop/Sword_Worldslayer/Artwork/
        /assets/prop/Sword_Worldslayer/Geometry/
        /assets/prop/Sword_Worldslayer/Texture/
        /assets/prop/Sword_Worldslayer/Reference/
        /assets/prop/Sword_Worldslayer/Rig/


- **Environment** (no rig)

        /assets/env/Battle_Arena_A/
        /assets/env/Battle_Arena_A/Reference/
        /assets/env/Battle_Arena_A/Concept/
        /assets/env/Battle_Arena_A/Geometry/
        /assets/env/Battle_Arena_A/Texture/
        /assets/env/Battle_Arena_A/Lighting/

#### Asset Versions and Exports
All exported assets should be generated using completely committed files and
code and be sure to provide a clear relationship to their their committed state
within the repository.

These exported assets can then be linked to from the Unity folder for game
development usage.



### c) Game Development

Store final game engine code and copied exports from asset output (or referenced, if possible).

> Note: For Unity projects, the game directory will be named `/unity/`, and the internal struture determined by the software.*



### d) Personal Experimentation

When working on new ideas or code which you would like to maintain history and/or share your files with others on the team, it is ideal to work under a _custom git branch_ . This way users are not forced into pulling unneeded files/assets that are not yet offically part of the required asset pool. _(see "Advanced Usage > Branching" below)_

> Note: Originally we suggested storing this type of content within the `/personal/...` folder, but this structure is not ideal for organization or efficient file storage/transfers.




Advanced Usage
---------------------------------------

### Branching

#### Required Branches

`master` - Versioned, stable code ready for public consumption (alpha, beta, live).  (It is not advised to ever work directly within the master branch)

`develop` - Code expected for everyone to keep current with.  When a commit has proven stable, it can be merged into master, and marked with a specific version

#### Custom Branches

`feature/...` - When working on specific features or assets or need an area to collaborate with others outside of `develop` , it’s easy to create and share a feature branch to collaborate easily before promoting those files or changes for the rest of the team.



### Large File Storage

During game development, it will be a common need to store and share large files within a repo.  For this we use “git-lfs” technology.  If you have a filetype that is likely to exceed a few megabytes, we should set git-lfs to *automatically* handle its type and store it properly.

> __IMPORTANT:__ Please check with the tech team to make sure your Git LFS is setup properly on your workstation.  Otherwise, problems can occur and might disrupt the workflow of the entire team.

> Note: If you are not comfortable editing `.gitattributes` to include new file extensions for git-lfs, please feel free to ask for help in the #help Slack Channel.



### Ignoring Files

There are many files that are often created automatically which do not need to be tracked within Git.  Each user might have different needs based on their OS, or workflow… but a single “.gitignore” policy will help keep the repo tidy and free of junk.

#### Examples:
- __Unity:__ https://github.com/github/gitignore/blob/master/Unity.gitignore
- __MacOS:__ https://github.com/github/gitignore/blob/master/Global/macOS.gitignore


> If you are not comfortable setting up new file rules for .gitignore, please feel free to ask for help in the #help Slack Channel.




