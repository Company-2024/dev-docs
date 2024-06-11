# Visual Studio

## Environment Variables

`$LIBHOME` an environment variable that it set to the directory where all the
3rd party libraries are located, which can be `\\iserver\Development\Libraries`
or a local copy of the same directory.

## Add SharedLibs

Might need to delete x64 if it's there. <!-- Troubleshooting -->

## Using Libraries from `com/`

If you would like to include libraries from `com` e.g.

```cpp
#include "com/peralex/projects/ELINTAnalyser/ElintProcessor/DataTypes/PDWRecording.h"
```

add the `BranchDefaults.props` property sheet from
`W:\dev\Utilities\VisualStudioPropertySheets`

## Adding Package to Visual Studio

Open your Visual Studio project settings and add:

### Setting Up Project

Change Solution Platforms to your correct architecture.

Debug vs. Release: Debug will show you build errors etc. while release is
faster.

### Static Linking

Use `$(LIBHOME)`

C/C++ -> General -> Additional Include Directories:
`\\iserver\development\Libraries\com\github\microsoft\onnxruntime-1.16.2\onnxruntime-win-x64-1.16.2\include`

Linker -> General -> Additional Library Directories:
`\\iserver\development\Libraries\com\github\microsoft\onnxruntime-1.16.2\onnxruntime-win-x64-1.16.2\lib`

Linker -> Input -> Additional Dependencies: `onnxruntime.lib`

Ensure there is a semi-colon separating your added paths or filenames in the
string.
