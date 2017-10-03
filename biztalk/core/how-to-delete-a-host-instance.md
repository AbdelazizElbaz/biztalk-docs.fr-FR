---
title: "Supprimer une Instance d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35a06480-0962-4bdc-add2-56f979a2f1c9
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 798ea341ef61b15729dd15742eef7701641e7547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delete-a-host-instance"></a>Supprimer une Instance d’hôte

## <a name="overview"></a>Vue d'ensemble
La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) permet de supprimer des instances de l'hôte. Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md). Pour plus d’informations sur l’utilisation de WMI pour supprimer une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Lorsque vous supprimez une instance d'hôte, l'instance du composant d'exécution de BizTalk Server est supprimée du serveur associé et la base de données de gestion BizTalk est mise à jour pour supprimer cette instance de l'hôte.  
  
 Pour éviter de perdre des messages lorsque vous supprimez une instance d'hôte, BizTalk Server termine tous les traitements avant la suppression effective de l'instance.  
  
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
  
3.  Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
4.  Dans le **confirmer supprimer une instance hôte** boîte de dialogue, cliquez sur **Oui**.  
  
    > [!NOTE]
    >  Si BizTalk Server ne peut pas supprimer l'instance de l'hôte, une boîte de dialogue vous permettant d'imposer la suppression de l'instance de l'hôte s'affiche. Après avoir lu les informations fournies, cliquez sur **Oui** pour supprimer l’instance d’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md)   
 [Comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)   
 [Comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)   
 [Comment modifier les propriétés de l’Instance hôte](../core/how-to-modify-host-instance-properties.md)