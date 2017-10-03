---
title: Des Scripts Windows PowerShell | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9848e3ed-8686-4bb8-b8f5-7e3111a83177
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cb314445fe489c50ff5c50364647895219c9907
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-powershell-scripts"></a><span data-ttu-id="ab64a-102">Scripts Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab64a-102">Windows PowerShell Scripts</span></span>
<span data-ttu-id="ab64a-103">Cette rubrique contient des scripts Windows PowerShell qui peuvent être exécutées sur les ordinateurs dans un environnement BizTalk Server pour appliquer des paramètres de Registre décrits dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="ab64a-103">This topic contains Windows PowerShell scripts that can be run on the computers in a BizTalk Server environment to apply registry settings described in this guide.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ab64a-104">Ces scripts ne doivent être exécutés sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], et non sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab64a-104">These scripts should only be run on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], not on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="ab64a-105">Alors que ces scripts sont exécutés avec succès sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], atelier de test a indiqué que ces scripts ne fournissent pas les avantages significative des performances sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab64a-105">While these scripts will execute successfully on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], lab testing has indicated that these scripts do not provide any significant performance advantage on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="ab64a-106">Ces scripts ne doivent être exécutés sur un [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] environnement de production après un test approfondi et d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="ab64a-106">These scripts should only be run on a [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] production environment after thorough testing and evaluation.</span></span>  
  
## <a name="optimizing-operating-system-performance-through-registry-settings"></a><span data-ttu-id="ab64a-107">Optimisation des performances du système d’exploitation via les paramètres de Registre</span><span class="sxs-lookup"><span data-stu-id="ab64a-107">Optimizing operating system performance through registry settings</span></span>  
 <span data-ttu-id="ab64a-108">Le script Windows PowerShell suivant peut être utilisé pour appliquer les paramètres de Registre décrites dans [optimisation des performances de système d’exploitation](../technical-guides/optimizing-operating-system-performance.md).</span><span class="sxs-lookup"><span data-stu-id="ab64a-108">The following Windows PowerShell script can be used to apply the registry settings described in [Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md).</span></span>  
  
 <span data-ttu-id="ab64a-109">Copiez le script ci-dessous dans le bloc-notes et l’enregistrer en tant que jeu-OSRegSettings.ps1.</span><span class="sxs-lookup"><span data-stu-id="ab64a-109">Copy the script below into Notepad and save as Set-OSRegSettings.ps1.</span></span> <span data-ttu-id="ab64a-110">Puis exécutez le script sur chaque ordinateur dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement en suivant les instructions de [optimisation des performances de système d’exploitation](../technical-guides/optimizing-operating-system-performance.md):</span><span class="sxs-lookup"><span data-stu-id="ab64a-110">Then run the script on each computer in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by following the instructions in [Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md):</span></span>  
  
```  
#Set-OSRegSettings.ps1  
param($RAMMb, $NumCPU,$VolType)  
if (($RAMMb -eq $null) -or ($NumCPU -eq $null) -or ($VolType -eq $null) -or ($VolType -gt 4))  
{  
"`r"  
"Please specify required paramemters of -RAMMb and -NumCPU and -VolType"  
"Usage: .\OSSettings.ps1 -RAMMb 2048 -NumCPU 2 -VolType 4"  
"Valid VolType values are: 1(few files), 2 or 3(moderate files), 4(many files)"  
"`r"  
exit  
}  
$ErrorActionPreference = "SilentlyContinue"  
$LogFileName="OSSettings.log"  
$LogTime=([System.DateTime]::Now).ToString("dd-MM-yyyy hh:mm:ss")   
Add-Content $LogFileName "*********** Settings changed at $LogTime ************"  
  
