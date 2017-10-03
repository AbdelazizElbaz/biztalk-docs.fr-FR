---
title: "Comment désinstaller une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], uninstalling
- applications, uninstalling
- uninstalling, applications
- undeploying, uninstalling
ms.assetid: ab721c6e-194e-4b8a-bfd1-d0139d284373
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cba0c5f4ea8340612bb42c4a15257acd449848d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-uninstall-a-biztalk-application"></a>Désinstallation d'une application BizTalk
Cette rubrique explique comment désinstaller une application BizTalk à l'aide de l'outil Ajout/Suppression de programmes du Panneau de configuration ou de l'outil de ligne de commande BTSTask. Ces deux méthodes sont les seules prises en charge pour la désinstallation d'une application. Si vous avez installé plusieurs fichiers .msi pour cette application, notamment pour la mettre à jour, double-cliquer sur le fichier .msi ou utiliser msiexec ne permettra peut-être pas de désinstaller complètement l'application.  
  
> [!CAUTION]
>  La désinstallation d'une application BizTalk lors de son exécution peut générer des erreurs dans celle-ci. Afin d’éviter ce problème, nous vous recommandons de vérifier qu’il est recommandé sont sans exécution du service des instances de l’application, comme décrit dans [recherche de toutes les Instances de Service](../core/how-to-search-for-all-service-instances.md). Si nécessaire, vous pouvez cesser de l’application à l’aide de l’option arrêt complet pour arrêter complètement toutes les instances en cours d’exécution, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md). Sachez qu'en procédant de cette façon, les messages en cours de traitement ne s'exécuteront pas.  
  
 Un script de prétraitement ou de post-traitement doit être inclus dans le fichier .msi de l'application afin de supprimer tous les fichiers et paramètres associés à celle-ci lors de sa désinstallation. Si un script de prétraitement ou de post-traitement  n'a pas été inclus, les procédures indiquées dans cette rubrique supprimeront ses fichiers et paramètres du système de fichiers local, sauf dans les cas suivants :  
  
-   Si l'application inclut un répertoire virtuel, ce répertoire et ses fichiers sont supprimés, sauf si les fichiers ont été ajoutés au répertoire virtuel après l'installation de l'application. Dans ce cas, le répertoire virtuel et les fichiers ajoutés ne sont pas supprimés. Pour supprimer le répertoire virtuel et les fichiers ajoutés, vous devez le faire explicitement.  
  
-   Les scripts de prétraitement et de post-traitement sont supprimés, mais les fichiers ajoutés par les scripts lors de l'installation ou de la désinstallation ne sont pas supprimés, et les actions prises par les scripts ne sont pas annulées. Pour supprimer les fichiers ajoutés par les scripts et ou annuler leurs actions, vous devez le faire explicitement.  
  
    > [!NOTE]
    >  Seuls les scripts de prétraitement ou de post-traitement dont l'emplacement de destination est spécifié dans les propriétés de déploiement lors de l'importation de l'application s'exécuteront lors de la désinstallation. Pour plus d’informations, consultez [Ajout antérieur à la version ou un Script de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
-   Les certificats ne sont jamais supprimés lorsque vous désinstallez une application BizTalk. Pour supprimer un certificat, vous devez le faire explicitement. En outre, les composants ne sont pas supprimés du registre Windows et les assemblys BizTalk ne sont pas supprimés du GAC. Pour les supprimer, vous devez le faire explicitement. Pour plus d’informations, consultez [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
 Si vous annulez la désinstallation avant qu'elle ne soit terminée, BizTalk Server l'annule, sauf si des scripts de prétraitement ou de post-traitement ont commencé des actions avant l'annulation de l'opération. Pour restaurer l'application à l'état tel qu'il était avant que vous ne commenciez la désinstallation, double-cliquez sur le fichier .msi et réinstallez l'application. Si plusieurs fichiers .msi ont été installés pour cette application, double-cliquez sur chacun d'entre eux pour la réinstaller dans l'ordre dans lequel ils ont été initialement installés.  
  
 Pour plus d’informations sur les scripts de post-traitement, voir [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
> [!NOTE]
>  Pour annuler complètement le déploiement d’une application BizTalk, vous devez également la supprimer du groupe BizTalk, comme décrit dans [comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures décrites dans cette rubrique, vous devez disposer des autorisations appropriées. Pour plus d’informations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-uninstall-a-biztalk-application"></a>Pour désinstaller une application BizTalk  
  
#### <a name="using-uninstall-or-change-a-program"></a>Utilisation de Désinstaller ou modifier un programme  
  
1.  Sur l’ordinateur exécutant l’application, cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis double-cliquez sur **programmes et fonctionnalités**.  
  
2.  Sur **désinstaller ou modifier un programme** page, cliquez sur l’application BizTalk à supprimer, puis cliquez sur **désinstallation**.  
  
     Windows Installer supprime l'application spécifiée.  
  
3.  Si l'application s'exécute sur plusieurs ordinateurs, répétez ces étapes pour chacun d'eux.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante, en remplaçant par la valeur appropriée, comme décrit dans le tableau suivant :  
  
     **BTSTask UninstallApp** [**« ApplicationName » :***valeur*]  
  
     Exemple :  
  
     **BTSTask UninstallApp /ApplicationName:MyApplication**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à désinstaller. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)   
 [Commande UninstallApp](../core/uninstallapp-command.md)