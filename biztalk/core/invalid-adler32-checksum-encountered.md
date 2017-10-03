---
title: "De contrôle Adler32 non valide rencontré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c069e6435c3840e9a535d492943dfc3956a513f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-adler32-checksum-encountered"></a>Total de contrôle Adler32 non valide rencontré
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|InvalidAdler32ChecksumInCompressedMessageError|  
|Texte du message|Total de contrôle Adler32 non valide rencontré|  
  
## <a name="explanation"></a>Explication  
 Cette erreur fait référence à la structure ASN.1 des données compressées. Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L’utilisation de **de contrôle Adler32 non valide rencontré** indique une probabilité élevée de falsification. Recherchez toute falsification si vous voyez **de contrôle Adler32 non valide rencontré**.