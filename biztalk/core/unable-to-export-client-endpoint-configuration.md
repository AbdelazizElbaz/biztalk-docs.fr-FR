---
title: "Impossible d’exporter la configuration de point de terminaison client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d93fe5e-fdb2-49c5-86de-d428b1ecda7f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 941d42ff01bcf578bd7ba7c426c6fe5ca2bfbce3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-client-endpoint-configuration"></a>Impossible d'exporter la configuration du point de terminaison client
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'exporter la configuration du point de terminaison client vers « {0} »|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique l'un des problèmes suivants :  
  
-   L'utilisateur ne dispose pas d'autorisation en écriture dans la destination.  
  
     \- - OU -  
  
-   Certaines propriétés requises ont été pas correctement spécifiés, tel que **adresse (URI)** et **Type de liaison**.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez la procédure suivante pour vérifier les autorisations utilisateur et confirmer **adresse (URI)** et **Type de liaison** les paramètres sont valides.  
  
#### <a name="to-verify-user-permissions-and-confirm-settings"></a>Pour vérifier les autorisations d'utilisateur et confirmer les paramètres  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Localisez votre application, puis votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Vérifiez que l'écriture dans le dossier de destination est autorisée.  
  
10. Vérifier la **comportement** onglet et la **identité du point de terminaison** paramètres **général** onglet pour vous assurer qu’ils sont valides.  
  
> [!NOTE]
>  Vous devez disposer d'autorisations en écriture dans le dossier de destination. Pour les obtenir, contactez l'administrateur de l'ordinateur.