---
title: "Le décodeur AS2 a échoué, car le MDN a indiqué que le traitement des messages a échoué AS2 de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bce620a-f336-435e-b7c3-3db060f2819d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20454f1c551b6b4828c42e09f0442b83275256ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-indicated-the-as2-message-failed-processing"></a>Le traitement du décodeur AS2 a échoué car le MDN a indiqué que le traitement du message AS2 a échoué.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderMdnProcessingFailureReturned|  
|Texte du message|Le traitement du décodeur AS2, car le MDN a indiqué que le message AS2 le traitement a échoué.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que la réponse MDN signale que le destinataire du message AS2 original n'a pas pu traiter le message AS2 original.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, contactez le destinataire du message AS2, déterminez la raison de l'échec du traitement à son niveau, réparez le message AS2 original, puis renvoyez-le.