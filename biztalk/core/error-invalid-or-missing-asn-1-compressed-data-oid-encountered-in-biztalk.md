---
title: "Non valide ou manquante compressé données OID ASN.1 rencontré lors du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0171daa8-289a-43f1-8cbf-d779ef9dc2ea
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05af1fc0c9f6516f180cf629cd0a21d838f0b4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-asn1-compressed-data-oid-encountered-during-decompression-processing"></a>OID de données compressées ASN.1 non valide ou manquant lors de la décompression.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|OID de données compressées ASN.1 non valide ou manquant lors de la décompression.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur fait référence à la structure ASN.1 des données compressées. Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Passez en revue la structure des données compressées et recherchez toute falsification du message.