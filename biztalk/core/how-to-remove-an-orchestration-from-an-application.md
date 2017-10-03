---
title: "Comment supprimer une Orchestration à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, orchestrations
- deleting, orchestrations
- managing [orchestrations], deleting
- orchestrations, applications
- orchestrations, deleting
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef4909f5430ae2d0435d519823abe9735cbc1cc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-an-orchestration-from-an-application"></a>Suppression d'une orchestration dans une application
Cette rubrique décrit comment supprimer une orchestration dans une application BizTalk à l'aide de la console Administration de BizTalk Server ou de l'invite de commande. La suppression d'une orchestration dans une application entraîne également sa suppression dans la base de données de gestion BizTalk pour le groupe BizTalk.  
  
 Lorsque vous supprimez une orchestration, voici ce qui se produit :  
  
-   L'orchestration est supprimée de la base de données de gestion BizTalk.  
  
-   L'assembly BizTalk qui contient l'orchestration est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements.  
  
-   Par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.  
  
 Avant de supprimer une orchestration dans une application, gardez les points suivants à l'esprit :  
  
-   Si d'autres artefacts ont des dépendances avec cette orchestration ou avec les artefacts contenus dans l'assembly également supprimé, ils ne fonctionneront plus correctement une fois l'orchestration supprimée. Pour des informations générales sur les dépendances, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
-   Vous ne pouvez pas supprimer d'orchestrations ayant des instances en cours d'exécution. Vous devez mettre fin à toute instance en cours d'exécution.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-remove-an-orchestration-from-an-application"></a>Pour supprimer une orchestration dans une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez supprimer.  
  
3.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **désinscrire**.  
  
4.  Sélectionnez l’orchestration, pointez sur **vue**, puis cliquez sur **informations sur l’Instance**.  
  
5.  Dans le volet de résultats de requête, cliquez sur les instances d’orchestration, puis cliquez sur **Terminate**.  
  
    > [!NOTE]
    >  Vous pouvez désinscrire, arrêter les instances en cours d’exécution et arrêter tous les orchestrations dans une application à la fois à l’aide de l’option arrêt complet de l’application, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
6.  Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **supprimer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**/ ApplicationName**|Nom de l'application BizTalk contenant l'orchestration à supprimer. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («). L'application par défaut est utilisée si ce paramètre n'est pas spécifié.|  
    |**/ Luid**|Identificateur unique local (LUID) de l'orchestration. Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Database. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Server. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Commande RemoveResource](../core/removeresource-command.md)