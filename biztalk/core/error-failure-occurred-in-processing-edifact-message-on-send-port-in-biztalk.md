---
title: "Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cffc4705-164f-4779-8f04-c6a2a7f1bbda
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4cb2b0637c54f6fdd13dc5f0d17d71817ce4453
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a>Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un échec s'est produit lors du traitement du message EDIFACT sur le port d'envoi {0}. Il n’existe aucun accord pour les paires qualificateur/identificateur expéditeur et destinataire pour {{1}, {2}, {3}, {4}.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre le tiers pour l'échange EDIFACT, car il n'a pas réussi à établir de correspondance entre les propriétés promues du qualificateur et de l'identificateur de l'expéditeur, ainsi qu'entre celles du qualificateur et de l'identificateur du récepteur, et les valeurs correspondantes d'un tiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Définition des segments UNB associée au tiers, assurez-vous que le qualificateur et l'identificateur de l'expéditeur (UNB2.1 et UNB2.2) et que le qualificateur et l'identificateur du récepteur (UNB3.1 et UNB3.2) qui y sont définis correspondent aux propriétés promues dans le contexte de l'échange.