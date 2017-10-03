---
title: "Création d’un projet de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b584e3ab-e824-4977-b4ed-4fc197a6cf7a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eead267abbb990933e6fd3150d099d07b007526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-pipeline-project"></a>Création d’un projet de Pipeline
Pour créer un projet de pipeline :  
  
1.  Dans Visual Studio, créez un projet BizTalk.  
  
2.  Ajouter un élément de pipeline de réception et un élément de pipeline d’envoi pour le projet.  
  
3.  Ouvrez le fichier ReceivePipeline.btp.  
  
4.  Dans le Concepteur de Pipeline, ouvrez la boîte à outils.  
  
5.  Cliquez sur le **boîte à outils** surface, puis sélectionnez **choisir des éléments de**.  
  
6.  Dans la fenêtre Choisir des éléments de boîte à outils, cliquez sur le **composants de Pipeline** onglet et sélectionnez les composants suivants :  
  
    -   SwiftMXDisassembler  
  
    -   SwiftMXAssembler  
  
    -   Composant d’encodeur MXRR SWIFT  
  
    -   Composant du décodeur MXRR SWIFT  
  
    -   Composant de programme de résolution de tiers de corrélation MXRR SWIFT  
  
7.  Faites glisser le **SwiftMXDisassembler** composant dans l’espace réservé du désassembleur dans le Pipeline de réception.  
  
8.  Dans les propriétés du composant SwiftMXDisassembler, définissez le **BRE Validation** propriété à TRUE ou FALSE selon que vous souhaitez activer la Validation des règles d’entreprise sur les messages entrants. Définir le **TransportHeaderRequired** propriété à TRUE ou FALSE selon que vous souhaitez fournir l’en-tête de transport dans les messages.  
  
9. Faites glisser le composant décodeur de MXRR Swift et résolution de tiers Swift MXRR corrélation dans le décodeur et l’espace réservé du programme de résolution de tiers dans le Pipeline de réception.  
  
10. Sélectionnez le **résolution de tiers de corrélation MXRR** dans le pipeline. Dans la fenêtre Propriétés du composant de Pipeline, définissez la **activer la journalisation BAM pour rapprochement** propriété à TRUE ou FALSE, selon que vous souhaitez activer le rapprochement entre les réponses SWIFT.  
  
11. Ouvrez le **SendPipeline.btp** fichier, dans le Concepteur de Pipeline, ouvrir le **boîte à outils**.  
  
12. Dans la boîte à outils, faites glisser le **SwiftMXAssembler** composant dans l’espace réservé d’assembleur dans le Pipeline d’envoi.  
  
13. Faites glisser le **Swift MXRR encodeur** composant dans les espaces réservés d’encodeur du Pipeline d’envoi.  
  
14. Sélectionnez le **MXRR encodeur tiers résolveur** dans le pipeline, puis, dans la fenêtre Propriétés du composant de Pipeline, définissez les propriétés suivantes.  
  
15. Activer **journalisation de l’analyse BAM pour rapprochement** TRUE ou FALSE selon que vous souhaitez activer le rapprochement entre les réponses SWIFT.  
  
16. Définir le **LAU requis** TRUE ou FALSE selon que vous disposez activer la signature du message à l’accès de Alliance SWIFT (SAA).  
  
17. Si la propriété LAU requis a été a été défini à TRUE, puis fournissez LAU clé première partie et le deuxième partie LAU clé (les valeurs doivent être les mêmes que ceux qui ont été fournies lors de la configuration de la SAA.)  
  
18. Générez et déployez le projet.