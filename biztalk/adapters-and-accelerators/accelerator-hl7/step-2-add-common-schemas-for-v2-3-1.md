---
title: "Étape 2 : Ajouter des schémas courants pour v2.3.1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da98fe6c-4776-4cb8-8454-af3128dea4ab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba84c9f45c477aefe7615eca906c40014b06bd04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-common-schemas-for-v231"></a><span data-ttu-id="d5130-102">Étape 2 : Ajouter des schémas courants pour v2.3.1</span><span class="sxs-lookup"><span data-stu-id="d5130-102">Step 2: Add Common Schemas for v2.3.1</span></span>
<span data-ttu-id="d5130-103">Dans cette étape, vous créez un projet basé sur le modèle de projet de BTAHL7231Common.</span><span class="sxs-lookup"><span data-stu-id="d5130-103">In this step, you create a new project based on the BTAHL7231Common Project template.</span></span> <span data-ttu-id="d5130-104">Ce modèle contient les trois schémas courants (pour les types de données, les segments et les valeurs de table) qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise pour valider des instances de message v2.3.1.</span><span class="sxs-lookup"><span data-stu-id="d5130-104">This template contains the three common schemas (for data types, segments, and table values) that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses to validate v2.3.1 message instances.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d5130-105">utilise ces schémas courants avec les schémas HL7 v2.3.1, y compris le schéma que vous utiliserez pour les messages individuels dans le traitement par lots entrant (ADT ^ A03).</span><span class="sxs-lookup"><span data-stu-id="d5130-105"> uses these common schemas in conjunction with the HL7 v2.3.1 schemas, including the schema that you will use for the individual messages in the incoming batch (ADT^A03).</span></span>  
  
 <span data-ttu-id="d5130-106">À la fin de l’étape, vous attribuer une clé forte à l’assembly et déployez.</span><span class="sxs-lookup"><span data-stu-id="d5130-106">At the end of the step, you assign a strong key to the assembly and deploy.</span></span> <span data-ttu-id="d5130-107">Vous n’avez pas à créer une deuxième clé forte ; Vous pouvez utiliser la clé forte que vous avez créé dans [étape 1 : ajouter des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="d5130-107">You do not have to create a second strong key; you can use the strong key that you created in [Step 1: Add Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md).</span></span>  
  
### <a name="to-add-v231-common-schemas-and-deploy-the-assembly"></a><span data-ttu-id="d5130-108">Pour ajouter des schémas courants v2.3.1 et de déployer l’assembly</span><span class="sxs-lookup"><span data-stu-id="d5130-108">To add v2.3.1 common schemas and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="d5130-109">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="d5130-109">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d5130-110">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="d5130-110">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="d5130-111">Dans le **modèles** section, sélectionnez **BTAHL7V231Common projet**.</span><span class="sxs-lookup"><span data-stu-id="d5130-111">In the **Templates** section, select **BTAHL7V231Common Project**.</span></span>  
  
4.  <span data-ttu-id="d5130-112">Dans le **nom** , entrez **BTAHL7V231Common projet** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="d5130-112">In the **Name** box, enter **BTAHL7V231Common Project** as the project name.</span></span>  
  
5.  <span data-ttu-id="d5130-113">Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.</span><span class="sxs-lookup"><span data-stu-id="d5130-113">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="d5130-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5130-114">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5130-115">Dans l’Explorateur de solutions, les trois schémas (datatypes_231.xsd, segments_231.xsd et tablevalues_231.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="d5130-115">In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.</span></span>  
  
7.  <span data-ttu-id="d5130-116">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d5130-116">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="d5130-117">Dans la boîte de dialogue Pages de propriétés BTAHL7V231Common, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="d5130-117">On the BTAHL7V231Common Property Pages dialog box, click **Signing**.</span></span>  
  
9. <span data-ttu-id="d5130-118">Vérifiez **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="d5130-118">Check **Sign the assembly** check box.</span></span>  
  
10. <span data-ttu-id="d5130-119">Dans choisir un fichier de clé de nom fort dérouler la liste, sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="d5130-119">In Choose a strong name key file drop down list select.</span></span>  
  
11. <span data-ttu-id="d5130-120">Accédez à **: \Batching didacticiel**, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d5130-120">Browse to **:\Batching Tutorial**, select **key.snk**, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="d5130-121">Avec le bouton droit **BTAHL7V231Common**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d5130-121">Right-click **BTAHL7V231Common**, and then click **Deploy**.</span></span> <span data-ttu-id="d5130-122">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="d5130-122">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5130-123">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="d5130-123">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="d5130-124">Passez à [étape 3 : ajouter un schéma d’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span><span class="sxs-lookup"><span data-stu-id="d5130-124">Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span></span>