---
title: "Impossible d’exporter la configuration de point de terminaison de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b36fa47d9302f3f88f65575bfa8f74c6469e9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-service-endpoint-configuration"></a>Impossible d'exporter la configuration du point de terminaison du service
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'exporter la configuration du point de terminaison du service vers « {0} »|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'utilisateur ne dispose pas d'autorisation en écriture vers la destination ou que certaines propriétés requises n'ont pas été correctement spécifiées, par exemple Adresse (URI) et Type de liaison.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer l'identité du point de terminaison.  
  
#### <a name="to-configure-the-endpoint-identity"></a>Pour configurer l'identité du point de terminaison  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  WCF **[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Assurez-vous que l’écriture dans le dossier de destination est autorisé.  
  
10. Vérifiez le **comportement** onglet et la **identité du point de terminaison** paramètres dans le **général** onglet pour vous assurer qu’ils sont valides.  
  
    > [!NOTE]
    >  Vous devez disposer d'autorisations en écriture dans le dossier de destination. Pour les obtenir, contactez l'administrateur de l'ordinateur.