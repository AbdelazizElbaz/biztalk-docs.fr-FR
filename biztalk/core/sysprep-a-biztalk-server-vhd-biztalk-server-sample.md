---
title: Sysprep un disque dur virtuel (exemple BizTalk Server) de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35f0146d-60ed-4265-983a-0e3665ef2ae4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc6ec29ece503f324758cdc08a6ff1351c066af4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="sysprep-a-biztalk-server-vhd-biztalk-server-sample"></a><span data-ttu-id="9363d-102">Création d'un disque dur virtuel (VHD) BizTalk Server à l'aide de Sysprep (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="9363d-102">Sysprep a BizTalk Server VHD (BizTalk Server Sample)</span></span>
<span data-ttu-id="9363d-103">Sysprep crée une capture instantanée d'un ordinateur virtuel sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé pour permettre un déploiement rapide sur d'autres ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="9363d-103">Sysprep creates a snapshot of a virtual machine with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed for quick deployment on other virtual machines.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9363d-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9363d-104">Prerequisites</span></span>  
 <span data-ttu-id="9363d-105">Avant d'utiliser Sysprep, vous devez maîtriser l'utilisation des ordinateurs virtuels avec Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="9363d-105">Before using Sysprep, you should have some knowledge of using virtual machines with Hyper-V.</span></span> <span data-ttu-id="9363d-106">Vous devez également disposer d'un ordinateur virtuel sur lequel BizTalk Server et tous ses composants requis sont installés correctement et par défaut.</span><span class="sxs-lookup"><span data-stu-id="9363d-106">You should also have a virtual machine with a clean, typical installation of BizTalk Server and all of its prerequisites.</span></span>  
  
 <span data-ttu-id="9363d-107">Sysprep est exécuté sous Windows Server 2008 et Windows Vista avec SP1.</span><span class="sxs-lookup"><span data-stu-id="9363d-107">Sysprep will run on Windows Server 2008 and Windows Vista with SP1.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="9363d-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="9363d-108">What This Sample Does</span></span>  
 <span data-ttu-id="9363d-109">Sysprep crée un disque dur virtuel (VHD) d'une installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (système d'exploitation et composants requis inclus) pour un déploiement rapide sur d'autres ordinateurs virtuels.</span><span class="sxs-lookup"><span data-stu-id="9363d-109">Sysprep creates a VHD of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation (including the operating system and all prerequisites) for quick deployment on other virtual machines.</span></span> <span data-ttu-id="9363d-110">Une image créée à l'aide de Sysprep choisit un nouveau nom d'ordinateur afin de joindre le domaine lors de son premier démarrage.</span><span class="sxs-lookup"><span data-stu-id="9363d-110">An image created using Sysprep will choose a new computer name in order to join the domain the first time it starts.</span></span> <span data-ttu-id="9363d-111">L'exécution correcte de BizTalk Server requiert la mise à jour des diverses instances du nom d'ordinateur stockées dans le Registre et les bases de données.</span><span class="sxs-lookup"><span data-stu-id="9363d-111">To get BizTalk Server running properly, it is necessary to update various instances of the computer name that are stored in the registry and databases.</span></span>  
  
 <span data-ttu-id="9363d-112">Ce document, basé sur l'hypothèse que BizTalk Server est configuré pour être exécuté sur un ordinateur unique, montre comment mettre à jour les autres instances du nom d'ordinateur avec le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="9363d-112">This document assumes that BizTalk Server is configured to run on a single computer, and shows how to update other instances of the computer name with the new name.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="9363d-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="9363d-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="9363d-114">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="9363d-114">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="9363d-115">\<*Exemples de chemin d’accès*\>\Admin\Sysprep\\</span><span class="sxs-lookup"><span data-stu-id="9363d-115">\<*Samples Path*\>\Admin\Sysprep\\</span></span>  
  
 <span data-ttu-id="9363d-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="9363d-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9363d-117">Les fichiers .vbs et .cmd du tableau ci-après sont tous automatisés dans les fichiers de réponses Sysprep (Sysprep.xml et SetupCompletecmd.txt) et sont répertoriés ici pour référence uniquement.</span><span class="sxs-lookup"><span data-stu-id="9363d-117">The .vbs and .cmd files in the table below are all automated in the Sysprep answer files (Sysprep.xml and SetupCompletecmd.txt), and are listed here for reference only.</span></span> <span data-ttu-id="9363d-118">Si vous devez exécuter ces scripts manuellement, faites-le dans leur ordre d'apparition dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="9363d-118">If you do need to run these scripts manually, run them in the order that they appear in the table.</span></span>  
  
