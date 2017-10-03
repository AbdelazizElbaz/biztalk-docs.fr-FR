---
title: "Suivi des événements commerciaux asynchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 6d51fadf-b329-4536-9618-d982d9c17882
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7191d9b0be94b4b089a91e78dd526867171c68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="asynchronous-business-event-tracking"></a>Suivi asynchrone des événements commerciaux
Asynchrone (à l’aide de `BufferedEventStream`)-ce modèle offre des améliorations significatives des performances. Il utilise une interface API similaire à celle du modèle synchrone mais le constructeur est différent. Au lieu d'envoyer les données vers la base de données d'importation principale, la classe BufferedEventStream conserve les données d'événements en mémoire sous forme binaire avant de les insérer sous forme d'enregistrement de table unique dans une base de données temporaire (MessageBox). Le service Bus d'événements lit les données placées dans la file d'attente de la base de données MessageBox par BizTalk, puis les importe dans la base de données d'importation principale.  
  
 Pour configurer l'analyse BAM de sorte qu'elle effectue des opérations asynchrones, le service Bus d'événements et l'application d'appel (ex. : hôte d'orchestration) doivent être exécutés sur des ordinateurs différents. Cela permet à l'application d'appel de se débarrasser des données d'événements immédiatement et de faire en sorte que ces données soient traitées par l'UC d'un autre ordinateur.  
  
 D'autre part, cette topologie BAM est cohérente avec les transactions. En effet, vous n'obtiendrez pas de données BAM pour des transactions annulées ayant réintégré l'application d'appel car le service Bus d'événements lit uniquement les données validées provenant de la base de données MessageBox. Les données BAM obtenues pour des transactions validées s'affichent avec une latence faible pour l'interrogation et l'agrégation.  
  
 Si des erreurs se produisent, le service Bus d'événements lance plusieurs tentatives en utilisant les délais d'attente, la logique de reprise sur sinistre, etc. En revanche, si le format des données n'est pas valide, ces données sont envoyées vers des tables spéciales. Un événement est reproduit dans le journal des événements afin d'indiquer ce cas de figure. Cela constitue un point de défaillance supplémentaire qui rend difficile la gestion du système.  
  
 La méthode asynchrone à partir du code est aussi simple d'utilisation qu'un remplacement de classe DirectEventStream par une classe BufferedEventStream. Il suffit de définir la chaîne de connexion pour la base de données MessageBox du constructeur au lieu de la définir pour l'importation principale BAM.  
  
 Dans votre code, tenez compte des éléments suivants relatifs au suivi asynchrone des événements commerciaux :  
  
-   Utilisez systématiquement une ligne de continuation lorsque l'activité englobe plusieurs applications et que vous envoyez des données de manière asynchrone vers le composant BAM, même si vous propagez l'ID de l'activité à tous les composants. Dans ce cas, utilisez un ID d'activité différent dans chaque application en ajoutant un préfixe sous la forme d'une chaîne unique (le nom de l'application, par exemple). Cette opération est nécessaire dans la mesure où les données des différentes applications sont susceptibles d'arriver au composant BAM dans un ordre aléatoire et que ce dernier doit gérer les événements sans tenir compte de l'ordre chronologique pour que les résultats de l'interrogation et de l'agrégation soient corrects.  
  
-   Les méthodes d'analyse des événements habituelles (modèle d'événement faiblement couplé COM+, événements WMI) ne sont pas applicables à l'analyse BAM car les données d'événements sont indépendantes des transactions. Par exemple, il peut vous sembler avoir reçu 10 bons de commande d'un total de 10 000 dollars quand il s'agit en fait d'un seul bon de commande entrant de 1 000 dollars dont la tentative d'enregistrement dans la base de données a échoué 10 fois.  
  
## <a name="see-also"></a>Voir aussi  

 [Suivi des événements commerciaux synchrone](../core/synchronous-business-event-tracking.md)