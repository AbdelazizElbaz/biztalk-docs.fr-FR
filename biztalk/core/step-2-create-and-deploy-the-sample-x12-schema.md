---
title: "Étape 2 : Créer et déployer l’exemple X12 schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5862168-6621-40ab-8c97-3f317530d34e
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe4f937af910ceef1ed461e25ea3c62cad5cbc29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-and-deploy-the-sample-x12-schema"></a><span data-ttu-id="4ae4b-102">Étape 2 : Créer et déployer l’exemple X12 schéma</span><span class="sxs-lookup"><span data-stu-id="4ae4b-102">Step 2: Create and Deploy the Sample X12 Schema</span></span>
<span data-ttu-id="4ae4b-103">![Étape 2 sur 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")</span><span class="sxs-lookup"><span data-stu-id="4ae4b-103">![Step 2 of 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")</span></span>  
  
 <span data-ttu-id="4ae4b-104">Au cours de cette étape, vous allez créer et déployer le projet qui fournit un exemple de schéma EDI X12 requis pour traiter l'échange EDI X12 entrant transporté via AS2.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-104">In this step, you build and deploy the project that provides a sample EDI X12 schema that is required to process the incoming EDI X12 interchange transported over AS2.</span></span> <span data-ttu-id="4ae4b-105">Pour ce didacticiel, ce schéma est X12_00401_864.xsd.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-105">For this tutorial, that schema is X12_00401_864.xsd.</span></span> <span data-ttu-id="4ae4b-106">Vous ne devez pas modifier le projet fourni avec le didacticiel AS2. Vous devez juste le générer.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-106">You do not need to change the project that is shipped with the AS2 tutorial; you just need to build it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ae4b-107">Le fichier de schéma X12_00401_864.xsd que ce didacticiel utilise est stocké dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] SDK\AS2 Tutorial\Schemas.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-107">The schema file X12_00401_864.xsd that this tutorial uses is stored in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas.</span></span> <span data-ttu-id="4ae4b-108">Il a déjà été ajouté au projet Schémas que vous allez créer et déployer au cours de cette étape.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-108">It has already been added to the Schemas project that you will build and deploy in this step.</span></span> <span data-ttu-id="4ae4b-109">Ce schéma est différent du fichier X12_00401_864.xsd téléchargé sur votre ordinateur en exécutant MicrosoftEdiXsdTemplates.exe dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-109">This schema is different from the X12_00401_864.xsd file downloaded onto your computer by executing MicrosoftEdiXsdTemplates.exe in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span></span> <span data-ttu-id="4ae4b-110">Le didacticiel ne fonctionnera que si vous utilisez le fichier X12_00401_864.xsd qui a été ajouté à Schemas.btproj.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-110">The tutorial will only work if you use the X12_00401_864.xsd file that has been added to Schemas.btproj.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4ae4b-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4ae4b-111">Prerequisites</span></span>  
 <span data-ttu-id="4ae4b-112">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ae4b-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-and-deploy-the-sample-x12-schema"></a><span data-ttu-id="4ae4b-113">Pour créer et déployer l'exemple de schéma X12</span><span class="sxs-lookup"><span data-stu-id="4ae4b-113">To create and deploy the sample X12 schema</span></span>  
  
1.  <span data-ttu-id="4ae4b-114">Démarrer **Microsoft Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-114">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
2.  <span data-ttu-id="4ae4b-115">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez la solution [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-115">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ae4b-116">Cette rubrique part du principe que vous avez déjà ajouté une référence de votre application à l'application BizTalk EDI, qui contient les schémas, pipelines et orchestrations EDI.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-116">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="4ae4b-117">Dans le cas contraire, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span><span class="sxs-lookup"><span data-stu-id="4ae4b-117">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
3.  <span data-ttu-id="4ae4b-118">Cliquez sur le projet de schémas, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-118">Right-click the Schemas project, and then click **Properties**.</span></span> <span data-ttu-id="4ae4b-119">Cliquez sur le **signature** onglet Concepteur de projets.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-119">Click the **Signing** tab in project designer.</span></span> <span data-ttu-id="4ae4b-120">Vérifiez le **signer l’Assembly** case à cocher, pour **choisir un fichier de nom fort de la clé**, sélectionnez  **\<nouveau... >** et entrez `Schemas.snk`.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-120">Check the **Sign the Assembly** checkbox, for **Choose a strong key name file**, select **\<New…>** and enter `Schemas.snk`.</span></span> <span data-ttu-id="4ae4b-121">Désactivez **protéger mon fichier de clé avec un mot de passe** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-121">Clear **Protect my key file with a password** and then click **OK**.</span></span> <span data-ttu-id="4ae4b-122">Fermez la page des propriétés du projet et enregistrez les modifications.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-122">Close the project properties dialog and save the changes.</span></span>  
  
4.  <span data-ttu-id="4ae4b-123">Créez et déployez Schemas.btproj.</span><span class="sxs-lookup"><span data-stu-id="4ae4b-123">Build and deploy Schemas.btproj.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4ae4b-124">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4ae4b-124">Next Steps</span></span>  
 <span data-ttu-id="4ae4b-125">Vous configurez un tiers et un profil métier de votre organisation (Contoso), comme décrit dans [étape 3 : configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md).</span><span class="sxs-lookup"><span data-stu-id="4ae4b-125">You configure a party and business profile for your organization (Contoso), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae4b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ae4b-126">See Also</span></span>  
 [<span data-ttu-id="4ae4b-127">Schémas de Document EDI</span><span class="sxs-lookup"><span data-stu-id="4ae4b-127">EDI Document Schemas</span></span>](../core/edi-document-schemas.md)