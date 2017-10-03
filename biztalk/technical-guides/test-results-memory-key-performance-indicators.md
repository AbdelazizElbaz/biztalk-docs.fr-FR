---
title: "Résultats des tests : Indicateurs de Performance clés de mémoire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 224c40e5-08a7-4d30-b03a-4b6add5cde1f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4edf88023ee9e30e7fd0c808346b6231112f8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-results-memory-key-performance-indicators"></a>Résultats des tests : Indicateurs de Performance clés de mémoire
Cette rubrique résume la mémoire performances indicateurs clés (KPI) observé sur les scénarios de test. Ces tests évaluée la mémoire disponible en tant que mesurée par le **\Memory\Available Mo** compteur Perfmon.  
  
## <a name="summary-of-memory-key-performance-indicators"></a>Résumé des indicateurs de Performance clés de mémoire  
 **Comparaison des indicateurs de Performance clé mémoire –** mémoire totale disponible pour SQL Server et BizTalk Server, telle que mesurée par le **\Memory\Available Mo** compteur Analyseur de performances a été relativement homogène pour tous les scénarios de test. La différence dans la mémoire moyenne disponible pour les ordinateurs physiques de BizTalk Server et la moyenne de la mémoire disponible pour les ordinateurs BizTalk Server en cours d’exécution sur des ordinateurs virtuels est dû au fait que deux ordinateurs physiques de BizTalk Server ont été utilisés pour le test lors de trois ordinateurs BizTalk Server en cours d’exécution sur des machines virtuelles ont été utilisés pour le test.  
  
 Le graphique ci-dessous illustre les performances de la mémoire sur les différentes plateformes de test :  
  
 ![Indicateurs de Performance clés mémoire](../technical-guides/media/memorykpi.gif "MemoryKPI")  
  
 Le tableau ci-dessous illustre les performances relatives de l’indicateur collectées pour chaque configuration. Chaque jeu de résultats est calculée en pourcentage de la configuration de base indicateur de performance clé  
  
|Indicateur de performance clé|Virtuel BizTalk/physiques SQL|Virtuel BizTalk/virtuel SQL sur des hôtes distincts|Virtuel SQL BizTalk/virtuel dans l’environnement de consolidé|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|Mémoire SQL Server disponible (Mo) par serveur|100.1%|97.1%|103.2%|  
|BizTalk totale de mémoire disponible (Mo)|88.3%|95.9%|96%|  
|Moyenne par serveur / BizTalk de mémoire disponible (Mo)|58.9%|63.9%|64%|  
  
 Pour plus d’informations sur la façon d’évaluer les performances de la mémoire, consultez le **mesure les performances de mémoire** section de la rubrique [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).