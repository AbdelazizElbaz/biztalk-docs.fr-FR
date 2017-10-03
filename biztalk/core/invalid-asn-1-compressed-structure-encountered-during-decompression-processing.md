---
title: "Structure durant la décompression compressée ASN.1 non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e5ebbd6-249a-4746-8ee6-cfb1f52ecc94
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825889d3379a4cbc1dc61bc688eb5ffc28745a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-asn1-compressed-structure-encountered-during-decompression-processing"></a>Structure compressée ASN.1 non valide lors de la décompression
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|InvalidASN1CompressedStructureEncountered|  
|Texte du message|En-tête compressé ASN.1 non valide ou manquant lors de la décompression|  
  
## <a name="explanation"></a>Explication  
 Cette erreur fait référence à la structure ASN.1 des données compressées. Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Passez en revue la structure des données compressées et recherchez toute falsification du message.