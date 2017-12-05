---
title: "Personnalisation d’un processus privé pour travailler avec une adresse PIP spécifique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, PIPs
- private processes, customizing
- developing, private processes
- PIPs, private processes
- customizing private processes
ms.assetid: 88494e87-25a0-4c94-9396-61a0e07964aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f84cd2de6d5f79062592dbf71947587b6d7a6ff0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="customizing-a-private-process-to-work-with-a-specific-pip"></a><span data-ttu-id="966be-102">Personnalisation d’un processus privé pour travailler avec une adresse PIP spécifique</span><span class="sxs-lookup"><span data-stu-id="966be-102">Customizing a Private Process to Work with a Specific PIP</span></span>
<span data-ttu-id="966be-103">Vous pouvez créer une expression de filtre qui provoque un répondeur orchestration de processus privé pour traiter ou pas les instances de processus de des processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="966be-103">You can create a filter expression that will cause a responder private-process orchestration to process or not process instances of a specific Partner Interface Process (PIP).</span></span> <span data-ttu-id="966be-104">Cela vous donne la souplesse de création d’un processus personnalisé privé pour recevoir et traiter certaines instances PIP et d’utilisation des processus privé par défaut toutes les autres instances PIP.</span><span class="sxs-lookup"><span data-stu-id="966be-104">This gives you the flexibility of creating a custom private process to receive and process some PIP instances, and using the default private process to process all other PIP instances.</span></span>  
  
 <span data-ttu-id="966be-105">Pour créer un processus personnalisé privé pour travailler avec un spécifique PIP ou plusieurs PIP spécifique, vous créez une expression de filtre pour la forme réception de l’orchestration de processus privé.</span><span class="sxs-lookup"><span data-stu-id="966be-105">To create a custom private process to work with a specific PIP or multiple specific PIPs, you create a filter expression for the receive shape of the private-process orchestration.</span></span> <span data-ttu-id="966be-106">Par exemple, l’orchestration PIP3A4PrivateResponder.odx dans les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="966be-106">An example is the PIP3A4PrivateResponder.odx orchestration in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="966be-107">Il se trouve à \< *lecteur*\>: \Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PIP3A4Process à l’aide de Business Rules\PIP3A4PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="966be-107">It is located at \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PIP3A4Process Using Business Rules\PIP3A4PrivateResponder.</span></span>  
  
 <span data-ttu-id="966be-108">En plus de créer un processus privé qui traitent uniquement des instances d’un PIP spécifique, vous devez personnaliser le processus privé de BTARN par défaut afin qu’il ne traitera pas les instances pour ce PIP.</span><span class="sxs-lookup"><span data-stu-id="966be-108">Besides creating a private process that process only instances of a specific PIP, you must customize the default BTARN private process so that it will not process instances for that PIP.</span></span>  
  
### <a name="to-customize-a-responder-private-process-to-work-with-a-specific-pip"></a><span data-ttu-id="966be-109">Pour personnaliser un processus privé répondeur pour travailler avec une adresse PIP spécifique</span><span class="sxs-lookup"><span data-stu-id="966be-109">To customize a responder private process to work with a specific PIP</span></span>  
  
1.  <span data-ttu-id="966be-110">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], créez une orchestration de processus privé répondeur personnalisés pour travailler avec une adresse PIP spécifique.</span><span class="sxs-lookup"><span data-stu-id="966be-110">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], create a custom responder private-process orchestration for working with a specific PIP.</span></span> <span data-ttu-id="966be-111">Vous pouvez baser l’orchestration sur l’orchestration de processus privé par défaut BTARN répondeur.</span><span class="sxs-lookup"><span data-stu-id="966be-111">You can base the orchestration on the default BTARN responder private-process orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="966be-112">Vous pouvez trouver la valeur par défaut orchestration de processus privé de répondeur, nommée PrivateResponder.odx, dans le SDK de BTARN.</span><span class="sxs-lookup"><span data-stu-id="966be-112">You can find the default responder private-process orchestration, named PrivateResponder.odx, in the BTARN SDK.</span></span> <span data-ttu-id="966be-113">Il se trouve à  *\<lecteur\>*: \Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="966be-113">It is located at *\<drive\>*:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder.</span></span>  
  
2.  <span data-ttu-id="966be-114">Ajouter une orchestration personnalisée à votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="966be-114">Add the custom orchestration to your BizTalk project.</span></span> <span data-ttu-id="966be-115">Assurez-vous que votre projet contient une référence au fichier Microsoft.Solutions.BTARN.GlobalSchemas.dll.</span><span class="sxs-lookup"><span data-stu-id="966be-115">Make sure that your project has a reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.</span></span>  
  
3.  <span data-ttu-id="966be-116">Ouvrez l’orchestration personnalisée dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="966be-116">Open the custom orchestration in Orchestration Designer.</span></span>  
  
