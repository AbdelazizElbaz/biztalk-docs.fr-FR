---
title: "Démarrer une Instance d’hôte | Documents Microsoft"
description: "Utilisez l’Administration de BizTalk pour démarrer une instance d’hôte dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96a4362-2147-4b8e-a270-bf9a17477ba3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5cccc48b33dda4b6458f8dfa8f56a84ad3cd62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="start-a-host-instance"></a>Démarrer une Instance d’hôte
Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) pour démarrer des instances d'hôte. Après avoir ajouté ou arrêté une instance d'hôte, vous devez la démarrer pour qu'elle s'exécute et achemine des messages vers les bases de données MessageBox.  
  
> [!IMPORTANT]
>  Le compte de service que vous spécifiez pour une instance d'hôte doit être un membre du groupe Windows pour l'hôte associé. Sinon, cette instance risque de ne pas disposer des autorisations ou de l'authentification appropriées au moment de l'exécution. En outre, pour des raisons de sécurité, le compte doit disposer de privilèges minimaux, car les orchestrations hébergées par l'instance de l'hôte peuvent exécuter un code personnalisé potentiellement nuisible.  
  
 Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md). Pour plus d’informations sur l’utilisation de WMI pour démarrer une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.  
  
 Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :  
  
-   importation principale BAM (BAMPrimaryImport).  
  
-   gestion BizTalk (BizTalkMgmtDb) ;  
  
-   MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;  
  
-   suivis BizTalk (BizTalkDTADb) ;  
  
-   moteur des règles (BizTalkRuleEngineDb) ;  
  
> [!CAUTION]
>  Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation). De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.  
  
## <a name="steps"></a>Étapes
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.  
  
3.  Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez démarrer, puis cliquez sur **Démarrer**.  
  
     L’état de l’instance d’hôte devient **attente de démarrage**. Une fois que l’instance d’hôte démarre, l’état passe à **en cours d’exécution**.  
  
 Après avoir lancé une instance d'hôte, vous pouvez l'arrêter pour l'empêcher d'acheminer des messages vers la base de données MessageBox. Vous devez arrêter une instance d'hôte pour pouvoir désinstaller BizTalk Server d'un ordinateur donné. Pour plus d’informations sur l’arrêt d’une instance d’hôte, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Ajouter une Instance d’hôte](../core/how-to-add-a-host-instance.md)   
 [Arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)   
 [Supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md)   
 [Modifier les propriétés de l’Instance hôte](../core/how-to-modify-host-instance-properties.md)