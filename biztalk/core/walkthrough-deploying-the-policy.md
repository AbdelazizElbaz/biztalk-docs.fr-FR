---
title: "Procédure pas à pas : Déploiement de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 205760e2-9cd4-496f-93cd-0f93bc5d3231
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d235fa0f6882ecd9e180aabd26999b1d7f73390
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-deploying-the-policy"></a><span data-ttu-id="13c61-102">Procédure pas à pas : Déploiement de la stratégie</span><span class="sxs-lookup"><span data-stu-id="13c61-102">Walkthrough: Deploying the Policy</span></span>
<span data-ttu-id="13c61-103">Cette procédure pas à pas fournit des instructions détaillées pour déployer le **ProcessPurchaseOrder** stratégie de trois manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="13c61-103">This walkthrough provides step-by-step instructions for deploying the **ProcessPurchaseOrder** policy in the following three ways:</span></span>  
  
-   <span data-ttu-id="13c61-104">en exportant et important la stratégie à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise ;</span><span class="sxs-lookup"><span data-stu-id="13c61-104">Exporting and importing the policy by using the Business Rules Engine Deployment Wizard.</span></span>  
  
-   <span data-ttu-id="13c61-105">en exportant la stratégie dans un fichier XML et en l'important d'un fichier XML par l'intermédiaire de la console Administration de BizTalk Server ;</span><span class="sxs-lookup"><span data-stu-id="13c61-105">Exporting the policy to an XML file and importing the policy from an XML file by using the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="13c61-106">en exportant la stratégie en tant que partie d'un fichier MSI et en important le fichier MSI par l'intermédiaire de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13c61-106">Exporting the policy as part of an MSI file and importing the MSI file by using BizTalk Server Administration console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13c61-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="13c61-107">Prerequisites</span></span>  
 <span data-ttu-id="13c61-108">Vous devez effectuer la [procédure pas à pas : exécution de la stratégie de suivi](../core/walkthrough-tracking-policy-execution.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="13c61-108">You must complete the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="13c61-109">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="13c61-109">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="13c61-110">Cette rubrique contient les trois procédures pas à pas suivantes :</span><span class="sxs-lookup"><span data-stu-id="13c61-110">This topic  contains the following three walkthroughs:</span></span>  
  
1.  <span data-ttu-id="13c61-111">La première procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="13c61-111">The first walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using the Business Rules Engine Deployment Wizard.</span></span> <span data-ttu-id="13c61-112">Le tableau ci-dessous décrit en détail les procédures internes qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="13c61-112">The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="13c61-113">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="13c61-113">Procedure title</span></span>|<span data-ttu-id="13c61-114">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="13c61-114">Procedure description</span></span>|  
    |---------------------|---------------------------|  
    |<span data-ttu-id="13c61-115">Pour exporter POVocabulary 1.0 et 1.1 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="13c61-115">To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard</span></span>|<span data-ttu-id="13c61-116">Fournit des instructions détaillées pour l’exportation des versions 1.0 et 1.1 de la **POVocabulary** vocabulaire XML des fichiers à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="13c61-116">Provides step-by-step instructions for exporting versions 1.0 and 1.1 of the **POVocabulary** vocabulary to XML files by using the Business Rules Engine Deployment Wizard.</span></span>|  
    |<span data-ttu-id="13c61-117">Pour exporter ProcessPurchaseOrder 1.3 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="13c61-117">To export ProcessPurchaseOrder 1.3 by using the Business Rules Engine Deployment Wizard</span></span>|<span data-ttu-id="13c61-118">Fournit des instructions détaillées pour l’exportation de la version 1.3 de la **ProcessPurchaseOrder** stratégie vers un fichier XML à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="13c61-118">Provides step-by-step instructions for exporting version 1.3 of the **ProcessPurchaseOrder** policy to an XML file by using the Business Rules Engine Deployment Wizard.</span></span>|  
    |<span data-ttu-id="13c61-119">Pour supprimer ProcessPurchaseOrder et POVocabulary</span><span class="sxs-lookup"><span data-stu-id="13c61-119">To delete ProcessPurchaseOrder and POVocabulary</span></span>|<span data-ttu-id="13c61-120">Fournit des instructions détaillées pour la suppression de la **ProcessPurchaseOrder** stratégie et **POVocabulary** vocabulaire afin que vous puissiez tester l’importation du XML des fichiers pour recréer ces derniers.</span><span class="sxs-lookup"><span data-stu-id="13c61-120">Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary so that you can test importing the XML files to re-create them.</span></span>|  
    |<span data-ttu-id="13c61-121">Pour importer POVocabulary 1.0 et 1.1 depuis un fichier XML et les recréer</span><span class="sxs-lookup"><span data-stu-id="13c61-121">To import from XML to re-create POVocabulary 1.0 and 1.1</span></span>|<span data-ttu-id="13c61-122">Fournit des instructions détaillées pour l’importation du fichier de vocabulaire XML que vous avez créé dans la première procédure pour recréer le **POVocabulary** vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="13c61-122">Provides step-by-step instructions for importing the vocabulary XML file you created in the first procedure to re-create the **POVocabulary** vocabulary.</span></span>|  
    |<span data-ttu-id="13c61-123">Pour vérifier que POVocabulary 1.0 et 1.1 ont été recréés</span><span class="sxs-lookup"><span data-stu-id="13c61-123">To verify that POVocabulary 1.0 and 1.1 are re-created</span></span>|<span data-ttu-id="13c61-124">Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que les versions 1.0 et 1.1 de **POVocabulary** sont recréés.</span><span class="sxs-lookup"><span data-stu-id="13c61-124">Provides step-by-step instructions for using the Business Rule Composer to verify that versions 1.0 and 1.1 of **POVocabulary** are re-created.</span></span>|  
    |<span data-ttu-id="13c61-125">Pour importer ProcessPurchaseOrder 1.3 depuis un fichier XML et la recréer</span><span class="sxs-lookup"><span data-stu-id="13c61-125">To import from XML to re-create ProcessPurchaseOrder 1.3</span></span>|<span data-ttu-id="13c61-126">Fournit des instructions détaillées pour l’importation du fichier XML de stratégie que vous avez créé dans la deuxième procédure pour recréer la version 1.3 de la **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-126">Provides step-by-step instructions for importing the policy XML file you created in the second procedure to re-create version 1.3 of the **ProcessPurchaseOrder** policy.</span></span>|  
    |<span data-ttu-id="13c61-127">Pour vérifier que ProcessPurchaseOrder 1.3 a été recréée</span><span class="sxs-lookup"><span data-stu-id="13c61-127">To verify that ProcessPurchaseOrder 1.3 is re-created</span></span>|<span data-ttu-id="13c61-128">Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que la version 1.3 de la **ProcessPurchaseOrder** stratégie est recréée.</span><span class="sxs-lookup"><span data-stu-id="13c61-128">Provides step-by-step instructions for using the Business Rule Composer to verify that version 1.3 of the **ProcessPurchaseOrder** policy is re-created.</span></span>|  
  
2.  <span data-ttu-id="13c61-129">La deuxième procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide d’un fichier XML exporté à partir de la console Administration de BizTalk Server suit tableau décrit les procédures dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="13c61-129">The second walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an XML file exported from the BizTalk Server Administration console The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="13c61-130">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="13c61-130">Procedure title</span></span>|<span data-ttu-id="13c61-131">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="13c61-131">Procedure description</span></span>|  
    |---------------------|---------------------------|  
    |<span data-ttu-id="13c61-132">Pour exporter la stratégie ProcessPurchaseOrder 1.3 et le vocabulaire POVocabulary dans un fichier XML</span><span class="sxs-lookup"><span data-stu-id="13c61-132">To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file</span></span>|<span data-ttu-id="13c61-133">Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour exporter les **ProcessPurchaseOrder** stratégie et le **POVocabulary** le vocabulaire vers un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="13c61-133">Provides step-by-step instructions for using the BizTalk Server Administration console to export the **ProcessPurchaseOrder** policy and the **POVocabulary** vocabulary to an XML file.</span></span>|  
    |<span data-ttu-id="13c61-134">Pour supprimer la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="13c61-134">To delete the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="13c61-135">Fournit des instructions détaillées pour la suppression de la **ProcessPurchaseOrder** stratégie à partir de **RuleTestApp** et la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="13c61-135">Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy from **RuleTestApp** and the rule engine database.</span></span>|  
    |<span data-ttu-id="13c61-136">Pour importer le fichier XML afin de recréer la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="13c61-136">To import the XML file to re-create the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="13c61-137">Fournit des instructions détaillées pour l’importation du fichier XML que vous avez exporté dans la première procédure pour recréer le **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-137">Provides step-by-step instructions for importing the XML file you exported in the first procedure to re-create the **ProcessPurchaseOrder** policy.</span></span>|  
    |<span data-ttu-id="13c61-138">Pour ajouter la stratégie ProcessPurchaseOrder à l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-138">To add the ProcessPurchaseOrder policy to the RuleTestApp application</span></span>|<span data-ttu-id="13c61-139">Fournit des instructions détaillées pour l’ajout du **ProcessPurchaseOrder** stratégie pour le **RuleTestApp** application.</span><span class="sxs-lookup"><span data-stu-id="13c61-139">Provides step-by-step instructions for adding the **ProcessPurchaseOrder** policy to the **RuleTestApp** application.</span></span>|  
  
3.  <span data-ttu-id="13c61-140">La troisième procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide d’un fichier MSI exporté à partir de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13c61-140">The third walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an MSI file exported from the BizTalk Server Administration console.</span></span> <span data-ttu-id="13c61-141">Le tableau ci-dessous décrit en détail les procédures internes qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="13c61-141">The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="13c61-142">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="13c61-142">Procedure title</span></span>|<span data-ttu-id="13c61-143">La procédure contient des instructions détaillées correspondant à l'objectif suivant :</span><span class="sxs-lookup"><span data-stu-id="13c61-143">Procedure has step-by-step instructions for</span></span>|  
    |---------------------|---------------------------------------------------|  
    |<span data-ttu-id="13c61-144">Pour exporter l'application RuleTestApp dans un fichier MSI</span><span class="sxs-lookup"><span data-stu-id="13c61-144">To export the RuleTestApp application to an MSI file</span></span>|<span data-ttu-id="13c61-145">Fournit des instructions détaillées pour l’exportation de la **RuleTestApp** application dans un fichier MSI, qui est utilisée ultérieurement pour recréer l’application.</span><span class="sxs-lookup"><span data-stu-id="13c61-145">Provides step-by-step instructions for exporting the **RuleTestApp** application to an MSI file, which is used later to re-create the application.</span></span>|  
    |<span data-ttu-id="13c61-146">Pour supprimer l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-146">To delete the RuleTestApp application</span></span>|<span data-ttu-id="13c61-147">Fournit des instructions détaillées pour la suppression de la **RuleTestApp** application afin que vous puissiez tester recréer l’application à l’aide du fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="13c61-147">Provides step-by-step instructions for deleting the **RuleTestApp** application so that you can test re-creating the application by using the MSI file.</span></span>|  
    |<span data-ttu-id="13c61-148">Pour vérifier la suppression de la stratégie ProcessPurchaseOrder et du vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="13c61-148">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted</span></span>|<span data-ttu-id="13c61-149">Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que le **ProcessPurchaseOrder** stratégie et vocabulaire POVocabulary sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="13c61-149">Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and POVocabulary vocabulary are deleted.</span></span>|  
    |<span data-ttu-id="13c61-150">Pour importer le fichier MSI afin de recréer l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-150">To import the MSI file to re-create the RuleTestApp application</span></span>|<span data-ttu-id="13c61-151">Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour importer le fichier MSI pour recréer le **RuleTestApp** application.</span><span class="sxs-lookup"><span data-stu-id="13c61-151">Provides step-by-step instructions for using the BizTalk Server Administration console to import the MSI file to re-create the **RuleTestApp** application.</span></span>|  
    |<span data-ttu-id="13c61-152">Pour vérifier l'ajout de la stratégie ProcessPurchaseOrder à l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-152">To verify that the ProcessPurchaseOrder policy is added to RuleTestApp</span></span>|<span data-ttu-id="13c61-153">Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour vérifier que le **ProcessPurchaseOrder** stratégie est ajoutée à la **RuleTestApp** application.</span><span class="sxs-lookup"><span data-stu-id="13c61-153">Provides step-by-step instructions for using the BizTalk Server Administration console to verify that the **ProcessPurchaseOrder** policy is added to the **RuleTestApp** application.</span></span>|  
    |<span data-ttu-id="13c61-154">Pour vérifier que la stratégie ProcessPurchaseOrder et le vocabulaire POVocabulary ont été recréés</span><span class="sxs-lookup"><span data-stu-id="13c61-154">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created</span></span>|<span data-ttu-id="13c61-155">Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que le **ProcessPurchaseOrder** stratégie et **POVocabulary** vocabulaire sont recréées.</span><span class="sxs-lookup"><span data-stu-id="13c61-155">Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary are re-created.</span></span>|  
    |<span data-ttu-id="13c61-156">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="13c61-156">To test the solution</span></span>|<span data-ttu-id="13c61-157">Fournit des instructions pas à pas pour le test de la solution.</span><span class="sxs-lookup"><span data-stu-id="13c61-157">Provides step-by-step instructions for testing the solution.</span></span>|  
  
## <a name="procedures-for-deploying-the-processpurchaseorder-policy-by-using-the-business-rules-engine-deployment-wizard"></a><span data-ttu-id="13c61-158">Procédures de déploiement de la stratégie ProcessPurchaseOrder à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="13c61-158">Procedures for Deploying the ProcessPurchaseOrder Policy by Using the Business Rules Engine Deployment Wizard</span></span>  
  
#### <a name="to-export-povocabulary-10-and-11-by-using-the-business-rules-engine-deployment-wizard"></a><span data-ttu-id="13c61-159">Pour exporter POVocabulary 1.0 et 1.1 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="13c61-159">To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard</span></span>  
  
1.  <span data-ttu-id="13c61-160">Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-160">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-161">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-161">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-162">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-162">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-163">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-163">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="13c61-164">Sur le **la tâche de déploiement** page, sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-164">On the **Deployment Task** page, select **Export Policy/Vocabulary to file from database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="13c61-165">Sur le **magasin de stratégies** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-165">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="13c61-166">Sur le **Exporter stratégie/vocabulaire** , cliquez sur **vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="13c61-166">On the **Export Policy/Vocabulary** page, click **Vocabulary**.</span></span>  
  
6.  <span data-ttu-id="13c61-167">Sélectionnez **povocabulary 1.0** dans la liste déroulante pour **stratégie/le vocabulaire**, tapez ou cliquez sur Parcourir pour spécifier le nom de fichier de sortie XML en tant que **C:\BRE-walkthroughs\POVocabulary10.xml**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-167">Select **POVocabulary.1.0** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary10.xml**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="13c61-168">Sur le **prêt** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-168">On the **Ready** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="13c61-169">Sur le **Exporter stratégie/vocabulaire** , cliquez sur **suivant.**</span><span class="sxs-lookup"><span data-stu-id="13c61-169">On the **Exporting Policy/Vocabulary** page, click **Next.**</span></span>  
  
9. <span data-ttu-id="13c61-170">Sélectionnez **réexécuter cet Assistant**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-170">Select **Run this wizard again**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="13c61-171">Étant donné que vous avez sélectionné **réexécuter cet Assistant**, le premier écran de l’Assistant s’affiche à nouveau.</span><span class="sxs-lookup"><span data-stu-id="13c61-171">Because you selected **Run this wizard again**, the first screen of the wizard appears again.</span></span>  
  
10. <span data-ttu-id="13c61-172">Répétez les étapes 2 à 6.</span><span class="sxs-lookup"><span data-stu-id="13c61-172">Repeat steps 2-6.</span></span>  
  
11. <span data-ttu-id="13c61-173">Sélectionnez **povocabulary 1.1** dans la liste déroulante pour **stratégie/le vocabulaire**, tapez ou cliquez sur Parcourir pour spécifier le nom de fichier de sortie XML en tant que **C:\BRE-walkthroughs\POVocabulary11.xml**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-173">Select **POVocabulary.1.1** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary11.xml**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="13c61-174">Répétez les étapes 8 et 9.</span><span class="sxs-lookup"><span data-stu-id="13c61-174">Repeat steps 8 and 9.</span></span>  
  
13. <span data-ttu-id="13c61-175">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-175">Click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-176">Vous devez exporter les versions 1.0 et 1.1 de **POVocabulary** car **ProcessPurchaseOrder** 1.3 repose sur les deux versions de **POVocabulary**.</span><span class="sxs-lookup"><span data-stu-id="13c61-176">You need to export both version 1.0 and version 1.1 of **POVocabulary** because **ProcessPurchaseOrder** 1.3 depends on both versions of **POVocabulary**.</span></span> <span data-ttu-id="13c61-177">Le **nombre maximal d’éléments autorisés** définition est utilisée à partir de la version 1.1 du vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="13c61-177">The **Maximum number of items allowed** definition is used from version 1.1 of the vocabulary.</span></span> <span data-ttu-id="13c61-178">Le **quantité requise** et **état de la demande** définitions sont utilisées à partir de la version 1.0.</span><span class="sxs-lookup"><span data-stu-id="13c61-178">The **Requested Quantity** and **Request Status** definitions are used from version 1.0.</span></span>  
  
#### <a name="to-export-processpurchaseorder-13-by-using-the-business-rule-engine-deployment-wizard"></a><span data-ttu-id="13c61-179">Pour exporter ProcessPurchaseOrder 1.3 à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="13c61-179">To export ProcessPurchaseOrder 1.3 by using the Business Rule Engine Deployment Wizard</span></span>  
  
1.  <span data-ttu-id="13c61-180">Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-180">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-181">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-181">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-182">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-182">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-183">Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-183">On the **Welcome to the Rules Engine Deployment Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="13c61-184">Sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-184">Select **Export Policy/Vocabulary to file from database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="13c61-185">Sur le **magasin de stratégies** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-185">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="13c61-186">Vérifiez que le **stratégie** option est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="13c61-186">Verify that the **Policy** option is selected.</span></span>  
  
6.  <span data-ttu-id="13c61-187">Sélectionnez **ProcessPurchaseOrder.1.3** dans la liste déroulante pour **stratégie/le vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="13c61-187">Select **ProcessPurchaseOrder.1.3** from the drop-down list for **Policy/Vocabulary**.</span></span>  
  
7.  <span data-ttu-id="13c61-188">Tapez ou cliquez sur Parcourir pour spécifier **C:\BRE-walkthroughs\ProcessPOPolicy13.xml** comme nom de fichier de sortie XML.</span><span class="sxs-lookup"><span data-stu-id="13c61-188">Type or browse to specify **C:\BRE-walkthroughs\ProcessPOPolicy13.xml** as the XML output file name.</span></span>  
  
8.  <span data-ttu-id="13c61-189">Cliquez sur **suivant** trois reprises, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-189">Click **Next** thrice, and then click **Finish**.</span></span>  
  
#### <a name="to-delete-processpurchaseorder-and-povocabulary"></a><span data-ttu-id="13c61-190">Pour supprimer ProcessPurchaseOrder et POVocabulary</span><span class="sxs-lookup"><span data-stu-id="13c61-190">To delete ProcessPurchaseOrder and POVocabulary</span></span>  
  
1.  <span data-ttu-id="13c61-191">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-191">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="13c61-192">Si vous avez Éditeur des règles d’entreprise déjà ouvrir, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-192">If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-193">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-193">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-194">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-194">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-195">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-195">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Delete**.</span></span> <span data-ttu-id="13c61-196">Si **supprimer** est désactivé, cliquez sur **Version 1.0**, puis cliquez sur **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="13c61-196">If **Delete** is disabled, right-click **Version 1.0**, and then click **Undeploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-197">Les versions de la stratégie déployée ne peuvent être supprimées.</span><span class="sxs-lookup"><span data-stu-id="13c61-197">The deployed policy versions cannot be deleted.</span></span> <span data-ttu-id="13c61-198">Vous devez annuler le déploiement d'une stratégie avant de pouvoir en supprimer une version.</span><span class="sxs-lookup"><span data-stu-id="13c61-198">You must undeploy a policy before deleting a policy version.</span></span>  
  
3.  <span data-ttu-id="13c61-199">Cliquez sur **Oui** dans la boîte de message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="13c61-199">Click **Yes** in the confirmation message box.</span></span>  
  
4.  <span data-ttu-id="13c61-200">Répétez les étapes 2 et 3 pour supprimer **Version 1.1**.</span><span class="sxs-lookup"><span data-stu-id="13c61-200">Repeat steps 2 and 3 to delete **Version 1.1**.</span></span>  
  
5.  <span data-ttu-id="13c61-201">Répétez les étapes 2 et 3 pour supprimer **Version 1.2**.</span><span class="sxs-lookup"><span data-stu-id="13c61-201">Repeat steps 2 and 3 to delete **Version 1.2**.</span></span>  
  
6.  <span data-ttu-id="13c61-202">Avec le bouton droit **Version 1.3 déployée**, puis cliquez sur **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="13c61-202">Right-click **Version 1.3 - Deployed**, and then click **Undeploy**.</span></span> <span data-ttu-id="13c61-203">Si le **annuler le déploiement** option est désactivée, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="13c61-203">If the **Undeploy** option is disabled, ignore this step.</span></span>  
  
7.  <span data-ttu-id="13c61-204">Dans la fenêtre Explorateur de faits, développez **vocabulaires**, avec le bouton droit **POVocabulary**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-204">In the Facts Explorer window, expand **Vocabularies**, right-click **POVocabulary**, and then click **Delete**.</span></span>  
  
#### <a name="to-import-from-xml-to-re-create-povocabulary-10-and-11"></a><span data-ttu-id="13c61-205">Pour importer POVocabulary 1.0 et 1.1 depuis un fichier XML et les recréer</span><span class="sxs-lookup"><span data-stu-id="13c61-205">To import from XML to re-create POVocabulary 1.0 and 1.1</span></span>  
  
1.  <span data-ttu-id="13c61-206">Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-206">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-207">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-207">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-208">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-208">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-209">Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-209">On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="13c61-210">Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-210">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="13c61-211">Sur le **magasin de stratégies** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-211">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="13c61-212">Rechercher et sélectionner le **POVocabulary10.xml** fichier que vous avez créé dans la première procédure.</span><span class="sxs-lookup"><span data-stu-id="13c61-212">Browse and select the **POVocabulary10.xml** file you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="13c61-213">Cliquez sur **ouvrir** ou double-cliquez sur **POVocabulary10.xml**.</span><span class="sxs-lookup"><span data-stu-id="13c61-213">Click **Open** or double-click **POVocabulary10.xml**.</span></span>  
  
7.  <span data-ttu-id="13c61-214">Cliquez sur **suivant** dans l’Assistant Déploiement du moteur des règles.</span><span class="sxs-lookup"><span data-stu-id="13c61-214">Click **Next** in the Business Rules Engine Deployment Wizard.</span></span>  
  
8.  <span data-ttu-id="13c61-215">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-215">Click **Next**.</span></span>  
  
9. <span data-ttu-id="13c61-216">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-216">Click **Next**.</span></span>  
  
10. <span data-ttu-id="13c61-217">Sélectionnez **réexécuter cet Assistant**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-217">Select **Run this wizard again**, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="13c61-218">Répétez les étapes 2 à 9 pour importer **POVocabulary11.xml**.</span><span class="sxs-lookup"><span data-stu-id="13c61-218">Repeat steps 2-9 to import **POVocabulary11.xml**.</span></span>  
  
12. <span data-ttu-id="13c61-219">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-219">Click **Finish**.</span></span>  
  
#### <a name="to-verify-that-povocabulary-10-and-11-are-re-created"></a><span data-ttu-id="13c61-220">Pour vérifier que POVocabulary 1.0 et 1.1 ont été recréés</span><span class="sxs-lookup"><span data-stu-id="13c61-220">To verify that POVocabulary 1.0 and 1.1 are re-created</span></span>  
  
1.  <span data-ttu-id="13c61-221">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-221">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="13c61-222">Si vous avez déjà ouvert, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-222">If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-223">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-223">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-224">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-224">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-225">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="13c61-225">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
3.  <span data-ttu-id="13c61-226">Développez **vocabulaires**, et vous devez voir **POVocabulary**.</span><span class="sxs-lookup"><span data-stu-id="13c61-226">Expand **Vocabularies**, and you should see **POVocabulary**.</span></span>  
  
4.  <span data-ttu-id="13c61-227">Développez **POVocabulary**, et vous devez voir **Version 1.0** et **Version 1.1**.</span><span class="sxs-lookup"><span data-stu-id="13c61-227">Expand **POVocabulary**, and you should see **Version 1.0** and **Version 1.1**.</span></span>  
  
#### <a name="to-import-from-xml-to-re-create-processpurchaseorder-13"></a><span data-ttu-id="13c61-228">Pour importer ProcessPurchaseOrder 1.3 depuis un fichier XML et la recréer</span><span class="sxs-lookup"><span data-stu-id="13c61-228">To import from XML to re-create ProcessPurchaseOrder 1.3</span></span>  
  
1.  <span data-ttu-id="13c61-229">Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-229">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-230">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-230">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-231">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-231">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-232">Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-232">On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="13c61-233">Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/le vocabulaire à base de données de base de données fichierPour à partir du fichier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-233">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from fileto database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="13c61-234">Sur le **magasin de stratégies** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-234">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="13c61-235">Rechercher et sélectionner le **ProcessPOPolicy13.xml** fichier que vous avez créé précédemment dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="13c61-235">Browse and select the **ProcessPOPolicy13.xml** file you created earlier in this walkthrough.</span></span>  
  
6.  <span data-ttu-id="13c61-236">Cliquez sur **ouvrir** ou double-cliquez sur **ProcessPOPolicy13.xml**.</span><span class="sxs-lookup"><span data-stu-id="13c61-236">Click **Open** or double-click **ProcessPOPolicy13.xml**.</span></span>  
  
7.  <span data-ttu-id="13c61-237">Cliquez sur **suivant** dans l’Assistant Déploiement du moteur des règles.</span><span class="sxs-lookup"><span data-stu-id="13c61-237">Click **Next** in the Business Rules Engine Deployment Wizard.</span></span>  
  
8.  <span data-ttu-id="13c61-238">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-238">Click **Next**.</span></span>  
  
9. <span data-ttu-id="13c61-239">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-239">Click **Next**, and then click **Finish**.</span></span>  
  
#### <a name="to-verify-that-processpurchaseorder-13-is-re-created"></a><span data-ttu-id="13c61-240">Pour vérifier que ProcessPurchaseOrder 1.3 a été recréée</span><span class="sxs-lookup"><span data-stu-id="13c61-240">To verify that ProcessPurchaseOrder 1.3 is re-created</span></span>  
  
1.  <span data-ttu-id="13c61-241">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-241">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="13c61-242">Si vous avez déjà ouvert, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-242">If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-243">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-243">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-244">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-244">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-245">Dans la fenêtre Explorateur de stratégies, développez **stratégies** et vous devez voir **ProcessPurchaseOrder**.</span><span class="sxs-lookup"><span data-stu-id="13c61-245">In the Policy Explorer window, expand **Policies** and you should see **ProcessPurchaseOrder**.</span></span>  
  
3.  <span data-ttu-id="13c61-246">Développez **ProcessPurchaseOrder** et vous devez voir **Version 1.3 publiée**.</span><span class="sxs-lookup"><span data-stu-id="13c61-246">Expand **ProcessPurchaseOrder** and you should see **Version 1.3 - Published**.</span></span>  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-xml-file-exported-from-the-biztalk-server-administration-console"></a><span data-ttu-id="13c61-247">Procédures de déploiement de la stratégie à l'aide d'un fichier XML exporté depuis la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="13c61-247">Procedures for Deploying the Policy by Using an XML file Exported from the BizTalk Server Administration Console</span></span>  
  
#### <a name="to-export-the-processpurchaseorder-13-policy-and-the-povocabulary-vocabulary-to-an-xml-file"></a><span data-ttu-id="13c61-248">Pour exporter la stratégie ProcessPurchaseOrder 1.3 et le vocabulaire POVocabulary dans un fichier XML</span><span class="sxs-lookup"><span data-stu-id="13c61-248">To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file</span></span>  
  
1.  <span data-ttu-id="13c61-249">Sur le **Démarrer** menu, ouvrez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13c61-249">On the **Start** menu, open [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span> <span data-ttu-id="13c61-250">Si l'outil est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-250">If you have the tool already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="13c61-251">Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez **RuleTestApp** .</span><span class="sxs-lookup"><span data-stu-id="13c61-251">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="13c61-252">Cliquez sur **stratégies** et assurez-vous que la stratégie ProcessPurchaseOrder 1.3 dans la liste.</span><span class="sxs-lookup"><span data-stu-id="13c61-252">Click **Policies** and make sure that you see the ProcessPurchaseOrder 1.3 policy in the list.</span></span>  
  
4.  <span data-ttu-id="13c61-253">Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="13c61-253">Right-click **ProcessPurchaseOrder**, and then click **Export**.</span></span>  
  
5.  <span data-ttu-id="13c61-254">Dans le **exporter les stratégies** boîte de dialogue zone, assurez-vous que le **ProcessPurchaseOrder** stratégie et le **POVocabulary** sont sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="13c61-254">In the **Export Policies** dialog box, make sure the **ProcessPurchaseOrder** policy and the **POVocabulary** are selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-255">Vous pouvez exporter toutes les stratégies dans une application dans un fichier XML en cliquant sur **RuleTest** , puis en cliquant sur **exporter** sur la **stratégies** menu.</span><span class="sxs-lookup"><span data-stu-id="13c61-255">You can export all the policies in an application to an XML file by right-clicking **RuleTest** and then clicking **Export** on the **Policies** menu.</span></span> <span data-ttu-id="13c61-256">Cela vous permet d'exporter l'ensemble des stratégies et le vocabulaire utilisés par cette application dans un fichier XML unique.</span><span class="sxs-lookup"><span data-stu-id="13c61-256">This way you can export all the policies and vocabulary used by this application to a single XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-257">Vous pouvez exporter toutes les stratégies dans toutes les applications dans un fichier XML en cliquant sur le **Applications** nœud, puis cliquez sur **exporter** sur la **stratégies** menu.</span><span class="sxs-lookup"><span data-stu-id="13c61-257">You can export all the policies in all the applications to an XML file by right-clicking the **Applications** node and then clicking **Export** on the **Policies** menu.</span></span> <span data-ttu-id="13c61-258">Cela vous permet d'exporter l'ensemble des stratégies et des vocabulaires utilisés par ces applications dans un fichier XML unique.</span><span class="sxs-lookup"><span data-stu-id="13c61-258">This way you can export all the policies and vocabularies used by all the applications into a single XML file.</span></span>  
  
6.  <span data-ttu-id="13c61-259">Spécifiez un nom de fichier de sortie XML (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**), puis cliquez sur **Ok**.</span><span class="sxs-lookup"><span data-stu-id="13c61-259">Specify an output XML file name (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**), and then click **Ok**.</span></span>  
  
#### <a name="to-delete-the-processpurchaseorder-policy"></a><span data-ttu-id="13c61-260">Pour supprimer la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="13c61-260">To delete the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="13c61-261">Dans la console Administration de BizTalk Server, cliquez sur **ProcessPurchaseOrder** dans la liste, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-261">In BizTalk Server Administration, right-click **ProcessPurchaseOrder** in the list, and then click **Remove**.</span></span>  
  
2.  <span data-ttu-id="13c61-262">Cliquez sur **Oui** dans les **supprimer la stratégie** boîte de message.</span><span class="sxs-lookup"><span data-stu-id="13c61-262">Click **Yes** in the **Remove Policy** message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-263">Si la stratégie affiche l'état déployé, il est impossible de la supprimer.</span><span class="sxs-lookup"><span data-stu-id="13c61-263">If the policy is in the deployed state, it cannot be removed.</span></span> <span data-ttu-id="13c61-264">Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **annuler le déploiement** pour annuler le déploiement de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-264">Right-click **ProcessPurchaseOrder**, and then click **Undeploy** to undeploy the policy.</span></span> <span data-ttu-id="13c61-265">Le **supprimer** élément de menu est disponible lorsque la stratégie est annulée.</span><span class="sxs-lookup"><span data-stu-id="13c61-265">The **Remove** menu item is available when the policy is undeployed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-266">Les vocabulaires sur lesquels le **ProcessPurchaseOrder** dépend de la stratégie, dans ce cas **POVocabulary**, sont également supprimés.</span><span class="sxs-lookup"><span data-stu-id="13c61-266">The vocabularies on which the **ProcessPurchaseOrder** policy depends, in this case **POVocabulary**, are also deleted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-267">Lorsque vous supprimez une stratégie d'une application, la stratégie et les vocabulaires sur lesquels elle repose sont supprimés de la base de données du moteur de règles et non uniquement de l'application.</span><span class="sxs-lookup"><span data-stu-id="13c61-267">When you remove a policy from an application, the policy and the vocabularies that it depends on are deleted from the rule engine database as well, not just from the application.</span></span>  
  
#### <a name="to-import-the-xml-file-to-re-create-the-processpurchaseorder-policy"></a><span data-ttu-id="13c61-268">Pour importer le fichier XML afin de recréer la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="13c61-268">To import the XML file to re-create the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="13c61-269">Dans la console Administration de BizTalk Server, développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="13c61-269">In BizTalk Server Administration, expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span>  
  
2.  <span data-ttu-id="13c61-270">Avec le bouton droit **Applications**, pointez sur **importation**, puis cliquez sur **stratégies**.</span><span class="sxs-lookup"><span data-stu-id="13c61-270">Right-click **Applications**, point to **Import**, and then click **Policies**.</span></span>  
  
3.  <span data-ttu-id="13c61-271">Recherchez et double-cliquez sur le fichier XML (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) que vous avez créé dans la première procédure.</span><span class="sxs-lookup"><span data-stu-id="13c61-271">Browse, and double-click the XML file (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) that you created in the first procedure.</span></span>  
  
4.  <span data-ttu-id="13c61-272">Développez  **\<tous les artefacts\>**  sous **Applications**.</span><span class="sxs-lookup"><span data-stu-id="13c61-272">Expand **\<All Artifacts\>** under **Applications**.</span></span>  
  
5.  <span data-ttu-id="13c61-273">Cliquez sur **stratégies**, et vous devez voir la version 1.3 de la **ProcessPurchaseOrder** stratégie dans la liste.</span><span class="sxs-lookup"><span data-stu-id="13c61-273">Click **Policies**, and you should see version 1.3 of the **ProcessPurchaseOrder** policy in the list.</span></span>  
  
6.  <span data-ttu-id="13c61-274">Appuyez sur F5 pour actualiser la vue.</span><span class="sxs-lookup"><span data-stu-id="13c61-274">Press F5 to refresh the view.</span></span> <span data-ttu-id="13c61-275">Le **ProcessPurchaseOrder** stratégie doit être dans le **pas publiées** état.</span><span class="sxs-lookup"><span data-stu-id="13c61-275">The **ProcessPurchaseOrder** policy should be in the **Not Published** state.</span></span>  
  
#### <a name="to-add-the-processpurchaseorder-policy-to-the-ruletestapp-application"></a><span data-ttu-id="13c61-276">Pour ajouter la stratégie ProcessPurchaseOrder à l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-276">To add the ProcessPurchaseOrder policy to the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="13c61-277">Dans la console Administration de BizTalk Server, cliquez sur **ProcessPurchaseOrder** stratégie, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="13c61-277">In BizTalk Server Administration, right-click **ProcessPurchaseOrder** policy, and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-278">Seules les stratégies publiées peuvent être ajoutées à une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="13c61-278">Only published policies can be added to a BizTalk application.</span></span>  
  
2.  <span data-ttu-id="13c61-279">Dans le **Applications** nœud, développez **RuleTestApp**.</span><span class="sxs-lookup"><span data-stu-id="13c61-279">In the **Applications** node, expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="13c61-280">Cliquez sur **stratégies** dans **RuleTestApp**.</span><span class="sxs-lookup"><span data-stu-id="13c61-280">Click **Policies** in **RuleTestApp**.</span></span>  
  
4.  <span data-ttu-id="13c61-281">Avec le bouton droit dans la liste de droite, pointez sur **ajouter**, puis cliquez sur **stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13c61-281">Right-click in the list on the right, point to **Add**, and then click **Policy**.</span></span>  
  
5.  <span data-ttu-id="13c61-282">Développez le **ProcessPurchaseOrder** nœud, sélectionnez la case à cocher **Version 1.3 (publiée)**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="13c61-282">Expand the **ProcessPurchaseOrder** node, select the check box for **Version 1.3 (Published)**, and then click **OK**.</span></span> <span data-ttu-id="13c61-283">.</span><span class="sxs-lookup"><span data-stu-id="13c61-283">.</span></span>  
  
6.  <span data-ttu-id="13c61-284">Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-284">Right-click **ProcessPurchaseOrder**, and then click **Deploy**.</span></span> <span data-ttu-id="13c61-285">Si vous ne voyez pas **ProcessPurchaseOrder** dans la liste, appuyez sur F5 pour actualiser l’affichage.</span><span class="sxs-lookup"><span data-stu-id="13c61-285">If you do not see **ProcessPurchaseOrder** in the list, press F5 to refresh the view.</span></span>  
  
7.  <span data-ttu-id="13c61-286">Cliquez sur **Oui** dans la boîte de message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="13c61-286">Click **Yes** in the confirmation message box.</span></span>  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-msi-file"></a><span data-ttu-id="13c61-287">Procédures de déploiement de la stratégie à l'aide d'un fichier MSI</span><span class="sxs-lookup"><span data-stu-id="13c61-287">Procedures for Deploying the Policy by Using an MSI File</span></span>  
  
#### <a name="to-export-the-ruletestapp-application-to-an-msi-file"></a><span data-ttu-id="13c61-288">Pour exporter l'application RuleTestApp dans un fichier MSI</span><span class="sxs-lookup"><span data-stu-id="13c61-288">To export the RuleTestApp application to an MSI file</span></span>  
  
1.  <span data-ttu-id="13c61-289">Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="13c61-289">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="13c61-290">Si l'outil est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-290">If you have the tool already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="13c61-291">Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="13c61-291">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="13c61-292">Avec le bouton droit **RuleTestApp**, pointez sur **exporter**, puis cliquez sur **fichier MSI**.</span><span class="sxs-lookup"><span data-stu-id="13c61-292">Right-click **RuleTestApp**, point to **Export**, and then click **MSI file**.</span></span>  
  
4.  <span data-ttu-id="13c61-293">Sur le **Bienvenue dans l’Assistant Exportation de fichier MSI** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-293">On the **Welcome to the Export MSI File Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="13c61-294">Sur le **sélectionner les ressources** page, passez en revue toutes les options par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-294">On the **Select Resources** page, review all the default options, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="13c61-295">Sur le **spécifier les hôtes IIS** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-295">On the **Specify IIS Hosts** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="13c61-296">Sur le **dépendances** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-296">On the **Dependencies** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="13c61-297">Sur le **Destination** , spécifiez le répertoire et le nom du fichier MSI **C:\BRE-Walkthroughs\RuleTestApp.msi**.</span><span class="sxs-lookup"><span data-stu-id="13c61-297">On the **Destination** page, specify the directory and name for the MSI as **C:\BRE-Walkthroughs\RuleTestApp.msi**.</span></span>  
  
9. <span data-ttu-id="13c61-298">Cliquez sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="13c61-298">Click **Export**.</span></span>  
  
10. <span data-ttu-id="13c61-299">Sur le **Résumé** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-299">On the **Summary** page, click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-300">Lorsque vous exportez l'application RuleTestApp, les stratégies et vocabulaires qu'elle utilise sont également exportés dans le fichier MSI.</span><span class="sxs-lookup"><span data-stu-id="13c61-300">When you export the RuleTestApp application, the policies and vocabularies used by the application are also exported in the MSI file.</span></span> <span data-ttu-id="13c61-301">Quand vous procéderez à l'importation du fichier MSI, le vocabulaire, l'application et l'application seront tous recréés.</span><span class="sxs-lookup"><span data-stu-id="13c61-301">Later, when you import the MSI file, the vocabulary, policy, and application are all re-created.</span></span>  
  
#### <a name="to-delete-the-ruletestapp-application"></a><span data-ttu-id="13c61-302">Pour supprimer l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-302">To delete the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="13c61-303">Dans la console Administration de BizTalk Server, cliquez sur **RuleTestApp**et vérifiez si le **supprimer** menu est activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="13c61-303">In BizTalk Server Administration, right-click **RuleTestApp**, and check if the **Delete** menu is enabled or disabled.</span></span>  
  
2.  <span data-ttu-id="13c61-304">Si **supprimer** est désactivé, cliquez sur **RuleTestApp**, cliquez sur **arrêter**, sélectionnez **arrêt complet - arrêter l’Instance**, puis cliquez sur  **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="13c61-304">If **Delete** is disabled, right-click **RuleTestApp**, click **Stop**, select **Full Stop - Terminate Instance**, and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="13c61-305">Avec le bouton droit **RuleTestApp**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-305">Right-click **RuleTestApp**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="13c61-306">Cliquez sur **Oui** pour confirmer la suppression.</span><span class="sxs-lookup"><span data-stu-id="13c61-306">Click **Yes** to confirm deletion.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-307">Lorsque vous supprimez une application, toutes les stratégies qu'elle contient, ainsi que les vocabulaires qui lui sont associés, sont également supprimés de la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="13c61-307">When you delete an application, all the policies in the application and dependent vocabularies are deleted from the rule engine database as well.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-deleted"></a><span data-ttu-id="13c61-308">Pour vérifier la suppression de la stratégie ProcessPurchaseOrder et du vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="13c61-308">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted</span></span>  
  
1.  <span data-ttu-id="13c61-309">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-309">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="13c61-310">Si vous avez Éditeur des règles d’entreprise déjà ouvert, appuyez sur F5 pour actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-310">If you have Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-311">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-311">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-312">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-312">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-313">Dans la fenêtre Explorateur de stratégies, développez **stratégies**et assurez-vous que la stratégie ProcessPurchaseOrder n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="13c61-313">In the Policy Explorer window, expand **Policies**, and make sure that the ProcessPurchaseOrder policy does not exist.</span></span>  
  
3.  <span data-ttu-id="13c61-314">Dans la fenêtre Explorateur de faits, développez **vocabulaires**et assurez-vous que POVocabulary n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="13c61-314">In the Facts Explorer window, expand **Vocabularies**, and make sure that POVocabulary does not exist.</span></span>  
  
#### <a name="to-import-the-msi-file-to-re-create-the-ruletestapp-application"></a><span data-ttu-id="13c61-315">Pour importer le fichier MSI afin de recréer l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-315">To import the MSI file to re-create the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="13c61-316">Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="13c61-316">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="13c61-317">Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-317">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="13c61-318">Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="13c61-318">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span>  
  
3.  <span data-ttu-id="13c61-319">Avec le bouton droit **Applications**, pointez sur **importation**, puis cliquez sur **fichier MSI**.</span><span class="sxs-lookup"><span data-stu-id="13c61-319">Right-click **Applications**, point to **Import**, and then click **MSI file**.</span></span>  
  
4.  <span data-ttu-id="13c61-320">Sur le **Bienvenue dans l’Assistant Importation de** page, recherchez et sélectionnez le fichier MSI (Ruletestapp) que vous avez exporté précédemment pour le **fichier MSI à importer** paramètre.</span><span class="sxs-lookup"><span data-stu-id="13c61-320">On the **Welcome to the Import Wizard** page, browse and select the MSI file (RuleTestApp.msi) you exported earlier for the **MSI file to import** setting.</span></span>  
  
5.  <span data-ttu-id="13c61-321">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-321">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="13c61-322">Sur le **paramètres de l’Application** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-322">On the **Application Settings** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="13c61-323">Sur le **paramètres d’environnement cible Application** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13c61-323">On the **Application Target Environment Settings** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="13c61-324">Sur le **résumé d’importation** , cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="13c61-324">On the **Import Summary** page, click **Import**.</span></span>  
  
9. <span data-ttu-id="13c61-325">Sur le **importation réussie** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-325">On the **Import Succeeded** page, click **Finish**.</span></span> <span data-ttu-id="13c61-326">Vous devez voir que la **RuleTestApp** application est créée sous **Applications** dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13c61-326">You should see that the **RuleTestApp** application is created under **Applications** in the BizTalk Server Administration console.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-is-added-to-ruletestapp"></a><span data-ttu-id="13c61-327">Pour vérifier l'ajout de la stratégie ProcessPurchaseOrder à l'application RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="13c61-327">To verify that the ProcessPurchaseOrder policy is added to RuleTestApp</span></span>  
  
1.  <span data-ttu-id="13c61-328">Développez **RuleTestApp** dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13c61-328">Expand **RuleTestApp** in the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="13c61-329">Sélectionnez **stratégies** et vous devez voir **ProcessPurchaseOrder** dans la liste dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="13c61-329">Select **Policies** and you should see **ProcessPurchaseOrder** in the list in the right pane.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-re-created"></a><span data-ttu-id="13c61-330">Pour vérifier que la stratégie ProcessPurchaseOrder et le vocabulaire POVocabulary ont été recréés</span><span class="sxs-lookup"><span data-stu-id="13c61-330">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created</span></span>  
  
1.  <span data-ttu-id="13c61-331">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13c61-331">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="13c61-332">S'il est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-332">If you have it already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-333">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="13c61-333">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="13c61-334">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="13c61-334">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="13c61-335">Dans la fenêtre Explorateur de stratégies, développez **stratégies**et vous assurer que **ProcessPurchaseOrder** existe.</span><span class="sxs-lookup"><span data-stu-id="13c61-335">In the Policy Explorer window, expand **Policies**, and make sure that **ProcessPurchaseOrder** exists.</span></span>  
  
3.  <span data-ttu-id="13c61-336">Dans la fenêtre Explorateur de faits, développez **vocabulaires**et vous assurer que **POVocabulary** existe.</span><span class="sxs-lookup"><span data-stu-id="13c61-336">In the Facts Explorer window, expand **Vocabularies**, and make sure that **POVocabulary** exists.</span></span>  
  
#### <a name="to-test-the-solution"></a><span data-ttu-id="13c61-337">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="13c61-337">To test the solution</span></span>  
  
1.  <span data-ttu-id="13c61-338">Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="13c61-338">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="13c61-339">Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="13c61-339">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="13c61-340">Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="13c61-340">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="13c61-341">Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-341">Right-click **RuleTestApp**, and then click **Start**.</span></span>  
  
4.  <span data-ttu-id="13c61-342">Cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="13c61-342">Click **Start**.</span></span>  
  
5.  <span data-ttu-id="13c61-343">Copie **SamplePO.xml** que vous avez créé dans [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) dans le répertoire d’entrée pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="13c61-343">Copy **SamplePO.xml** that you created in [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) to the input directory for the orchestration.</span></span>  
  
6.  <span data-ttu-id="13c61-344">Vous devez voir un fichier de sortie dans le répertoire de sortie de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="13c61-344">You should see an output file in the output directory for the orchestration.</span></span> <span data-ttu-id="13c61-345">Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="13c61-345">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
7.  <span data-ttu-id="13c61-346">Répétez les étapes 3 et 4 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**XYZ**).</span><span class="sxs-lookup"><span data-stu-id="13c61-346">Repeat steps 3 and 4 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**XYZ**).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="13c61-347">Commentaires</span><span class="sxs-lookup"><span data-stu-id="13c61-347">Comments</span></span>  
  
