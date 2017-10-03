---
title: "Intégration de MSBUILD avec Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedcabf7-b2cf-482a-9ade-7311e104bff9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4a639945881625dd697798080c913ec0e5e3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msbuild-integration-with-visual-studio"></a><span data-ttu-id="43345-102">Intégration de MSBUILD avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43345-102">MSBUILD Integration with Visual Studio</span></span>
<span data-ttu-id="43345-103">Visual Studio utilise le format de fichier de projet MSBUILD pour stocker les informations de version des projets gérés, y compris des projets BizTalk.</span><span class="sxs-lookup"><span data-stu-id="43345-103">Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects.</span></span> <span data-ttu-id="43345-104">Les paramètres de projet ajoutés et modifiés dans Visual Studio sont spécifiés dans le fichier .btproj généré pour chaque projet.</span><span class="sxs-lookup"><span data-stu-id="43345-104">Project settings added and changed through Visual Studio are reflected in the .btproj file that is generated for each project.</span></span> <span data-ttu-id="43345-105">Visual Studio utilise une instance hébergée de MSBUILD pour développer des projets BizTalk. Ainsi, il est possible de générer un projet BizTalk dans Visual Studio ou à partir de la ligne de commande en obtenant un résultat identique.</span><span class="sxs-lookup"><span data-stu-id="43345-105">Visual Studio uses a hosted instance of MSBUILD to build BizTalk projects, meaning that a BizTalk project can be built in Visual Studio or from the command line, with identical results.</span></span>  
  
 <span data-ttu-id="43345-106">Pour plus d’informations sur MSBUILD, consultez [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span><span class="sxs-lookup"><span data-stu-id="43345-106">For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
 <span data-ttu-id="43345-107">Les procédures suivantes présentent l'utilisation de MSBUILD pour développer un exemple de projet BizTalk à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="43345-107">The following procedure shows you how to use MSBUILD to build a sample BizTalk project from command line.</span></span>  
  
## <a name="to-build-a-biztalk-project-from-a-command-line"></a><span data-ttu-id="43345-108">Pour générer un projet BizTalk à partir d'une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="43345-108">To build a BizTalk project from a command line</span></span>  
  
1.  <span data-ttu-id="43345-109">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="43345-109">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="43345-110">Accédez au répertoire du projet, puis exécutez une commande MSBUILD pour créer la solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="43345-110">Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.</span></span>  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="43345-111">La solution peut contenir des projets BizTalk et non-BizTalk, tels qu'une bibliothèque de classes C#.</span><span class="sxs-lookup"><span data-stu-id="43345-111">The solution may contain BizTalk and non-BizTalk projects, such as a C# class library.</span></span>