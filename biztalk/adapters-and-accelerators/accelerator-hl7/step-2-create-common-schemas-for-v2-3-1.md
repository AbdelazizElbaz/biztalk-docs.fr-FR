---
title: "Étape 2 : Créer des schémas courants pour V2.3.1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, common schemas
- common schemas
ms.assetid: db1a2206-559f-475a-803d-55522cce007e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d65e2860e2140a16749ad434ead77bf8a4f49eb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-common-schemas-for-v231"></a><span data-ttu-id="3ee02-102">Étape 2 : Créer des schémas courants pour V2.3.1</span><span class="sxs-lookup"><span data-stu-id="3ee02-102">Step 2: Create Common Schemas for V2.3.1</span></span>
<span data-ttu-id="3ee02-103">Les schémas V2.3.1 sont communément référencés schémas, ce qui vous permet de valider l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="3ee02-103">The V2.3.1 schemas are commonly referenced schemas, which you use to validate the message instance.</span></span>  
  
### <a name="to-create-a-common-schema-for-v231"></a><span data-ttu-id="3ee02-104">Pour créer un schéma commun pour V2.3.1</span><span class="sxs-lookup"><span data-stu-id="3ee02-104">To create a common schema for V2.3.1</span></span>  
  
1.  <span data-ttu-id="3ee02-105">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="3ee02-106">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-106">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="3ee02-107">Dans la section modèles, sélectionnez **BTAHL7V231Common projet**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-107">In the Templates section, select **BTAHL7V231Common Project**.</span></span>  
  
4.  <span data-ttu-id="3ee02-108">Dans le **nom** , entrez **BTAHL7V231Common projet** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="3ee02-108">In the **Name** box, enter **BTAHL7V231Common Project** as the project name.</span></span>  
  
5.  <span data-ttu-id="3ee02-109">Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-109">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="3ee02-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-110">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ee02-111">Dans l’Explorateur de solutions, les trois schémas (datatypes_231.xsd, segments_231.xsd et tablevalues_231.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="3ee02-111">In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.</span></span>  
  
7.  <span data-ttu-id="3ee02-112">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-112">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="3ee02-113">Dans la Page de propriétés BTAHL7V231Common, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-113">On the BTAHL7V231Common Property Page, click **Signing**.</span></span>  
  
9. <span data-ttu-id="3ee02-114">Sélectionnez le **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="3ee02-114">Select the **Sign the assembly** check box.</span></span>  
  
10. <span data-ttu-id="3ee02-115">Dans **choisir un fichier de clé de nom fort**, sélectionnez  **\<Parcourir... >** .</span><span class="sxs-lookup"><span data-stu-id="3ee02-115">In **Choose a strong name key file**, select **\<Browse…>** .</span></span>  
  
11. <span data-ttu-id="3ee02-116">Accédez à \<lecteur > : \Batching Tutorial, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-116">Browse to \<drive>:\Batching Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="3ee02-117">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Common projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="3ee02-117">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Deploy**.</span></span> <span data-ttu-id="3ee02-118">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="3ee02-118">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ee02-119">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="3ee02-119">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="3ee02-120">Passez à [étape 3 : ajouter un schéma d’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span><span class="sxs-lookup"><span data-stu-id="3ee02-120">Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span></span>