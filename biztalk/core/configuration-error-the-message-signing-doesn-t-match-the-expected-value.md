---
title: "Erreur de configuration. Le message de signature ne &#39; t correspond à la valeur attendue. | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f067351-b6b0-479d-b2ff-81e9f45b5924
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7aaba3aa00b15b3e015cbc010901c6d50818c42
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuration-error-the-message-signing-doesn39t-match-the-expected-value"></a>Erreur de configuration. Le message de signature ne &#39; t correspond à la valeur attendue.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderPartySigningConfigurationError|  
|Texte du message|Erreur de configuration. La signature du message ne correspond pas à la valeur attendue. Contactez le partenaire émetteur et vérifiez l'utilisation de la signature. AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu traiter le message AS2, car la signature est définie dans les paramètres du tiers, mais le message AS2 n'est pas signé, ou car la signature est spécifiée de façon à ne pas être activée, mais le message est signé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le message AS2 entrant est signé si la signature est spécifiée dans les paramètres du tiers, ou qu'il n'est pas signé si la signature est définie comme n'étant pas activée dans ces mêmes paramètres. Procédez de l'une des manières suivantes :  
  
1.  Si le **remplacer les propriétés du message entrant** propriété est sélectionnée dans la partie en tant que page de l’expéditeur du Message AS2 de la boîte de dialogue propriétés AS2 dans la Console Administration de BizTalk Server, le **Message doit être signé** propriété est sélectionnée, mais le message n’est pas signé, contactez le tiers qui a envoyé le message et demandez-lui de signer le message et le renvoyer. Vous pouvez désactiver le **Message doit être signé** propriété, ou le **remplacer les propriétés du message entrant** propriété.  
  
2.  Si le **remplacer les propriétés du message entrant** propriété est sélectionnée, le **Message doit être signé** propriété est désactivée, mais le message est signé, contactez le tiers qui a envoyé le message et demandez-lui de ne pas signer le message et le renvoyer. Vous pouvez également sélectionner le **Message doit être signé** propriété.