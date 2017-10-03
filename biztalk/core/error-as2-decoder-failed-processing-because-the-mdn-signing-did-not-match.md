---
title: "Le décodeur AS2 a échoué car la signature du MDN ne correspondait à notre demande de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc0660a64ff0aeb35976ad1aa45a602d8db0913a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-signing-did-not-match-our-request"></a>Le traitement du décodeur AS2 a échoué car la signature du MDN ne correspondait pas à notre demande
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2DecoderMdnSigningMismatchFailureDuringProcessing|  
|Texte du message|Le traitement du décodeur AS2 a échoué car la signature du MDN ne correspondait pas à notre demande.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le MDN entrant, soit parce que ce dernier était signé par erreur, soit parce qu'il n'était pas signé alors qu'il aurait dû l'être.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
1.  Modifiez la demande de signature pour que le MDN corresponde à la demande. Pour ce faire, ouvrez la page Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés AS2, activez la propriété « Exiger le MDN » et activez ou désactivez la propriété « Exiger le MDN signé ».  
  
2.  Contactez le destinataire du message AS2 d'origine pour déterminer si les MDN doivent être signés ou non.