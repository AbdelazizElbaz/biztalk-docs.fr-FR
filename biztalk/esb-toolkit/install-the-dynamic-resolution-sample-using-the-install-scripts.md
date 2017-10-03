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
# <a name="install-the-dynamic-resolution-sample-using-the-install-scripts"></a><span data-ttu-id="5e681-102">Installer l’exemple de résolution dynamique à l’aide de Scripts d’installation</span><span class="sxs-lookup"><span data-stu-id="5e681-102">Install the Dynamic Resolution Sample Using the Install Scripts</span></span>
<span data-ttu-id="5e681-103">Cette section décrit comment vous pouvez installer l’exemple de résolution dynamique à partir de l’installation de scripts fournis avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e681-103">This section describes how you can install the Dynamic Resolution sample from the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="5e681-104">**Pour installer l’exemple de résolution dynamique à partir de scripts d’installation**</span><span class="sxs-lookup"><span data-stu-id="5e681-104">**To install the Dynamic Resolution sample from the install scripts**</span></span>  
  
1.  <span data-ttu-id="5e681-105">Si vous souhaitez exécuter les exemples de messagerie unidirectionnels qui utilisent FTP, créez le site FTP suivant :</span><span class="sxs-lookup"><span data-stu-id="5e681-105">If you want to execute one-way messaging examples that use FTP, create the following FTP site:</span></span>  
  
    -   <span data-ttu-id="5e681-106">Nom du répertoire virtuel FTP : Out</span><span class="sxs-lookup"><span data-stu-id="5e681-106">FTP Virtual Directory name: Out</span></span>  
  
    -   <span data-ttu-id="5e681-107">Emplacement : \Source\Samples\DynamicResolution\Test\FTP\Out</span><span class="sxs-lookup"><span data-stu-id="5e681-107">Location: \Source\Samples\DynamicResolution\Test\FTP\Out</span></span>  
  
    -   <span data-ttu-id="5e681-108">Autorisations : Lire et écrire</span><span class="sxs-lookup"><span data-stu-id="5e681-108">Permissions: Read and Write</span></span>  
  
    -   <span data-ttu-id="5e681-109">Vérifiez que le groupe d’utilisateurs d’applications BizTalk dispose des droits d’accès complet pour cet emplacement</span><span class="sxs-lookup"><span data-stu-id="5e681-109">Ensure the BizTalk Application Users group has full access permission for this location</span></span>  
  
2.  <span data-ttu-id="5e681-110">Si vous souhaitez exécuter les exemples de messagerie bidirectionnelles qui utilisent MQSeries, utilisez l’Explorateur WebSphere pour créer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5e681-110">If you want to execute two-way messaging examples that use MQSeries, use WebSphere Explorer to create the following:</span></span>  
  
    -   <span data-ttu-id="5e681-111">Un gestionnaire de file d’attente avec le nom ESB. PROGRAMME DEP. Sample.QueueManager</span><span class="sxs-lookup"><span data-stu-id="5e681-111">A queue manager with the name ESB.DEP.Sample.QueueManager</span></span>  
  
    -   <span data-ttu-id="5e681-112">Une file d’attente nommée TEST. OUT dans l’architecture ESB. PROGRAMME DEP. Sample.QueueManager</span><span class="sxs-lookup"><span data-stu-id="5e681-112">A queue named TEST.OUT within the ESB.DEP.Sample.QueueManager</span></span>  
  
3.  <span data-ttu-id="5e681-113">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="5e681-113">On the **Start** menu, click **Run**.</span></span>  
  
4.  <span data-ttu-id="5e681-114">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis appuyez sur ENTRÉE pour ouvrir l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="5e681-114">In the **Run** dialog box, type **cmd**, and then press ENTER to open the command prompt.</span></span>  
  
5.  <span data-ttu-id="5e681-115">Exécutez la commande suivante, en remplaçant le \<chemin d’accès > paramètre avec le chemin d’accès complet au fichier .cmd à installer (le chemin d’accès par défaut dans cette version est \Source\Samples\DynamicResolution\Install\Scripts\\) :</span><span class="sxs-lookup"><span data-stu-id="5e681-115">Run the following command, replacing the \<path> parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\DynamicResolution\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```