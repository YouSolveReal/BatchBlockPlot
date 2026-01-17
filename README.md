# BatchBlockPlot Plugin Setup Guide for AutoCAD 2026

## Project Configuration

This plugin is now configured for **AutoCAD 2026** with .NET 8.0.

### Current Setup
- **Target Framework**: .NET 8.0 Windows
- **AutoCAD Version**: 2026
- **Platform**: x64
- **Output Type**: Class Library (DLL)

## AutoCAD References

The following AutoCAD 2026 assemblies are referenced:
- `acdbmgd.dll` - Database management
- `acmgd.dll` - Application services
- `accoremgd.dll` - Core functionality
- `AcWindows.dll` - Windows integration

All references point to: `C:\Program Files\Autodesk\AutoCAD 2026\`

## How to Load the Plugin in AutoCAD 2026

### Method 1: Using NETLOAD Command (Quick Testing)

1. Build the project (Debug or Release)
2. Open AutoCAD 2026
3. Type `NETLOAD` in the command line
4. Browse to the built DLL:
   - Deploy: `\Deploy\AutoCAD2026\BatchBlockPlot.dll`
5. Select the DLL and click Open
6. Type `BATCHPLOT` to launch the plugin

### Method 2: Auto-load on AutoCAD Startup

Create or edit the `acad.lsp` file in one of these locations:
- User Support: `%APPDATA%\Autodesk\AutoCAD 2026\R25.1\enu\Support\acad.lsp`
- AutoCAD Support: `C:\Program Files\Autodesk\AutoCAD 2026\Support\acad.lsp`

Add this line:
```lisp
(command "NETLOAD" "C:\\Path\\To\\Deploy\\AutoCAD2026\\BatchBlockPlot.dll")
```

### Method 3: Using AutoCAD Bundle (Professional Method)

1. Create folder structure:
   ```
   C:\ProgramData\Autodesk\ApplicationPlugins\BatchBlockPlot.bundle\
   ├── PackageContents.xml
   └── Contents\
       └── BatchBlockPlot.dll
   ```

2. Copy `PackageContents.xml` to the bundle root
3. Copy the built DLL to `Contents\` folder
4. Restart AutoCAD 2026
5. The plugin will auto-load and `BATCHPLOT` command will be available

## Available Commands

Once loaded, use these commands in AutoCAD:
- `BATCHPLOT` - Opens the Batch Block Plot dialog

### Plugin doesn't load
- Check AutoCAD's command line for error messages
- Try loading manually with NETLOAD first
- Verify the DLL isn't blocked (Right-click → Properties → Unblock)
