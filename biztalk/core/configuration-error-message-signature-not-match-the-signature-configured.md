---
title: "Erreur de configuration. Le n de signature de message &#39; t correspond à la signature configurée pour ce tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cea0016-12e8-4ee8-ac44-11024b5e74ef
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23214832300fe6125318ce67083f6bee0a364158
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-the-message-signature-doesn39t-match-the-signature-configured-for-this-party"></a>Erreur de configuration. Le n de signature de message &#39; t correspond à la signature configurée pour ce tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Erreur de configuration. La signature du message ne correspond pas à la signature configurée pour ce tiers. Contactez le partenaire émetteur et vérifiez le certificat utilisé. AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 n'a pas pu vérifier la signature lors de l'exécution du traitement MIME. Cela peut être dû à l'utilisation, lors du traitement du message reçu, d'un certificat différent de celui que l'expéditeur a utilisé pour signer le message. Cette situation peut se produire lorsque BizTalk Server utilise les paramètres d'un tiers erroné pour vérifier la signature d'un message AS2 entrant.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Assurez-vous que le tiers approprié est déterminé par le processus de résolution de tiers pour le message AS2 entrant. Pour ce faire, vérifiez que le tiers approprié est résolu lorsque BizTalk Server tente de trouver une correspondance entre l'en-tête AS2-From du message entrant et la valeur de EDIINT-AS2 From dans la liste des alias de la page Général de la boîte de dialogue Propriétés du tiers. Si cette opération ne résout pas le tiers, vérifiez que le tiers adéquat est résolu lorsque BizTalk Server tente de trouver une correspondance entre la propriété de contexte AS2-From définie pour le message entrant et le nom d'un tiers.  
  
-   Assurez-vous que le certificat défini dans la page Certificat de la boîte de dialogue Propriétés du tiers, et stocké dans le magasin Ordinateur local\Autres personnes, correspond à celui utilisé pour signer le message.