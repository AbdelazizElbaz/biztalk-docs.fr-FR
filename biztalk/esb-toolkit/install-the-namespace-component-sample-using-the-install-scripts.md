---
title: "Installer l’exemple de composant de Namespace à l’aide de Scripts d’installation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66046ef4-91a2-4fe7-93ad-3b8137294411
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 822f2b2f97374b5e5953f81025fb02027328f054
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-namespace-component-sample-using-the-install-scripts"></a><span data-ttu-id="5a869-102">Installer l’exemple de composant de Namespace à l’aide de Scripts d’installation</span><span class="sxs-lookup"><span data-stu-id="5a869-102">Install the Namespace Component Sample Using the Install Scripts</span></span>
<span data-ttu-id="5a869-103">Cette section décrit comment vous pouvez installer l’exemple de composant de Namespace à partir du fichier Windows Installer avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a869-103">This section describes how you can install the Namespace Component sample from the Windows Installer file provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="5a869-104">**Pour installer l’exemple de composant de Namespace dans les scripts d’installation**</span><span class="sxs-lookup"><span data-stu-id="5a869-104">**To install the Namespace Component sample from the install scripts**</span></span>  
  
1.  <span data-ttu-id="5a869-105">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="5a869-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="5a869-106">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis appuyez sur ENTRÉE pour ouvrir une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="5a869-106">In the **Run** dialog box, type **cmd**, and then press ENTER to open a command prompt.</span></span>  
  
3.  <span data-ttu-id="5a869-107">Exécutez la commande suivante, en remplaçant le  *\<chemin d’accès >* paramètre avec le chemin d’accès complet au fichier .cmd à installer (le chemin d’accès par défaut dans cette version est \Source\Samples\Namepace\Install\Scripts\\) :</span><span class="sxs-lookup"><span data-stu-id="5a869-107">Run the following command, replacing the *\<path>* parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\Namepace\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```