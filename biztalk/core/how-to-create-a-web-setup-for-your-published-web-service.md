---
title: "Comment créer un programme d’installation Web pour votre Service Web publié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
- Web services, .msi file
- .msi files, Web services
ms.assetid: 77c86242-1d27-4d99-ae00-fe2614bc13ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87c5ec4fe61c8649fe951460917cfde8788f2e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-web-setup-for-your-published-web-service"></a><span data-ttu-id="09aa4-102">Création d'un projet d'installation Web pour votre service Web publié</span><span class="sxs-lookup"><span data-stu-id="09aa4-102">How to Create a Web Setup for Your Published Web Service</span></span>
<span data-ttu-id="09aa4-103">Vous pouvez créer un package d'installation pour simplifier la configuration de votre service Web dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="09aa4-103">You can create an installation package to facilitate setting up your Web service in a production environment.</span></span> <span data-ttu-id="09aa4-104">Cette opération génère un fichier .MSI.</span><span class="sxs-lookup"><span data-stu-id="09aa4-104">This produces an .MSI file.</span></span>  
  
### <a name="to-create-an-installation-package-to-produce-an-msi-file-using-visual-studio"></a><span data-ttu-id="09aa4-105">Pour créer un package d’installation afin de générer un fichier .MSI à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09aa4-105">To create an installation package to produce an .MSI file using Visual Studio</span></span>  
  
1.  <span data-ttu-id="09aa4-106">Ouvrez le projet de service Web ASP.NET publié.</span><span class="sxs-lookup"><span data-stu-id="09aa4-106">Open your published ASP.NET Web service project.</span></span>  
  
2.  <span data-ttu-id="09aa4-107">Dans l’Explorateur de solutions, cliquez sur le nœud solution, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-107">In Solution Explorer, right-click the solution node, click **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="09aa4-108">Dans le **ajouter un nouveau projet** boîte de dialogue le **Types de projets** zone, développez **autres Types de projets**, développez **le programme d’installation et les projets de déploiement**, puis sélectionnez **le programme d’installation de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-108">In the **Add New Project** dialog box, in the **Project Types** area, expand **Other Project Types**, expand **Setup and Deployment Projects**, and then select **Visual Studio Installer**.</span></span> <span data-ttu-id="09aa4-109">Dans le **modèles** zone, sélectionnez **projet d’installation Web**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-109">In the **Templates** area, select **Web Setup Project**.</span></span>  
  
4.  <span data-ttu-id="09aa4-110">Dans le **nom** zone de texte, tapez un nom pour le projet d’installation Web.</span><span class="sxs-lookup"><span data-stu-id="09aa4-110">In the **Name** text box, type a name for the Web Setup Project.</span></span> <span data-ttu-id="09aa4-111">Vous pouvez utiliser le même nom que le projet de Service Web ASP.NET, ajoutez « _Setup » comme suffixe, puis cliquez **OK**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-111">You can use the same name as the ASP.NET Web Service project and add "_Setup" as a suffix and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="09aa4-112">Dans l’Explorateur de solutions, cliquez sur le nœud du projet d’installation Web nouvellement créé, puis pointez sur **vue**, puis cliquez sur **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-112">In Solution Explorer, right-click the newly created Web setup project node, and point to **View**, and then click **File System**.</span></span>  
  
6.  <span data-ttu-id="09aa4-113">Dans le **système de fichiers** fenêtre, avec le bouton droit le **dossier d’Application Web** nœud et pointez sur **ajouter**, puis cliquez sur **sortie du projet**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-113">In the **File System** window, right-click the **Web Application Folder** node and point to **Add**, then click **Project Output**.</span></span>  
  
7.  <span data-ttu-id="09aa4-114">Dans le **ajouter un groupe de sorties de projet** boîte de dialogue, sélectionnez **sortie principale** et **les fichiers de contenu** du Service Web ASP.NET du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-114">In the **Add Project Output Group** dialog box, select **Primary Output** and **Content Files** from the ASP.NET Web Service project and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="09aa4-115">Dans l’Explorateur de solutions, développez le **dépendances détectées** nœud sous le projet d’installation Web.</span><span class="sxs-lookup"><span data-stu-id="09aa4-115">In Solution Explorer, expand the **Detected Dependencies** node under the Web setup project.</span></span>  
  
9. <span data-ttu-id="09aa4-116">Sélectionnez toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="09aa4-116">Select all dependencies.</span></span> <span data-ttu-id="09aa4-117">Dans le **propriétés** , configurez la **exclure** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="09aa4-117">In the **Properties** window, set the **Exclude** property to **True**.</span></span>  
  
10. <span data-ttu-id="09aa4-118">Générez le projet d'installation Web.</span><span class="sxs-lookup"><span data-stu-id="09aa4-118">Build your Web setup project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09aa4-119">Pour plus d’informations sur la création de projets d’installation Web, consultez « Comment pour créer ou ajouter un projet d’installation Web » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62268](http://go.microsoft.com/fwlink/?LinkId=62268).</span><span class="sxs-lookup"><span data-stu-id="09aa4-119">For more information about creating Web setup projects, see "How to Create or Add a Web Setup Project" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62268](http://go.microsoft.com/fwlink/?LinkId=62268).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09aa4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09aa4-120">See Also</span></span>  
 [<span data-ttu-id="09aa4-121">Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09aa4-121">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)