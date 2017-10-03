---
title: "La notification EDIFACT a été générée par le système. Toutefois, elle ne contient pas de propriété de contexte pour l'ensemble de délimiteurs. Il ne peut pas être sérialisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7b1e62-3230-4cdc-830f-3267de1efd1c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d21ce485c2cd5c55bb941afdfc15d2ad545db61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-acknowledgement-was-generated-by-the-system-however-it-is-missing-a-context-property-for-delimiter-set-it-cannot-be-serialized"></a>La notification EDIFACT a été générée par le système. Toutefois, elle ne contient pas de propriété de contexte pour l'ensemble de délimiteurs. Elle ne peut pas être sérialisée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|La notification EDIFACT a été générée par le système. Toutefois, elle ne contient pas de propriété de contexte pour l'ensemble de délimiteurs. Elle ne peut pas être sérialisée|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que BizTalk Server ne peut pas sérialiser l'accusé de réception EDIFACT et qu'une propriété de contexte pour l'ensemble de délimiteurs est manquante dans le message BizTalk.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous d'enregistrer la propriété de contexte de l'ensemble de délimiteurs dans le contexte de message BizTalk pour les accusés de réception EDIFACT.