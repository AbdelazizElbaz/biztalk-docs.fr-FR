---
title: "Comment afficher les remplacements d’un Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8261a514-b4c4-4e6b-ac35-40a3e3e090e0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28c4ab2ef8f82fdd770203816239ad78e74418e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-overrides-for-a-management-pack"></a>Comment afficher les remplacements d’un Pack d’administration
Pour afficher les remplacements d’un Pack d’administration, utilisez la procédure suivante.  
  
### <a name="to-display-overrides-for-a-management-pack"></a>Pour afficher les remplacements d’un Pack d’administration  
  
1.  Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center**.  
  
2.  Cliquez sur **interface de commande**.  
  
3.  Dans l’interface de commande, tapez la commande suivante :   
    `$mp = get-scommanagementpack -DisplayName "Operations Manager Internal Library"`   
    `$mp.GetOverrides()`  
  
4.  Un fichier .csv est créé. Le fichier .csv peut être ouvert dans Office Excel.  
  
    > [!NOTE]  
    >  Dans Office Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.  
  
 Par exemple, la commande suivante affiche les remplacements pour un des packs d’administration principaux :   
`$mp = get-scommanagementpack -DisplayName "Contoso.BizTalk.Overrides.mp"`  
`$mp.GetOverrides()`