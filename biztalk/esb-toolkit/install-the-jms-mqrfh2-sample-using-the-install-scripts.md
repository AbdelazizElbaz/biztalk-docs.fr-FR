---
title: "Installer l’exemple de MQRFH2 JMS à l’aide de Scripts d’installation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 785f3e32-83b4-406a-af1b-9499115fbb8f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edb3102fabc84818cb42fcdcba6a034d085bdcc4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-jms-mqrfh2-sample-using-the-install-scripts"></a>Installer l’exemple de MQRFH2 JMS à l’aide de Scripts d’installation
Cette section décrit comment vous pouvez installer l’exemple JMS MQRFH2 à l’aide de l’installation de scripts fournis avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **Pour installer les exemples JMS MQRFH2 dans les scripts d’installation**  
  
1.  À l’aide de l’Explorateur de WebSphere, créez un gestionnaire de file d’attente portant le nom **ESB. JMS. Sample.QueueManager**.  
  
2.  À l’aide de WebSphere Explorer, créer des files de quatre attente suivantes dans **ESB. JMS. Sample.QueueManager :**  
  
    -   ESB. JMS. EXEMPLE. DYNAMICQ1  
  
    -   ESB. JMS. EXEMPLE. DYNAMICQ2  
  
    -   ESB. JMS. EXEMPLE. RÉPONSE  
  
    -   ESB. JMS. EXEMPLE. SENDTOBIZTALK  
  
3.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
4.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis appuyez sur ENTRÉE.  
  
5.  Exécutez la commande suivante, en remplaçant le  *\<chemin d’accès\>*  paramètre avec le chemin d’accès complet au fichier .cmd à installer (le chemin d’accès par défaut dans cette version est \Source\Samples\JMS\Install\Scripts\\):  
  
    ```  
    <path>\Setup_bin.cmd  
    ```