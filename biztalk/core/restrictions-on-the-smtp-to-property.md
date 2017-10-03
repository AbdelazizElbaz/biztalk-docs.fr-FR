---
title: "Restrictions sur la propriété To SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: c876d30e-44ab-462d-8c98-64416ed6dd1f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b59495ac94b3591801101607533eb9c7dba158fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-smtp-to-property"></a>Restrictions sur la propriété To SMTP
Le **à** propriété est une chaîne qui spécifie l’adresse SMTP du destinataire du message. Vous pouvez répertorier plusieurs adresses avec un séparateur pris en charge par le serveur SMTP.  
  
 Aucune restriction particulière ne s'applique au format d'une adresse SMTP. Cela signifie que l'adaptateur accepte tout format pris en charge par un serveur SMTP. Si un utilisateur renseigne des adresses non valides, l'opération d'envoi échouera et l'adaptateur d'envoi SMTP signalera une erreur.  
  
 Toutefois, cette propriété ne peut pas être vide et sa taille ne doit pas dépasser 256 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions relatives à la configuration de l’adaptateur SMTP](../core/restrictions-when-configuring-the-smtp-adapter.md)