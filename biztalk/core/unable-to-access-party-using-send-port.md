---
title: "Impossible d’accéder au tiers avec port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffacba77-76e8-4f03-be26-134a9999d6c1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aa582319226b114720ef234b8e3f65e416a94d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-party-using-send-port"></a>Impossible d'accéder au tiers avec port d'envoi
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|UnableToLocateAS2PartyBySendPortNameError|  
|Texte du message|Impossible d’accéder au tiers avec port d’envoi : {0}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le pipeline d'envoi n'a pas réussi à trouver le tiers associé au port d'envoi spécifié pour le message AS2 sortant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, associez un tiers au port d'envoi spécifié :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.  
  
3.  Cliquez avec le bouton droit sur le tiers approprié.  
  
4.  Cliquez sur **Propriétés**.  
  
5.  Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, dans le volet gauche, cliquez sur **Ports d’envoi**.  
  
6.  Entrez le nom de port d’envoi dans le **Ports d’envoi** liste.  
  
7.  Cliquez sur **OK**.