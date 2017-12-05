---
title: Comment installer un Assembly dans le GAC | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6afc2f81-fa28-4144-b4bd-21c8f35f2270
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80e3a5126a56b945b2aa7b53aec71fbe83d678a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-install-an-assembly-in-the-gac"></a>Installation d'un assembly dans le GAC
Installer et désinstaller un assembly BizTalk dans le global assembly cache (GAC) à l’aide de l’outil Gacutil fourni avec manuellement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 À l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez avoir des assemblys BizTalk automatiquement installés dans le GAC lorsqu’ils sont déployés à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Définir cette option dans les propriétés de déploiement du projet BizTalk ; consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Vous ne pouvez pas utiliser cette méthode pour installer des assemblys .NET non - BizTalk dans le GAC ; Vous devez les installer manuellement, comme décrit dans cette rubrique.  
  
> [!NOTE]
>  Vous pouvez également spécifier des options de déploiement pour les assemblys après leur déploiement dans une application BizTalk, à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez [comment modifier les Options de déploiement d’un Assembly BizTalk](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md), et [comment modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui a l’autorisation d’écriture dans le GAC. Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.  

  
## <a name="install-using-gacutil"></a>Installer à l’aide de gacutil
  
1.  Copiez l’assembly BizTalk sur votre ordinateur local.  
  
2.  Ouvrez **invite de commandes développeur pour Visual Studio** en tant qu’administrateur.  
  
3.  Tapez la commande suivante :  
  
     `gacutil /i path_to_assembly_file /f`

    Par exemple, tapez :  
    `gacutil /i c:\temp\filename.dll /f`
    
Le `/f` option remplace tout assembly existant qui porte le même nom d’assembly. Pour plus d’informations sur les options et les commandes de gacutil, tapez `gacutil /?`. 

## <a name="uninstall-using-gacutil"></a>Désinstallation à l’aide de gacutil
Désinstallation d’un assembly à partir du global assembly cache (GAC) est nécessaire pour annuler complètement le déploiement d’une application. Vous pouvez automatiser ce processus. Avant de déployer l’application dans un environnement de production, écrivez un script de pré-traitement qui désinstalle automatiquement l’assembly du GAC lors de la désinstallation de l’application. Consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement de l’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
 Vous pouvez également utiliser un script pour supprimer des paramètres et des fichiers supplémentaires. Consultez [comment supprimer les autres fichiers et paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
 
#### <a name="using-the-windows-interface"></a>Utilisation de l'interface Windows  
  
1.  Ouvrez à % systemdrive%\Windows\Assembly.  
  
2.  Avec le bouton droit de chaque fichier d’assembly inclus dans votre application, sélectionnez **désinstallation**, puis sélectionnez **Oui** pour confirmer.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez **invite de commandes développeur pour Visual Studio** en tant qu’administrateur. 
  
2.  Tapez la commande suivante :  
  
     `gacutil /u`\< *nom d’assembly qualifié complet*\>  
  
     Par exemple, tapez :  
     `gacutil /u "hello,Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"`
       
## <a name="see-also"></a>Voir aussi  
 [Déploiement des assemblys BizTalk à partir de Visual Studio dans une application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
[Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)   
 [Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)   
 [Comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)
 