---
title: "Échecs des orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception block [Orchestration Designer], suspended orchestrations
- HAT, Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], HAT
- orchestrations, troubleshooting [HAT]
- orchestrations, errors
- HAT, Orchestration Debugger
- Orchestration Debugger
- errors, orchestrations
- HAT, troubleshooting orchestrations
- orchestrations, HAT
- HAT, orchestrations
ms.assetid: d0a799fb-7859-4774-b444-979f22f04215
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d95cab903ae9bf5faacdf385f667c33f9a2d5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-failures"></a>Échecs des orchestrations
Les orchestrations sont plus ou moins complexes. Elles peuvent, par exemple, appeler un objet .NET ou construire des messages par le biais des formes Transformer et Assignation du message. Du fait du large éventail de contenu et du niveau de personnalisation, il est donc impossible de répertorier tous les échecs possibles. Cependant, toutes les défaillances rencontrées dans les orchestrations apparaissent en tant qu'exceptions.  
  
 Si une orchestration ne comprend aucun **CatchException** forme pour une exception, l’exception entraîne l’orchestration puisse être suspendue, mais ne peut pas être repris. Autrement dit, l'instance ne peut pas être restaurée à l'aide du suivi des messages et des instances de service ou d'un script WMI. Néanmoins, à l'aide de ce suivi (ou du script WMI), vous pouvez enregistrer tous les messages associés à l'instance interrompue (sans reprise possible) afin d'établir un diagnostic et d'effectuer manuellement une nouvelle tentative.  
  
 Pour diagnostiquer le problème, utilisez le débogueur de l'orchestration pour voir la dernière forme exécutée avant que l'instance ne soit interrompue. Cet outil permet également de consulter les détails de l'exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)   
 [Débogage d’une Orchestration](../core/debugging-an-orchestration.md)