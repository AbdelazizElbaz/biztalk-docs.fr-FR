---
title: "Déploiement des schémas d’enveloppe A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, envelope schemas
- A4SWIFT, deploying envelope schemas
- envelope schemas
- schemas, envelope schemas
ms.assetid: 6440608c-d30d-4d82-827a-8a4b2738db85
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8811f1dd056ca5a4ea4582d593af30e2ffc879f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-a4swift-envelope-schemas"></a><span data-ttu-id="a71f7-102">Déploiement des schémas d’enveloppe A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="a71f7-102">Deploying A4SWIFT Envelope Schemas</span></span>
<span data-ttu-id="a71f7-103">Chaque fois que vous configurez Message Repair et New Submission, vous devez inclure les schémas d’enveloppe dans les projets de schéma.</span><span class="sxs-lookup"><span data-stu-id="a71f7-103">You must include envelope schemas in schema projects whenever you set up Message Repair and New Submission.</span></span> <span data-ttu-id="a71f7-104">Un schéma d’enveloppe, tels que EnvelopeMT103.xsd, est requis pour écrire sur site MRSR.</span><span class="sxs-lookup"><span data-stu-id="a71f7-104">An envelope schema, such as EnvelopeMT103.xsd, is required to write to MRSR site.</span></span>  
  
 <span data-ttu-id="a71f7-105">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="a71f7-105">**Summary**</span></span>  
  
 <span data-ttu-id="a71f7-106">Ajoutez les schémas d’enveloppe à votre projet, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a71f7-106">Add envelope schemas to your project, as follows:</span></span>  
  
-   <span data-ttu-id="a71f7-107">Dans Visual Studio, pour le projet qui contient vos schémas de message, ajoutez un schéma d’enveloppe pour chaque schéma de message.</span><span class="sxs-lookup"><span data-stu-id="a71f7-107">In Visual Studio, to the project that contains your message schemas, add an envelope schema for each message schema.</span></span>  
  
-   <span data-ttu-id="a71f7-108">Ajoutez une référence à RuntimeSchemas.dll à un projet qui contient un ou plusieurs schémas d’enveloppe.</span><span class="sxs-lookup"><span data-stu-id="a71f7-108">Add a reference to RuntimeSchemas.dll to any project that contains one or more envelope schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a71f7-109">Ajout d’une référence à RuntimeSchemas.dll est requis pour un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] uniquement lorsque vous avez ajouté un schéma d’enveloppe pour Message Repair et New Submission au projet du projet.</span><span class="sxs-lookup"><span data-stu-id="a71f7-109">Adding a reference to RuntimeSchemas.dll is required for an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] project only when you have added an envelope schema for Message Repair and New Submission to the project.</span></span>  
  
-   <span data-ttu-id="a71f7-110">Ajoutez le schéma d’enveloppe de Message non analysé (EnvelopeUnparsedMessage.xsd) au projet.</span><span class="sxs-lookup"><span data-stu-id="a71f7-110">Add the Unparsed Message envelope schema (EnvelopeUnparsedMessage.xsd) to the project.</span></span>  
  
### <a name="to-add-a-swift-envelope-schema"></a><span data-ttu-id="a71f7-111">Pour ajouter un schéma d’enveloppe SWIFT</span><span class="sxs-lookup"><span data-stu-id="a71f7-111">To add a SWIFT envelope schema</span></span>  
  
1.  <span data-ttu-id="a71f7-112">Dans l’Explorateur de solutions de Visual Studio, ouvrez votre projet de schémas.</span><span class="sxs-lookup"><span data-stu-id="a71f7-112">In Solution Explorer of Visual Studio, open your schemas project.</span></span>  
  
2.  <span data-ttu-id="a71f7-113">Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-113">Right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="a71f7-114">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** balise.</span><span class="sxs-lookup"><span data-stu-id="a71f7-114">In the Add Reference dialog box, click the **Browse** tag.</span></span>  
  
4.  <span data-ttu-id="a71f7-115">Dans la boîte de dialogue Sélectionner le composant, ouvrez le **Regarder dans** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a71f7-115">In the Select Component dialog box, open the **Look in** drop-down list.</span></span> <span data-ttu-id="a71f7-116">Déplacer vers   ***\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\Assemblies**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-116">Move to ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\Assemblies**.</span></span> <span data-ttu-id="a71f7-117">Sélectionnez **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** dans la liste des assemblys, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-117">Select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** from the list of assemblies, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="a71f7-118">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-118">In the **Add Reference** dialog box, click **OK**.</span></span>  
  
6.  <span data-ttu-id="a71f7-119">Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-119">Right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
7.  <span data-ttu-id="a71f7-120">Dans la zone Ajouter un élément existant boîte de dialogue, dans le **Regarder dans** zone déroulante, accédez à  **\<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\>Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Categoryn\MTxxx**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-120">In the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Categoryn\MTxxx**.</span></span> <span data-ttu-id="a71f7-121">Sélectionnez le schéma d’enveloppe, par exemple, **EnvelopeMT103.xsd**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-121">Select the envelope schema, for example, **EnvelopeMT103.xsd**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a71f7-122">Dans la zone Ajouter un élément existant boîte de dialogue, dans le **Regarder dans** zone déroulante, accédez à.</span><span class="sxs-lookup"><span data-stu-id="a71f7-122">In the Add Existing Item dialog box, in the **Look in** drop-down box, move to.</span></span> <span data-ttu-id="a71f7-123">Sélectionnez le schéma d’enveloppe, par exemple, EnvelopeMT103.xsd et puis cliquez sur Ajouter.</span><span class="sxs-lookup"><span data-stu-id="a71f7-123">Select the envelope schema, for example, EnvelopeMT103.xsd, and then click Add.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a71f7-124">A4SWIFT ajoute le schéma d’enveloppe pour votre projet, comme indiqué dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="a71f7-124">A4SWIFT adds the envelope schema for your project, as shown in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="a71f7-125">Dans l’Explorateur de solutions, cliquez sur votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-125">In Solution Explorer, right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
9. <span data-ttu-id="a71f7-126">Si vous utilisez la fonctionnalité de Message Repair et New Submission, dans la boîte de dialogue Ajouter un élément existant dans le **Regarder dans** zone déroulante, accédez à  **\<* lecteur* \>: \Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Unparsed Message **.</span><span class="sxs-lookup"><span data-stu-id="a71f7-126">If using the Message Repair and New Submission feature, in the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<*drive*\>:\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Unparsed Message**.</span></span> <span data-ttu-id="a71f7-127">Sélectionnez **EnvelopeUnparsedMessage.xsd**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-127">Select **EnvelopeUnparsedMessage.xsd**, and then click **Add**.</span></span>  
  
10. <span data-ttu-id="a71f7-128">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-128">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
11. <span data-ttu-id="a71f7-129">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="a71f7-129">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>