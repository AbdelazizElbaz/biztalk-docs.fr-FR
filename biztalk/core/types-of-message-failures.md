---
title: "Types d’échecs de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transformation stage
- assembly stage
- errors, disassembly stage
- errors, assembly stage
- routing, errors
- errors, transformation stage
- errors, messages [HAT]
- errors, routing
- disassembly stage, errors
- messages, errors [HAT]
ms.assetid: 3a8e1c58-4b53-4439-837d-aaa233eb9158
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 466c7c21fd1a00e192307dd82384dc613b6697a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-message-failures"></a>Types d'échecs associés aux messages
Cette rubrique répertorie les différents stades auxquels un échec de message peut survenir.  
  
 **Échecs dans la phase de désassemblage**  
  
 Le traitement peut échouer au cours de la phase de désassemblage, suite à la défaillance de l'un des composants de pipeline. Par exemple, le déchiffrement peut échouer en raison de l'absence de certificat de chiffrement sur le serveur de traitement ou un échec d'analyse peut être dû à un problème au niveau du schéma ou du message.  
  
 **Échecs lors du routage**  
  
 Une fois que le désassemblage du message a été correctement effectué, le point de défaillance potentiel suivant est le routage, par exemple lorsque des utilisateurs activent un emplacement de réception correspondant à une orchestration et qu'ils oublient d'inscrire l'orchestration. Dans ce cas, le routage du message collecté à partir de l'emplacement de réception échoue et la base de données MessageBox génère un rapport d'échec du routage.  
  
 Les rapports d'échec de routage sont répertoriés dans la console Administration de BizTalk Server comme des messages suspendus ne pouvant être repris. Chaque rapport d'échec de routage contient un instantané de la propriété du message pris lors de l'échec du routage. Vous pouvez utiliser les informations contenues dans chaque rapport pour déterminer la raison de l'échec du routage pour le message concerné. Si ce message peut être repris, vous pouvez corriger le problème de routage et reprendre le message afin de poursuivre son traitement. Les rapports d'échec de routage sont affichés dans la liste de résultats avec un nom de service et un type de service non renseignés. Lorsque vous terminez une instance suspendue, le rapport de l'échec du routage associé à cette instance est automatiquement supprimé par le travail Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb exécuté toutes les minutes par défaut. Pour plus d’informations sur le travail Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb, voir [Structure de base de données et les travaux](../core/database-structure-and-jobs.md).  
  
 **Échecs lors de la phase de transformation**  
  
-   **Messages reçus**. lorsqu'un message est reçu à partir d'un emplacement de réception, il est désassemblé (par exemple, déchiffré et analysé), il peut éventuellement être transformé en un format différent par le biais d'un mappage entrant spécifié sur un port de réception, puis il est publié dans la base de données MessageBox en vue de son routage vers une orchestration ou un port d'envoi. Dans ce cas, le traitement peut échouer au cours de la phase de transformation en raison d'un mappage entrant incorrect ou de problèmes dans le schéma ou dans le message reçu.  
  
-   **Les Messages envoyés**. lorsqu'un message est envoyé vers un emplacement d'envoi, un mappage sortant, configuré sur le port d'envoi, peut éventuellement transformer le message. Ensuite, le message transformé est assemblé et transmis à l'adaptateur pour être transféré vers l'emplacement d'envoi. Dans ce cas, le traitement peut échouer au cours de la phase de transformation, du fait d'un mappage sortant incorrect ou d'un problème dans le schéma ou dans le message source.  
  
 **Échecs dans la phase d’assemblage**  
  
 Le traitement peut également échouer lors de la phase d'assemblage, c'est-à-dire suite à une défaillance d'un composant de pipeline. Une fois le message correctement assemblé, le point de défaillance potentiel suivant est la transmission à l'emplacement d'envoi. Par exemple, l'emplacement d'envoi (qui appartient au partenaire) peut être défaillant ou absent.  
  
## <a name="see-also"></a>Voir aussi  
 [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)