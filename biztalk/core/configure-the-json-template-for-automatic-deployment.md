---
title: "Configurer le modèle JSON pour le déploiement automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 0b7755a6-5a5a-4a6b-8f99-ac12a5fbf3d4
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: dba2870a2a7f9aeaaa627dba00afca85f3ca71c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-json-template-for-automatic-deployment"></a><span data-ttu-id="464cc-102">Configurer le modèle JSON pour le déploiement automatique</span><span class="sxs-lookup"><span data-stu-id="464cc-102">Configure the JSON template for automatic deployment</span></span>


<span data-ttu-id="464cc-103">Lorsque vous générez vos applications à l’aide de Visual Studio Team Services, un nouveau fichier de projet BizTalk est créée – (.btaproj).</span><span class="sxs-lookup"><span data-stu-id="464cc-103">When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – (.btaproj).</span></span> <span data-ttu-id="464cc-104">Ce projet conserve toutes les applications BizTalk que vous créez à l’aide de VSTS.</span><span class="sxs-lookup"><span data-stu-id="464cc-104">This new project holds all the BizTalk applications that you build using VSTS.</span></span> 

<span data-ttu-id="464cc-105">Votre projet inclut le `BizTalkServerInventory.json` fichier.</span><span class="sxs-lookup"><span data-stu-id="464cc-105">Your project includes the `BizTalkServerInventory.json` file.</span></span> <span data-ttu-id="464cc-106">Dans ce fichier, ajouter vos assemblys BizTalk, ajoutez les fichiers de liaison pour votre application BizTalk et définir une séquence de déploiement.</span><span class="sxs-lookup"><span data-stu-id="464cc-106">In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and set a deployment sequence.</span></span> 

<span data-ttu-id="464cc-107">Cette rubrique montre comment mettre à jour le fichier json.</span><span class="sxs-lookup"><span data-stu-id="464cc-107">This topic shows you how to update the json file.</span></span> 

## <a name="add-assemblies-binding-files-and-deployment-sequence"></a><span data-ttu-id="464cc-108">Ajouter des assemblys, fichiers de liaison et la séquence de déploiement</span><span class="sxs-lookup"><span data-stu-id="464cc-108">Add assemblies, binding files, and deployment sequence</span></span>

1. <span data-ttu-id="464cc-109">Ouvrez le `BizTalkServerInventory.json` de fichiers dans votre **Application BizTalk Server** projet (.btaproj).</span><span class="sxs-lookup"><span data-stu-id="464cc-109">Open the `BizTalkServerInventory.json` file in your **BizTalk Server Application** project (.btaproj).</span></span>

2. <span data-ttu-id="464cc-110">Le modèle inclut les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="464cc-110">The template includes the following sections:</span></span> 

    | | |
    |---|---|
    |<span data-ttu-id="464cc-111">BizTalkAssemblies</span><span class="sxs-lookup"><span data-stu-id="464cc-111">BizTalkAssemblies</span></span> | <span data-ttu-id="464cc-112">Les assemblys utilisés dans vos applications</span><span class="sxs-lookup"><span data-stu-id="464cc-112">The assemblies used in your applications</span></span> |
    |<span data-ttu-id="464cc-113">BindingFiles</span><span class="sxs-lookup"><span data-stu-id="464cc-113">BindingFiles</span></span> | <span data-ttu-id="464cc-114">Les fichiers de liaison que vous référencez</span><span class="sxs-lookup"><span data-stu-id="464cc-114">The binding files you are referencing</span></span>|
    | <span data-ttu-id="464cc-115">DeploymentSequence</span><span class="sxs-lookup"><span data-stu-id="464cc-115">DeploymentSequence</span></span> | <span data-ttu-id="464cc-116">La séquence des éléments à installer</span><span class="sxs-lookup"><span data-stu-id="464cc-116">The sequence for the elements to be installed</span></span>|
    
    <span data-ttu-id="464cc-117">Exemple de modèle :</span><span class="sxs-lookup"><span data-stu-id="464cc-117">Sample template:</span></span> 
    
    ![Image de modèle FP1 Json 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > <span data-ttu-id="464cc-119">Selon la complexité de votre solution, les éléments que vous souhaitez dans la build doivent être référencées dans ce fichier de modèle JSON.</span><span class="sxs-lookup"><span data-stu-id="464cc-119">Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.</span></span>

3. <span data-ttu-id="464cc-120">Dans `BizTalkAssemblies`, ajoutez les assemblys utilisés par vos applications BizTalk :</span><span class="sxs-lookup"><span data-stu-id="464cc-120">In `BizTalkAssemblies`, add the assemblies used by your BizTalk applications:</span></span> 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. <span data-ttu-id="464cc-121">Dans `BindingsFiles`, ajoutez les fichiers de liaison pour vos applications BizTalk :</span><span class="sxs-lookup"><span data-stu-id="464cc-121">In `BindingsFiles`, add the binding files for your BizTalk applications:</span></span> 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. <span data-ttu-id="464cc-122">Dans `DeploymentSequence`, ajoutez les noms d’application dans l’ordre que vous souhaitez les déployé et installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="464cc-122">In `DeploymentSequence`, add the application names in the order you want them deployed and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span></span> 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```
    
6. <span data-ttu-id="464cc-123">**Enregistrer** vos modifications.</span><span class="sxs-lookup"><span data-stu-id="464cc-123">**Save** your changes.</span></span> 

<span data-ttu-id="464cc-124">Une fois terminé, la tâche de déploiement de Service Visual Studio Team honore les fichiers requis et la séquence d’installation.</span><span class="sxs-lookup"><span data-stu-id="464cc-124">Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence.</span></span> 

## <a name="next-step"></a><span data-ttu-id="464cc-125">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="464cc-125">Next step</span></span>
<span data-ttu-id="464cc-126">[Configurer les variables et jetons](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md) dans votre fichier de liaison pour déployer la même application BizTalk à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s.</span><span class="sxs-lookup"><span data-stu-id="464cc-126">[Configure tokens and variables](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md) in your binding file to deploy the same BizTalk application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s.</span></span>

 