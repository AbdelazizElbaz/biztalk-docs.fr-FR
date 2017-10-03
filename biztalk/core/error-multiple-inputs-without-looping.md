---
title: "Erreur : plusieurs entrées sans bouclage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.multipleInputsWithoutLooping
ms.assetid: 7e55ad22-06a8-4a56-839d-a30b82819a68
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a8a11b25c3c1df52827bdbf4098f0cd37bdd8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-inputs-without-looping"></a>Erreur : plusieurs entrées sans bouclage
**Code d’erreur**  
  
 btm1004  
  
 **Explication**  
  
 Plusieurs liens sont connectés au nœud indiqué dans le schéma de destination, qui est valide uniquement lorsqu’un des nœuds ancêtres du nœud indiqué est connecté à un **bouclage** fonctoid.  
  
 **Action de l’utilisateur**  
  
 Supprimez tous les liens, sauf un, associés au nœud indiqué dans le schéma de destination ou connectez l'un des nœuds de niveau supérieur du nœud indiqué à un fonctoid de bouclage.