---
title: "Arrêter une Instance d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1f2e0c1-a387-4182-82ef-e25f49ac509b
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837b08c30263b48ad481c7e03820cfba0b6c0ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="stop-a-host-instance"></a>Arrêter une Instance d’hôte

## <a name="overview"></a>Vue d'ensemble
Vous pouvez utiliser la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration ou de Windows Management Instrumentation (WMI) pour arrêter les instances de l’hôte. Vous devez arrêter une instance d'hôte avant de pouvoir la supprimer ou avant de pouvoir désinstaller BizTalk Server d'un ordinateur donné. Vous pouvez arrêter une instance d'hôte installée et démarrée. Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).  
  
 Pour plus d’informations sur l’utilisation de WMI pour arrêter une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
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
  
3.  Dans le volet de détails, cliquez sur l’instance d’hôte que vous voulez arrêter, puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
 Après avoir arrêté une instance d'hôte, vous pouvez la démarrer, la supprimer ou désinstaller BizTalk Server de l'ordinateur. Pour plus d’informations sur le démarrage d’une instance d’hôte, consultez [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md). Pour plus d’informations sur la suppression d’une instance d’hôte, consultez [comment supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md)   
 [Comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)   
 [Comment supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md)   
 [Comment modifier les propriétés de l’Instance hôte](../core/how-to-modify-host-instance-properties.md)