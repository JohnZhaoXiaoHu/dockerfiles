FROM jashook/chocolatey:latest

# Download useful tools to C:\tools
ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\tools\\nuget.exe

# Download the Build Tools bootstrapper outside of the PATH.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

################################################################################
# Component IDs:
# Please see https://docs.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools for more information
# on component IDs if there are any that need to be modified or added.
#
################################################################################
#
# MS Build Tools
#
# Microsoft.Component.MSBuild:                              MSBuild
# Microsoft.VisualStudio.Component.CoreBuildTools:              Visual Studio Build Tools Core
# Microsoft.VisualStudio.Component.Roslyn.Compiler:             C# and Visual Basic Roslyn compilers
#
# VC++ 2017
#
# Microsoft.VisualStudio.Component.VC.CoreBuildTools:               Visual C++ Build Tools core features
# Microsoft.VisualStudio.Component.VC.Redist.14.Latest:             Visual C++ 2017 Redistributable Update
# Microsoft.VisualStudio.Component.Windows10SDK:                    Windows Universal C Runtime
# Microsoft.VisualStudio.Component.Static.Analysis.Tools:           Static analysis tools
# Microsoft.VisualStudio.Component.VC.CMake.Project:                Visual C++ tools for CMake
# Microsoft.VisualStudio.Component.VC.Tools.x86.x64:                VC++ 2017 v141 toolset (x86,x64)
#
# UCRT
#
# Microsoft.Component.VC.Runtime.UCRTSDK:                           Windows Universal CRT SDK
# Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81:        Windows 8.1 SDK and UCRT SDK
#
# VC++ Arm(64)
#
# Microsoft.VisualStudio.Component.VC.Tools.ARM:                    Visual C++ compilers and libraries for ARM
# Microsoft.VisualStudio.Component.VC.Tools.ARM64:                  Visual C++ compilers and libraries for ARM64
#
# .Net
#
# Microsoft.Net.Component.4.5.TargetingPack:                        .NET Framework 4.5 targeting pack
# Microsoft.VisualStudio.Component.PortableLibrary:                 .NET Portable Library targeting pack
#
# Microsoft.Net.Component.4.6.SDK:                                  .NET Framework 4.6 SDK
# Microsoft.Net.Component.4.6.TargetingPack:                        .NET Framework 4.6 targeting pack
# Microsoft.Net.ComponentGroup.TargetingPacks.Common:               .NET Framework 4 – 4.6 development tools
#
# VC++ 2015
#
# Microsoft.VisualStudio.Component.VC.140:                          VC++ 2015.3 v140 toolset for desktop (x86,x64)
#
# Windows SDKs
# 
# Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop:      Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 and x64]
# Microsoft.VisualStudio.Component.Windows81SDK:                    Windows 8.1 SDK
# Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop:      Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 and x64]
# Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm:  Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM and ARM64]

RUN C:\\TEMP\\vs_buildtools.exe --wait --quiet --norestart --nocache --installPath C:\BuildTools \
####
#    MSBuild Components
####
    --add Microsoft.Component.MSBuild \
    --add Microsoft.VisualStudio.Component.CoreBuildTools \
    --add Microsoft.VisualStudio.Component.Roslyn.Compiler \
####
#   VC++ Components
####
    --add Microsoft.VisualStudio.Component.VC.CoreBuildTools \
    --add Microsoft.VisualStudio.Component.VC.Redist.14.Latest \
    --add Microsoft.VisualStudio.Component.Windows10SDK \
    --add Microsoft.VisualStudio.Component.Static.Analysis.Tools \
    --add Microsoft.VisualStudio.Component.VC.CMake.Project \
    --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 \
####
#   UCRT
####
    --add Microsoft.Component.VC.Runtime.UCRTSDK \
    --add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 \
####
####
#   .Net
####
    --add Microsoft.Net.Component.4.5.TargetingPack \
    --add Microsoft.VisualStudio.Component.PortableLibrary \
    --add Microsoft.Net.Component.4.6.SDK \
    --add Microsoft.Net.Component.4.6.TargetingPack \
    --add Microsoft.Net.ComponentGroup.TargetingPacks.Common \
####
#   VC++ 2015
#
# Notes:
#
# msdia120.dll is required for building coreclr.
#
####
    --add Microsoft.VisualStudio.Component.VC.140 \
####
#    ARM | Arm64
####
    --add Microsoft.VisualStudio.Component.VC.Tools.ARM \
    --add Microsoft.VisualStudio.Component.VC.Tools.ARM64 \
####
#   Windows SDK
####
    --add Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop \
    --add Microsoft.VisualStudio.Component.Windows81SDK \
    --add Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop \
    --add Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&