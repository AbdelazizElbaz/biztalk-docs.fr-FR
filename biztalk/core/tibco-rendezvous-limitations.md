---
title: TIBCO Rendezvous Limitations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TIBCO Rendezvous, limitations
ms.assetid: 8e210457-2887-43f9-a249-be1daa6ee4eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717188e42450d13dee92364cd9c673aaaf48eaf6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-limitations"></a>Restrictions en relation avec TIBCO Rendezvous
Dans TIBCO Rendezvous, l'unicité des noms de champ n'est pas garantie. Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.  
  
 Les autres limitations suivantes s'appliquent :  
  
-   Il n'est pas possible de classer/trier les champs.  
  
-   Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés. L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.  
  
-   La connexion sécurisée aux démons n'est pas prise en charge.  
  
-   Les types de données personnalisés ne sont pas pris en charge.  
  
-   La messagerie certifiée n'est pas prise en charge du côté transmetteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)