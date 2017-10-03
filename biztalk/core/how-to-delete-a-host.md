---
title: "Suppression d’un hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3df8719-27cb-4010-82e3-68226ab74b17
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd5f54fa84ddb521444cfb3f2351a8062c4de00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delete-a-host"></a>Suppression d’un hôte
Vous ne pouvez supprimer un hôte que dans les cas suivants :  
  
-   Il ne s'agit pas de l'hôte par défaut.  
  
-   Cet hôte n'est pas seul à effectuer le suivi des hôtes.  
  
-   Il n'héberge pas de gestionnaires d'adaptateur.  
  
-   Aucune orchestration n'est inscrite pour cet hôte.  
  
-   Aucune instance de l'hôte n'est lancée.  
  
-   Si l'hôte n'est pas mis en cluster.  
  
 Pour plus d’informations sur les ordinateurs hôtes, consultez [hôtes](../core/hosts.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer des droits d'utilisateur suivants pour créer ou supprimer des hôtes et pour modifier leurs propriétés :  
  
-   Vous devez être membre du groupe d'administrateurs BizTalk Server.  
  
-   Les droits suivants sont requis dans SQL Server :  
  
    -   Vous devez être soit un administrateur SQL Server, soit un membre des rôles de base de données SQL Server db_owner ou db_securityadmin dans la base de données des suivis BizTalk (BizTalk DTADb), dans les bases de données MessageBox (BizTalkMsgBoxDb) et dans la base de données d'importation principale BAM (BAMPrimaryImport).  
  
    -   Vous devez être membre du rôle SQL Server sysadmin sur tous les ordinateurs où résident des bases de données MessageBox, ou membre du rôle SQL Server db_owner ou db_ddladmin pour toutes les bases de données MessageBox.  
  
## <a name="steps"></a>Étapes 
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **hôtes**.  
  
3.  Dans le volet de détails, cliquez sur l’hôte que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
4.  Dans le **confirmer la suppression hôte** boîte de dialogue, cliquez sur **Oui**.  
  
## <a name="see-also"></a>Voir aussi  
-  [Gestion des hôtes et des instances d’hôte BizTalk](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [Comment créer un nouvel hôte](../core/how-to-create-a-new-host.md)   
-  [Comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md)   
-  **MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]