---
title: Composant de Pipeline message Editor | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, Message Editor Pipeline Component
- Message Editor Pipeline Component
- messages, editing
- pipelines, Message Editor Pipeline Component
ms.assetid: f2b22dea-54e8-410b-868f-2978139f438b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f5877fe04a87a8387340c8e4b004300f41e609e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="message-editor-pipeline-component"></a><span data-ttu-id="eff58-102">Composant de pipeline Message Editor</span><span class="sxs-lookup"><span data-stu-id="eff58-102">Message Editor Pipeline Component</span></span>
<span data-ttu-id="eff58-103">Ce composant vous permet de modifier automatiquement une partie d'un message en plusieurs parties dans un pipeline d'envoi ou de réception.</span><span class="sxs-lookup"><span data-stu-id="eff58-103">This component lets you edit automatically any part of a multipart message within a send or receive pipeline.</span></span> <span data-ttu-id="eff58-104">Vous ajoutez ce composant à un pipeline existant pour configurer le remplacement dans le cadre du traitement par défaut.</span><span class="sxs-lookup"><span data-stu-id="eff58-104">You add this component to an existing pipeline to set up the replacement as part of typical processing.</span></span>  
  
## <a name="building-the-message-editor-pipeline-component-into-an-existing-pipeline"></a><span data-ttu-id="eff58-105">Génération du composant de pipeline Message Editor dans un pipeline existant</span><span class="sxs-lookup"><span data-stu-id="eff58-105">Building the Message Editor Pipeline Component into an Existing Pipeline</span></span>  
 <span data-ttu-id="eff58-106">Pour utiliser le composant de pipeline Message Editor, vous devez l'ajouter à un pipeline existant.</span><span class="sxs-lookup"><span data-stu-id="eff58-106">To use the Message Editor Pipeline Component, you have to add the component to an existing pipeline.</span></span> <span data-ttu-id="eff58-107">Pour plus d’informations, consultez « Création de Pipelines avec le Concepteur de Pipeline » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="eff58-107">For more information, see "Creating Pipelines with Pipeline Designer" in BizTalk Server Help.</span></span>  
  
#### <a name="to-add-the-message-editor-pipeline-component-to-an-existing-pipeline"></a><span data-ttu-id="eff58-108">Pour ajouter le composant de pipeline Message Editor à un pipeline existant</span><span class="sxs-lookup"><span data-stu-id="eff58-108">To add the Message Editor Pipeline Component to an existing pipeline</span></span>  
  
1.  <span data-ttu-id="eff58-109">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eff58-109">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="eff58-110">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="eff58-110">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="eff58-111">Accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component, sélectionnez **MessageEditor.csproj**, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="eff58-111">Move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component, select **MessageEditor.csproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="eff58-112">Démarrez l’invite de commandes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eff58-112">Start Visual Studio command prompt.</span></span>  
  
5.  <span data-ttu-id="eff58-113">À l'invite de commandes, accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug.</span><span class="sxs-lookup"><span data-stu-id="eff58-113">At the command prompt, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug.</span></span>  
  
6.  <span data-ttu-id="eff58-114">À l'invite de commandes, tapez **sn -k MessageEditor.snk** pour créer une clé, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="eff58-114">At the command prompt, type **sn -k MessageEditor.snk** to create a key, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="eff58-115">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **MessageEditor**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eff58-115">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **MessageEditor**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="eff58-116">Dans la page **Propriété de MessageEditor** , cliquez sur l'onglet **Signature** , puis cochez la case **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="eff58-116">In the **MessageEditor Property** page, click **Signing** tab, and then click **Sign the assembly** checkbox.</span></span>  
  
9. <span data-ttu-id="eff58-117">Dans la liste déroulante **Choisir un fichier de clé de nom fort** , accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug et sélectionnez **MessageEditor.snk** , puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="eff58-117">In **Choose a strong name key file** drop-down, browse to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\ SDK\Message Editor Pipeline Component\obj\debug and select **MessageEditor.snk** and then click **Open**.</span></span>  
  
10. <span data-ttu-id="eff58-118">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **MessageEditor**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="eff58-118">In Solution Explorer, right-click **MessageEditor**, and then click **Build**.</span></span> <span data-ttu-id="eff58-119">Dans le volet de sortie, vérifiez que la génération a réussi.</span><span class="sxs-lookup"><span data-stu-id="eff58-119">Verify in the Output pane that the build succeeded.</span></span>  
  
11. <span data-ttu-id="eff58-120">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.</span><span class="sxs-lookup"><span data-stu-id="eff58-120">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
12. <span data-ttu-id="eff58-121">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] avec le bouton droit de l’Explorateur de solutions, le déplacement à C:\Program Files\Microsoft BizTalk 2013 Accelerator RosettaNet\SDK\Message éditeur Pipeline Component\obj\debug, **Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="eff58-121">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug, right-click **Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**, and then click **Copy**.</span></span>  
  
13. <span data-ttu-id="eff58-122">Accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline Components, cliquez avec le bouton droit sur **Composants de pipeline**, puis cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="eff58-122">Move to C:\Program Files\Microsoft BizTalk Server 2013\Pipeline Components, right-click **Pipeline Components**, and then click **Paste**.</span></span>  
  
