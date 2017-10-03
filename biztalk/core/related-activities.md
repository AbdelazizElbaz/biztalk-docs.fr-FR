---
title: "Activités connexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], related activities
- Query Builder [BAM portal], related activities
- queries [BAM], related activities
- Query Builder [BAM portal], viewing details
- queries [BAM], viewing details
ms.assetid: 141b7943-d244-4810-aa88-12aa4a2b7658
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fea95a74a15c685f2cff202fcf7f04c86244041b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="related-activities"></a>Activités associées
La zone Activités associées contient une liste des activités associées à l'activité sur laquelle repose la requête. Par exemple, plusieurs activités d'expédition peuvent être associées à une activité Bon de commande, car il est possible d'envoyer les éléments d'un même bon de commande par l'intermédiaire de plusieurs expéditions.  
  
## <a name="creating-related-activities"></a>Création d'activités associées  
 La liste des activités associées peut être générée de deux façons :  
  
-   Vous définissez deux activités et créez ensuite une vue les incluant toutes les deux. Votre développeur établit alors une connexion de corrélation entre les deux activités en implémentant les relations de clé, de champ et de valeur entre les activités.  
  
-   Vous définissez deux activités. Votre développeur établit une connexion de corrélation dans votre application personnalisée en appelant AddRelationship() et en définissant les relations de clé, de champ et de valeur entre les activités.  
  
 Définition des relations d’activité dans une des manières suivantes ajoute une ligne dans le \<nomactivité > _Relationships table.  
  
> [!NOTE]
>  Seule la première de ces méthodes permet aux activités associées de contenir des liens actifs les reliant les unes aux autres. La seconde méthode ne permet pas de définir une vue d'ensemble et le portail ne peut donc pas avoir connaissance de l'existence de relations entre les deux activités.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment afficher les résultats d’une recherche d’activité](../core/how-to-view-the-results-of-an-activity-search.md)