function SetProperty([string]$path, [string]$key, [string]$Value)   
{  
#Clear Error Count  
$error.clear()  
$oldValue = (Get-ItemProperty -path $path).$key  
#Set the Registry Key  
Set-ItemProperty -path $path -name $key -Type DWORD -Value $Value  
#if error count is 0, regkey was updated OK  
if ($error.count -eq 0)  
{  
$newValue = (Get-ItemProperty -path $path).$key  
$data =  "$path\$key=$oldValue"   
if($oldvalue -eq $null)  
{  
Write-Output "Value for $path\$key created and set to $newValue"  
Add-Content $LogFileName "Value for $path\$key created and set to $newValue"  
}  
else  
{  
Write-Output "Value for $path\$key changed from $oldValue to $newValue"  
Add-Content $LogFileName "Value for $path\$key changed from $oldValue to $newValue"  
}  
}  
#if error count is greater than 0 an error occurred and the regkey was not set  
else  
{  
Add-Content $LogFileName "Error: Could not set key $path\$key"  
Add-Content $LogFileName $Error[$error.count-1].exception.message  
Write-Output "Error: Could not set key $path\$key"  
Write-Output $Error[$error.count-1].exception  
}  
}  
  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Services\ldap" "ldapclientintegrity" 0x0  
  
#Work out Value of $IoPageLockLimit  
$IoPageLockLimit = ($RAMMb - 65) * 1024  
if ($IoPageLockLimit -gt 4294967295)  
{  
$IoPageLockLimit = "0xFFFFFFFF"  
}  
else  
{  
#Convert to Hexadecimal  
  
$IoPageLockLimit = "{0:X}" -f $IoPageLockLimit   
$IoPageLockLimit = "0x" + $IoPageLockLimit  
}  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" "IoPageLockLimit" ($IoPageLockLimit)  
  
#Work out Value of $WorkerThreads  
$WorkerThreads = $NumCPU * 16  
if ($WorkerThreads -gt 64)  
{$WorkerThreads = "0x40"} #Hexadecimal Value of 64  
else  
{  
$WorkerThreads = "{0:X}" -f $WorkerThreads  
$WorkerThreads = "0x" + $WorkerThreads  
}  
  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Executive" "AdditionalDelayedWorkerThreads" 0x10  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Executive" "AdditionalCriticalWorkerThreads" 0x10  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" "MaxWorkItems" 8192  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" "MaxMpxCt" 2048  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters" "MaxCmds" 2048  
#Value depends of -VolType parameter passed in  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" "NtfsMftZoneReservation" $VolType  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" "NTFSDisableLastAccessUpdate" 1  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" "NTFSDisable8dot3NameCreation" 1  
SetProperty "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" "DontVerifyRandomDrivers" 1  
SetProperty "HKLM:\System\CurrentControlSet\Services\LanmanServer\Parameters" "Size" 3  
SetProperty "HKLM:\System\CurrentControlSet\Control\Session Manager\Memory Management" "LargeSystemCache" 0          
```  
  
## <a name="optimizing-network-performance-through-registry-settings"></a><span data-ttu-id="ab64a-111">Optimisation des performances réseau via les paramètres de Registre</span><span class="sxs-lookup"><span data-stu-id="ab64a-111">Optimizing network performance through registry settings</span></span>  
 <span data-ttu-id="ab64a-112">Le script Windows PowerShell suivant peut être utilisé pour appliquer les paramètres de Registre décrites dans [optimisation des performances réseau](../technical-guides/optimizing-network-performance.md).</span><span class="sxs-lookup"><span data-stu-id="ab64a-112">The following Windows PowerShell script can be used to apply the registry settings described in [Optimizing Network Performance](../technical-guides/optimizing-network-performance.md).</span></span>  
  
 <span data-ttu-id="ab64a-113">Copiez le script ci-dessous dans le bloc-notes et l’enregistrer en tant que jeu-NetworkRegSettings.ps1.</span><span class="sxs-lookup"><span data-stu-id="ab64a-113">Copy the script below into Notepad and save as Set-NetworkRegSettings.ps1.</span></span> <span data-ttu-id="ab64a-114">Puis exécutez le script sur chaque ordinateur dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement en suivant les instructions de [optimisation des performances réseau](../technical-guides/optimizing-network-performance.md):</span><span class="sxs-lookup"><span data-stu-id="ab64a-114">Then run the script on each computer in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by following the instructions in [Optimizing Network Performance](../technical-guides/optimizing-network-performance.md):</span></span>  
  
```  
#Set-NetworkRegSettings.ps1  
param([int] $MTUSize = $(throw "usage: ./Set-NetworkSettings <MTU Size>"))  
  
