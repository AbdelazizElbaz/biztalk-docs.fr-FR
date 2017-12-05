---
title: "Utilitaire de déploiement BRE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5868172b566a12ab6299e0eaabe12fa2153bfb97
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="bre-deployment-utility"></a><span data-ttu-id="e372d-102">Utilitaire de déploiement BRE</span><span class="sxs-lookup"><span data-stu-id="e372d-102">BRE Deployment Utility</span></span>
<span data-ttu-id="e372d-103">Vous pouvez utiliser l’utilitaire de déploiement du moteur BRE à publier et déployer les vocabulaires de moteur de règles d’entreprise (BRE) et les stratégies requises pour un schéma SWIFT.</span><span class="sxs-lookup"><span data-stu-id="e372d-103">You can use the BRE Deployment Utility to publish and deploy the Business Rule Engine (BRE) vocabularies and policies required for a SWIFT schema.</span></span> <span data-ttu-id="e372d-104">Publication et le déploiement de ces stratégies et les vocabulaires sont requis pour activer la validation BRE pour le type de message.</span><span class="sxs-lookup"><span data-stu-id="e372d-104">Publishing and deploying these vocabularies and policies is required to enable BRE validation for the message type.</span></span>  
  
 <span data-ttu-id="e372d-105">Vous pouvez également déployer des règles d’entreprise en utilisant les Guides de mise en production de normes de SWIFT (SRGs) pour identifier les règles requises, puis en utilisant la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outil Éditeur des règles d’entreprise pour déployer les stratégies et vocabulaires.</span><span class="sxs-lookup"><span data-stu-id="e372d-105">You can also deploy business rules by using the SWIFT Standards Release Guides (SRGs) to identify the required rules, and then using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Composer tool to deploy the vocabularies and policies.</span></span> <span data-ttu-id="e372d-106">Toutefois, il est beaucoup plus facile d’à l’aide de l’utilitaire de déploiement du moteur BRE.</span><span class="sxs-lookup"><span data-stu-id="e372d-106">However, using the BRE Deployment Utility is much easier.</span></span>  
  
 <span data-ttu-id="e372d-107">L’utilitaire de déploiement du moteur BRE effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e372d-107">The BRE Deployment Utility accomplishes the following:</span></span>  
  
-   <span data-ttu-id="e372d-108">Examine l’assembly déployé que vous spécifiez et détermine les schémas de message que vous avez déployé l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e372d-108">Examines the deployed assembly that you specify and determines the message schemas that you deployed for the assembly.</span></span>  
  
-   <span data-ttu-id="e372d-109">Publie le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml les vocabulaires requis pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] le traitement des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="e372d-109">Publishes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml vocabularies required for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business rules processing.</span></span>  
  
-   <span data-ttu-id="e372d-110">Publie et déploie les SWIFT base stratégies (stratégie de référence, la stratégie d’identificateur de tiers et les stratégies de règles de réseau) associées avec les schémas de message.</span><span class="sxs-lookup"><span data-stu-id="e372d-110">Publishes and deploys the SWIFT base policies (reference policy, party identifier policy, and network rule policies) associated with the message schemas.</span></span>  
  
-   <span data-ttu-id="e372d-111">Publie et déploie la stratégie principal et la stratégie de validation associée à chaque schéma de message.</span><span class="sxs-lookup"><span data-stu-id="e372d-111">Publishes and deploys the master policy and validation policy associated with each message schema.</span></span>  
  
