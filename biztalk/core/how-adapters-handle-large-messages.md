---
title: "Comment gérer les Messages volumineux adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c48671fd-b6cf-4507-92b4-35a4cd135714
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fccfd1e988dc1395f14d6eb92a980ede184d0e0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-adapters-handle-large-messages"></a>Comment les adaptateurs de traiter les Messages volumineux
Le moteur de messagerie BizTalk peut traiter des messages très volumineux et n'impose aucune restriction quant à la taille maximale d'un message. Vous devez cependant envisager de limiter la taille des messages pour garantir des performances et une gestion des ressources optimales. Plus la taille des messages est importante, plus le nombre de messages traités par seconde diminue. Prenez en compte la taille moyenne des messages, le type de message et le nombre de messages traités par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de la conception de votre scénario et de la planification de la capacité.  
  
## <a name="stream-based-processing"></a>Traitement basé sur un flux de données  
 Il est important de tenir compte du traitement des messages volumineux lors du développement des adaptateurs. Il est fortement déconseillé de charger l'intégralité du flux de données dans la mémoire indépendamment de sa taille, car ceci risque de causer l'arrêt du processus BizTalk Server. Selon la taille et le nombre des messages traités par le moteur à un instant donné, un problème de mémoire virtuelle insuffisante peut se produire. Les messages doivent plutôt être traités en flux continu comme indiqué ci-dessous :  
  
-   **Messages entrants.** pour les messages entrants, le flux réseau est lié au message BizTalk par l'adaptateur de réception, l'« extraction » du flux étant assurée par le moteur de messagerie BizTalk.  
  
-   **Messages sortants.** pour les messages sortants, l'adaptateur assure l'extraction du flux. Le flux est effectivement extrait de la base de données MessageBox et passe par le pipeline d'envoi. L'adaptateur doit transférer les données sur le réseau en un flux continu.  
  
 L'illustration suivante représente le traitement basé sur le flux sur le côté réception du moteur de messagerie.  
  
 ![](../core/media/streambasedprocessing.gif "Streambasedprocessing")  
  
 Lorsqu'un adaptateur envoie un message au moteur, il doit lier son flux de données au message BizTalk. Pour certains adaptateurs, cela peut signifier l'implémentation d'un flux réseau. Lorsque le message est envoyé, le moteur exécute le pipeline de réception. Lors de l'exécution du pipeline, les composants de pipeline qui veulent modifier les données clonent le message, en raccordant le flux provenant du nouveau message au flux du message précédent. Une fois le pipeline exécuté, le moteur de messagerie extrait un message du pipeline et exécute une boucle en lisant le flux de ce message. Cette lecture du flux appelle une lecture sur le flux précédent, qui à son tour appelle une lecture sur le flux précédent, et ainsi de suite jusqu'au flux réseau. Le moteur purge régulièrement les données transmises à la base de données MessageBox pour garantir une gestion linéaire de la mémoire (« flat memory model »).  
  
 **Conseil de dépannage :** côté envoi, l’adaptateur est responsable de la lecture du flux. Si l'adaptateur d'envoi veut lire des propriétés de contexte de message qui sont promues ou écrites dans le pipeline d'envoi, ces propriétés risquent de ne pas être écrites tant que l'intégralité du flux n'a pas été lue. C'est seulement une fois que le flux a été intégralement lu que l'adaptateur peut avoir l'assurance que tous les composants de pipeline ont été exécutés.  
  
## <a name="locating-a-specific-byte-in-the-stream"></a>Recherche d'un octet spécifique dans le flux  
 Dans certains cas, un adaptateur peut avoir besoin de rechercher le flux en remontant jusqu'à son début pour traiter des messages dont la transmission a échoué et qui doivent être suspendus. Il peut s'agir, par exemple, d'un adaptateur HTTP qui reçoit des données en utilisant un codage mémorisé en boc pour envoyer le message de réponse dans une paire sollicitation-réponse.  
  
 Toutefois, dans un grand nombre de cas, vous risquez de ne pas pouvoir réaliser le suivi du flux de données. Par exemple, considérons un adaptateur HTTP qui reçoit les données avec un codage mémorisé en bloc. Pour que le flux de données soit conçu de manière à vous permettre de trouver les messages en échec, l'adaptateur devrait mettre les données en cache à mesure qu'il les lit, dans la mémoire ou sur disque. Cette méthode ne semble évidemment pas optimale et requiert des ressources supplémentaires. De plus, un grand nombre de composants de pipeline standard fonctionnent selon un mode de transmission continue vers l'avant uniquement. Pour ces scénarios, l’adaptateur BaseAdapter du Kit de développement logiciel utilise une classe helper appelée **VirtualStream**. Le fichier contenant cette fonctionnalité se nomme VirtualStream.cs.  
  
> [!NOTE]
>  Le fichier VirtualStream.cs est situé à deux emplacements sous Pipelines SDK Samples : SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler et SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.  
  
 Le principe du flux virtuel est que les données du flux sont mises en cache dans un flux de mémoire jusqu'à ce qu'elles atteignent un seuil déterminé au-delà duquel les données en excédent sont transférées vers un emplacement sécurisé sur le disque. Après la fermeture du flux, le fichier disque est automatiquement supprimé. Les flux vers l'avant uniquement peuvent être conçus de cette manière.