$LogFileName="NetworkRegSettings.log"  
$LogTime=([System.DateTime]::Now).ToString("dd-MM-yyyy hh:mm:ss")   
Add-Content $LogFileName "*********** Settings changed at $LogTime ************"  
  
function SetProperty([string]$path, [string]$key, [string]$Value) {  
$oldValue = (Get-ItemProperty -path $path).$key  
Set-ItemProperty -path $path -name $key -Type DWORD -Value $Value  
$newValue = (Get-ItemProperty -path $path).$key  
$data =  "$path\$key=$oldValue"   
Add-Content $LogFileName $data  
Write-Output "Value for $path\$key changed from $oldValue to $newValue"  
}  
SetProperty "HKLM:\System\CurrentControlSet\Control\Session Manager\Memory Management" "DisablePagingExecutive" 1  
# Set SystemPages to 0xFFFFFFFF  
# Maximize system pages. The system creates the largest number of page table entries possible within physical memory.   
# The system monitors and adjusts this value dynamically when the configuration changes.  
SetProperty "HKLM:\System\CurrentControlSet\Control\Session Manager\Memory Management" "SystemPages" 0xFFFFFFFF  
# HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters  
# ======  
$path = "HKLM:\System\CurrentControlSet\Services\LanmanServer\Parameters"  
$returnValue = (Get-ItemProperty -path $path).IRPStackSize  
if ( $returnValue -eq $null) {  
SetProperty $path "IRPStackSize" 0x20 # IRPStackSize -> +10 (Use DWORD 0x20 (32) if not present)  
}else{  
$returnValue = $returnValue + 1  
SetProperty $path "IRPStackSize" $returnValue  
}  
SetProperty $path "SizReqBuf" 0x4000 # SizReqBuf -> 0x4000 (16384)  
  
# HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters  
# =============  
$path = "HKLM:\System\CurrentControlSet\Services\Tcpip\Parameters"  
SetProperty $path "DefaultTTL" 0x40 # DefaultTTL -> 0x40 (64)  
SetProperty $path "EnablePMTUDiscovery" 1 # EnablePMTUDiscovery -> 1 (do not enable this if your server is directly exposed to potential attackers)  
SetProperty $path "EnablePMTUBHDetect" 1 # EnablePMTUBHDetect -> 1 (if your system is using a SOAP or HTTP and/or initiating web connections to other systems)  
SetProperty $path "TcpMaxDupAcks" 2 # TcpMaxDupAcks -> 2  
SetProperty $path "Tcp1323Opts" 1 # Tcp1323Opts -> 1 (experiment with a value of 3 for possible improved performance, especially if you are experiencing high packet loss/retransmits)  
SetProperty $path "SackOpts" 1 # SackOpts -> 1 (VERY important for large TCP window sizes, such as specified below)  
SetProperty $path "MaxFreeTcbs" 0x5000 # MaxFreeTcbs -> 0x5000 (20480)  
SetProperty $path "TcpMaxSendFree" 0xFFFF # TcpMaxSendFree -> 0xFFFF (65535)  
SetProperty $path "MaxHashTableSize" 0xFFFF # MaxHashTableSize -> 0xFFFF (65535)  
SetProperty $path "MaxUserPort" 0xFFFF # MaxUserPort -> 0xFFFF (65535)  
SetProperty $path "TcpTimedWaitDelay" 0x1E # TcpTimedWaitDelay -> 0x1E (30)  
SetProperty $path "GlobalMaxTcpWindowSize" 0xFFFF # GlobalMaxTcpWindowSize -> 0xFFFF (65535)  
SetProperty $path "NumTCPTablePartitions" 4 # NumTCPTablePartitions -> 2 per Processor/Core (include processor cores BUT NOT hyperthreading)  
# TcpAckFrequency (requires Windows Server 2K3 Hotfix 815230)  
# SetProperty $path "TcpAckFrequency" 5 #5 for 100Mb, 13 for 1Gb (requires Windows Server 2K3 Hotfix 815230) - can also be set at the interface level if mixed speeds; only set for connections primarily processing data  
SetProperty $path "SynAttackProtect" 0 # SynAttackProtect -> 0 (Only set this on systems with web exposure if other H/W or S/W is providing DOS attack protection)  
#Dedicated Network (DATA)  
#------------------------  
#Interfaces\<adapter ID>\MTU -> 1450-1500, test for maximum value that will pass on each interface using PING -f -l <MTU Size> <Interface Gateway Address>, pick the value that works across all interfaces  
$RegistryEntries = Get-ItemProperty -path "HKLM:\system\currentcontrolset\services\tcpip\parameters\interfaces\*"  
foreach ( $iface in $RegistryEntries ) {   
$ip = $iface.DhcpIpAddress  
if ( $ip -ne $null ) { $childName = $iface.PSChildName}  
else {  
$ip = $iface.IPAddress  
if ($ip -ne $null) { $childName = $iface.PSChildName }  
}  
$Interface = Get-ItemProperty -path "HKLM:\system\currentcontrolset\services\tcpip\parameters\interfaces\$childName"  
$path = $Interface.PSPath  
SetProperty $path MTU $MTUSize  
}  
$path = "HKLM:\System\CurrentControlSet\Services\Tcpip\Parameters"  
$ForwardBufferMemory = 100*$MTUSize  
SetProperty $path "ForwardBufferMemory" $ForwardBufferMemory # ForwardBufferMemory -> 100*MTUSize, rounded up to the nearest 256 byte boundary  
SetProperty $path "MaxForwardBufferMemory" $ForwardBufferMemory # MaxForwardBufferMemory -> ForwardBufferMemory  
$NumForwardPackets = $ForwardBufferMemory/256  
SetProperty $path "NumForwardPackets" $NumForwardPackets # NumForwardPackets -> ForwardBufferMemory / 256  
SetProperty $path "MaxNumForwardPackets" $NumForwardPackets # MaxNumForwardPackets -> NumForwardPackets  
SetProperty $path "TcpWindowSize" 0xFBA4 # TcpWindowSize -> 0xFBA4 (64420) (make this a multiple of the TCP MSS (Max Segment Size)  
# HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AFD\Parameters  
# ===========  
$path = "HKLM:\SYSTEM\CurrentControlSet\Services\AFD\Parameters"  
SetProperty $path "EnableDynamicBacklog" 1 # EnableDynamicBacklog -> 1  
SetProperty $path "MinimumDynamicBacklog" 0xc8 # MinimumDynamicBacklog -> 0xc8 (200)  
SetProperty $path "MaximumDynamicBacklog" 0x4e20 # MaximumDynamicBacklog -> 0x4e20 (20000)  
SetProperty $path "DynamicBacklogGrowthDelta" 0x64 # DynamicBacklogGrowthDelta -> 0x64 (100)  
#S/W Configuration  
#=============  
#Disable NETBIOS on cluster private network, if configured  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab64a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab64a-115">See Also</span></span>  
 [<span data-ttu-id="ab64a-116">Optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="ab64a-116">Optimizing Performance</span></span>](../technical-guides/optimizing-performance.md)