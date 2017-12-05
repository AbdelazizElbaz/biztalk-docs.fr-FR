---
title: "Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : tiers non ayant le nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678baacb-1f21-4081-b788-ef346c3598ca
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6becad3fefaa8167c9cf1af051731aa08be0d80a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-party-with-name"></a>Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : tiers non ayant le nom
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|EDI de BizTalk Server|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un échec s'est produit lors du traitement du message EDIFACT sur le port d'envoi {0}. Il n’existe aucun tiers avec {{1} du nom.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre le tiers pour l'échange EDIFACT, car il n'a pas réussi à faire correspondre le port d'envoi abonné à l'échange au port d'envoi associé au tiers. Cette erreur se produit lorsque ni la propriété DestinationPartyName ni les propriétés du qualificateur et de l'identificateur de l'expéditeur ainsi que celles du qualificateur et de l'identificateur du récepteur ne sont promues. Elles ne sont donc pas disponibles pour la résolution du tiers côté envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le port d’envoi abonné à l’échange correspond au port d’envoi associé au tiers.