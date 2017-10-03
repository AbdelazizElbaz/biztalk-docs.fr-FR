---
title: "Requis la propriété type de liaison non spécifié (R2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8e45783-6454-44e2-867e-e30092725f51
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a34de62453bd252e110edd0caf8a71996f25ae3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="required-property-binding-type-not-specified-r2"></a>La propriété obligatoire Type de liaison n'a pas été spécifiée (R2)
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Propriété obligatoire Type de liaison non spécifié|  
  
## <a name="explanation"></a>Explication  
 Vous n'avez pas défini la propriété Type de liaison lors de la configuration d'un transport WCF-Custom ou WCF-CustomIsolated.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer la propriété Type de liaison.  
  
#### <a name="to-configure-the-binding-type-property"></a>Pour configurer la propriété Type de liaison  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF--[***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Spécifiez une valeur dans la **Type de liaison** liste.  
  
 Pour plus d'informations sur la configuration des liaisons, consultez les ressources suivantes :  
  
-   [Pour configurer les emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-Custom](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [Comment configurer un Port d’envoi WCF-Custom](../core/how-to-configure-a-wcf-custom-send-port.md)