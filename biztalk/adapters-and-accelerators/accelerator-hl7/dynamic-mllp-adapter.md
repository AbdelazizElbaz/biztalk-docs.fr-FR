---
title: Adaptateur dynamique MLLP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e22fabb-0edf-4931-b8b2-74a5daccee4a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7d1d7046135de1dc1837d1fb8961ef440b5009
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-mllp-adapter"></a>Adaptateur MLLP dynamique
En commençant par [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], les propriétés de l’adaptateur MLLP peuvent être configurées lors de l’exécution à l’aide d’un port d’envoi unidirectionnel ou bidirectionnel (requête-réponse).  
  
## <a name="dynamic-properties"></a>Propriétés dynamiques  
 Les propriétés suivantes sont dans le **GlobalPropertySchemas** espace de noms :  
  
|Propriété| Description|  
|--------------|-----------------|  
|Message (MLLP.acceptableACKCodes) = « Tous les Codes de l’accusé de réception » ;|Ces valeurs comprennent :<br /><br /> -Tous les Codes de l’accusé de réception<br />-AA et l’autorité de certification<br />-AA, l’autorité de certification, AE et CE<br />-AA, l’autorité de certification, AR et CR<br /><br /> Ceci est similaire à la **les Codes de l’accusé de réception Acceptable** propriété dans un Port d’envoi statique MLLP.|  
|Message (MLLP. CarriageReturn) = « 0D » ;|Caractère de retour chariot ASCII|  
|Message (MLLP.endBlockDelimiter) = « 1c » ;|Caractère de fin de bloc ASCII|  
|Message (MLLP.startBlockDelimiter) = 0 « b » ;|Caractère de début de bloc ASCII|  
|Message (MLLP.timeout) = « 60000 » ;|Compter le socket émetteur inactive sur le serveur BTAHL7 arrive à expiration (0 ne correspond à aucun délai d’expiration)|  
|SendPortName(Microsoft.XLANGs.BaseTypes.Address) = « 127.0.0.1:11000 » ;|Adresse et Port pour le routage du message|  
|SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = « MLLP » ;|Type d’adaptateur (MLLP)|  
  
## <a name="additional"></a>Supplément  
  
-   Lorsque vous créez un message à parties multiples dans une orchestration pour HL7, créez les parties de message dans cet ordre :  
  
    1.  Segment de MSH  
  
    2.  BodySegments  
  
    3.  ZSegments  
  
     Si vous spécifiez les parties de message dans un ordre différent, l’erreur suivante se produit :  
  
     WrongBodyPartException  
  
-   Les propriétés de l’itinéraire adaptateur peuvent être spécifiées sur l’orchestration pour prendre en charge le routage dynamique.  
  
## <a name="see-also"></a>Voir aussi  
 [Les paramètres de configuration pour l’envoi et les adaptateurs de réception](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [Traitement de l’adaptateur de réception de MLLP](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [Traitement d’adaptateur MLLP envoi](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)