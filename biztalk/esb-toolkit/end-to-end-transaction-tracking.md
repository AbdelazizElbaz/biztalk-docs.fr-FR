---
title: Suivi de bout en bout Transaction | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebacd2e4-6b5c-4dc4-8361-b5b77042debc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffa49372c54dc526f45e04317e002604ac0914d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-transaction-tracking"></a>Suivi de la Transaction de bout en bout
Visibilité de l’entreprise par rapport à la possibilité de contrôler le flux de trafic via l’environnement d’exécution des opérateurs et des utilisateurs. Les entreprises doivent être en mesure de suivre les processus et les transactions transitant via leurs systèmes à chaque étape pour vous assurer qu’ils jouent leurs à contribuer à la génération de revenus. AmberPoint SMS simplifie la mesure et le suivi de ces messages dans Microsoft BizTalk Server. Le système permet aux utilisateurs de définir de nouvelles unités de gestion qui s’alignent sur les flux de processus d’entreprise de bout en bout, au lieu de se conformer à la façon dont les développeurs choisi pour empaqueter et déployer des composants de service individuels. La figure 1 illustre l’écran pour définir les unités de gestion.  
  
 ![Définition de Transaction de BizTalk](../esb-toolkit/media/ch9-biztalkdefiningtransaction.gif "Ch9-BizTalkDefiningTransaction")  
  
 **Figure 1**  
  
 **Définition d’une transaction comme une nouvelle unité de gestion**  
  
 Après avoir défini les transactions, les utilisateurs peuvent instrumenter et suivre les messages associés à chaque transaction en utilisant les mêmes outils qui fournissent une visibilité en un seul service. Ces outils peuvent exposer les métriques de performances, surveiller les performances par rapport aux contrats de niveau de service et générer des journaux de messages, comme illustré dans la Figure 2.  
  
 ![Analyse de BizTalk](../esb-toolkit/media/ch9-biztalkmonitoring.gif "Ch9-BizTalkMonitoring")  
  
 **Figure 2**  
  
 **Analyse des performances de bout en bout d’un pipeline**  
  
 Une condition requise pour la gouvernance de l’exécution réussie et la surveillance du système est la détection d’événements commerciaux importants, tels que les exceptions et erreurs d’application risquent de perturber le traitement de logique métier de flux de transaction. AmberPoint SMS permet d’opérateurs et utilisateurs d’obtenir un éclairage opérationnel et des événements commerciaux et surveiller l’impact de ces événements sur tous les composants qui dépendent du service qui a généré le problème. En outre, les opérateurs et les utilisateurs peuvent résoudre rapidement les l’ensemble du système pour identifier la cause d’un problème.