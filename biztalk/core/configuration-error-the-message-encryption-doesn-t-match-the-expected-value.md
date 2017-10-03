---
title: "Erreur de configuration. Le n chiffrement de message &#39; t correspond à la valeur attendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b17460c4dcd6f9d2a8c18e5e7284cd36940d6820
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-the-message-encryption-doesn39t-match-the-expected-value"></a>Erreur de configuration. Le n chiffrement de message &#39; t correspond à la valeur attendue
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderPartyEncryptionConfigurationError|  
|Texte du message|Erreur de configuration. Le chiffrement du message ne correspondait pas à la valeur attendue. Contactez le partenaire émetteur et vérifiez l'utilisation du chiffrement. AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu traiter le message AS2 car le chiffrement est spécifié dans les paramètres de tiers, mais le message AS2 n'est pas chiffré ou il l'est bien que le chiffrement ne soit pas autorisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le message AS2 entrant est chiffré si le chiffrement est spécifié dans les paramètres de tiers ou qu'il ne l'est pas dans le cas contraire. Procédez de l'une des manières suivantes :  
  
1.  Si le **remplacement de propriété des propriétés de message entrant est sélectionnée** dans la page tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue propriétés AS2 dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, le **Message doit être chiffré.**  propriété est sélectionnée, mais le message n’est pas chiffré, contactez le tiers qui a envoyé le message et demandez-lui de chiffrer le message et le renvoyer. Ou vous pouvez effacer le **Message doit être chiffré** propriété, ou la **remplacer les propriétés du message entrant** propriété.  
  
2.  Si le **remplacer les propriétés du message entrant** propriété est sélectionnée, le **Message doit être chiffré** propriété est désactivée, mais le message est chiffré, contactez le tiers qui a envoyé le message et demandez-lui de ne pas chiffrer le message et le renvoyer. Vous pouvez également sélectionner le **Message doit être chiffré** propriété.