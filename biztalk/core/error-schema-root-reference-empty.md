---
title: "Erreur : référence de racine du schéma vide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.rootRefEmpty
ms.assetid: 172e6ad8-6118-40db-9451-92808a3a2051
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7217f6f9ea328aff4864cfdf3bee9ea71de3741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-root-reference-empty"></a>Erreur : référence de racine du schéma vide
**Code d’erreur**  
  
 BEC2005  
  
 **Explication**  
  
 Le **référence de racine** propriété de la **schéma** nœud n’est pas défini. Lorsque le **Standard** propriété de la **schéma** nœud a une valeur autre que **XML**, vous devez définir le **référence de racine** propriété indiquer quel nœud enfant de la **schéma** nœud est destiné à être utilisé en tant que la racine du message défini par ce schéma.  
  
 **Action de l’utilisateur**  
  
 Comme il convient pour votre schéma, soit définir la **Standard** propriété de la **schéma** nœud **XML**, ou définir le **référence de racine** propriété de la **schéma** nœud vers le nœud enfant approprié de la **schéma** nœud. Les nœuds enfants sont disponibles dans le **référence de racine** liste de propriétés de liste déroulante.