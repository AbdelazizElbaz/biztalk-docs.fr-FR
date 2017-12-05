---
title: Des Documents relatifs aux | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], document references
- definition files [BAM], related documents
- Query Builder [BAM portal], viewing details
- document references [BAM]
- Query Builder [BAM portal], document references
- queries [BAM], viewing details
ms.assetid: 9c5f2175-fe7c-40ec-910d-1ac5c8142045
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b87f0d31010a8bf80e09c59f05f2f9302a510e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="related-documents"></a>Documents associés
La zone Documents associés des détails des résultats de requête affiche une liste de documents de référence associés à l'activité. Il peut s'agir de documents de tout type : image CAO, fichier .WAV ou bon de commande. Par exemple, une activité Bon de commande est généralement associée à un document de base de type Bon de commande. La liste contient un lien vers le bon de commande.  
  
## <a name="adding-document-references"></a>Ajout de références de document  
 La liste des documents associés peut être générée de deux façons :  
  
-   Lorsque vous développez votre modèle de suivi, vous incluez un nœud Document Reference URL dans l'arborescence d'activité, puis le mappez à partir d'une source contenant un pointeur de référence vers le document physique.  
  
-   Votre développeur d'intégration remplit la liste à l'aide d'un programme en appelant votre application personnalisée.  
  
 Définition de la référence de document à l’aide de ces méthodes ajoute une ligne dans le \<activityname\>_References table avec l’emplacement du document.  
  
 Si aucune de ces tâches n’a été effectuée, le **Document associé** zone est vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)