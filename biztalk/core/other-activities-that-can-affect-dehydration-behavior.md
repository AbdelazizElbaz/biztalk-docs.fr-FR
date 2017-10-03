---
title: "Autres activités qui peuvent affecter le comportement de mise en attente | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed940448-d3b1-4308-9b38-887904e03bd0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4622c77876607664b210de2581929154973b45d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="other-activities-that-can-affect-dehydration-behavior"></a>Autres activités susceptibles d'affecter la mise en attente
Les activités ci-dessous ont un impact direct ou indirect sur la mise en attente et les performances globales du système. Elles doivent donc être prises en compte dans les scénarios de test.  
  
-   **Requêtes de la Console Administration de BizTalk Server.** Ces requêtes consomment des ressources et affectent le débit global, dans des proportions qui dépendent du type et de la fréquence des requêtes.  
  
-   **Sauvegarde, l’archivage et la purge des activités.** Ces activités consomment également des ressources et doivent être prises en compte dans les scénarios de test.  
  
-   **Hôtes 32 bits et 64 bits mixtes.** Veuillez prendre les éléments suivants en compte lorsque vous utilisez des hôtes 32 bits et 64 bits mixtes :  
  
    -   Dans des situations de forte charge, nous mesurons la mémoire virtuelle et physique consommée et nous la comparons à des seuils donnés. Dans les systèmes 64 bits, le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise plus de mémoire. La stratégie de mise en attente est donc différente de celle des systèmes 32 bits présentant le même système et les mêmes valeurs par défaut. Veillez donc à séparer les hôtes d'orchestration, de réception, d'envoi et de boîtes de message.  
  
         La différence n'est pas aussi visible lorsque vous utilisez les seuils 32 bits par défaut sur les systèmes 64 bits, tant que seul l'hôte d'orchestration figure sur la boîte 64 bits. Toutefois, les différents contrainte sous **MemoryThrottlingCriteria** paramètres doivent être au moins doublés ou trois fois (tant que vous disposez de suffisamment de mémoire), mais le scénario doit être réglé pour optimiser le débit car il existe de nombreux facteurs qui entrent en jeu. Vous devez adapter les seuils de mise en attente en cas de forte charge de façon à trouver le réglage optimal.  
  
    -   Le comportement lié à la mise en attente dépend de l'historique des délais de remise de chaque abonnement. Les historiques peuvent être différents pour les divers abonnements. Pensez-y lorsque vous définissez les valeurs des propriétés de mise en attente.  
  
    -   Lorsque le service de l'hôte d'orchestration est recyclé sur un hôte mais pas sur un autre, les historiques sont différents.  
  
    -   Lorsque les serveurs utilisent des versions différentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ils présentent des stratégies de mise en attente différentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)