---
title: "Identification de perte des données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, HAT
- reporting tools
- Orchestration Debugger
- Tracking database, data loss
- HAT, data loss
- HAT, Operation View tool
- HAT, reporting tools
- Operation View tool, MessageBox database
- MessageBox database, Operation View tool
- Operation View tool, data loss
ms.assetid: 1ac13e2c-cd5e-437e-b924-d4547931874e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d7a61d974a51e3a811a8cce84a1e22c24a5e84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-lost-tracking-data"></a>Identification des données de suivi perdues
La console Administration de BizTalk Server permet d'identifier les données de suivi perdues à la suite d'une défaillance matérielle. Elle peut être utilisée tant pour les données actives que pour les données archivées.  
  
 Vous pouvez utiliser la console Administration de BizTalk Server pour déterminer les services qui étaient actives au moment de que la MessageBox a été récupérée. En raison de l'écart existant entre l'heure de la défaillance matérielle et l'heure de récupération de la base de données, vous ne pourrez peut-être pas déterminer l'état de certaines transactions.  
  
 Les données de suivi permettent d'identifier les instances de service terminées et celles démarrées après le point de récupération, comme suit :  
  
-   Recherchez les instances terminées et démarrées depuis la dernière sauvegarde de la base de données.  
  
-   Si les données de la base de données des suivis BizTalk (BizTalkDTADb) indiquent qu'un message démarré n'est pas terminé, et que celui-ci ne figure pas dans la base de données, cela signifie que ce message a été envoyé après la dernière sauvegarde.  
  
 Le suivi permet de répertorier les services terminés et les services démarrés. Les données de suivi sont mises en lot dans la base de données MessageBox avant d'être déplacées vers la base de données des suivis BizTalk. Les données mises en lot sont susceptibles d'être perdues dans l'accumulation des messages du service de bus d'événements BAM.  
  
 Si toutes les bases de données doivent être restaurées au niveau de la même marque pour des raisons opérationnelles, vous pouvez utiliser une base de données des suivis BizTalk (non perdue) en mode Archive pour afficher les événements postérieurs à la marque.  
  
 Si le suivi affiche une instance de service comme terminée, vous pouvez mettre fin à cette instance. Le suivi peut également afficher les instances démarrées après le point de récupération. Dans ce cas, vous devez compenser chaque action effectuée par ces instances, puis renvoyer leurs messages d'activation initiaux.  
  
 Utilisez le débogueur de l'orchestration pour afficher les dernières formes exécutées, puis le flux de messages pour identifier les messages qui auraient dû être envoyés ou reçus.  
  
 En cas de perte de la base de données des suivis BizTalk, vous devez utiliser les mécanismes de création de rapports des systèmes externes pour découvrir les événements survenus après le point de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de la perte de données](../core/resolving-data-loss.md)