---
title: "Analyse de la Solution gestion des processus d’entreprise avec BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, monitoring
- monitoring, process management solutions
ms.assetid: 7c5fde9d-6eef-41c9-979c-ac7e5a172812
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26a8b795b90b75518f6c1ec21a6ca6d8f0f0d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-business-process-management-solution-with-bam"></a>Surveillance de la solution de gestion des processus d'entreprise à l'aide de l'analyse BAM
La solution contrôle les étapes de traitement des commandes à l'aide de l'API BAM (Business Activity Monitoring). Le processus d'entreprise fractionne les activités en plusieurs étapes. Les activités peuvent être recombinées pour créer une impression de processus continu. L'analyse BAM fournit également des données agrégées qui vous informent de la durée des systèmes principaux, du nombre de commandes exécutées et d'autres informations semblables.  
  
 Comme la solution orientée services, il utilise le nouveau **OrchestrationEventStream** objet. Pour en savoir plus sur les **OrchestrationEventStream** d’objets, consultez « Quel est l’objet OrchestrationEventStream » dans [analyse la Solution orientée services avec BAM](../core/monitoring-the-service-oriented-solution-with-bam.md).  
  
 Pour obtenir des informations générales sur l’analyse BAM, consultez [à l’aide de l’analyse BAM](../core/using-business-activity-monitoring.md). Pour plus d’informations sur l’éditeur de profil de suivi (TPE), consultez [éditeur](../core/tracking-profile-editor.md).  
  
## <a name="wrapping-the-orchestrationeventstream-object"></a>Classe enveloppante de l'objet OrchestrationEventStream  
 Comme la solution orientée services, la solution de gestion des processus métier encapsule le **OrchestrationEventStream** objet. Par ailleurs, toutes les méthodes sont statiques de sorte que les orchestrations n'ont pas besoin de créer des instances des objets pour utiliser les méthodes. Ainsi, les objets utilisés dans le cadre du suivi n'ont pas besoin d'être sérialisés ou enregistrés si le moteur met une orchestration en attente. La solution gestion des processus d’entreprise, toutefois encapsule **OrchestrationEventStream** avec plusieurs objets dérivés d’un seul objet abstrait.  
  
 La classe abstraite est **BasicActivity**. Bien qu'elle soit abstraite, elle ne sert pas vraiment de modèle pour les classes dérivées. Elle fournit plutôt, via ses méthodes statiques, un ensemble de méthodes disponibles sans qualification dans une classe dérivée. Ceci vous offre quatre implémentations par défaut des méthodes. Les quatre méthodes statiques sont : **CreateActivityId**, **BeginActivity**, **UpdateActivity**, et **EndActivity**.  
  
 Les surcharges de la classe le **BeginActivity** (méthode). Une de ses versions récupère un nom d'activité en tant qu'argument unique, crée un GUID à utiliser comme identificateur d'activité, puis appelle sa version qui récupère un nom d'activité et un identificateur d'activité, avant de renvoyer l'identificateur d'activité. Cette version d'argument unique est utile lorsqu'une commande peut avoir plusieurs identificateurs.  
  
 Le **CreateActivityId** méthode prend une chaîne et un identificateur unique tel que l’identificateur de la demande et retourne une chaîne avec un trait de soulignement. Cette méthode, abondamment utilisée dans les classes dérivées, fournit un identificateur d'activité unique. Le **BeginActivity**, **UpdateActivity**, et **EndActivity** appel de méthodes le **Beginactivity**, **UpdateActivity** , et **EndActivity** méthodes de **OrchestrationEventStream**.  
  
 La solution dérive les classes de **BasicActivity** pour le courtier de commandes (**CustomerOrderRequest**), Gestionnaire de commandes (**OrderManager**) et les étapes de traitement ( **ServiceOrderRequest**). Les classes individuelles correspondent à une activité. Chaque classe fournit une chaîne pour le nom de l’activité à utiliser dans **CreateActivityId** pour créer l’activité identificateur, ainsi que des méthodes spécialisées pour les étapes majeures d’activité.  
  
 Comme le courtier de commandes remet la commande avant de recevoir une réponse , il inclut une méthode permettant de récupérer l'identificateur d'activité donné à l'identificateur de requête de la commande. Ceci permet au processus d'entreprise de continuer à suivre les derniers éléments du traitement de la commande.  
  
> [!NOTE]
>  Si vous transmettez des commandes via la fonction de fichier plutôt que l'application Web Service clientèle, vous devez ajouter un identificateur unique à chaque requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’une Solution de gestion des processus métiers](../core/developing-a-business-process-management-solution.md)