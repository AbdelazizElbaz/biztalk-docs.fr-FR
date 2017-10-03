---
title: "Le décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe2d76d-b0f1-4118-8483-547c2c9fffb7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90388f27c44314d1c5bc795744366cfc88ed6321
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-when-validating-the-mic-value-returned-in-the-mdn"></a>Le traitement du décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderMdnMicFailureDuringProcessing|  
|Texte du message|Le décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN de traitement.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter le MDN entrant, car la validation du MIC (Message Integrity Check) a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que l'algorithme utilisé pour générer le MDN (dans l'en-tête Signed-Receipt-MICalg du message d'origine) est le même que celui spécifié dans la propriété Signed-Receipt-MICalg pour le récepteur des messages AS2. Les deux doivent être soit SHA1, soit MD5. Si l'algorithme spécifié est le même, vérifiez que le champ d'extension Received-Content-MIC de la seconde partie du message MDN signé à parties multiples inclut une synthèse MIC valide. Si tel est le cas, déterminez la raison pour laquelle le MDN ne correspond pas à l'échange envoyé.