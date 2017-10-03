---
title: "Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : tiers non ayant le nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af059a04-3b7c-48e2-a3bf-48ad62deb139
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0e620797d45fb0b3d2ef929865a4b8bb98d2d90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-party-with-name"></a>Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : tiers non ayant le nom
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un échec s'est produit lors du traitement du message X12 sur le port d'envoi {0}. Il n’existe aucun tiers avec {{1} du nom.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre le tiers pour l'échange X12, car il n'a pas réussi à faire correspondre le port d'envoi abonné à l'échange au port d'envoi associé au tiers. Cette erreur se produit lorsque ni la propriété DestinationPartyName ni les propriétés du qualificateur d'expéditeur, de l'identificateur de l'expéditeur, du qualificateur du récepteur et de l'identificateur du récepteur ne sont promues. Elles ne sont donc pas disponibles pour la résolution du tiers côté envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le port d'envoi abonné à l'échange correspond au port d'envoi associé à un tiers.