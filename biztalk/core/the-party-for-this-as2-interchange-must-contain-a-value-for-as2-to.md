---
title: "Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-pour | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 029eae5d-4c13-402d-90c5-8e9ef3814a1f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adda90c2ae0e5dfa659e3bd36dcadfc58f815ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-to"></a>Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-To.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|InvalidAgreementAS2ToName|  
|Texte du message|Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-de.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter le message AS2 sortant, car la propriété AS2 n'était pas définie pour le tiers résolu considéré comme récepteur des messages. Cela indique le tiers correspondant au message AS2 sortant a été résolu en faisant correspondre le port d'envoi associé au tiers avec le port d'envoi qui s'est abonné au message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Accédez au nœud Tiers, puis ouvrez la boîte de dialogue Propriétés AS2 correspondant au tiers résolu pour le message.  
  
3.  Cliquez sur le nœud Tiers considéré comme récepteur des messages.  
  
4.  Entrez une valeur pour la propriété AS2-To.