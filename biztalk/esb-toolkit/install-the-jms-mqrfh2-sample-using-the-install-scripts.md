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
ms.openlocfilehash: 27b3606d53f692ff52779eeac3505fd8062bed28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-jms-mqrfh2-sample-using-the-install-scripts"></a><span data-ttu-id="ee656-102">Installer l’exemple de MQRFH2 JMS à l’aide de Scripts d’installation</span><span class="sxs-lookup"><span data-stu-id="ee656-102">Install the JMS MQRFH2 Sample Using the Install Scripts</span></span>
<span data-ttu-id="ee656-103">Cette section décrit comment vous pouvez installer l’exemple JMS MQRFH2 à l’aide de l’installation de scripts fournis avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee656-103">This section describes how you can install the JMS MQRFH2 sample using the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="ee656-104">**Pour installer les exemples JMS MQRFH2 dans les scripts d’installation**</span><span class="sxs-lookup"><span data-stu-id="ee656-104">**To install the JMS MQRFH2 samples from the install scripts**</span></span>  
  
1.  <span data-ttu-id="ee656-105">À l’aide de l’Explorateur de WebSphere, créez un gestionnaire de file d’attente portant le nom **ESB. JMS. Sample.QueueManager**.</span><span class="sxs-lookup"><span data-stu-id="ee656-105">Using WebSphere Explorer, create a Queue Manager with the name **ESB.JMS.Sample.QueueManager**.</span></span>  
  
2.  <span data-ttu-id="ee656-106">À l’aide de WebSphere Explorer, créer des files de quatre attente suivantes dans **ESB. JMS. Sample.QueueManager :**</span><span class="sxs-lookup"><span data-stu-id="ee656-106">Using WebSphere Explorer, create the following four queues within **ESB.JMS.Sample.QueueManager:**</span></span>  
  
    -   <span data-ttu-id="ee656-107">ESB. JMS. EXEMPLE. DYNAMICQ1</span><span class="sxs-lookup"><span data-stu-id="ee656-107">ESB.JMS.SAMPLE.DYNAMICQ1</span></span>  
  
    -   <span data-ttu-id="ee656-108">ESB. JMS. EXEMPLE. DYNAMICQ2</span><span class="sxs-lookup"><span data-stu-id="ee656-108">ESB.JMS.SAMPLE.DYNAMICQ2</span></span>  
  
    -   <span data-ttu-id="ee656-109">ESB. JMS. EXEMPLE. RÉPONSE</span><span class="sxs-lookup"><span data-stu-id="ee656-109">ESB.JMS.SAMPLE.REPLY</span></span>  
  
    -   <span data-ttu-id="ee656-110">ESB. JMS. EXEMPLE. SENDTOBIZTALK</span><span class="sxs-lookup"><span data-stu-id="ee656-110">ESB.JMS.SAMPLE.SENDTOBIZTALK</span></span>  
  
3.  <span data-ttu-id="ee656-111">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="ee656-111">On the **Start** menu, click **Run**.</span></span>  
  
4.  <span data-ttu-id="ee656-112">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ee656-112">In the **Run** dialog box, type **cmd**, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="ee656-113">Exécutez la commande suivante, en remplaçant le  *\<chemin d’accès >* paramètre avec le chemin d’accès complet au fichier .cmd à installer (le chemin d’accès par défaut dans cette version est \Source\Samples\JMS\Install\Scripts\\) :</span><span class="sxs-lookup"><span data-stu-id="ee656-113">Run the following command, replacing the *\<path>* parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\JMS\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```