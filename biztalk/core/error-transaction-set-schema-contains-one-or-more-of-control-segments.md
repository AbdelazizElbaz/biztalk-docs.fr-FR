---
title: "Schéma du document informatisé contient un ou plusieurs des contrôle les segments ISA, IEA, GS, GE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7589d8f0-c727-47df-afbc-77b0f190f3e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff90a7ea80208f0a69ee8aca5c7593c7b6253c53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-schema-contains-one-or-more-of-control-segments-isa-iea-gs-ge"></a>Le schéma du document informatisé contient un ou plusieurs segments de contrôle ISA, IEA, GS, GE
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|SchemaCode114EOtherControlSegmentsPresent|  
|Texte du message|Le schéma du document informatisé contient un ou plusieurs segments de contrôle ISA, IEA, GS, GE|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le document informatisé entrant ou que le pipeline d'envoi n'a pas pu traiter le document informatisé sortant, car le schéma du document informatisé impose la présence d'au moins un segment ISA, IEA, GS ou GE.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, annulez le déploiement du schéma de document, supprimez le segment ISA, IEA, GS ou GE du schéma, puis redéployez-le.