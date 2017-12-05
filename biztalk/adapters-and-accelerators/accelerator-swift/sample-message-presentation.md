---
title: "Exemple de Message présentation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, SWIFT message block
- SWIFT messages, message block example
ms.assetid: 3136a7da-658d-4100-bbe5-2186ee8bafd1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8a3d03e35f6184e6aed6ba4af71e01a9b65e342
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sample-message-presentation"></a>Exemple de présentation de Message
Le tableau suivant montre un exemple de disposition de bloc d’un message SWIFT.  
  
|Block|Exemple|  
|-----------|-------------|  
|**Bloc 1** en-tête de base|{1:F01BCITITMMAXXX0012000123}|  
|**Bloc 2** (I) Application en-tête entrée (SWIFT)<br /><br /> Ou<br /><br /> **Bloc 2** en-tête sortie de l’Application (O) (à partir de SWIFT)|{2:I103VBOEATWWXXXXN} Ou {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3|  
|**Bloc 3** en-tête de l’utilisateur|{3 : {108:BCITITMMA950906}}|  
|**Bloquer les 4** texte|{4 :\<CRLF\> : 20:1234567890\<CRLF\> : 23B:CRED\<CRLF\> : 32A:010605GBP45000,\<CRLF\> : 33B:GBP45000,\<CRLF\> : 50K:MASTERS IMPORTATION\<CRLF\> RUE DES ARBRES 119\<CRLF\> CAMBRAI\<CRLF\> : 52A:BNPAFRPPCAM\<CRLF\> : 53 BIS : POCIITMM680\<CRLF\> : 57A:BCITITMM680\<CRLF\> : 59 : / P03452032022819 30\<CRLF\> IMPORTATION GÉNÉRAL\<CRLF\> PESCARA\< CRLF\> : 70 : RFB/INVENTAIRE 5591\<CRLF\> : 71A:SHA\<CRLF\> -}|  
|**Bloquer 5** codes de fin|{5 : {MAC : 12345678} {CHK:123456789ABC}}|  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-schemas.md)