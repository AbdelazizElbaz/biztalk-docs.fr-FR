---
title: "Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-à partir de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d338759-5646-4dc2-8319-a42aaa8c3d9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b52f153cce06eac014d98fa1908978694fc67706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-from"></a>Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-From
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|InvalidAgreementAS2FromName|  
|Texte du message|Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-From.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu envoyer le message AS2 car la propriété AS2-From n'a pas été définie pour le tiers qui a été résolu comme récepteur des messages.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, ouvrez la console Administration de BizTalk Server, accédez au nœud Tiers, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message, cliquez sur le nœud Tiers considéré comme récepteur des messages AS2, puis entrez une valeur pour la propriété AS2-From.