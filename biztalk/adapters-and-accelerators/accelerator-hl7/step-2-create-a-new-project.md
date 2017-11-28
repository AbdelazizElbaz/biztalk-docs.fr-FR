---
title: "Étape 2 : Créer un nouveau projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, projects
- projects, creating
- message enrichment tutorial, projects
ms.assetid: 6e994845-53b8-4de8-a64f-32d36f7b5412
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78cfd1341100fe803679e81300609962a9c0e1f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-a-new-project"></a><span data-ttu-id="05b87-102">Étape 2 : Créer un nouveau projet</span><span class="sxs-lookup"><span data-stu-id="05b87-102">Step 2: Create a New Project</span></span>
<span data-ttu-id="05b87-103">Dans cette étape, vous générez une solution à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="05b87-103">In this step, you build a new solution by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] environment.</span></span> <span data-ttu-id="05b87-104">Tout d’abord, vous créez un nouveau projet (BTAHL7V22Common) qui contient les schémas courants trois (pour les types de données, les segments et les valeurs de la table) que les schémas de la version 2.2 du HL7 utilisent, y compris le schéma que vous utiliserez pour le message HL7 sortant.</span><span class="sxs-lookup"><span data-stu-id="05b87-104">First, you create a new project (BTAHL7V22Common) that contains the three common schemas (for data types, segments, and table values) that the HL7 V2.2 schemas use, including the schema that you will use for the outgoing HL7 message.</span></span> <span data-ttu-id="05b87-105">Ensuite, vous générez un autre projet (BTAHL7V2XCommon) qui contient le schéma standard couramment utilisé pour les en-têtes des messages de HL7 (MSH_25_GLO_DEF).</span><span class="sxs-lookup"><span data-stu-id="05b87-105">Second, you build another new project (BTAHL7V2XCommon) that contains the common standard schema used for headers in HL7 messages (MSH_25_GLO_DEF).</span></span>  
  
### <a name="to-create-a-new-project"></a><span data-ttu-id="05b87-106">Pour créer un nouveau projet</span><span class="sxs-lookup"><span data-stu-id="05b87-106">To create a new project</span></span>  
  
1.  <span data-ttu-id="05b87-107">Démarrer  **[!INCLUDE[vs2012](../../includes/vs2012-md.md)]** .</span><span class="sxs-lookup"><span data-stu-id="05b87-107">Start **[!INCLUDE[vs2012](../../includes/vs2012-md.md)]**.</span></span>  
  
2.  <span data-ttu-id="05b87-108">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="05b87-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="05b87-109">Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.</span><span class="sxs-lookup"><span data-stu-id="05b87-109">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
4.  <span data-ttu-id="05b87-110">Dans le **modèles** volet, cliquez sur **BTAHL7V22Common projet**.</span><span class="sxs-lookup"><span data-stu-id="05b87-110">In the **Templates** pane, click **BTAHL7V22Common Project**.</span></span>  
  
5.  <span data-ttu-id="05b87-111">Dans le **nom** , tapez **BTAHL7V22Common** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="05b87-111">In the **Name** field, type **BTAHL7V22Common** as the project name.</span></span>  
  
6.  <span data-ttu-id="05b87-112">Dans le **emplacement** , tapez  *\<lecteur >***: \Tutorial** comme chemin d’accès, puis cliquez sur **OK** pour ouvrir le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="05b87-112">In the **Location** field, type *\<drive>***:\Tutorial** as the path, and then click **OK** to open the new project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05b87-113">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) ajoute un nouveau projet à l’Explorateur de solutions avec les trois schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="05b87-113">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) adds a new project to Solution Explorer with the three common schemas:</span></span>  
  
    -   <span data-ttu-id="05b87-114">datatypes_22.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-114">datatypes_22.xsd</span></span>  
  
    -   <span data-ttu-id="05b87-115">segments_22.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-115">segments_22.xsd</span></span>  
  
    -   <span data-ttu-id="05b87-116">tablevalues_22.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-116">tablevalues_22.xsd</span></span>  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="05b87-117">crée le dossier du projet et les fichiers dans le \< *lecteur*> : \Tutorial\BTAHL7V22Common dossier.</span><span class="sxs-lookup"><span data-stu-id="05b87-117"> creates the project folder and files in the \<*drive*>:\Tutorial\BTAHL7V22Common folder.</span></span>  
  
7.  <span data-ttu-id="05b87-118">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="05b87-118">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
8.  <span data-ttu-id="05b87-119">Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.</span><span class="sxs-lookup"><span data-stu-id="05b87-119">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
9. <span data-ttu-id="05b87-120">Dans le **modèles** volet, cliquez sur **BTAHL7V2XCommon projet**.</span><span class="sxs-lookup"><span data-stu-id="05b87-120">In the **Templates** pane, click **BTAHL7V2XCommon Project**.</span></span>  
  
10. <span data-ttu-id="05b87-121">Dans le **nom** , tapez **BTAHL7V2XCommon** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="05b87-121">In the **Name** field, type **BTAHL7V2XCommon** as the project name.</span></span>  
  
11. <span data-ttu-id="05b87-122">Dans le **emplacement** , tapez  *\<lecteur >***: \Tutorial** en tant que le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="05b87-122">In the **Location** field, type *\<drive>***:\Tutorial** as the path.</span></span>  
  
12. <span data-ttu-id="05b87-123">Dans le **Solution** champ, sélectionnez **ajouter à la Solution**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="05b87-123">In the **Solution** field, select **Add to Solution**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="05b87-124">Ajoute un nouveau projet à l’Explorateur de solutions avec les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="05b87-124"> adds a new project to Solution Explorer with the following schemas:</span></span>  
  
    -   <span data-ttu-id="05b87-125">ACK_24_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-125">ACK_24_GLO_DEF.xsd</span></span>  
  
    -   <span data-ttu-id="05b87-126">ACK_25_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-126">ACK_25_GLO_DEF.xsd</span></span>  
  
    -   <span data-ttu-id="05b87-127">MSH_25_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="05b87-127">MSH_25_GLO_DEF.xsd</span></span>  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="05b87-128">crée le dossier du projet et les fichiers dans le  **\<lecteur > : \Tutorial\BTAHL7V22Common\BTAHL72XCommon** dossier.</span><span class="sxs-lookup"><span data-stu-id="05b87-128"> creates the project folder and files in the **\<drive>:\Tutorial\BTAHL7V22Common\BTAHL72XCommon** folder.</span></span>  
  
 <span data-ttu-id="05b87-129">Passez à [étape 3 : assigner un nom fort à l’Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="05b87-129">Proceed to [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b87-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05b87-130">See Also</span></span>  
 [<span data-ttu-id="05b87-131">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="05b87-131">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)