-   <span data-ttu-id="13c61-348">Il s’agit de **très important** pour n’oubliez pas que lorsque vous supprimez une stratégie à partir d’une application, vous ne supprimez pas uniquement l’association entre l’application et la stratégie ; vous également supprimer la stratégie et son vocabulaire de la règle moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="13c61-348">It is **very important** to remember that when you remove a policy from an application, you do not just remove the association between the application and the policy; you also delete the policy and its associated vocabulary from the rule engine database.</span></span>  
  
-   <span data-ttu-id="13c61-349">Lorsque vous démarrez une application, elle procède par défaut au déploiement automatique des stratégies.</span><span class="sxs-lookup"><span data-stu-id="13c61-349">When you start an application, by default, it deploys the policies automatically.</span></span> <span data-ttu-id="13c61-350">De même, lorsque vous arrêtez une application et sélectionnez **arrêt complet - arrêter les Instances**, les stratégies associées soient automatiquement annulés.</span><span class="sxs-lookup"><span data-stu-id="13c61-350">Similarly, when you stop an application and select **Full Stop - Terminate Instances**, the associated policies are undeployed automatically.</span></span> <span data-ttu-id="13c61-351">Lorsque vous sélectionnez **arrêt partiel - Suspendre les instances en cours d’exécution**, les stratégies associées ne sont pas automatiquement annulés.</span><span class="sxs-lookup"><span data-stu-id="13c61-351">When you select **Partial Stop - Suspend running instances**, the associated policies are not undeployed automatically.</span></span>  
  
