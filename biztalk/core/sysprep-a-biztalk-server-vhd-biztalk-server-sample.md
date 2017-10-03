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
ms.openlocfilehash: 3da0d65917598dbbce4e203a97a9e843b5ba70c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sysprep-a-biztalk-server-vhd-biztalk-server-sample"></a>Création d'un disque dur virtuel (VHD) BizTalk Server à l'aide de Sysprep (exemple BizTalk Server)
Sysprep crée une capture instantanée d'un ordinateur virtuel sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé pour permettre un déploiement rapide sur d'autres ordinateurs virtuels.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d'utiliser Sysprep, vous devez maîtriser l'utilisation des ordinateurs virtuels avec Hyper-V. Vous devez également disposer d'un ordinateur virtuel sur lequel BizTalk Server et tous ses composants requis sont installés correctement et par défaut.  
  
 Sysprep est exécuté sous Windows Server 2008 et Windows Vista avec SP1.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Sysprep crée un disque dur virtuel (VHD) d'une installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (système d'exploitation et composants requis inclus) pour un déploiement rapide sur d'autres ordinateurs virtuels. Une image créée à l'aide de Sysprep choisit un nouveau nom d'ordinateur afin de joindre le domaine lors de son premier démarrage. L'exécution correcte de BizTalk Server requiert la mise à jour des diverses instances du nom d'ordinateur stockées dans le Registre et les bases de données.  
  
 Ce document, basé sur l'hypothèse que BizTalk Server est configuré pour être exécuté sur un ordinateur unique, montre comment mettre à jour les autres instances du nom d'ordinateur avec le nouveau nom.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\Sysprep\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
> [!NOTE]
>  Les fichiers .vbs et .cmd du tableau ci-après sont tous automatisés dans les fichiers de réponses Sysprep (Sysprep.xml et SetupCompletecmd.txt) et sont répertoriés ici pour référence uniquement. Si vous devez exécuter ces scripts manuellement, faites-le dans leur ordre d'apparition dans le tableau.  
  
|Fichier| Description|  
|----------|-----------------|  
|Sysprep.xml|Fichier de réponses|  
|SetupCompletecmd.txt|Fichier de réponses|  
|ReplaceMachineName.vbs|Objectif : Ouvre un fichier et remplace toutes les instances d’une chaîne donnée avec le nom de l’ordinateur actuel. Utile pour préparer les autres fichiers de script et xml et pour mettre à jour le fichier bm.exe.config.<br /><br /> Utilisation : ReplaceMachineName.vbs \<fichier à ouvrir > \<chaîne à remplacer >|  
|UpdateRegistry.vbs|Objectif : Met à jour le nom d’ordinateur stocké dans les paramètres du Registre BizTalk.<br /><br /> Utilisation : UpdateRegistry.vbs \<UpdateInfo.xml >. Veillez à remplacer toutes les instances de $(OLDCOMPUTERNAME) et $(NEWCOMPUTERNAME) dans ce fichier xml.|  
|UpdateDatabase.vbs|Objectif : Met à jour le nom d’ordinateur stocké dans les bases de données de gestion BizTalk.<br /><br /> Utilisation : UpdateDatabase.vbs \<UpdateInfo.xml >|  
|UpdateBAMDb.vbs|Objectif : Met à jour le nom d’ordinateur stocké dans les bases de données BAM.<br /><br /> Utilisation : UpdateBamDb.vbs \<UpdateInfo.xml >|  
|UpdateSSO.cmd|Objectif : Reconfigure le serveur de secret Enterprise Single Sign-on (SSO).<br /><br /> Utilisation : sso.cmd \<UpdateInfo.xml >|  
|UpdateSqlServerAndInstanceName.cmd|Objectif : Reconfigure SQL et SQL Express, redémarre une série de services dépendants et réinscrit BAMAlerts.<br /><br /> Utilisation : Modifier le script et remplacez toutes les instances de $(NEWCOMPUTERNAME) et mettre à jour serviceusername et servicepassword pour les alertes BAM. Exécutez ensuite UpdateSqlServerAndInstanceName.cmd en transmettant l'ancien nom d'ordinateur comme premier argument.|  
  
## <a name="creating-the-answer-files-and-running-sysprep"></a>Création des fichiers de réponses et exécution de Sysprep  
  
#### <a name="to-create-the-answer-files"></a>Pour créer les fichiers de réponses  
  
1.  Installez et configurez [!INCLUDE[prague](../includes/prague-md.md)] sur un ordinateur virtuel. Veillez à utiliser les options d'installation et de configuration par défaut car Sysprep ne prend pas en charge l'installation personnalisée.  
  
2.  Copiez le contenu du dossier « scripts » inclus dans C:\Scripts sur l'ordinateur virtuel.  
  
3.  Préparez un fichier de réponses sysprep en modifiant les lignes suivantes dans Sysprep.xml. (Remarque : ces lignes sont marquées avec un « ! » avant de les). Vous pouvez utiliser comme modèle, ou créer vos propres et recopiez les \<FirstLogonCommands > section.  
  
    -   $(OLDCOMPUTERNAME) Remplacez par le nom d'ordinateur actuel de l'ordinateur virtuel.  
  
    -   Comptes d'utilisateur  
  
    -   Mots de passe  
  
    -   Les informations relatives à la société doivent également être mises à jour dans UpdateSqlServerAndInstance.cmd et votre fichier Sysprep.xml.  
  
     Vous pouvez également créer un fichier de réponses Sysprep à l’aide d’utiliser le [Kit d’Installation automatisée (AIK)](http://www.microsoft.com/downloads/details.aspx?FamilyID=94bb6e34-d890-4932-81a5-5b50c657de08&DisplayLang=en) sur Windows Server 2008. Vérifiez que votre \<FirstLogonCommands > section corresponde aux exemples afin que les scripts BizTalk soient exécutés au premier démarrage.  
  
#### <a name="to-run-sysprep"></a>Pour exécuter Sysprep  
  
1.  Ouvrez une invite de commandes et exécutez Sysprep. La commande ressemble à ce qui suit :  
  
    ```  
    C:\windows\system32\sysprep\sysprep.exe /oobe /generalize /shutdown /unattend:c:\scripts\unattend_Win2K8x64.xml  
    ```  
  
2.  L'exécution de Sysprep prend environ une demi-heure. L'ordinateur virtuel s'arrête automatiquement une fois l'exécution terminée.  
  
3.  Fusionnez alors les captures instantanées et copiez votre fichier VHD dans un emplacement sécurisé.  
  
4.  Votre disque dur virtuel (VHD) est maintenant prêt à être déployé complètement sur d'autres ordinateurs virtuels, avec le système d'exploitation, BizTalk Server et tous les composants requis.  
  
 **SetupCompletecmd.txt**  
  
```  
del /Q /F c:\windows\system32\sysprep\sysprep.xml  
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
```  
  
 **Sysprep.Xml**  
  
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
  
## <a name="comments"></a>Commentaires  
 Ces scripts ne modifient pas Microsoft Office SharePoint Server. Si vous utilisez l'adaptateur Windows SharePoint Services, vous devrez probablement reconfigurer Microsoft Office SharePoint Server, puis mettre à jour la clé SharePointAdapterManagementGroup sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\TPM.