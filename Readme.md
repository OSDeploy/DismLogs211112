#1 Test with CAB.log (ZIPPED)
OneCore LCU CAB file was applied to mounted Windows 11, resulted in error. Log file is less than 50MB.  LogLevel Debug

#2 Test with MSU.log (ZIPPED)
OneCore LCU CAB file was renamed to MSU and then applied to mounted Windows 11, resulted in success.  Log file is over 100MB. LogLevel Debug

#LCU was downloaded from Windows Update
http://download.windowsupdate.com/c/msdownload/update/software/secu/2021/11/windows10.0-kb5007215-x64_0257394e095bfcaffd59f41dc30df4d94edbb7e2.cab

#Tested with Windows 11 Enterprise x64
PS C:\> Get-WindowsImage -ImagePath "T:\211112\install.wim" -Index 1
ImageIndex       : 1
ImageName        : Windows 11 Enterprise
ImageDescription : Windows 11 Enterprise
ImageSize        : 16,131,426,863 bytes
WIMBoot          : False
Architecture     : x64
Hal              : 
Version          : 10.0.22000.258
SPBuild          : 258
SPLevel          : 0
EditionId        : Enterprise
InstallationType : Client
ProductType      : WinNT
ProductSuite     : Terminal Server
SystemRoot       : WINDOWS
DirectoryCount   : 22011
FileCount        : 101772
CreatedTime      : 9/13/2021 10:10:42 AM
ModifiedTime     : 10/13/2021 11:06:43 PM
Languages        : en-US (Default)

#Package returns a OnePackage, which contains an LCU and SSU and other hidden ingredients
PS C:\> Get-WindowsPackage -PackagePath "T:\211112\windows10.0-kb5007215-x64.cab" -Online
PackageName              : OnePackage~~~~0.0.0.0
Applicable               : True
Copyright                : 
Company                  : 
CreationTime             : 
Description              : 
InstallClient            : 
InstallPackageName       : 
InstallTime              : 
LastUpdateTime           : 
DisplayName              : 
ProductName              : 
ProductVersion           : 
ReleaseType              : Other
RestartRequired          : Possible
SupportInformation       : 
PackageState             : Installed
CompletelyOfflineCapable : Undetermined
SelfServicingPackage     : False
CapabilityId             : 
Custom Properties        : 
Features                 : {}

#Expanded OneCore LCU information of the SSU
PS C:\> Get-WindowsPackage -Online -PackagePath "T:\211112\windows10.0-kb5007215-x64\SSU-22000.280-x64.cab"
PackageName              : Package_for_ServicingStack_280~31bf3856ad364e35~amd64~~22000.280.1.0
Applicable               : True
Copyright                : Microsoft Corporation
Company                  : Microsoft Corporation
CreationTime             : 2/10/1601 9:16:50 PM
Description              : Fix for ServicingStack 10.0.22000.280
InstallClient            : UpdateAgentLCU
InstallPackageName       : Package_for_ServicingStack_280~31bf3856ad364e35~amd64~~22000.280.1.0.mum
InstallTime              : 11/9/2021 8:38:43 PM
LastUpdateTime           : 2/10/1601 9:16:50 PM
DisplayName              : Servicing Stack 10.0.22000.280
ProductName              : Package_for_ServicingStack_280
ProductVersion           : 
ReleaseType              : Update
RestartRequired          : Possible
SupportInformation       : 
PackageState             : Installed
CompletelyOfflineCapable : No
SelfServicingPackage     : True
CapabilityId             : 
Custom Properties        : 
Features                 : {}

#Expanded OneCore LCU information of the LCU
PS C:\> Get-WindowsPackage -Online -PackagePath "T:\211112\windows10.0-kb5007215-x64\Windows10.0-KB5007215-x64.cab"
PackageName              : Package_for_RollupFix~31bf3856ad364e35~amd64~~22000.318.1.8
Applicable               : True
Copyright                : Microsoft Corporation
Company                  : Microsoft Corporation
CreationTime             : 2/10/1601 9:16:50 PM
Description              : Fix for KB5007215
InstallClient            : UpdateAgentLCU
InstallPackageName       : Package_for_RollupFix~31bf3856ad364e35~amd64~~22000.318.1.8.mum
InstallTime              : 11/9/2021 8:55:29 PM
LastUpdateTime           : 2/10/1601 9:16:50 PM
DisplayName              : default
ProductName              : Package_for_RollupFix
ProductVersion           : 
ReleaseType              : SecurityUpdate
RestartRequired          : Possible
SupportInformation       : https://support.microsoft.com/help/5007215
PackageState             : Installed
CompletelyOfflineCapable : Undetermined
SelfServicingPackage     : False
CapabilityId             : 
Custom Properties        : 
                           \Version : 10.0.22000.318
                           \PackageFormat : PSFX
                           \PSFXVersion : 2
                           \PSFXDeltaFormat : ForwardOnly
Features                 : {}