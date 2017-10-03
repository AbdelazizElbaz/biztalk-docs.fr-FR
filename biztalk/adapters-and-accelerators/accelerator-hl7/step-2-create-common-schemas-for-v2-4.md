---
title: "Étape 2 : Créer des schémas courants pour V2.4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, common schemas
ms.assetid: 333ae85a-a307-4ab1-97f4-4d7b986e91de
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07260c5f0d161698545ff7fd5b5177a5374f3d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-common-schemas-for-v24"></a><span data-ttu-id="c8d18-102">Étape 2 : Créer des schémas courants pour V2.4</span><span class="sxs-lookup"><span data-stu-id="c8d18-102">Step 2: Create Common Schemas for V2.4</span></span>
<span data-ttu-id="c8d18-103">Les schémas V2.4 sont communément référencés schémas, ce qui vous permet de valider les instances de message de requête et de réponse.</span><span class="sxs-lookup"><span data-stu-id="c8d18-103">The V2.4 schemas are commonly referenced schemas, which you use to validate the query and response message instances.</span></span>  
  
### <a name="to-create-the-common-schemas-for-v24"></a><span data-ttu-id="c8d18-104">Pour créer des schémas courants pour V2.4</span><span class="sxs-lookup"><span data-stu-id="c8d18-104">To create the common schemas for V2.4</span></span>  
  
1.  <span data-ttu-id="c8d18-105">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c8d18-106">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-106">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="c8d18-107">Dans le **modèles** liste, sélectionnez **BTAHL7V24Common projet**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-107">In the **Templates** list, select **BTAHL7V24Common Project**.</span></span>  
  
4.  <span data-ttu-id="c8d18-108">Dans le **nom** , tapez **Interrogative_24Schemas**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-108">In the **Name** field, type **Interrogative_24Schemas**.</span></span>  
  
5.  <span data-ttu-id="c8d18-109">Dans le champ de la Solution, sélectionnez **ajouter à la Solution**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-109">In the Solution field, select **Add to Solution**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c8d18-110">Dans l’Explorateur de solutions, notez que trois schémas (datatypes_24.xsd, segments_24.xsd et tablevalues_24.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="c8d18-110">In Solution Explorer, notice that three schemas (datatypes_24.xsd, segments_24.xsd, and tablevalues_24.xsd) are included in the project.</span></span>  
  
6.  <span data-ttu-id="c8d18-111">Dans l’Explorateur de solutions, cliquez sur **Interrogative_24Schemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-111">In Solution Explorer, right-click **Interrogative_24Schemas** project,and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="c8d18-112">Dans la boîte de dialogue Pages de propriétés Interrogative_24Schemas, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-112">In the Interrogative_24Schemas Property Pages dialog box, click **Assembly**.</span></span>  
  
8.  <span data-ttu-id="c8d18-113">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="c8d18-113">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
9. <span data-ttu-id="c8d18-114">Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\Interrogative didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-114">In the **Assembly Key File** dialog box, browse to \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="c8d18-115">Dans la boîte de dialogue Pages de propriétés Interrogative_24Schemas, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="c8d18-115">In the Interrogative_24Schemas Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
11. <span data-ttu-id="c8d18-116">Dans l’Explorateur de solutions, cliquez sur **Interrogative_24Schemas** de projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="c8d18-116">In Solution Explorer, right-click **Interrogative_24Schemas** project, and then click **Deploy**.</span></span> <span data-ttu-id="c8d18-117">Cliquez sur **OK** à la boîte de dialogue vous invitant à enregistrer les modifications apportées à la solution.</span><span class="sxs-lookup"><span data-stu-id="c8d18-117">Click **OK** to the dialog box asking you to save changes to the solution.</span></span> <span data-ttu-id="c8d18-118">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="c8d18-118">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8d18-119">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="c8d18-119">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="c8d18-120">Passez à [étape 3 : créer et déployer un projet de l’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md).</span><span class="sxs-lookup"><span data-stu-id="c8d18-120">Proceed to [Step 3: Create and Deploy a Trigger Event (Message) Project](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md).</span></span>