|<span data-ttu-id="9363d-119">Fichier</span><span class="sxs-lookup"><span data-stu-id="9363d-119">File</span></span>|<span data-ttu-id="9363d-120"> Description</span><span class="sxs-lookup"><span data-stu-id="9363d-120">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9363d-121">Sysprep.xml</span><span class="sxs-lookup"><span data-stu-id="9363d-121">Sysprep.xml</span></span>|<span data-ttu-id="9363d-122">Fichier de réponses</span><span class="sxs-lookup"><span data-stu-id="9363d-122">Answer file</span></span>|  
|<span data-ttu-id="9363d-123">SetupCompletecmd.txt</span><span class="sxs-lookup"><span data-stu-id="9363d-123">SetupCompletecmd.txt</span></span>|<span data-ttu-id="9363d-124">Fichier de réponses</span><span class="sxs-lookup"><span data-stu-id="9363d-124">Answer file</span></span>|  
|<span data-ttu-id="9363d-125">ReplaceMachineName.vbs</span><span class="sxs-lookup"><span data-stu-id="9363d-125">ReplaceMachineName.vbs</span></span>|<span data-ttu-id="9363d-126">Objectif : Ouvre un fichier et remplace toutes les instances d’une chaîne donnée avec le nom de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9363d-126">Purpose: Opens a file and replaces all instances of a given string with the current computer name.</span></span> <span data-ttu-id="9363d-127">Utile pour préparer les autres fichiers de script et xml et pour mettre à jour le fichier bm.exe.config.</span><span class="sxs-lookup"><span data-stu-id="9363d-127">Useful to prepare the other script and xml files, and to update bm.exe.config.</span></span><br /><br /> <span data-ttu-id="9363d-128">Utilisation : ReplaceMachineName.vbs \<fichier à ouvrir\> \<chaîne à remplacer\></span><span class="sxs-lookup"><span data-stu-id="9363d-128">Usage: ReplaceMachineName.vbs \<file to open\> \<string to replace\></span></span>|  
|<span data-ttu-id="9363d-129">UpdateRegistry.vbs</span><span class="sxs-lookup"><span data-stu-id="9363d-129">UpdateRegistry.vbs</span></span>|<span data-ttu-id="9363d-130">Objectif : Met à jour le nom d’ordinateur stocké dans les paramètres du Registre BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9363d-130">Purpose: Updates the computer name stored in the BizTalk registry settings.</span></span><br /><br /> <span data-ttu-id="9363d-131">Utilisation : UpdateRegistry.vbs \<UpdateInfo.xml\>.</span><span class="sxs-lookup"><span data-stu-id="9363d-131">Usage: UpdateRegistry.vbs \<UpdateInfo.xml\>.</span></span> <span data-ttu-id="9363d-132">Veillez à remplacer toutes les instances de $(OLDCOMPUTERNAME) et $(NEWCOMPUTERNAME) dans ce fichier xml.</span><span class="sxs-lookup"><span data-stu-id="9363d-132">Make sure to replace all instances of $(OLDCOMPUTERNAME) and $(NEWCOMPUTERNAME) in this xml file.</span></span>|  
|<span data-ttu-id="9363d-133">UpdateDatabase.vbs</span><span class="sxs-lookup"><span data-stu-id="9363d-133">UpdateDatabase.vbs</span></span>|<span data-ttu-id="9363d-134">Objectif : Met à jour le nom d’ordinateur stocké dans les bases de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9363d-134">Purpose: Updates the computer name stored in the BizTalk Management databases.</span></span><br /><br /> <span data-ttu-id="9363d-135">Utilisation : UpdateDatabase.vbs \<UpdateInfo.xml\></span><span class="sxs-lookup"><span data-stu-id="9363d-135">Usage: UpdateDatabase.vbs \<UpdateInfo.xml\></span></span>|  
|<span data-ttu-id="9363d-136">UpdateBAMDb.vbs</span><span class="sxs-lookup"><span data-stu-id="9363d-136">UpdateBAMDb.vbs</span></span>|<span data-ttu-id="9363d-137">Objectif : Met à jour le nom d’ordinateur stocké dans les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="9363d-137">Purpose: Updates the computer name stored in the BAM databases.</span></span><br /><br /> <span data-ttu-id="9363d-138">Utilisation : UpdateBamDb.vbs \<UpdateInfo.xml\></span><span class="sxs-lookup"><span data-stu-id="9363d-138">Usage: UpdateBamDb.vbs \<UpdateInfo.xml\></span></span>|  
|<span data-ttu-id="9363d-139">UpdateSSO.cmd</span><span class="sxs-lookup"><span data-stu-id="9363d-139">UpdateSSO.cmd</span></span>|<span data-ttu-id="9363d-140">Objectif : Reconfigure le serveur de secret Enterprise Single Sign-on (SSO).</span><span class="sxs-lookup"><span data-stu-id="9363d-140">Purpose: Reconfigures the Enterprise Single Sign-on (SSO) secret server.</span></span><br /><br /> <span data-ttu-id="9363d-141">Utilisation : sso.cmd \<UpdateInfo.xml\></span><span class="sxs-lookup"><span data-stu-id="9363d-141">Usage: sso.cmd \<UpdateInfo.xml\></span></span>|  
|<span data-ttu-id="9363d-142">UpdateSqlServerAndInstanceName.cmd</span><span class="sxs-lookup"><span data-stu-id="9363d-142">UpdateSqlServerAndInstanceName.cmd</span></span>|<span data-ttu-id="9363d-143">Objectif : Reconfigure SQL et SQL Express, redémarre une série de services dépendants et réinscrit BAMAlerts.</span><span class="sxs-lookup"><span data-stu-id="9363d-143">Purpose: Reconfigures SQL and SQL Express, restarts a series of dependent services, and reregisters BAMAlerts.</span></span><br /><br /> <span data-ttu-id="9363d-144">Utilisation : Modifier le script et remplacez toutes les instances de $(NEWCOMPUTERNAME) et mettre à jour serviceusername et servicepassword pour les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="9363d-144">Usage: Edit the script and replace all instances of $(NEWCOMPUTERNAME), and update the serviceusername and servicepassword for BAM Alerts.</span></span> <span data-ttu-id="9363d-145">Exécutez ensuite UpdateSqlServerAndInstanceName.cmd en transmettant l'ancien nom d'ordinateur comme premier argument.</span><span class="sxs-lookup"><span data-stu-id="9363d-145">Then run UpdateSqlServerAndInstanceName.cmd passing the old computer name as the first argument.</span></span>|  
  