-   <span data-ttu-id="13c61-352">Vous devez actualiser la vue de l'Éditeur des règles d'entreprise et de la console Administration de BizTalk Server pour vous assurer que vous avez devant vous les informations les plus récentes avant de procéder à la moindre opération.</span><span class="sxs-lookup"><span data-stu-id="13c61-352">You should refresh the views in Business Rule Composer and BizTalk Server Administration console to make sure you are looking at the latest information before performing any operation.</span></span>  
  
-   <span data-ttu-id="13c61-353">Si vous créez une nouvelle version d'une stratégie dont la version précédente est associée à une application BizTalk, vous devez ajouter manuellement la nouvelle version de la stratégie à l'application.</span><span class="sxs-lookup"><span data-stu-id="13c61-353">If you create a new version of the policy whose earlier version is associated with a BizTalk application, you should manually add the new version of the policy to the application.</span></span> <span data-ttu-id="13c61-354">Ne supprimez pas l'ancienne version de la stratégie, sauf si vous êtes sûr(e) de vouloir la supprimer du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="13c61-354">You should not remove the old version of the policy unless you really want to delete it from the rule engine database.</span></span>  
  
-   <span data-ttu-id="13c61-355">Vous pouvez fusionner deux ou plusieurs fichiers XML BRL (Business Rule Language) dans un seul fichier BRL avant de procéder à l'importation</span><span class="sxs-lookup"><span data-stu-id="13c61-355">You can merge two or more BRL (Business Rule Language XML file) files into a single BRL file before importing.</span></span> <span data-ttu-id="13c61-356">Le code ci-après illustre trois fichiers BRL :</span><span class="sxs-lookup"><span data-stu-id="13c61-356">The following code shows three BRL files.</span></span> <span data-ttu-id="13c61-357">Le premier fichier contient le **POVocabulary** vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="13c61-357">The first BRL file contains the **POVocabulary** vocabulary.</span></span> <span data-ttu-id="13c61-358">Le deuxième fichier BRL contient le **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-358">The second BRL file contains the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="13c61-359">Le troisième fichier BRL contient à la fois le **POVocabulary** vocabulaire et **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-359">The third BRL file contains both the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="13c61-360">Ce dernier fichier est créé selon les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="13c61-360">The third BRE file is created by performing the following steps:</span></span>  
  
    1.  <span data-ttu-id="13c61-361">Créer un nouveau fichier à l’aide de n’importe quel fichier éditeur et l’enregistrer dans un fichier XML (par exemple : POPolicyVocabulary.xml).</span><span class="sxs-lookup"><span data-stu-id="13c61-361">Create a new file using any file editor and save it as an XML file (for example: POPolicyVocabulary.xml).</span></span>  
  
    2.  <span data-ttu-id="13c61-362">Copiez l'intégralité du fichier XML depuis le fichier BRL file contenant le vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="13c61-362">Copy the entire XML content from the first BRL file containing the vocabulary.</span></span>  
  
    3.  <span data-ttu-id="13c61-363">Copiez le bloc de ruleset (commence par la \<ruleset\> balise et se termine par le \</ruleset\> balise) à partir de la deuxième fichier BRL.</span><span class="sxs-lookup"><span data-stu-id="13c61-363">Copy the ruleset block (starts with the \<ruleset\> tag and ends with the \</ruleset\> tag) from the second BRL file.</span></span>  
  
    4.  <span data-ttu-id="13c61-364">Enregistrez le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="13c61-364">Save the new file.</span></span> <span data-ttu-id="13c61-365">Vous pouvez importer ce fichier XML unique pour créer le **POVocabulary** vocabulaire et **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="13c61-365">You can import this single XML file to create the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13c61-366">L'ordre des nœuds du vocabulaire et de l'ensemble de règles dans le fichier BRL fusionné n'a pas d'importance.</span><span class="sxs-lookup"><span data-stu-id="13c61-366">It does not matter in which order the vocabulary and ruleset nodes are listed in the merged BRL file.</span></span> <span data-ttu-id="13c61-367">Le nœud de l'ensemble de règles peut se trouver avant le nœud du vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="13c61-367">You can have the ruleset node ahead of the vocabulary node.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
    </brl>  
  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
    ```