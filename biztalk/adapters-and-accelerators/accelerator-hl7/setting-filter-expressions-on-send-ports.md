---
title: "Définition des Expressions de filtre sur les Ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, context properties
- filtering, send ports
- send ports, filtering
- context properties, send ports
- context properties, filtering
- filtering, context properties
ms.assetid: 48c7c83b-9464-4ed9-bd8d-cf5b75e16702
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b94497f4e1412f81c36df3195994aafa32ecc451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-filter-expressions-on-send-ports"></a>Définition d’Expressions de filtre sur les Ports d’envoi
Vous définissez des propriétés de contexte dans les expressions de filtre sur le port d’envoi pour contrôler ce que le port envoie. Vous pouvez définir les expressions de filtre avec un nombre d’opérateurs qui vous offrent une grande souplesse dans la façon dont vous filtrez de la propriété (égalité ou inégalité, existe, supérieur à, supérieur ou égal à, inférieur à et inférieur ou égal à).  
  
### <a name="to-set-the-filter-expression-on-a-send-port"></a>Pour définir l’expression de filtre sur un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** (ou une autre application). Cliquez sur **Ports d’envoi**.  
  
2.  Cliquez sur le port d’envoi que vous souhaitez définir pour l’expression de filtre, puis cliquez sur **propriétés**.  
  
3.  Dans l’arborescence de la boîte de dialogue Propriétés de Port d’envoi, cliquez sur **filtres**.  
  
4.  Cliquez sur la zone de texte dans le **propriété** colonne, puis sélectionnez la propriété de contexte à partir de la **propriété** liste déroulante.  
  
5.  Cliquez sur le **opérateur** dans la ligne de la propriété et sélectionnez l’opérateur pour la propriété dans la liste déroulante.  
  
6.  Cliquez sur le **valeur** dans la ligne de la propriété, puis tapez une expression de valeur.  
  
7.  Si vous devez ajouter une autre clause de l’expression de filtre, cliquez sur le **Group By** dans la ligne de la propriété et sélectionnez **et** ou **ou** pour déterminer la relation entre le clauses.  
  
8.  Répétez les étapes 4 à 6 pour ajouter une autre clause de filtre.  
  
9. Vérifiez que l’expression de filtre est correcte dans le volet du bas de la **filtres** volet.  
  
10. Lorsque vous avez ajouté toutes les clauses de filtre, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [À l’aide des propriétés de contexte](../../adapters-and-accelerators/accelerator-hl7/using-context-properties.md)