## <a name="creating-the-answer-files-and-running-sysprep"></a><span data-ttu-id="9363d-146">Création des fichiers de réponses et exécution de Sysprep</span><span class="sxs-lookup"><span data-stu-id="9363d-146">Creating the Answer Files and Running Sysprep</span></span>  
  
#### <a name="to-create-the-answer-files"></a><span data-ttu-id="9363d-147">Pour créer les fichiers de réponses</span><span class="sxs-lookup"><span data-stu-id="9363d-147">To create the answer files</span></span>  
  
1.  <span data-ttu-id="9363d-148">Installez et configurez BizTalk Server sur un ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="9363d-148">Install and configure BizTalk Server on a virtual machine.</span></span> <span data-ttu-id="9363d-149">Veillez à utiliser les options d'installation et de configuration par défaut car Sysprep ne prend pas en charge l'installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9363d-149">Be sure to use default installation and configuration options, since Sysprep does not support customized installation.</span></span>  
  
2.  <span data-ttu-id="9363d-150">Copiez le contenu du dossier « scripts » inclus dans C:\Scripts sur l'ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="9363d-150">Copy the contents of the included “scripts” folder to C:\Scripts on the virtual machine.</span></span>  
  
3.  <span data-ttu-id="9363d-151">Préparez un fichier de réponses sysprep en modifiant les lignes suivantes dans Sysprep.xml.</span><span class="sxs-lookup"><span data-stu-id="9363d-151">Prepare a sysprep answer file by modifying the following lines in Sysprep.xml.</span></span> <span data-ttu-id="9363d-152">(Remarque : ces lignes sont marquées avec un « ! »</span><span class="sxs-lookup"><span data-stu-id="9363d-152">(Note: These lines are marked with a “!”</span></span> <span data-ttu-id="9363d-153">avant de les). Vous pouvez utiliser comme modèle, ou créer vos propres et recopiez les \<FirstLogonCommands\> section.</span><span class="sxs-lookup"><span data-stu-id="9363d-153">before them.) You can use these as a template, or make your own and copy over the \<FirstLogonCommands\> section.</span></span>  
  
    -   <span data-ttu-id="9363d-154">$(OLDCOMPUTERNAME) Remplacez par le nom d'ordinateur actuel de l'ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="9363d-154">$(OLDCOMPUTERNAME) Replace with the current computer name of the virtual machine.</span></span>  
  
    -   <span data-ttu-id="9363d-155">Comptes d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9363d-155">User accounts</span></span>  
  
    -   <span data-ttu-id="9363d-156">Mots de passe</span><span class="sxs-lookup"><span data-stu-id="9363d-156">Passwords</span></span>  
  
    -   <span data-ttu-id="9363d-157">Les informations relatives à la société doivent également être mises à jour dans UpdateSqlServerAndInstance.cmd et votre fichier Sysprep.xml.</span><span class="sxs-lookup"><span data-stu-id="9363d-157">Any company details should also be updated in UpdateSqlServerAndInstance.cmd and your Sysprep.xml.</span></span>  
  
     <span data-ttu-id="9363d-158">Vous pouvez également créer un fichier de réponses Sysprep à l’aide d’utiliser le [Kit d’Installation automatisée (AIK)](http://www.microsoft.com/downloads/details.aspx?FamilyID=94bb6e34-d890-4932-81a5-5b50c657de08&DisplayLang=en) sur Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9363d-158">Alternatively, you can create a Sysprep answer file from scratch using use the [Automated Installation Kit (AIK)](http://www.microsoft.com/downloads/details.aspx?FamilyID=94bb6e34-d890-4932-81a5-5b50c657de08&DisplayLang=en) on Windows Server 2008.</span></span> <span data-ttu-id="9363d-159">Vérifiez que votre \<FirstLogonCommands\> section corresponde aux exemples afin que les scripts BizTalk soient exécutés au premier démarrage.</span><span class="sxs-lookup"><span data-stu-id="9363d-159">Ensure that your \<FirstLogonCommands\> section matches the samples so the BizTalk scripts will run on the first boot.</span></span>  
  
#### <a name="to-run-sysprep"></a><span data-ttu-id="9363d-160">Pour exécuter Sysprep</span><span class="sxs-lookup"><span data-stu-id="9363d-160">To run Sysprep</span></span>  
  
1.  <span data-ttu-id="9363d-161">Ouvrez une invite de commandes et exécutez Sysprep.</span><span class="sxs-lookup"><span data-stu-id="9363d-161">Open a command prompt and run Sysprep.</span></span> <span data-ttu-id="9363d-162">La commande ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9363d-162">The command will look something like:</span></span>  
  
    ```  
    C:\windows\system32\sysprep\sysprep.exe /oobe /generalize /shutdown /unattend:c:\scripts\unattend_Win2K8x64.xml  
    ```  
  
2.  <span data-ttu-id="9363d-163">L'exécution de Sysprep prend environ une demi-heure.</span><span class="sxs-lookup"><span data-stu-id="9363d-163">Sysprep takes about half an hour to run.</span></span> <span data-ttu-id="9363d-164">L'ordinateur virtuel s'arrête automatiquement une fois l'exécution terminée.</span><span class="sxs-lookup"><span data-stu-id="9363d-164">When it is complete, it will automatically shut down the virtual machine.</span></span>  
  
3.  <span data-ttu-id="9363d-165">Fusionnez alors les captures instantanées et copiez votre fichier VHD dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="9363d-165">After the virtual machine has been shut down, merge any snapshots, and copy your VHD file to a safe location.</span></span>  
  
4.  <span data-ttu-id="9363d-166">Votre disque dur virtuel (VHD) est maintenant prêt à être déployé complètement sur d'autres ordinateurs virtuels, avec le système d'exploitation, BizTalk Server et tous les composants requis.</span><span class="sxs-lookup"><span data-stu-id="9363d-166">Your VHD is now ready to be deployed on other virtual machines, complete with operating system, BizTalk Server, and all prerequisites.</span></span>  
  
 <span data-ttu-id="9363d-167">**SetupCompletecmd.txt**</span><span class="sxs-lookup"><span data-stu-id="9363d-167">**SetupCompletecmd.txt**</span></span>  
  
```  
del /Q /F c:\windows\system32\sysprep\sysprep.xml  
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
```  
  
 <span data-ttu-id="9363d-168">**Sysprep.Xml**</span><span class="sxs-lookup"><span data-stu-id="9363d-168">**Sysprep.xml**</span></span>  
  
```  
- <!--   
References:  
"Unattended Installation Settings Reference" @ http://technet.microsoft.com/library/cc749204.aspx  
"How to Sysprep in Windows 2008 " @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008  
  
Make sure to modify the values specified for the   
<Credentials> and <DomainAccounts> sections of this unattend file.  
  
SetupComplete.cmd should be copied to the C:\Windows\Setup\Scripts\ folder before running sysprep.  
Contents of SetupComplete.cmd:  
  
del /Q /F c:\windows\system32\sysprep\sysprep.xml   
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
Sysprep.xml (this file) should be copied to the C:\Windows\System32\sysprep\ folder.  
  
Run sysprep with the following options:  
  
sysprep /generalize /oobe /shutdown /unattend:sysprep.xml  
  -->   
  <?xml version="1.0" encoding="utf-8" ?>   
- <unattend xmlns="urn:schemas-microsoft-com:unattend">  
- <settings pass="oobeSystem">  
- <component name="Microsoft-Windows-International-Core" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <InputLocale>0409:00000409</InputLocale>   
  <SystemLocale>en-US</SystemLocale>   
  <UILanguage>en-US</UILanguage>   
  <UILanguageFallback>en-US</UILanguageFallback>   
  <UserLocale>en-US</UserLocale>   
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <UserAccounts>  
- <!--   
This sets the password for the Administrator account back to pass@word1   
  -->   
- <AdministratorPassword>  
  <Value>pass@word1</Value>   
  <PlainText>true</PlainText>   
  </AdministratorPassword>  
- <!--   
Enter the appropriate value for the <Name> and <Domain> elements here,   
this group/account will be added to the local Administrators and Remote Desktop Users groups.  
  -->   
- <DomainAccounts>  
- <DomainAccountList wcm:action="add">  
- <DomainAccount wcm:action="add">  
  <Name>MSMQ4TR</Name>   
  <Group>Administrators;RemoteDesktopUsers</Group>   
  </DomainAccount>  
  <Domain>Northamerica.corp.microsoft.com</Domain>   
  </DomainAccountList>  
- <!--   
Additional DomainAccountList section. Uncomment/modify this section if you need to add   
groups / users from multiple domains to the local Administrators and Remote Desktop Users groups.  
                    <DomainAccountList wcm:action="add">  
                        <DomainAccount wcm:action="add">  
                            <Name>OsloVM_NTDev</Name>  
                            <Group>Administrators;RemoteDesktopUsers</Group>  
                        </DomainAccount>  
                        <Domain>Ntdev.corp.microsoft.com</Domain>  
                    </DomainAccountList>  
  -->   
  </DomainAccounts>  
  </UserAccounts>  
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.  
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <TimeZone>Pacific Standard Time</TimeZone>   
- <Display>  
  <ColorDepth>16</ColorDepth>   
  <HorizontalResolution>1024</HorizontalResolution>   
  <VerticalResolution>768</VerticalResolution>   
  </Display>  
  <RegisteredOrganization />   
  <StartPanelOff>true</StartPanelOff>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <VisualEffects>  
  <FontSmoothing>ClearType</FontSmoothing>   
  </VisualEffects>  
  </component>  
  </settings>  
- <settings pass="specialize">  
- <component name="Microsoft-Windows-IE-ESC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <IEHardenAdmin>false</IEHardenAdmin>   
  <IEHardenUser>false</IEHardenUser>   
  </component>  
- <component name="Microsoft-Windows-UnattendedJoin" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
Enter credentials for a user account that has permissions to join a computer to the domain specified in the <JoinDomain> element. (Note: you must enter your password in plaintext here. This file will be deleted at the conclusion of Windows setup by SetupComplete.cmd in the C:\Windows\Setup\Scripts\ folder. For more information see the bottom of "How to Sysprep in Windows 2008" @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008)  
  -->   
- <Identification>  
- <Credentials>  
  <Domain>northamerica</Domain>   
  <Username>davidhamilton</Username>   
  <Password>******</Password>   
  </Credentials>  
  <JoinDomain>Redmond.corp.microsoft.com</JoinDomain>   
  </Identification>  
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
By specifying a value of "*" for <ComputerName>, Windows setup will generate a new computer name using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******  
  -->   
  <ComputerName>*</ComputerName>   
  <RegisteredOrganization />   
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.   
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <!--   
This setting will copy the profile of the original image to the renamed image when set to true   
  -->   
  <CopyProfile>true</CopyProfile>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  </component>  
  </settings>  
- <settings pass="generalize">  
- <component name="Microsoft-Windows-Security-Licensing-SLC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <SkipRearm>1</SkipRearm>   
  </component>  
- <component name="Microsoft-Windows-OutOfBoxExperience" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenInitialConfigurationTasksAtLogon>true</DoNotOpenInitialConfigurationTasksAtLogon>   
  </component>  
- <component name="Microsoft-Windows-ServerManager-SvrMgrNc" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenServerManagerAtLogon>true</DoNotOpenServerManagerAtLogon>   
  </component>  
  </settings>  
  <cpi:offlineImage cpi:source="catalog:e:/sources/install_windows longhorn serverenterprise.clg" xmlns:cpi="urn:schemas-microsoft-com:cpi" />   
  </unattend>  
- <!--   
When the virtual machine is started, Windows setup will:  
  
 - Assign the copy a random computer name: "OsloVPC-*****"  
 - Reset the local Administrators password to pass@word1  
 - Join the domain specified in the sysprep.xml file (under Microsoft-Windows-UnattendedJoin\Identification\JoinDomain)  
 - Add the groups/users specified under <DomainAccounts> to the local Administrators and the local Remote Desktop Users group.  
  
Known issues:  
  
 - Sysprep removes the Server Manager icon from the Quick Launch toolbar, investigating how to prevent this.  
 - To start SQL Server Management Studio, either connect to the new server name (OsloVPC-*******) or else connect to ".".  The "Server name:" drop-down box in SQL Server Management Studio is pre-populated with "PDC08-CSD" which will not work since the computer name has been changed by sysprep.  
 - There are some known issues associated with changing the computer name; renaming the computer after everything was installed was not a design, development or test requirement for this milestone.  
  -->  
```  
  
## <a name="comments"></a><span data-ttu-id="9363d-169">Commentaires</span><span class="sxs-lookup"><span data-stu-id="9363d-169">Comments</span></span>  
 <span data-ttu-id="9363d-170">Ces scripts ne modifient pas Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="9363d-170">These scripts do not modify Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="9363d-171">Si vous utilisez l'adaptateur Windows SharePoint Services, vous devrez probablement reconfigurer Microsoft Office SharePoint Server, puis mettre à jour la clé SharePointAdapterManagementGroup sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\TPM.</span><span class="sxs-lookup"><span data-stu-id="9363d-171">If you are using the Windows SharePoint Services adapter, you will probably need to reconfigure Microsoft Office SharePoint Server and then update the SharePointAdapterManagementGroup key under HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\TPM.</span></span>