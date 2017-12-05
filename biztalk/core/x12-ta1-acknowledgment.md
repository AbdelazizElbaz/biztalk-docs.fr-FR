---
title: "X12 accusé de réception TA1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68568a1a-3669-46f4-8edc-8d057b012544
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6a3de45744b40335999c1471165ff851ec60664
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="x12-ta1-acknowledgment"></a>Accusé de réception X12 TA1
L'accusé de réception X12 TA1 indique l'état du traitement de l'en-tête et du code de fin d'un échange par le récepteur d'adresse. Si l'en-tête ISA et le code de fin IEA du message X12 sont valides, un accusé de réception TA1 positif est envoyé, quel que soit l'état du contenu restant. Dans le cas contraire, un accusé de réception TA1 contenant un code d'erreur est envoyé.  
  
 L’accusé de réception TA1 est conforme à la X12_ de X12\<numéro de version\>_TA1.xsd schéma. L'accusé de réception TA1 est envoyé dans une enveloppe ISA/IEA. L'en-tête ISA et le code de fin IEA sont les mêmes que ceux des autres échanges.  
  
 Les segments dans l'échange d'un accusé de réception TA1 sont indiqués dans le tableau suivant.  
  
|Champ de TA1|Nom du champ|Mappé à l'échange entrant|Valeur|  
|------------------|-------------------|------------------------------------|-----------|  
|TA101|Numéro de contrôle de l'échange|ISA13 - Numéro de contrôle de l'échange|-|  
|TA102|Date de l'échange|ISA09 - Date de l'échange|-|  
|TA103|Heure de l'échange|ISA10 - Heure de l'échange|-|  
|TA104|Code de l'accusé de réception de l'échange*|Néant|Comportement du moteur : A, E ou R<br /><br /> A = accepter<br /><br /> E = échange accepté avec des erreurs<br /><br /> R = échange rejeté/interrompu|  
|TA105|Code de note de l'échange|Néant|Code d'erreur de résultat du traitement. **Remarque :** reportez-vous au tableau dans [X12 Codes d’erreur d’accusé de réception TA1](../core/x12-ta1-acknowledgment-error-codes.md).|  
  
 \*Comportement du moteur repose sur la validation d’élément de données ; à l’exception des informations de sécurité et d’authentification, lequel sera basée comparaisons de chaînes dans les informations de configuration.