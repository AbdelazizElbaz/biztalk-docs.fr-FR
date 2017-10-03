---
title: Parties de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- messages, message parts
- segments, messages
ms.assetid: 2bb6557e-cd4a-42b7-8bc2-f8b53a59517e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b6b02096a0cc75460552a6cd1dd56ef9e6c4e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-parts"></a>Parties du message
Un message HL7 contienne les éléments suivants : segments, les champs de données, les composants et éventuellement sous-composants. Les messages de HL7 ont la structure hiérarchique suivante :  
  
 Segment  
  
 Champ de données  
  
 Composant  
  
 Sous-composant (facultatif)  
  
 **Segments**  
  
 Un segment est un regroupement logique des champs de données. Les segments sont au niveau plus élevé (profondeur 1) de la hiérarchie de message. Chaque segment possède un nom qui inclut une valeur littérale de trois caractères. Le tableau suivant présente des exemples de noms de segment contenus dans les types de message ADT.  
  
|Segment de code| Description|  
|------------------|-----------------|  
|MSH|En-tête de message|  
|EVN|Type d’événement|  
|PID|Informations sur les patients|  
  
 Les messages HL7 ont un *en-tête de message* et *corps*. Les segments MSH définissent l’en-tête du message et tous les autres types de segments forment le corps du message.  
  
 **Champs de données**  
  
 Un champ de données est une chaîne de caractères qui se produisent au niveau de profondeur 2 de la hiérarchie de message. Types de données définissent les champs de données : Simple et complexe.  
  
 L’exemple suivant illustre la structure de message hiérarchique des segments MSH et EVN qui contient les champs de données MSH.1 et EVN.1 :  
  
 MSH  
  
 MSH.1  
  
 EVN  
  
 EVN.1  
  
 **Composants et les sous-composants**  
  
 Composants et les sous-composants davantage contiennent les données dans les champs de données. Composants et les sous-composants peuvent répéter dans le même champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)