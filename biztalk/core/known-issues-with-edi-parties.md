---
title: "Problèmes connus avec les tiers EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86475960-cdb2-4b39-817a-b5d834f498a9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fddda6dd62e8e3bd2d38574343b7fcb0e0d76f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-parties"></a>Problèmes connus avec les tiers EDI
Cette section contient des rubriques qui décrivent les problèmes connus avec les tiers EDI et le Gestionnaire d'accords partenaires.  
  
## <a name="a-cache-refresh-period-delays-availability-of-a-changed-party-property"></a>Le délai d'actualisation du cache retarde la disponibilité d'une propriété de tiers modifiée  
 Si vous modifiez une propriété de tiers ou globale dans le Gestionnaire d'accords partenaires, les propriétés seront disponibles pour l'exécution de BizTalk une fois que le cache est actualisé toutes les quinze minutes ou après un redémarrage du service BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des accusés de réception EDI](../core/configuring-edi-acknowledgments.md)   
 [Le rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md)   
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)   
 [Configuration des propriétés de l’accord Global ou de secours](../core/configuring-global-or-fallback-agreement-properties.md)