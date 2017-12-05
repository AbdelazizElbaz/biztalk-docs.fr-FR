---
title: MSBUILD autonome | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21aa3693-3788-4874-b506-6f4584fb4fd5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcee1d06bf57eb2ea98c214501c2499f0ce83d95
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="standalone-msbuild"></a><span data-ttu-id="d301b-102">MSBUILD autonome</span><span class="sxs-lookup"><span data-stu-id="d301b-102">Standalone MSBUILD</span></span>
<span data-ttu-id="d301b-103">Le **génération de projet** composant de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de créer des solutions BizTalk Server sans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d301b-103">The **Project Build** component of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows you to build BizTalk Server solutions without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="d301b-104">Pour installer le **génération de projet** composant sur votre serveur, sélectionnez le **composant de création de projet** option dans le **catégorie logiciels supplémentaires** pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="d301b-104">To install the **Project Build** component on your server, select the **Project Build Component** option in the **Additional Software category** during installation.</span></span> <span data-ttu-id="d301b-105">Vous devez désélectionner la **outils de développement et Kit de développement logiciel** lors de l’installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur sans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d301b-105">You should unselect the **Developer Tools and SDK** as you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d301b-106">Pour plus d’informations sur MSBUILD, consultez [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span><span class="sxs-lookup"><span data-stu-id="d301b-106">For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
## <a name="to-build-a-biztalk-project"></a><span data-ttu-id="d301b-107">Pour générer un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="d301b-107">To build a BizTalk project</span></span>  
  
1.  <span data-ttu-id="d301b-108">Cliquez sur **Démarrer**, puis sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="d301b-108">Click **Start**, and click **Run**.</span></span>  
  
2.  <span data-ttu-id="d301b-109">Type **cmd**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="d301b-109">Type **cmd**, and press ENTER.</span></span>  
  
3.  <span data-ttu-id="d301b-110">Accédez au répertoire du projet, puis exécutez une commande MSBUILD pour créer la solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d301b-110">Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.</span></span>  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d301b-111">Vous pouvez définir la variable d’environnement PATH pour pointer vers le dossier dans lequel msbuild.exe réside (\<*répertoire d’installation windows*\>\Microsoft.NET\Framework\v4).</span><span class="sxs-lookup"><span data-stu-id="d301b-111">You may need set the PATH environment variable to point to the folder in which msbuild.exe resides (\<*windows installation directory*\>\Microsoft.NET\Framework\v4).</span></span>