14. <span data-ttu-id="eff58-123">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="eff58-123">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
15. <span data-ttu-id="eff58-124">Ouvrez le projet contenant le pipeline auquel vous voulez ajouter l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="eff58-124">Open the project that contains the pipeline to which you want to add the editor.</span></span>  
  
16. <span data-ttu-id="eff58-125">Dans l'Explorateur de solutions, double-cliquez sur le nom du pipeline pour l'ouvrir dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="eff58-125">In Solution Explorer, double-click the pipeline name to open the pipeline in Pipeline Designer.</span></span>  
  
17. <span data-ttu-id="eff58-126">Cliquez avec le bouton droit dans le volet Composants de pipeline BizTalk du volet Boîte à outils, puis cliquez sur **Ajouter/supprimer des éléments**.</span><span class="sxs-lookup"><span data-stu-id="eff58-126">Right-click in the BizTalk Pipeline Components pane of the Toolbox pane, and then click **Add/Remove Items**.</span></span>  
  
18. <span data-ttu-id="eff58-127">Dans la boîte de dialogue **Personnaliser la boîte à outils** , sous l'onglet **Composants de pipeline BizTalk** , sélectionnez **BTARN Message Editor Component**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eff58-127">In the **Customize Toolbox** dialog box, on the **BizTalk Pipeline Components** tab, select **BTARN Message Editor Component**, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="eff58-128">Dans le volet Composants de pipeline BizTalk du volet Boîte à outils, cliquez en maintenant le bouton enfoncé sur **BTARN Message Editor Component**, puis faites glisser le composant à l'emplacement souhaité dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="eff58-128">In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.</span></span>  
  
20. <span data-ttu-id="eff58-129">Dans le volet Composants de pipeline BizTalk du volet Boîte à outils, cliquez en maintenant le bouton enfoncé sur **BTARN Message Editor Component**, puis faites glisser le composant à l'emplacement souhaité dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="eff58-129">In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eff58-130">Il est recommandé d'ajouter le composant de pipeline Message Editor après la phase de désassemblage dans le composant de pipeline de réception ou pendant la phase de préassemblage du composant de pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="eff58-130">It is recommended that you add the Message Editor Pipeline Component after the Disassemble stage in the receive pipeline component or in the Pre-Assemble stage of the send pipeline component.</span></span>  
  
21. <span data-ttu-id="eff58-131">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le Concepteur de Pipeline, sélectionnez le **BTARN Message Editor Component** forme.</span><span class="sxs-lookup"><span data-stu-id="eff58-131">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Pipeline Designer, select the **BTARN Message Editor Component** shape.</span></span>  
  
22. <span data-ttu-id="eff58-132">Dans le volet Propriétés, dans la zone de texte associée à **Requête XPath**, tapez le nom de l'élément XPath dont vous voulez modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="eff58-132">In the Properties pane, in the text box associated with **XPath Query**, type the name of the XPath element for which you want to change the value.</span></span>  
  
23. <span data-ttu-id="eff58-133">Dans la zone de texte associée à **Valeur XPath**, tapez la valeur avec laquelle vous voulez définir l'élément XPath.</span><span class="sxs-lookup"><span data-stu-id="eff58-133">In the text box associated with **XPath Value**, type the value to which you want to set the XPath element.</span></span>  
  
24. <span data-ttu-id="eff58-134">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="eff58-134">In Solutions Explorer, right-click the project name, and then click **Build**.</span></span> <span data-ttu-id="eff58-135">Vérifiez que la génération aboutit.</span><span class="sxs-lookup"><span data-stu-id="eff58-135">Verify that the build succeeds.</span></span>  
  
25. <span data-ttu-id="eff58-136">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="eff58-136">In Solutions Explorer, right-click the project name, and then click **Deploy**.</span></span> <span data-ttu-id="eff58-137">Vérifiez que le déploiement aboutit.</span><span class="sxs-lookup"><span data-stu-id="eff58-137">Verify that the deployment succeeds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff58-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="eff58-138">Example</span></span>  
 <span data-ttu-id="eff58-139">Pour modifier la valeur de l'élément `ProprietaryDocumentIdentifier` dans le schéma PIP 0C1, ajoutez la requête XPath indiquée dans la section de code suivante à la propriété de la requête XPath du composant de pipeline Message Editor.</span><span class="sxs-lookup"><span data-stu-id="eff58-139">To change the value of the element `ProprietaryDocumentIdentifier` in the 0C1 PIP Schema, add the XPath Query shown in the following Code section to the XPath Query property of the Message Editor Pipeline Component.</span></span>  
  
```  
/*[local-name()='Pip0C1AsynchronousTestNotification' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='thisDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='ProprietaryDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']  
```  
  
 <span data-ttu-id="eff58-140">Pour obtenir une requête XPath complète, ouvrez le schéma dans l'Éditeur BizTalk, puis copier le Xpath de la propriété `Instance XPath` sous la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="eff58-140">To obtain a complete XPath Query, open the schema in BizTalk Editor, and then copy the Xpath from the `Instance XPath` property under the Properties window.</span></span> <span data-ttu-id="eff58-141">La requête XPath que vous fournissez doit contenir toutes les références d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eff58-141">The XPath Query that you provide should have all the namespace references in it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff58-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eff58-142">See Also</span></span>  
 [<span data-ttu-id="eff58-143">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="eff58-143">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)