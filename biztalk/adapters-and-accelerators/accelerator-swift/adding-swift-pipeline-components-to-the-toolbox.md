---
title: "Ajout de composants de Pipeline SWIFT à la boîte à outils | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox, adding pipelines
- pipelines, adding to toolbox
ms.assetid: 3821c10e-ef9b-4657-b934-cff6d096f654
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaef345994a1d849e09025d9ad1bb0f133c1b224
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-swift-pipeline-components-to-the-toolbox"></a>Ajout de composants de Pipeline SWIFT à la boîte à outils
Vous devez ajouter les composants de pipeline SWIFT à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] boîte à outils, qui vous pouvez de créer des pipelines personnalisés à l’aide de ces composants. Cela est nécessaire pour créer des pipelines pour Message Repair et New Submission ou rapprochement de réponse de FIN.  
  
 **Résumé**  
  
 Ajouter les composants de pipeline SWIFT suivant à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] boîte à outils :  
  
-   Assembleur SWIFT (pour Message Repair et New Submission ou rapprochement de réponse FIN (FRR))  
  
-   Désassembleur SWIFT (pour Message Repair et New Submission ou FRR)  
  
-   Programme de résolution ensemble de corrélation Frr SWIFT (pour FRR)  
  
-   Décodeur de MQSeries Frr SWIFT (pour FRR)  
  
-   Composant d’envoi SWIFT Frr MQSeries (pour FRR)  
  
### <a name="to-add-a4swift-pipeline-components-to-the-toolbox"></a>Pour ajouter des composants de pipeline A4SWIFT à la boîte à outils  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.  
  
2.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue le **composants de Pipeline BizTalk** onglet, sélectionnez **SWIFT assembleur** et **SWIFT désassembleur**. Si vous utilisez Rapprochement de réponse de FIN, sélectionnez **SWIFT Frr corrélation définir résolution**, **SWIFT Frr MQSeries décodeur**, et **SWIFT Frr MQSeries envoyer composant**.  
  
3.  Cliquez sur **OK**.