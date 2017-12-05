---
title: "Étape 2 : Mettre à jour et déployer la Solution du didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03adfdd-1160-4e8c-a564-3acb2ecd0476
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67fd3d34f25dd409121a3a21c9eb419b4aadce6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-update-and-deploy-the-tutorial-solution"></a><span data-ttu-id="70846-102">Étape 2 : Mettre à jour et déployer la Solution du didacticiel</span><span class="sxs-lookup"><span data-stu-id="70846-102">Step 2: Update and Deploy the Tutorial Solution</span></span>
<span data-ttu-id="70846-103">![Étape 2 sur 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span><span class="sxs-lookup"><span data-stu-id="70846-103">![Step 2 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span></span>  
  
 <span data-ttu-id="70846-104">Au cours de cette étape, vous allez mettre à jour la solution fournie pour ce didacticiel, puis générer et déployer l'assembly du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="70846-104">In this step you update the solution provided for this tutorial, and then build and deploy the tutorial assembly.</span></span> <span data-ttu-id="70846-105">Les éléments nécessaires à ce didacticiel (schéma, pipeline d'envoi personnalisé et mappage) ont déjà été créés.</span><span class="sxs-lookup"><span data-stu-id="70846-105">For the purposes of this tutorial, the necessary schema, custom send pipeline, and map have already been created.</span></span> <span data-ttu-id="70846-106">Le mappage permet de convertir les données EDI 850 au format requis par votre système de commande.</span><span class="sxs-lookup"><span data-stu-id="70846-106">The map is used to convert the 850 EDI data into the format required by your Order System.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70846-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="70846-107">Prerequisites</span></span>  
 <span data-ttu-id="70846-108">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70846-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-enable-the-edi-inbound-processing-solution-to-be-built-in-visual-studio"></a><span data-ttu-id="70846-109">Pour activer la génération de la solution EDI Inbound Processing dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70846-109">To enable the EDI Inbound Processing solution to be built in Visual Studio</span></span>  
  
1.  <span data-ttu-id="70846-110">Démarrer **Microsoft Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="70846-110">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="70846-111">Si vous ne démarrez pas Visual Studio avec des privilèges d'administrateur, une erreur est générée lors du déploiement de la solution vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70846-111">If you do not start Visual Studio with administrator privileges, you will get an error while deploying the solution to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="70846-112">Dans Visual Studio, cliquez sur **fichier**, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="70846-112">In Visual Studio, click **File**, point to **Open**, and then click **Project/Solution**.</span></span> <span data-ttu-id="70846-113">Déplacer vers [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial, sélectionnez **EDI Inbound Processing.sln**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="70846-113">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial, select **EDI Inbound Processing.sln**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70846-114">Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI.</span><span class="sxs-lookup"><span data-stu-id="70846-114">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="70846-115">Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span><span class="sxs-lookup"><span data-stu-id="70846-115">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
3.  <span data-ttu-id="70846-116">Cliquez sur le **Inbound_EDI** de projet dans l’Explorateur de solutions, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="70846-116">Right-click the **Inbound_EDI** project in the Solution Explorer, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="70846-117">Dans l’arborescence de la **les Pages de propriétés de Inbound_EDI** boîte de dialogue, sélectionnez **déploiement** et dans le **Server** champ vous assurer que le nom de votre ordinateur est entré.</span><span class="sxs-lookup"><span data-stu-id="70846-117">In the console tree of the **Inbound_EDI Property Pages** dialog box, select  **Deployment** and in the **Server** field ensure that your computer name is entered.</span></span>  
  
5.  <span data-ttu-id="70846-118">Dans l’arborescence de la console, cliquez sur **signature** , puis sélectionnez **signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="70846-118">In the console tree, click **Signing** and then select **Sign the assembly**.</span></span> <span data-ttu-id="70846-119">Pour **choisir un fichier de nom fort de la clé**, sélectionnez \< **nouveau...**  \> et entrez **keyfile.snk** comme le **nom de fichier de clé**.</span><span class="sxs-lookup"><span data-stu-id="70846-119">For **Choose a strong key name file**, select \<**New…**\> and enter  **keyfile.snk** as the **Key file name**.</span></span> <span data-ttu-id="70846-120">Désactivez **protéger mon fichier de clé avec un mot de passe** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70846-120">Clear **Protect my key file with a password** and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="70846-121">Fermer le **les Pages de propriétés de Inbound_EDI** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="70846-121">Close the **Inbound_EDI Property Pages** dialog box.</span></span>  
  
### <a name="to-deploy-the-project"></a><span data-ttu-id="70846-122">Pour déployer le projet</span><span class="sxs-lookup"><span data-stu-id="70846-122">To deploy the project</span></span>  
  
1.  <span data-ttu-id="70846-123">Dans l’Explorateur de solutions, double-cliquez sur le **X12_00401_850.xsd** schéma.</span><span class="sxs-lookup"><span data-stu-id="70846-123">In Solution Explorer, double-click the **X12_00401_850.xsd** schema.</span></span> <span data-ttu-id="70846-124">Vérifiez qu'il est ouvert.</span><span class="sxs-lookup"><span data-stu-id="70846-124">Confirm that it opens.</span></span>  
  
2.  <span data-ttu-id="70846-125">Dans l’Explorateur de solutions, double-cliquez sur le **Inbound4010850_to_OrderFile.btm** carte.</span><span class="sxs-lookup"><span data-stu-id="70846-125">In Solution Explorer, double-click the **Inbound4010850_to_OrderFile.btm** map.</span></span> <span data-ttu-id="70846-126">Vérifiez qu'il est ouvert.</span><span class="sxs-lookup"><span data-stu-id="70846-126">Confirm that it opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70846-127">Le mappage Inbound4010850_to_OrderFile.btm du projet mappe les données du message test 850 entrant au fichier XML sortant placé dans le dossier OrderSystem (\toOrderSystem).</span><span class="sxs-lookup"><span data-stu-id="70846-127">The Inbound4010850_to_OrderFile.btm map in the project maps the data in the inbound 850 test message to the outbound XML file delivered to the OrderSystem folder (\toOrderSystem).</span></span>  
  
3.  <span data-ttu-id="70846-128">Dans l’Explorateur de solutions, cliquez sur le **Inbound_EDI** de projet et sélectionnez **générer** pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="70846-128">In Solution Explorer, right-click the **Inbound_EDI** project and select **Build** to build the project.</span></span>  
  
4.  <span data-ttu-id="70846-129">Dans l’Explorateur de solutions, cliquez sur le **Inbound_EDI** de projet et sélectionnez **déployer** pour déployer le projet.</span><span class="sxs-lookup"><span data-stu-id="70846-129">In Solution Explorer, right-click the **Inbound_EDI** project and select **Deploy** to deploy the project.</span></span>  
  
5.  <span data-ttu-id="70846-130">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, \<  **Tous les artefacts** \> , puis sélectionnez **ressources**.</span><span class="sxs-lookup"><span data-stu-id="70846-130">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, \<**All Artifacts**\> and then select **Resources**.</span></span> <span data-ttu-id="70846-131">Vérifiez que le **Inbound_EDI** assembly est répertorié.</span><span class="sxs-lookup"><span data-stu-id="70846-131">Verify that the **Inbound_EDI** assembly is listed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="70846-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="70846-132">Next Steps</span></span>  
 <span data-ttu-id="70846-133">Vous configurez un profil de tiers et d’entreprise pour votre organisation (**OrderSystem**), comme décrit dans [étape 3 : configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)</span><span class="sxs-lookup"><span data-stu-id="70846-133">You configure a party and business profile for your organization (**OrderSystem**), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70846-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70846-134">See Also</span></span>  
 [<span data-ttu-id="70846-135">Étape 1 : Préparer le didacticiel pour développeur d’interface EDI</span><span class="sxs-lookup"><span data-stu-id="70846-135">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)