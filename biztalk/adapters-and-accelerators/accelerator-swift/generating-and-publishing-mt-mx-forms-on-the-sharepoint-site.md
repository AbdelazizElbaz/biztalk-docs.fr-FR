---
title: "Génération et publication de formulaires MT-MX sur le Site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e2bd45c54bfc312a52d199a2f117a108207cdf5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-and-publishing-mtmx-forms-on-the-sharepoint-site"></a><span data-ttu-id="c2a53-102">Génération et publication de formulaires MT/MX sur le Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="c2a53-102">Generating and Publishing MT/MX Forms on the SharePoint Site</span></span>
<span data-ttu-id="c2a53-103">**Pour générer et publier des formulaires MT/MX sur un site SharePoint :**</span><span class="sxs-lookup"><span data-stu-id="c2a53-103">**To generate and publish MT/MX forms on a SharePoint site:**</span></span>  
  
1.  <span data-ttu-id="c2a53-104">Télécharger l’utilitaire Générateur de formulaire et l’enregistrer localement sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c2a53-104">Download the Form Generator Utility and save it locally on the computer.</span></span>  
  
2.  <span data-ttu-id="c2a53-105">Ouvrez le **FormGenerator.sln** à partir du dossier téléchargé ci-dessus et de compiler la solution.</span><span class="sxs-lookup"><span data-stu-id="c2a53-105">Open the **FormGenerator.sln** from the folder downloaded above and compile the solution.</span></span>  
  
3.  <span data-ttu-id="c2a53-106">À l’invite de commandes, accéder au dossier de l’exécutable compilé (FormGenerator.exe).</span><span class="sxs-lookup"><span data-stu-id="c2a53-106">At a command prompt, access the folder of compiled executable (FormGenerator.exe).</span></span> <span data-ttu-id="c2a53-107">Par exemple, si vous avez créé l’utilitaire en mode débogage, accéder à la **... \bin\Debug** dossier.</span><span class="sxs-lookup"><span data-stu-id="c2a53-107">For example, if you have built the utility in debug mode, access the **..\bin\debug** folder.</span></span>  
  
4.  <span data-ttu-id="c2a53-108">Tapez FormGenerator.exe [-b] [-\<non.</span><span class="sxs-lookup"><span data-stu-id="c2a53-108">Type FormGenerator.exe [-b] [-\<No.</span></span> <span data-ttu-id="c2a53-109">des chemins d’accès du dossier de modèle >]</span><span class="sxs-lookup"><span data-stu-id="c2a53-109">of Template folder paths>]</span></span>  
  
     <span data-ttu-id="c2a53-110">`<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`.</span><span class="sxs-lookup"><span data-stu-id="c2a53-110">`<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`.</span></span> <span data-ttu-id="c2a53-111">Remplacez les paramètres avec les noms de dossier nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="c2a53-111">Replace the parameters with the newly-created folder names.</span></span>  
  
5.  <span data-ttu-id="c2a53-112">La commande ci-dessus génère également le schéma d’enveloppe à MX message réparation.</span><span class="sxs-lookup"><span data-stu-id="c2a53-112">The above command will also generate the Envelope schema needed for MX message repair.</span></span>  
  
6.  <span data-ttu-id="c2a53-113">Accédez au dossier de sortie \<DestinationFolderPath >.</span><span class="sxs-lookup"><span data-stu-id="c2a53-113">Go to output folder \<DestinationFolderPath>.</span></span> <span data-ttu-id="c2a53-114">Dans \<DestinationFolderPath >, ouvrez le dossier du modèle de formulaire InfoPath pour lequel vous souhaitez générer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c2a53-114">In \<DestinationFolderPath>, open the folder of the InfoPath form template for which you want to generate the form.</span></span> <span data-ttu-id="c2a53-115">Par exemple, si vous souhaitez générer le formulaire InfoPath de MT103, ouvrez le dossier MT103 à la DestinationFolderPath et ouvrez le TemplateDS.sln.</span><span class="sxs-lookup"><span data-stu-id="c2a53-115">For example, if you want to generate the MT103 InfoPath form, then open the MT103 folder at the DestinationFolderPath and open the TemplateDS.sln.</span></span>  
  
7.  <span data-ttu-id="c2a53-116">Dans l’Explorateur de solutions, double-cliquez sur le **manifest.xsf**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-116">In the Solution Explorer, double click the **manifest.xsf**.</span></span> <span data-ttu-id="c2a53-117">Il ouvre le fichier de la conception du formulaire InfoPath qui prend un certain temps à obtenir ouvert.</span><span class="sxs-lookup"><span data-stu-id="c2a53-117">It will open the design file of the InfoPath form which will take some time to get opened.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2a53-118">MX messages manifest.xsf peut prendre 2 à 5 minutes obtenir ouvert.</span><span class="sxs-lookup"><span data-stu-id="c2a53-118">The MX messages manifest.xsf might take 2-5 minutes to get opened.</span></span>  
  
