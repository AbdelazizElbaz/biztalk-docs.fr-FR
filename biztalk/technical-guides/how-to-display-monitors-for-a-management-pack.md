---
title: "Comment afficher les moniteurs d’un Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c4d2b3-9c01-40f5-b983-bf29a3a5cacc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b3954052159633894e59b4251ee20b1ea0844a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-monitors-for-a-management-pack"></a>Comment afficher les moniteurs d’un Pack d’administration
Pour afficher une liste des sorties des moniteurs et des remplacements à l’aide de l’interface de commande un pack d’administration, utilisez la procédure suivante.  
  
### <a name="to-display-monitors-for-a-management-pack"></a>Pour afficher les moniteurs pour un Pack d’administration  
  
1.  Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center.**  
  
2.  Cliquez sur **interface de commande**.  
  
3.  Dans l’interface de commande, tapez la commande suivante :   
    `get-scommanagementpack –DisplayName “DisplayName” | get-scommonitor | export.csv filename`  
  
4.  Un fichier .csv est créé. Le fichier .csv peut être ouvert dans Microsoft Office Excel.  
  
    > [!NOTE]  
    >  Dans Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.  
  
 Par exemple, la commande suivante récupère les données pour les analyses associées à un des packs d’administration principaux :   
`get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-ScomMonitor | export-csv "c:\monitors.csv"`