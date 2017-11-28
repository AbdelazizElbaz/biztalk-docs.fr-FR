---
title: "Résolution de l’accord basée sur les propriétés de contexte de protocole a échoué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58fccd84-579c-4b5e-872b-33730d4079e8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76d74ad7aa4a73f4a0befcef32bc8051195cb080
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# La résolution de l'accord basée sur les propriétés de contexte du protocole a échoué.
## Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|AgreementResolutionContextPropertiesLookupFailed|  
|Texte du message|Résolution de l’accord basée sur les propriétés de contexte pour {0} protocole a échoué.|  
  
## Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre l'accord sur la base des propriétés de contexte fournies par le client.  
  
## Action de l'utilisateur  
 Pour résoudre cette erreur, renseignez les propriétés de contexte dans le message BizTalk de manière à ce que la résolution de l'accord puisse se produire.