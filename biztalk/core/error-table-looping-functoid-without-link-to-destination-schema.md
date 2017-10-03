---
title: "Erreur : fonctoid sans lien vers le schéma de Destination de bouclage de Table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.tableLoopingNoLinkToDestSchema
ms.assetid: cf162e6a-5c61-4adc-978b-af641db67ed2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329e6670288f05382acf0ea014ba9ae84c4cb645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---table-looping-functoid-without-link-to-destination-schema"></a>Erreur : fonctoid sans lien vers le schéma de Destination de bouclage de Table
**Code d’erreur**  
  
 btm1077  
  
 **Explication**  
  
 Contrairement à la plupart des fonctoids, la **bouclage de Table** fonctoid possède plusieurs sorties. Toutes sauf une de ces sorties doivent être connecté en tant que le premier paramètre d’entrée pour séparer les instances de la **extracteur de Table** fonctoid. La sortie restante doit être connectée à un **enregistrement** nœud (avec les paramètres de périodicité appropriés) dans le schéma de destination. Cette erreur se produit lorsque ce lien de sortie une **bouclage de Table** n’existe pas.  
  
 **Action de l’utilisateur**  
  
 Faites glisser le fonctoid **bouclage de Table** enregistrement approprié **enregistrement** nœud dans le schéma de destination pour créer le lien manquant.