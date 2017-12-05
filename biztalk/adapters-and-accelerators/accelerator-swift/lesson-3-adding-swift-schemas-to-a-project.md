---
title: "Leçon 3 : Ajout de schémas SWIFT à un projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, adding to projects
- projects
ms.assetid: e17ef4b8-f060-44cc-b988-0f9f54deab90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fb5741b75fb9792cbabf46bf7a0402972d7bb4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-3-adding-swift-schemas-to-a-project"></a><span data-ttu-id="09e6d-102">Leçon 3 : Ajout de schémas SWIFT à un projet</span><span class="sxs-lookup"><span data-stu-id="09e6d-102">Lesson 3: Adding SWIFT Schemas to a Project</span></span>
<span data-ttu-id="09e6d-103">Maintenant que vous avez une solution et un nouveau projet, vous pouvez ajouter des éléments au projet.</span><span class="sxs-lookup"><span data-stu-id="09e6d-103">Now that you have a solution and a new project, you can add items to the project.</span></span> <span data-ttu-id="09e6d-104">Le premier élément que vous ajoutez est un schéma pour un message de paiement de SWIFT MT103.</span><span class="sxs-lookup"><span data-stu-id="09e6d-104">The first item you add is a schema for an MT103 SWIFT Payment message.</span></span> <span data-ttu-id="09e6d-105">Lorsque vous sélectionnez le modèle de schéma, l’Éditeur BizTalk démarre.</span><span class="sxs-lookup"><span data-stu-id="09e6d-105">When you select the Schema template, BizTalk Editor starts.</span></span>  
  
### <a name="to-add-a-new-schema-to-the-project"></a><span data-ttu-id="09e6d-106">Pour ajouter un nouveau schéma au projet</span><span class="sxs-lookup"><span data-stu-id="09e6d-106">To add a new schema to the project</span></span>  
  
1.  <span data-ttu-id="09e6d-107">Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="09e6d-107">In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="09e6d-108">Dans la boîte de dialogue Ajouter existant élément-SWIFTSchemas, accédez à  **\<* lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base schémas **.</span><span class="sxs-lookup"><span data-stu-id="09e6d-108">In the Add Existing Item-SWIFTSchemas dialog box, browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Schemas**.</span></span>  
  
3.  <span data-ttu-id="09e6d-109">Sélectionnez le **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** schémas, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="09e6d-109">Select the **SWIFT Base Types.xsd** and the **SWIFT Common Data Types.xsd** schemas, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09e6d-110">Le Types.xsd Base SWIFT et schémas SWIFT commun Types.xsd de données s’affichent dans l’Explorateur de solutions sous le projet SWIFTSchemas.</span><span class="sxs-lookup"><span data-stu-id="09e6d-110">The SWIFT Base Types.xsd and the SWIFT Common Data Types.xsd schemas appear in Solution Explorer under the SWIFTSchemas project.</span></span>  
  
4.  <span data-ttu-id="09e6d-111">Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="09e6d-111">In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.</span></span>  
  
5.  <span data-ttu-id="09e6d-112">Dans la boîte de dialogue Ajouter existant élément-SWIFTSchemas, accédez à la  **\<* lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103** dossier.</span><span class="sxs-lookup"><span data-stu-id="09e6d-112">In the Add Existing Item-SWIFTSchemas dialog box, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103** folder.</span></span>  
  
6.  <span data-ttu-id="09e6d-113">Sélectionnez le **MT103.xsd** schéma, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="09e6d-113">Select the **MT103.xsd** schema, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09e6d-114">Le nouveau schéma, MT103.xsd, apparaît dans l’Explorateur de solutions sous le projet SWIFTSchemas.</span><span class="sxs-lookup"><span data-stu-id="09e6d-114">The new schema, MT103.xsd, appears in Solution Explorer under the SWIFTSchemas project.</span></span>  
  
7.  <span data-ttu-id="09e6d-115">Dans l’Explorateur de solutions, double-cliquez sur **MT103.xsd** pour afficher le schéma dans l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="09e6d-115">In Solution Explorer, double-click **MT103.xsd** to view the schema in BizTalk Editor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09e6d-116">L’arborescence du schéma (volet gauche) et l’affichage XSD (volet droit) s’affichent dans l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="09e6d-116">The schema tree (left pane) and XSD view (right pane) appear in BizTalk Editor.</span></span>  
  
8.  <span data-ttu-id="09e6d-117">Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="09e6d-117">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="09e6d-118">Passez à [leçon 4 : création et déploiement de l’Assembly](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="09e6d-118">Proceed to [Lesson 4: Building and Deploying the Assembly](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md).</span></span>