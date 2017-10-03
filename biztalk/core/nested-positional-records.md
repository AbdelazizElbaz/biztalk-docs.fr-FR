---
title: "Imbriqué enregistrements positionnels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e205e9d-f740-4177-b45a-5e1baadae99a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c278d3ac794c560d8cd886605c1d04c097793564
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-records"></a>Enregistrements positionnels imbriqués
Les enregistrements positionnels imbriqués sont autorisés si le **Max Occurs** des enregistrements enfants est définie sur un nombre entier positif. Le calcul automatique de champ doit être en mesure de gérer la nouvelle profondeur. Toutefois, son comportement est modifié. Concrètement, en raison de la possibilité d’appliquer des délimiteurs NULL, le calcul automatique des positions de champ ne fonctionne que si l'une des conditions suivantes est remplie :  
  
-   Le nœud sélectionné possède un parent qui est délimité par un infix.  
  
-   Le nœud sélectionné possède une position de départ spécifiée.  
  
 Notez qu'il existe une distinction entre les enregistrements positionnels imbriqués et les enregistrements positionnels dont le parent est un conteneur délimité pour lequel le délimiteur est null. Pour que les structures soient réellement positionnées de façon imbriquée, il ne doit subsister aucune ambiguïté en ce qui concerne leur longueur. Par exemple, un nœud de boucle délimité peut contenir un enregistrement positionnel à répétition se produisant entre 0 et N fois. Toutefois, pour que le nœud de boucle lui même soit positionnel, et contienne éventuellement aussi des champs en tant qu'homologues de l'enregistrement positionnel à répétition, l'occurrence de l'enregistrement positionnel à répétition doit être déterministe (un entier positif).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations concernant les enregistrements positionnels](../core/positional-record-considerations.md)