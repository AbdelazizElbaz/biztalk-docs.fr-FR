---
title: "Durée de vie non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2ddb6de-8c3b-4dee-a984-980e1caea95e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9171fd311a07317c0480e6e4d1ef35742e0e8bcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-time-to-live-timeout"></a>Durée de vie non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Durée de vie non valide. Plage valide : 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes|  
  
## <a name="explanation"></a>Explication  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer la plage du délai d'attente.  
  
#### <a name="to-configure-the-timeout-range"></a>Pour configurer la plage du délai d'attente  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** liste, sélectionnez **WCF-NetMsmq**.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Dans le **les paramètres de file d’attente** section, vérifiez que le **(dd:hh:mm:ss) en direct de temps du Message** plage est valide. Les valeurs acceptables vont de 0 à 23 heures, 0 à 59 minutes et 0 à 59 secondes.