8.  <span data-ttu-id="c2a53-119">Dans manifest.xsf, accédez à **Outils -> Options de formulaire - > sécurité et approbation** option de menu.</span><span class="sxs-lookup"><span data-stu-id="c2a53-119">In the manifest.xsf, go to **Tools ->Form Options-> Security and Trust** menu option.</span></span> <span data-ttu-id="c2a53-120">Vérifiez le **confiance totale** option doit être activée pour l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="c2a53-120">Check the **Full Trust** option must be enabled for the permission.</span></span>  
  
9. <span data-ttu-id="c2a53-121">Sélectionnez le **signer ce modèle de formulaire** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="c2a53-121">Select the **Sign this form Template** checkbox.</span></span> <span data-ttu-id="c2a53-122">Cliquez sur **sélectionner un certificat**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-122">Click **Select certificate**.</span></span> <span data-ttu-id="c2a53-123">Dans ce cas, sélectionnez le certificat avec lequel vous souhaitez signer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c2a53-123">In this, select the certificate with which you want to sign the form.</span></span> <span data-ttu-id="c2a53-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-124">Click **OK**.</span></span>  
  
10. <span data-ttu-id="c2a53-125">Enregistrer **manifest.xsf**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-125">Save **manifest.xsf**.</span></span>  
  
11. <span data-ttu-id="c2a53-126">Accédez à **Affichage -> tâches de conception**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-126">Go to **View -> Design Tasks**.</span></span> <span data-ttu-id="c2a53-127">Dans le volet de tâches de conception, cliquez sur **publier un modèle de formulaire** option.</span><span class="sxs-lookup"><span data-stu-id="c2a53-127">On the Design Tasks pane, click **Publish Form Template** option.</span></span>  
  
12. <span data-ttu-id="c2a53-128">Dans la fenêtre de l’Assistant Publication, sélectionnez **vers un emplacement réseau** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-128">In the publishing wizard window, select **To a network location** and click **Next**.</span></span>  
  
13. <span data-ttu-id="c2a53-129">Dans le formulaire modèle chemin d’accès et le fichier de zone de texte Nom, tapez **http://localhost/sites/BASSite/Templates/\<MessageType > .xsn** et type  **\<MessageType >** sous la forme Zone de texte Nom du modèle et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-129">In the Form template path and file name textbox, type **http://localhost/sites/BASSite/Templates/\<MessageType>.xsn** and type **\<MessageType>** in the Form Template name textbox and click **Next**.</span></span>  
  
14. <span data-ttu-id="c2a53-130">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-130">Click **Next**.</span></span>  
  
15. <span data-ttu-id="c2a53-131">Cliquez sur **publier et fermer**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-131">Click **Publish and close**.</span></span>  
  
16. <span data-ttu-id="c2a53-132">Dans Internet Explorer, ouvrez votre site SharePoint **http://localhost/sites/bassite/templates**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-132">In the Internet Explorer, open your SharePoint site **http://localhost/sites/bassite/templates**.</span></span>  
  
17. <span data-ttu-id="c2a53-133">Pointez sur  **\<MessageType >**et cliquez sur la flèche bas en regard de celui-ci, puis cliquez sur **modifier les propriétés de**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-133">Point to **\<MessageType>**, click the down arrow next to it, and then click **Edit Properties**.</span></span>  
  
18. <span data-ttu-id="c2a53-134">Dans les modèles :\< MessageType > fenêtre, dans la zone de Namespace :</span><span class="sxs-lookup"><span data-stu-id="c2a53-134">In the Templates:\< MessageType> window, in the Namespace box:</span></span>  
  
    -   <span data-ttu-id="c2a53-135">Si vous générez des formulaires InfoPath de MT, tapez : **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**</span><span class="sxs-lookup"><span data-stu-id="c2a53-135">If you are generating MT InfoPath forms, type: **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**</span></span>  
  
    -   <span data-ttu-id="c2a53-136">Si vous générez des formulaires InfoPath de MX, tapez : **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX _\<MessageName >**</span><span class="sxs-lookup"><span data-stu-id="c2a53-136">If you are generating MX InfoPath forms, type: **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageName>**</span></span>  
  
         <span data-ttu-id="c2a53-137">Cela permet d’identifier l’instance de message par le modèle correspondant.</span><span class="sxs-lookup"><span data-stu-id="c2a53-137">This will help in identifying the message instance with the corresponding template.</span></span>  
  
19. <span data-ttu-id="c2a53-138">Cliquez sur **enregistrer et fermer**.</span><span class="sxs-lookup"><span data-stu-id="c2a53-138">Click **Save and Close**.</span></span>