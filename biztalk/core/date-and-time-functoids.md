---
title: Fonctoids date et heure | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e2d49f5-1aaf-4e4d-8da1-e8605304dccb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ec31607ecefb417fef597b5ba700e6461c71a2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="date-and-time-functoids"></a>Fonctoids Date et heure

## <a name="overview"></a>Vue d'ensemble
**Date / heure** fonctoids peuvent être divisés en deux catégories. La première catégorie contient un seul fonctoid, **ajouter des jours**, ce qui permet d’ajouter un nombre de jours spécifié à une date et une valeur d’heure. C'est particulièrement utile lorsqu'un champ d'un message d'instance de sortie est censé comporter une estimation de date et d’heure futures. Par exemple, le **ajouter des jours** fonctoid peut être utilisé pour générer une estimation date d’expédition en fonction un delta fixe à partir de la date à laquelle une commande a été reçue.  
  
 La seconde catégorie comprend tous les autres fonctoids dans le **Date et heure** catégorie. Ils sont utilisés pour fournir un horodatage au moment de l’exécution, de sorte que la date et l'heure auxquelles la transformation du message est exécutée peuvent être intégrées au message d'instance de sortie.  
  
 Le **ajouter des jours** fonctoid accepte deux paramètres d’entrée, alors que le **Date**, **Date et heure**, et **temps** fonctoids n’ont aucune entrée. paramètres.  

## <a name="available-functoids"></a>Fonctoids disponibles  
 Le **Date / heure** fonctoids sont : 

* Ajouter des jours
* Date
* Date et heure
* Time

Plus de détails sur ces fonctoids **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **Référence des fonctoids date et heure**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]