---
title: "Étapes de développement d’orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designing, orchestrations
- orchestrations, designing
- orchestrations, creating
- creating, orchestrations
- Copy Local property
ms.assetid: 556b1e6c-63a6-4805-a0a5-e555f198fe4e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd0a19754871a6e736365e622513b193dcbf06a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="steps-in-orchestration-development"></a><span data-ttu-id="10ae5-102">Étapes du développement d'orchestrations</span><span class="sxs-lookup"><span data-stu-id="10ae5-102">Steps in Orchestration Development</span></span>
<span data-ttu-id="10ae5-103">Pour développer une orchestration, vous devrez généralement effectuer les opérations de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ae5-103">To develop an orchestration, you typically perform the following basic actions:</span></span>  
  
-   <span data-ttu-id="10ae5-104">Ajouter des formes pour représenter vos processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="10ae5-104">Add shapes to represent your business processes.</span></span>  
  
     <span data-ttu-id="10ae5-105">Le Concepteur d'orchestration vous fournit une boîte à outils de formes qui peuvent être utilisées pour représenter diverses actions et autres abstractions.</span><span class="sxs-lookup"><span data-stu-id="10ae5-105">Orchestration Designer provides you with a toolbox of shapes that can be used to represent different actions or other abstractions.</span></span> <span data-ttu-id="10ae5-106">Pour plus d’informations, consultez [formes d’Orchestration](../core/orchestration-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-106">For more information, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
-   <span data-ttu-id="10ae5-107">Définir des schémas pour décrire le format de vos messages.</span><span class="sxs-lookup"><span data-stu-id="10ae5-107">Define schemas to describe the format of your messages.</span></span>  
  
     <span data-ttu-id="10ae5-108">Vous pouvez définir des schémas avec l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="10ae5-108">You can define schemas with BizTalk Editor.</span></span> <span data-ttu-id="10ae5-109">Pour plus d’informations, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-109">For more information, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span>  
  
-   <span data-ttu-id="10ae5-110">Définir des ports via lesquels les messages sont envoyés et reçus.</span><span class="sxs-lookup"><span data-stu-id="10ae5-110">Define ports through which messages are sent and received.</span></span>  
  
     <span data-ttu-id="10ae5-111">Vous pouvez définir des ports pour indiquer comment et où les messages sont envoyés et reçus.</span><span class="sxs-lookup"><span data-stu-id="10ae5-111">You can define ports to specify how and where messages are sent and received.</span></span> <span data-ttu-id="10ae5-112">Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-112">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
-   <span data-ttu-id="10ae5-113">Lier **envoyer** et **réception** formes aux ports.</span><span class="sxs-lookup"><span data-stu-id="10ae5-113">Bind **Send** and **Receive** shapes to ports.</span></span>  
  
     <span data-ttu-id="10ae5-114">Vous pouvez vous connecter votre **envoyer** et **réception** formes aux ports et spécifier les opérations de port qu’ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="10ae5-114">You can connect your **Send** and **Receive** shapes to ports and specify the port operations that they use.</span></span> <span data-ttu-id="10ae5-115">Pour plus d’informations, consultez [comment configurer la forme envoi](../core/how-to-configure-the-send-shape.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-115">For more information, see [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md).</span></span> <span data-ttu-id="10ae5-116">Consultez également [comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-116">Also see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).</span></span>  
  
-   <span data-ttu-id="10ae5-117">Attribuer ou transformer des données entre des messages.</span><span class="sxs-lookup"><span data-stu-id="10ae5-117">Assign or transform data between messages.</span></span>  
  
     <span data-ttu-id="10ae5-118">Vous pouvez utiliser la **construire un Message** forme pour affecter des valeurs de message ou de des transformations de message.</span><span class="sxs-lookup"><span data-stu-id="10ae5-118">You can use the **Construct Message** shape to assign message values or do message transformations.</span></span> <span data-ttu-id="10ae5-119">Pour plus d’informations, consultez [construction de Messages](../core/constructing-messages.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-119">For more information, see [Constructing Messages](../core/constructing-messages.md).</span></span>  
  
-   <span data-ttu-id="10ae5-120">Identifier tous les composants personnalisés que vous pourrez souhaiter écrire ou ajouter en tant que référence afin de travailler dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="10ae5-120">Identify any custom components that you might want to write or add as reference to work within your orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10ae5-121">Si le **copie locale** de l’assembly référencé est définie sur **True**, Orchestration ne sera pas en mesure de récupérer toutes les modifications apportées à l’assembly externe une fois que la référence de l’ajout initial a lieu Projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="10ae5-121">If the **Copy Local** property of the referenced assembly is set to **True**, Orchestration will not be able to pick up any changes made to the external assembly after the initial add reference takes place in BizTalk project.</span></span>  
  
-   <span data-ttu-id="10ae5-122">Définir et attribuer des variables d'orchestration pour gérer les données dans votre orchestration en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="10ae5-122">Define and assign orchestration variables to manage data in your running orchestration.</span></span>  
  
     <span data-ttu-id="10ae5-123">Vous pouvez vous servir du dossier Variables de la fenêtre Vue Orchestration afin de déclarer vos variables d'orchestration, et de l'Éditeur d'expression BizTalk pour modifier les expressions qui attribuent et utilisent les variables dans différentes formes.</span><span class="sxs-lookup"><span data-stu-id="10ae5-123">You can use the Variables folder in the Orchestration View window to declare your orchestration variables, and BizTalk Expression Editor to edit expressions that assign and use the variables in various shapes.</span></span> <span data-ttu-id="10ae5-124">Pour plus d’informations, consultez [les Types de données XLANG-s](../core/xlang-s-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-124">For more information, see [XLANG-s Data Types](../core/xlang-s-data-types.md).</span></span>  
  
-   <span data-ttu-id="10ae5-125">Créer votre orchestration pour vérifier qu'elle est bien complète.</span><span class="sxs-lookup"><span data-stu-id="10ae5-125">Build your orchestration to test it for completeness.</span></span>  
  
     <span data-ttu-id="10ae5-126">Vous créez votre orchestration en compilant le projet ou la solution qui la contient.</span><span class="sxs-lookup"><span data-stu-id="10ae5-126">You build your orchestration when you compile the project or solution that contains it.</span></span> <span data-ttu-id="10ae5-127">Pour plus d’informations, consultez [comment générer des Orchestrations](../core/how-to-build-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="10ae5-127">For more information, see [How to Build Orchestrations](../core/how-to-build-orchestrations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ae5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10ae5-128">See Also</span></span>  
 <span data-ttu-id="10ae5-129">[Création et l’exécution des Orchestrations](../core/building-and-running-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="10ae5-129">[Building and Running Orchestrations](../core/building-and-running-orchestrations.md) </span></span>  
 <span data-ttu-id="10ae5-130">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="10ae5-130">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="10ae5-131">Création d’Orchestrations à l’aide du Concepteur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="10ae5-131">Creating Orchestrations Using Orchestration Designer</span></span>](../core/creating-orchestrations-using-orchestration-designer.md)