---
title: Résoudre les problèmes et les problèmes connus avec l’accélérateur BizTalk du RosettaNet (BTARN) installé sur BizTalk Server | Documents Microsoft »
description: Recommandations pour l’installation de SQL, le compte de service pour les instances d’hôte et les erreurs connues avec l’installation de BTARN dans BizTalk Server
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdca89c1a7a4ed3834103776f9f28c8631c5de0a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-the-installation-and-see-the-known-install-issues"></a>Résoudre les problèmes de l’installation et de voir les problèmes d’installation connus

  
## <a name="do-not-install-sql-server-on-the-domain-controller-computer"></a>N'installez pas SQL Server sur l'ordinateur du contrôleur de domaine  
 Si vous installez SQL Server sur le même ordinateur que votre ordinateur de contrôleur de domaine, il retourne le message d’erreur suivant quand il tente de créer les ports d’envoi SQL :  
  
```
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500.  
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500  

```
  
> [!IMPORTANT]
>  N’installez pas SQL Server sur l’ordinateur de contrôleur de domaine.  
  
## <a name="service-account-for-the-application-pools-must-be-the-same-as-the-service-account-for-the-isolated-host-and-host-instances"></a>Le compte de service pour les pools d'applications doit être le même que le compte de service pour les instances de l'hôte et de l'hôte isolé  
 Si le compte de service défini pour les pools d’applications BTARN est différent du compte de l’hôte isolé, BTARN ne traite pas correctement les messages entrants. Lorsque la page .aspx de réception appelle le pipeline, le pipeline n’a pas accès aux certificats appropriés. Par conséquent, il ne déchiffrer le message entrant ni valider la signature. En outre, il ne pourrez pas accéder à la base de données MessageBox.  
  

## <a name="known-install-issues"></a>Problèmes d’installation connus

  
### <a name="btarn-http-front-end-feature-configuration-fails"></a>Échec de la configuration de la fonctionnalité de fin avant de BTARN HTTP  
 **Problème**  
  
 Si vous effectuez une installation personnalisée pour installer uniquement la fonction frontale HTTP BTARN, la configuration BTARN peut échouer une fois l'installation terminée en affichant le message suivant : 

`Failed to create object for feature: WebApp`  
  
 **Résolution**  
  
Copier les fichiers et reconfigurer manuellement : 
  
1.  Copiez les deux fichiers suivants à partir d’un ordinateur BizTalk Server à l’ordinateur sur lequel vous avez installé la fonction frontale HTTP BTARN :
  
    -   Microsoft.VC80.ATL.manifest  
  
    -   atl80.dll  
  
     Si Visual Studio est installé sur le même ordinateur que BizTalk Server, le dossier source pour les deux fichiers est <*lecteur*> : \Program Files\Microsoft Visual Studio < version\>\VC\redist\x86\Microsoft.VC100.ATL .  
  
     Si Visual Studio n’est pas installé sur le même ordinateur BizTalk Server, le dossier source pour les deux fichiers est sous <*lecteur*> : \WINDOWS\WinSxS.  
  
2.  Ajoutez les fichiers copiés sur l'ordinateur sur lequel vous avez installé la fonction frontale HTTP BTARN. Par défaut, copiez les fichiers dans <*lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour RosettaNet.  
  
3.  Après avoir copié les fichiers sur l’ordinateur frontal HTTP, exécutez **Configuration.exe** à nouveau.  
  
### <a name="some-btarn-assemblies-stay-in-gac-after-uninstalling"></a>Certains assemblys BTARN demeurent dans le GAC après la désinstallation  
 **Problème**  
  
 Lorsque vous désinstallez BTARN, certains assemblys restent dans le global assembly cache (GAC).  
  
 **Résolution**  
  
 Supprimez les assemblys du GAC avant de réinstaller BTARN.  
  
 Utilisez le **BtarnClean** utilitaire à partir du SDK pour supprimer les assemblys. L'utilitaire effectue les opérations suivantes :  
  
-   Arrête et désinscrit toutes les orchestrations BTARN.  
  
-   Arrête et supprime tous les ports associés.  
  
-   Annule le déploiement de tous les assemblys Microsoft.Solutions.BTARN.*.  
  
 Après avoir exécuté l'utilitaire, si des assemblys demeurent dans le GAC, ouvrez l'Explorateur Windows, accédez au dossier « C:\Windows\Assembly », puis supprimez manuellement tous les assemblys en commençant par Microsoft.Solutions.BTARN.  
  
### <a name="service-unavailable-error-on-64-bit-os"></a>Erreur de service non disponible sur le système d’exploitation 64 bits
 **Problème**  
  
 Vous risquez d’obtenir un `Service Unavailable` lors de la tentative d’accès HTTP BTARN emplacement de réception sur les systèmes d’exploitation Windows 64 bits.  
  
 **Cause**  
  
 Ce problème peut être lié au filtre ISAPI « RPCProxy.dll ».  
  
 **Résolution**  
  
Supprimer les références au filtre ISAPI du proxy RPC et redémarrer les services IIS :
  
1.  Dans le Gestionnaire des Services Internet (IIS), cliquez sur **Sites Web**, puis cliquez sur **propriétés**.  
  
2.  Dans le **propriétés du Site Web** boîte de dialogue, cliquez sur le **filtres ISAPI** onglet, supprimez **Proxy RPC** filtrer, puis cliquez sur **OK**.  
  
3.  Redémarrez IIS.  
  
4.  Après avoir redémarré IIS, essayez d’accéder à http://localhost. Vous devrez recevoir le message 400 du navigateur Internet.  
  
### <a name="sql-server-mixed-mode-not-supported"></a>SQL Server en Mode mixte non pris en charge.  
BTARN ne prend pas en charge SQL Server en mode mixte.  
  
### <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample"></a>Exécutez setupx64.bat pour configurer la double action PIPAutomation exemple d’orchestration 

Exécutez setupx64.bat dans \Program Files\Microsoft BizTalk Accelerator pour le dossier RosettaNet\SDK\PIPAutomation\DoubleAction installer l’exemple d’Orchestration Double Action PIPAutomation.
  
### <a name="download-the-btarn-setup-file-from-the-web-to-a-temp-folder"></a>Télécharger le fichier d'installation BTARN du Web vers un dossier temporaire  
 **Problème**  
  
 Si vous téléchargez le fichier exécutable à partir du Web à extraction automatique de BTARN et l’enregistrer dans le dossier racine de BizTalk Server, lorsque vous essayez d’exécuter le fichier exécutable, BizTalk **Assistant** s’exécute, au lieu de l’Assistant Installation de BTARN.  
  
 **Résolution**  
  
 Téléchargez le fichier exécutable à extraction automatique de BTARN et enregistrez le fichier dans un dossier temporaire.