4.  <span data-ttu-id="966be-117">Avec le bouton droit de la première **réception** forme qui active l’orchestration, puis cliquez sur **modifier l’Expression de filtre**.</span><span class="sxs-lookup"><span data-stu-id="966be-117">Right-click the first **Receive** shape that activates the orchestration, and then click **Edit Filter Expression**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="966be-118">La forme réception pour l’orchestration de processus privé par défaut BTARN répondeur a deux conditions de filtre : Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == « AsyncAction » ou Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == « SyncAction ».</span><span class="sxs-lookup"><span data-stu-id="966be-118">The receive shape for the default BTARN responder private-process orchestration has two filter conditions: Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "AsyncAction" or Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "SyncAction".</span></span> <span data-ttu-id="966be-119">Cette expression permet de s’assurer que l’orchestration traite les messages RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="966be-119">This expression makes sure that the orchestration processes RosettaNet messages.</span></span> <span data-ttu-id="966be-120">Conserver cette expression de filtre dans une orchestration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="966be-120">Retain this filter expression in your custom orchestration.</span></span>  
  
5.  <span data-ttu-id="966be-121">Dans le **Expression de filtre** boîte de dialogue, dans la colonne de propriété dans la première ligne ouvrir, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante, dans la colonne d’opérateur Sélectionnez  **==**  dans la liste déroulante, dans la colonne valeur, tapez le code PIP à trois chiffres, par exemple, tapez **3 a 4**.</span><span class="sxs-lookup"><span data-stu-id="966be-121">In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list, in the Operator column, select **==** from the drop-down list, in the Value column, type the three-digit PIP code, for example, type **3A4**.</span></span>  
  
6.  <span data-ttu-id="966be-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="966be-122">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="966be-123">Ouvrez le projet d’orchestration de processus privé par défaut répondeur (PrivateResponder.btproj) dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="966be-123">Open the default responder private-process orchestration project (PrivateResponder.btproj) in Orchestration Designer.</span></span> <span data-ttu-id="966be-124">Assurez-vous que le projet contient une référence de travail dans le fichier Microsoft.Solutions.BTARN.GlobalSchemas.dll.</span><span class="sxs-lookup"><span data-stu-id="966be-124">Make sure that the project has a working reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.</span></span>  
  
8.  <span data-ttu-id="966be-125">Double-cliquez sur **PrivateResponder.odx**.</span><span class="sxs-lookup"><span data-stu-id="966be-125">Double-click **PrivateResponder.odx**.</span></span>  
  
9. <span data-ttu-id="966be-126">Cliquez sur le **ReceiveFromPublicProcessResponder** forme réception, puis cliquez sur **modifier l’Expression de filtre**.</span><span class="sxs-lookup"><span data-stu-id="966be-126">Right-click the **ReceiveFromPublicProcessResponder** receive shape, and then click **Edit Filter Expression**.</span></span>  
  
10. <span data-ttu-id="966be-127">Dans le **Expression de filtre** boîte de dialogue, dans la colonne de propriété dans la première ligne ouvrir, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="966be-127">In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span> <span data-ttu-id="966be-128">Dans la colonne d’opérateur, sélectionnez **! =** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="966be-128">In the Operator column, select **!=** from the drop-down list.</span></span> <span data-ttu-id="966be-129">Dans la colonne valeur, tapez le code PIP à trois chiffres, par exemple, tapez «**3 a 4 »**.</span><span class="sxs-lookup"><span data-stu-id="966be-129">In the Value column, type the three-digit PIP code, for example, type "**3A4"**.</span></span>  
  
11. <span data-ttu-id="966be-130">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="966be-130">Click **OK**.</span></span>  
  
12. <span data-ttu-id="966be-131">Dans l’Explorateur de solutions, cliquez sur le projet qui contient l’orchestration, puis **Build**.</span><span class="sxs-lookup"><span data-stu-id="966be-131">In Solution Explorer, right-click the project that contains the orchestration and then click **Build**.</span></span>  
  
13. <span data-ttu-id="966be-132">Une fois que le projet a été généré avec succès, cliquez sur le projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="966be-132">After the project has been successfully built, right-click the project, and then click **Deploy**.</span></span>  
  
14. <span data-ttu-id="966be-133">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="966be-133">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
15. <span data-ttu-id="966be-134">Déplacer vers \< *lecteur*\>: \Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder, sélectionnez **PrivateResponder.odx**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="966be-134">Move to \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder, select **PrivateResponder.odx**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="966be-135">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="966be-135">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
17. <span data-ttu-id="966be-136">Une fois que le projet a été généré avec succès, cliquez sur le projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="966be-136">After the project has been successfully built, right-click the project, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966be-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="966be-137">See Also</span></span>  
 [<span data-ttu-id="966be-138">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="966be-138">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)