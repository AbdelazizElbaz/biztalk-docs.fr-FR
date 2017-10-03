---
title: "Comment afficher toutes les règles de Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fdec550-6713-4f5f-8c04-d9218bf2df3c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08ec94eb3adb87bf6feaff032e00a61bc9b0fead
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-all-management-pack-rules"></a>Comment afficher toutes les règles de Pack d’administration
Utilisez la procédure suivante pour afficher une liste de règles pour les packs d’administration que vous avez importé. La liste des règles peut être affichée dans Office Excel.  
  
### <a name="to-display-management-pack-rules"></a>Pour afficher les règles du Pack d’administration  
  
1.  Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center**.  
  
2.  Cliquez sur **interface de commande**.  
  
3.  Dans l’interface de commande, tapez la commande suivante :   
    `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-SCOMRule | export-csv "c:\rules.csv"`  
  
4.  Un fichier .csv est créé. Vous pouvez ouvrir le fichier .csv dans Office Excel.  
  
    > [!NOTE]  
    >  Dans Office Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.