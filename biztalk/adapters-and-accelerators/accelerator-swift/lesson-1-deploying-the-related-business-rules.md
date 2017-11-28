---
title: "Leçon 1 : Déploiement des règles métier connexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, deploying
- deploying, business rules
ms.assetid: f8f5b103-4b66-4836-8165-99692574961a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e52712730546847a821d53a5f8013fff4d553501
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-deploying-the-related-business-rules"></a><span data-ttu-id="b582d-102">Leçon 1 : Déploiement des règles métier connexes</span><span class="sxs-lookup"><span data-stu-id="b582d-102">Lesson 1: Deploying the Related Business Rules</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="b582d-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] inclut un programme dans A4SWIFT Software Development Kit (SDK) appelé l’utilitaire de déploiement du moteur de règles d’entreprise (BRE).</span><span class="sxs-lookup"><span data-stu-id="b582d-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes a program in the A4SWIFT Software Development Kit (SDK) called the Business Rule Engine (BRE) Deployment Utility.</span></span> <span data-ttu-id="b582d-104">Dans cette leçon, vous utilisez cet utilitaire pour inspecter un assembly pour les schémas déployés, déterminer les règles requises et déployer les stratégies pour chaque schéma et les vocabulaires nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b582d-104">In this lesson, you use this utility to inspect an assembly for deployed schemas, determine the required rules, and deploy the necessary vocabularies and policies for each schema.</span></span>  
  
 <span data-ttu-id="b582d-105">Vous pouvez également déployer des règles en utilisant les Guides de mise en production normes SWIFT (SRG) pour identifier les règles nécessaires, puis utiliser l’outil Éditeur des règles d’entreprise pour déployer les stratégies et vocabulaires.</span><span class="sxs-lookup"><span data-stu-id="b582d-105">You can also deploy rules by using the SWIFT Standards Release Guides (SRG) to identify the necessary rules and then use the Business Rule Composer tool to deploy the vocabularies and policies.</span></span>  
  
### <a name="to-deploy-the-related-business-rules"></a><span data-ttu-id="b582d-106">Pour déployer les règles d’entreprise connexes</span><span class="sxs-lookup"><span data-stu-id="b582d-106">To deploy the related business rules</span></span>  
  
1.  <span data-ttu-id="b582d-107">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour SWIFT**, puis cliquez sur **BRE Utilitaire de déploiement**.</span><span class="sxs-lookup"><span data-stu-id="b582d-107">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="b582d-108">Dans la boîte de dialogue Utilitaire de déploiement du moteur BRE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b582d-108">In the BRE Deployment Utility dialog box, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="b582d-109">Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez **SWIFTSchemas**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b582d-109">In the .NET Global Assembly Cache dialog box, select **SWIFTSchemas**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b582d-110">SWIFTSchemas fait référence à l’assembly déployé précédemment.</span><span class="sxs-lookup"><span data-stu-id="b582d-110">SWIFTSchemas refers to the assembly you previously deployed.</span></span>  
  
4.  <span data-ttu-id="b582d-111">Cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="b582d-111">Click **Deploy**.</span></span>  
  
     <span data-ttu-id="b582d-112">Selon les schémas que vous avez déployé avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE.</span><span class="sxs-lookup"><span data-stu-id="b582d-112">Based on the schemas you deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE.</span></span> <span data-ttu-id="b582d-113">Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant :</span><span class="sxs-lookup"><span data-stu-id="b582d-113">When complete, the BRE Deployment Utility displays the following message:</span></span>  
  
     <span data-ttu-id="b582d-114">**Fin du déploiement. Pour plus d’informations, consulter le fichier journal ou l’éditeur des règles d’entreprise.**</span><span class="sxs-lookup"><span data-stu-id="b582d-114">**Deployment has completed. View the log file or Business Rules Composer for details.**</span></span>  
  
5.  <span data-ttu-id="b582d-115">Fermez la boîte de dialogue Utilitaire de déploiement BRE SWIFT.</span><span class="sxs-lookup"><span data-stu-id="b582d-115">Close the SWIFT BRE Deployment Utility dialog box.</span></span>  
  
6.  <span data-ttu-id="b582d-116">Dans l’Explorateur Windows, accédez à \< *lecteur*> : \Documents and Settings\All Users\Application Data pour confirmer que le fichier journal **BREDeploymentLog.txt** apparaît dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="b582d-116">In Windows Explorer, browse to \<*drive*>:\Documents and Settings\All Users\Application Data to confirm that the log file **BREDeploymentLog.txt** appears in the folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b582d-117">Vous pouvez ouvrir le fichier journal à l’aide d’un éditeur de texte pour confirmer chacune des étapes de déploiement.</span><span class="sxs-lookup"><span data-stu-id="b582d-117">You can open the log file using a text editor to confirm each of the deployment steps.</span></span>  
  
7.  <span data-ttu-id="b582d-118">Redémarrez le Service de mise à jour de moteur de règle.</span><span class="sxs-lookup"><span data-stu-id="b582d-118">Restart the Rule Engine Update Service.</span></span> <span data-ttu-id="b582d-119">En cliquant sur **Démarrer**, puis sur **exécuter**, saisie **services.msc**, puis en cliquant sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b582d-119">Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**.</span></span> <span data-ttu-id="b582d-120">Dans le **Services (Local)** fenêtre, avec le bouton droit **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="b582d-120">In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="b582d-121">Passez à [leçon 2 : confirmer le déploiement à l’aide de l’outil de Composer de règle métier](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b582d-121">Proceed to [Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md).</span></span>