-   <span data-ttu-id="e372d-112">Génère un fichier journal qui indique toutes les étapes nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e372d-112">Generates a log file that indicates all the steps that it takes.</span></span> <span data-ttu-id="e372d-113">Ce fichier est BREDeploymentLog.txt dans les \< *lecteur*\>: \Documents and Settings\All Users\Application et recommencez.</span><span class="sxs-lookup"><span data-stu-id="e372d-113">This file is BREDeploymentLog.txt in the \<*drive*\>:\Documents and Settings\All Users\Application Data folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e372d-114">L’utilitaire de déploiement du moteur BRE ne déploie pas les stratégies de Master BIC et Validation BIC.</span><span class="sxs-lookup"><span data-stu-id="e372d-114">The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy.</span></span> <span data-ttu-id="e372d-115">Vous devez déployer à l’aide de l’Assistant Déploiement du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="e372d-115">You must deploy these using the Rule Engine Deployment wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e372d-116">Si vous avez installé [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] dans un répertoire par défaut (autre que C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), ou que vous travaillez sur un ordinateur 64 bits, l’utilitaire de déploiement du moteur BRE ne fonctionnera pas correctement tant que vous modifiez les chemins d’accès dans le Fichier bredeployment.exe.config modifié.</span><span class="sxs-lookup"><span data-stu-id="e372d-116">If you have installed [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] in a non-default directory (other than C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), or you are working on a 64-bit computer, the BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file.</span></span> <span data-ttu-id="e372d-117">Ce fichier de configuration se trouve dans le \< *lecteur*\>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools dossier.</span><span class="sxs-lookup"><span data-stu-id="e372d-117">This configuration file is located in the \<*drive*\>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools folder.</span></span> <span data-ttu-id="e372d-118">Pour mettre à jour la configuration de l’utilitaire, ouvrez BREDeployment.exe.config dans le bloc-notes et modifier les dossiers pour les stratégies de base, les schémas et les répertoires de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="e372d-118">To update the utility's configuration, open BREDeployment.exe.config in Notepad, and change the folders for the base policies, schemas, and vocabulary directories.</span></span>  
  
 <span data-ttu-id="e372d-119">Vous pouvez également utiliser l’utilitaire de déploiement à l’inverse de ce processus, l’annulation du déploiement et annulation de la publication les stratégies et vocabulaires.</span><span class="sxs-lookup"><span data-stu-id="e372d-119">You can also use the deployment utility to reverse this process, undeploying and unpublishing the policies and vocabularies.</span></span> <span data-ttu-id="e372d-120">L’utilitaire a deux déployer et annuler le déploiement de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e372d-120">The utility has both deploy and undeploy functionality.</span></span>  
  
### <a name="to-use-the-bre-deployment-utility"></a><span data-ttu-id="e372d-121">Pour utiliser l’utilitaire de déploiement du moteur BRE</span><span class="sxs-lookup"><span data-stu-id="e372d-121">To use the BRE Deployment Utility</span></span>  
  
1.  <span data-ttu-id="e372d-122">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **l’utilitaire de déploiement BRE**.</span><span class="sxs-lookup"><span data-stu-id="e372d-122">Click **Start**, point to **Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="e372d-123">Dans l’utilitaire de déploiement BRE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="e372d-123">In the BRE Deployment Utility, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="e372d-124">Sélectionnez l’ou les assemblys pour lesquels vous souhaitez publier et déployer des stratégies et des vocabulaires, puis cliquez sur déployé **OK**.</span><span class="sxs-lookup"><span data-stu-id="e372d-124">Select the deployed assembly or assemblies for which you want to publish and deploy vocabularies and policies, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e372d-125">Cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="e372d-125">Click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e372d-126">Selon les schémas que vous avez déployé avec cet assembly, l’utilitaire de déploiement du moteur BRE passe par le processus d’identification des règles associées et de les publier pour une utilisation avec le moteur BRE.</span><span class="sxs-lookup"><span data-stu-id="e372d-126">Based on the schemas that you deployed with that assembly, the BRE Deployment Utility goes through the process of identifying the related rules and publishing them for use with the BRE.</span></span> <span data-ttu-id="e372d-127">Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant : **fin du déploiement**.</span><span class="sxs-lookup"><span data-stu-id="e372d-127">When complete, the BRE Deployment Utility displays the following message: **Deployment has completed**.</span></span> <span data-ttu-id="e372d-128">Utilisez l’éditeur des règles d’entreprise pour vérifier la réussite du déploiement.</span><span class="sxs-lookup"><span data-stu-id="e372d-128">Use the Business Rule Composer to verify successful deployment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e372d-129">Pour annuler le déploiement de stratégies et des vocabulaires, cliquez sur **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="e372d-129">To undeploy the policies and vocabularies, click **Undeploy**.</span></span> <span data-ttu-id="e372d-130">Le processus d’annuler le déploiement n’annulez pas le déploiement vocabulaires A4SWIFT_CodeLists.xml et A4SWIFT_Functions.xml, lequel peuvent être utilisés par d’autres stratégies déployées.</span><span class="sxs-lookup"><span data-stu-id="e372d-130">The undeploy process does not undeploy the A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies, which might be used by other deployed policies.</span></span>  
  
5.  <span data-ttu-id="e372d-131">Recherchez \< *lecteur*\>: \Documents and Settings\All Users\Application Data pour confirmer que l’utilitaire créé le journal fichier BREDeploymentLog.txt.</span><span class="sxs-lookup"><span data-stu-id="e372d-131">Locate \<*drive*\>:\Documents and Settings\All Users\Application Data to confirm that the utility created the log file BREDeploymentLog.txt.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e372d-132">Vous pouvez ouvrir le fichier journal à l’aide d’un éditeur de texte pour vérifier chaque étape de déploiement.</span><span class="sxs-lookup"><span data-stu-id="e372d-132">You can open the log file by using a text editor to confirm each deployment step.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e372d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e372d-133">See Also</span></span>  
 [<span data-ttu-id="e372d-134">Outils</span><span class="sxs-lookup"><span data-stu-id="e372d-134">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)