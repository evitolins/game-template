Maya Presets and Tools
===============================================================================

## FBX
Standardizing our FBX exports is important.  We export our characters in 2
different ways: rigs and animation.  Below will explain how to install and use
the provided FBX export presets.


### Install Presets
1. Copy `FBX` folder to Maya's global preferences folder


### Exporting FBX Files

#### Rig
Use the provided preset to export your rig in a standardized fashion.

1. Select Mesh and Joints
2. File > Export Selection Options
    1. General Options > File Type: "FBX Export"
    2. Click "Export Selection"
3. Set Preset to "HnP_FBX_rig_v0"
    - "Export Selection" > File Type Specific Options > Presets
4. Name fbx file `<character>_rig.fbx`  _(e.g. `potato_rig.fbx`)_


#### Animation
Use the provided preset to export your animation in a standardized fashion.
Each animation is to be saved as an individual file, labeled with the action.

1. Select Joints
2. File > Export Selection Options
    1. General Options > File Type: "FBX Export"
    2. Click "Export Selection"
3. Set Preset to "HnP_FBX_anim_v0"
    - "Export Selection" > File Type Specific Options > Presets
4. Name fbx file `<character>_rig@_<label>.fbx` _(e.g. `potato_rig@walkForward01.fbx`)_
