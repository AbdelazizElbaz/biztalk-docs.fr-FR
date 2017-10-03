---
title: "Réglage des seuils de limitation : Quand et pourquoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9afb26c8-e5f4-4b78-9a45-a1263e3cb6ab
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b49ae78d4b2d0cf2dabfc69af9023b1e8676dea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adjusting-throttling-thresholds-when-and-why"></a>Réglage des seuils de limitation : Quand et pourquoi
En matière de limitation, une seule taille ne convient pas nécessairement pour tous les cas de figure. Un grand nombre de facteurs déterminent les paramètres optimaux. Prêt à l'emploi, BizTalk Server fournit des valeurs par défaut qui ont été éprouvées par test afin de protéger efficacement un système contre l'accumulation des messages notamment. Toutefois, cela peut s'avérer trop agressif pour certains scénarios. Les exemples suivants illustrent cet aspect :  
  
## <a name="example-1-peak-loads-and-database-size"></a>Exemple 1 : Pics et taille de la base de données  
 Chaque solution basée sur BizTalk Server a un débit maximal acceptable. Tant que la charge est inférieure à ce niveau, le système la traite indéfiniment, par définition. En pratique, cependant, il est plus fréquent d'avoir des pics et des creux dans le profil de charge qu'une charge stable qui ne varie pas sur le temps.  
  
 Plutôt que de concevoir un système capable de traiter les pics les plus élevés indéfiniment, il est plus rentable d'en développer un qui peut traiter les messages accumulés en phase de pic, et récupérer en phase de creux. Cependant, si le nombre attendu de messages accumulés pendant les pics est supérieur à la valeur de limitation par défaut de la taille de base de données, le système bloque l'accumulation en limitant les entrées. Si cela n'est pas souhaitable, parce que vous devez, par exemple, utiliser l'ensemble des fichiers d'entrée le plus rapidement possible, la solution consiste à augmenter le seuil de taille de base de données afin d'accepter le nombre attendu de messages accumulés avant la limitation.  
  
## <a name="example-2-memory-usage-optimization"></a>Exemple 2 : Optimisation de l’utilisation de mémoire  
 Une autre ressource utilisée par la limitation pour évaluer la vitesse de traitement consiste à mesurer la disponibilité de la mémoire pour les processus hôtes. Si la mémoire disponible est trop faible par rapport au seuil, la limitation ralentit le nombre de messages que le moteur extrait des files d'attente hôtes à traiter. En raison de la variabilité de la quantité et de la disponibilité de mémoire des serveurs d'entreprise actuels, en particulier avec la prise en charge x64 dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il peut s'avérer nécessaire d'augmenter ou d'abaisser ce seuil afin d'optimiser l'utilisation de la mémoire.  
  
## <a name="recommendation"></a>Recommandation  
 La limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est configurée par défaut pour fournir une protection intégrée satisfaisante du système. Cependant, les paramètres par défaut ne doivent pas être considérés comme optimaux. Analysez les états de limitation sur les compteurs de performance afin de vérifier si la limitation a lieu, puis évaluez si la ressource sur laquelle la limitation est basée (par exemple, taille de base de données ou utilisation de la mémoire) est sous ou surutilisée, puis ajustez les seuils de limitation en fonction.