---
title: "Configurer des jetons de l’environnement et les variables pour un déploiement automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 7d148f79fceb68b24feb45882ab89767369ed7e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a><span data-ttu-id="8bb34-102">Configurer des jetons de l’environnement et les variables pour un déploiement automatique</span><span class="sxs-lookup"><span data-stu-id="8bb34-102">Configure environmental tokens and variables for automatic deployment</span></span>
<span data-ttu-id="8bb34-103">Utiliser des variables Visual Studio Team Services (VSTS) dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="8bb34-103">Use Visual Studio Team Services (VSTS) variables in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding files.</span></span>

## <a name="overview"></a><span data-ttu-id="8bb34-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8bb34-104">Overview</span></span>
<span data-ttu-id="8bb34-105">Dans un environnement de VSTS, vous pouvez ajouter des variables et les définir sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="8bb34-105">In a VSTS environment, you can add variables, and set them to a value.</span></span> <span data-ttu-id="8bb34-106">Par exemple, vous pouvez créer un *sendPortPath* variable et définissez sa valeur à un dossier physique sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8bb34-106">For example, you can create a *sendPortPath* variable, and set its value to a physical folder on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="8bb34-107">Dans la [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison d’application, les variables configurables peuvent s’agir d’une balise XML, telles que le nom d’emplacement de réception, héberger, URI du port d’envoi et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8bb34-107">Within the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] application binding file, the configurable variables can be anything within an XML tag, such as the receive location name, host, send port URI, and so on.</span></span> 

<span data-ttu-id="8bb34-108">Ces variables sont spécifiques à votre environnement de VSTS et peut être utilisés pour déployer la même application à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements.</span><span class="sxs-lookup"><span data-stu-id="8bb34-108">These variables are specific to your VSTS environment, and can be used to deploy the same application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span> 

<span data-ttu-id="8bb34-109">Dans cette rubrique, nous montrons comment ajouter de la variable VSTS dans votre fichier de liaison et la création de la variable dans VSTS.</span><span class="sxs-lookup"><span data-stu-id="8bb34-109">In this topic, we show you how add the VSTS variable in your binding file, and how to create the variable within VSTS.</span></span> 

## <a name="configure-the-variables-in-your-biztalk-binding-file"></a><span data-ttu-id="8bb34-110">Configurer les variables dans votre fichier de liaison BizTalk</span><span class="sxs-lookup"><span data-stu-id="8bb34-110">Configure the variables in your BizTalk Binding file</span></span>

<span data-ttu-id="8bb34-111">L’exemple suivant fait partie d’un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison et montre comment appliquer les jetons.</span><span class="sxs-lookup"><span data-stu-id="8bb34-111">The following example is a part of a [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding file, and shows how to apply the tokens.</span></span>

1. <span data-ttu-id="8bb34-112">Ouvrez le fichier de liaison d’application :</span><span class="sxs-lookup"><span data-stu-id="8bb34-112">Open the application binding file:</span></span>

    ![Pack de fonctionnalités de BizTalk 1 liaison 1](../core/media/biztalk-feature-pack-1-binding-1.png)

2. <span data-ttu-id="8bb34-114">Recherchez l’élément que vous souhaitez modifier :</span><span class="sxs-lookup"><span data-stu-id="8bb34-114">Find the element you want to change:</span></span>

    ![Pack de fonctionnalités de BizTalk 1 liaison 2](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. <span data-ttu-id="8bb34-116">Supprimer la valeur par défaut et remplacez-la par vous variables : `$(YourValue)`.</span><span class="sxs-lookup"><span data-stu-id="8bb34-116">Remove the populated value, and replace it with you variables: `$(YourValue)`.</span></span> <span data-ttu-id="8bb34-117">Par exemple, entrez `$(SendPort1)`:</span><span class="sxs-lookup"><span data-stu-id="8bb34-117">For example, enter `$(SendPort1)`:</span></span> 

    ![Pack de 1 à 3 de liaison BizTalk](../core/media/biztalk-feature-pack-1-binding-3.png)


4. <span data-ttu-id="8bb34-119">Lorsque vous avez terminé, enregistrez le fichier de liaison et l’appliquer à votre modèle de génération JSON.</span><span class="sxs-lookup"><span data-stu-id="8bb34-119">When done, save the binding file, and apply it to your JSON build template.</span></span>
5. <span data-ttu-id="8bb34-120">Connectez-vous à votre solution de Service d’équipe Visual Studio, puis sélectionnez **créer et libérer**.</span><span class="sxs-lookup"><span data-stu-id="8bb34-120">Sign in to your Visual Studio Team Service solution, and select **Build and release**.</span></span>
6. <span data-ttu-id="8bb34-121">Accédez à **version**.</span><span class="sxs-lookup"><span data-stu-id="8bb34-121">Go to **Release**.</span></span> <span data-ttu-id="8bb34-122">Sélectionnez votre **définition de la version**, ou créez-en un.</span><span class="sxs-lookup"><span data-stu-id="8bb34-122">Select your **Release definition**, or create a new one.</span></span>
7. <span data-ttu-id="8bb34-123">Sous **environnements**, sélectionnez **ajouter un nouvel environnement**, ou modifier dans un environnement existant :</span><span class="sxs-lookup"><span data-stu-id="8bb34-123">Under **Environments**, select **Add a new environment**, or change to an existing environment:</span></span> 

    ![Ajouter un nouvel environnement](../core/media/add-a-new-environment.png)

8. <span data-ttu-id="8bb34-125">Cliquez sur le bouton de sélection, puis sélectionnez **configurer les variables**:</span><span class="sxs-lookup"><span data-stu-id="8bb34-125">Click the ellipses, and select **configure variables**:</span></span>

    ![configurer les variables](../core/media/configure-variables.png)

9. <span data-ttu-id="8bb34-127">En ajoutant les variables pour chaque environnement, en utilisant les noms de jeton créés dans le fichier de liaison, vous pouvez déployer vos applications dans plusieurs environnements avec des valeurs différentes :</span><span class="sxs-lookup"><span data-stu-id="8bb34-127">By adding the variables for each environment, using the token names created in the binding file, you can deploy your applications to multiple environments with different values:</span></span>

    ![variables d’environnement spécifiques](../core/media/environment-specific-variables.png)
    
10. <span data-ttu-id="8bb34-129">Sélectionnez **OK** pour enregistrer les nouvelles variables.</span><span class="sxs-lookup"><span data-stu-id="8bb34-129">Select **OK** to save the new variables.</span></span>
11. <span data-ttu-id="8bb34-130">Une fois la build est lancée, les valeurs sont ajoutées à partir du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8bb34-130">Once the build is initiated, the values are added from binding file.</span></span>

## <a name="next-step"></a><span data-ttu-id="8bb34-131">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="8bb34-131">Next step</span></span>
[<span data-ttu-id="8bb34-132">Ajouter une application BizTalk dans VSTS</span><span class="sxs-lookup"><span data-stu-id="8bb34-132">Add a BizTalk application to VSTS</span></span>](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)