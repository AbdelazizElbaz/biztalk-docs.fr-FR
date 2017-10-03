---
title: "Comment utiliser un Assembly .NET comme Source de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rule Composer, data sources
ms.assetid: 14dbec48-acc9-4c3c-bd7f-737dabf29543
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa56370cf894d0d18a36320ca97c4d028fee487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-net-assembly-as-a-data-source"></a>Utilisation d'un assembly .NET comme source de données
Vous pouvez spécifier un assembly .NET en tant que source de données. Vous pouvez ensuite sélectionner une classe ou un membre de classe à partir de l’assembly et le déplacer dans une règle ou une définition.  
  
### <a name="to-specify-a-net-assembly-as-a-data-source"></a>Pour spécifier un assembly .NET comme source de données   
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **Classes .NET** onglet.  
  
2.  Cliquez sur le **Modules** nœud.  
  
3.  Parmi les assemblys disponibles, sélectionnez un assembly .NET.  
  
    > [!NOTE]
    >  Les assemblys doivent se trouver dans le Global Assembly Cache (GAC). L’éditeur des règles d’entreprise charge un assembly .NET lorsque vous recherchez l’assembly .NET dans le **l’Explorateur de faits** fenêtre ou dans le **classe .NET ou définition de membre de classe** page de la **vocabulaire Définition** fenêtre.  Si vous mettez à jour l'assembly dans le GAC, fermez l'Éditeur des règles d'entreprise et redémarrez-le afin de charger l'assembly .NET mis à jour. L'actualisation n'est en effet pas automatique.  
  
     ![Capture d’écran de faits de l’Explorateur d’arborescence de la définition. ] (../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")