# labelmaker2

Windows Forms label-printing application for generating Viking product barcodes, reading scale weight from a serial-connected device, and printing to a label printer.

## Stack

- .NET Framework 4.6.1
- Windows Forms
- ZXing.Net for barcode generation

## Repository layout

| Path | Purpose |
| --- | --- |
| `WindowsFormsApp1.sln` | Visual Studio solution |
| `WindowsFormsApp1/WindowsFormsApp1.csproj` | Main desktop application project |
| `WindowsFormsApp1/packages.config` | NuGet package definitions |

## Runtime assumptions

- Windows desktop environment
- Serial scale on `COM3`
- Label printer named `Rollo Printer`
- ZXing package restored through NuGet

## Build

Open the solution in Visual Studio, or build with MSBuild after restoring packages:

```powershell
nuget restore .\WindowsFormsApp1.sln
msbuild .\WindowsFormsApp1.sln /p:Configuration=Release
```

## Current behavior

The application:

1. Reads a live scale value from a serial port when available.
2. Builds a CODE_128 barcode string with product and date information.
3. Renders barcode and overlay text in the UI.
4. Prints labels to the configured printer.

## Maintenance notes

- Hardware dependencies are currently hard-coded in the application.
- Exception handling is mostly silent, so later hardening should surface failures more clearly.
- `labelmaker2` appears to be the maintained successor to `labelmaker`; compare both before making larger changes.
