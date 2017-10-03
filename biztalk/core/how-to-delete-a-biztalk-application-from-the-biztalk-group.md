---
title: Comment supprimer une Application BizTalk du groupe BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeploying, applications
- applications, deleting
- applications, groups
- undeploying, deleting
- managing [applications], deleting
- deleting, applications
- applications, undeploying
- managing [applications], groups
- groups, applications
ms.assetid: 968a6436-ae1a-4f85-bb44-e704826a0197
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 269ef99a3244d0aba55d9dad856c0262d0d14ba0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-biztalk-application-from-the-biztalk-group"></a>Suppression d'une application BizTalk du groupe BizTalk
Vous pouvez supprimer une application BizTalk du groupe BizTalk. Cette opération supprime l'ensemble des données de l'application des bases BizTalk du groupe, et celle-ci ne s'affiche plus dans la console Administration de BizTalk Server. L'application n'en est pas pour autant désinstallée.  
  
 Avant de supprimer une application, gardez les points suivants à l'esprit :  
  
-   Vous devez arrêter l'exécution de l'application avant de pouvoir la supprimer. Vous devez utiliser l’option arrêt complet de l’arrêt de l’application, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
-   Vous pouvez supprimer une application uniquement si aucune autre application ne contient de référence à celle-ci. Si d'autres applications contiennent des références à l'application que vous souhaitez supprimer, vous devez d'abord supprimer les références dans les autres applications. Pour obtenir des instructions, consultez [comment supprimer une référence à une autre Application](../core/how-to-remove-a-reference-to-another-application.md).  
  
-   Vous ne pouvez pas supprimer une application si elle contient un groupe de ports d'envoi dont un des ports d'envoi d'une autre application est membre. Dans ce cas, vous devez désinscrire le port d'envoi membre avant de supprimer l'application. Pour obtenir des instructions, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md).  
  
-   Vous ne pouvez pas supprimer une application contenant un port d'envoi référencé par un tiers. Vous pouvez supprimer la référence du tiers, supprimer le port d'envoi ou déplacer le port d'envoi vers une autre application. Pour obtenir des instructions sur la réalisation de ces tâches, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca), [comment supprimer un Port d’envoi](../core/how-to-delete-a-send-port.md), ou [comment déplacer un artefact vers une autre Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
-   Vous ne pouvez pas supprimer l'application par défaut. Si vous souhaitez la supprimer, vous devez d'abord définir une autre application en tant qu'application par défaut. Pour obtenir des instructions, consultez [la modification de l’Application par défaut](../core/how-to-change-the-default-application.md).  
  
-   Vous ne pouvez pas supprimer une application comprenant une orchestration dont une instance a été interrompue.  
  
-   Pour annuler complètement le déploiement d’une application BizTalk, vous devez également prendre les étapes décrites dans [comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md), et vous devez également supprimer les autres fichiers et paramètres, comme décrit dans [comment supprimer Autres fichiers et paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-delete-a-biztalk-application"></a>Pour supprimer une application BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk et **Applications**.  
  
3.  Cliquez sur le dossier d’application, puis cliquez sur **supprimer**.  
  
4.  Cliquez sur **Oui** pour confirmer la suppression.  
  
     BizTalk Server supprime l'ensemble des données de l'application des bases BizTalk et supprime l'application de la console d'administration.  
  
     Si BizTalk Server ne parvient à supprimer aucun des artefacts de l'application, l'opération échoue. Dans ce cas, BizTalk Server tente d'annuler la suppression.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **« ApplicationName » BTSTask RemoveApp :** *valeur* [**/Server :***valeur*] [**/Database :**  *valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveApp /ApplicationName:MyApplication**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à supprimer. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Database. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Server. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)   
 [Déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md)