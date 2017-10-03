---
title: "Installer l’exemple de résolution dynamique à l’aide de Scripts d’installation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 644b6403-9883-4256-80d5-37881a87ed0e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95145af75916001895c03bd0b2665894a43083cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-dynamic-resolution-sample-using-the-install-scripts"></a>Installer l’exemple de résolution dynamique à l’aide de Scripts d’installation
Cette section décrit comment vous pouvez installer l’exemple de résolution dynamique à partir de l’installation de scripts fournis avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **Pour installer l’exemple de résolution dynamique à partir de scripts d’installation**  
  
1.  Si vous souhaitez exécuter les exemples de messagerie unidirectionnels qui utilisent FTP, créez le site FTP suivant :  
  
    -   Nom du répertoire virtuel FTP : Out  
  
    -   Emplacement : \Source\Samples\DynamicResolution\Test\FTP\Out  
  
    -   Autorisations : Lire et écrire  
  
    -   Vérifiez que le groupe d’utilisateurs d’applications BizTalk dispose des droits d’accès complet pour cet emplacement  
  
2.  Si vous souhaitez exécuter les exemples de messagerie bidirectionnelles qui utilisent MQSeries, utilisez l’Explorateur WebSphere pour créer les éléments suivants :  
  
    -   Un gestionnaire de file d’attente avec le nom ESB. PROGRAMME DEP. Sample.QueueManager  
  
    -   Une file d’attente nommée TEST. OUT dans l’architecture ESB. PROGRAMME DEP. Sample.QueueManager  
  
3.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
4.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis appuyez sur ENTRÉE pour ouvrir l’invite de commandes.  
  
5.  Exécutez la commande suivante, en remplaçant le \<chemin d’accès > paramètre avec le chemin d’accès complet au fichier .cmd à installer (le chemin d’accès par défaut dans cette version est \Source\Samples\DynamicResolution\Install\Scripts\\) :  
  
    ```  
    <path>\Setup_bin.cmd  
    ```