---
title: "Génération d’une Instance (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362b9803-4d4a-4d17-9ad6-439ec4c7d8aa
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5696d1590859469b10def4a42c955ff098819d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-instance-edi"></a><span data-ttu-id="3c320-102">Génération d'une instance (EDI)</span><span class="sxs-lookup"><span data-stu-id="3c320-102">Generating an Instance (EDI)</span></span>
<span data-ttu-id="3c320-103">Vous pouvez générer une instance de message à partir d'un schéma EDI au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="3c320-103">You can generate a message instance from an EDI schema at design time.</span></span> <span data-ttu-id="3c320-104">Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span>  
  
 <span data-ttu-id="3c320-105">Vous pouvez générer soit un échange par lot complet (avec des en-têtes d'échange et de groupe) soit un document informatisé (avec en-tête d'échange et de groupe).</span><span class="sxs-lookup"><span data-stu-id="3c320-105">You can generate either a complete batched interchange (with interchange and group headers) or a transaction set (without interchange and group headers).</span></span> <span data-ttu-id="3c320-106">Si vous exécutez l'opération pour générer un échange complet, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produit un fichier contenant un en-tête d'échange, un groupe pour chaque schéma et trois documents informatisés identiques par groupe pour chaque schéma.</span><span class="sxs-lookup"><span data-stu-id="3c320-106">If you execute the operation to generate a complete interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with one interchange header, a group for each schema, and three identical transaction sets per group for each schema.</span></span> <span data-ttu-id="3c320-107">Si vous exécutez l'opération pour générer un document informatisé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produit un fichier contenant un seul document informatisé.</span><span class="sxs-lookup"><span data-stu-id="3c320-107">If you execute the operation to generate a transaction set, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with a single transaction set.</span></span>  
  
 <span data-ttu-id="3c320-108">Pour générer un échange par lot complet, vous exécutez la commande Générer-instance sur le schéma de lot.</span><span class="sxs-lookup"><span data-stu-id="3c320-108">To generate a complete batched interchange, you execute the generate-instance command on the batch schema.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c320-109">détecte les schémas de message dans le projet et inclut automatiquement des documents informatisés pour ces schémas.</span><span class="sxs-lookup"><span data-stu-id="3c320-109"> will detect the message schemas in the project, and will automatically include transaction sets for those schemas.</span></span>  
  
 <span data-ttu-id="3c320-110">Pour générer un document informatisé unique, vous exécutez la commande Générer-instance sur un schéma de message.</span><span class="sxs-lookup"><span data-stu-id="3c320-110">To generate a single transaction set, you execute the generate-instance command on a message schema.</span></span> <span data-ttu-id="3c320-111">Dans ce cas, le schéma de lot ne doit pas être ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="3c320-111">In this case, the batch schema does not need to be added to the project.</span></span> <span data-ttu-id="3c320-112">L'instance générée n'inclut pas d'en-tête d'échange ou de groupe. Vous devez donc les ajouter manuellement pour obtenir un échange EDI opérationnel.</span><span class="sxs-lookup"><span data-stu-id="3c320-112">The generated instance will not include an interchange or group header, however, so you will have to add those manually to have a functional EDI interchange.</span></span>  
  
 <span data-ttu-id="3c320-113">Lorsque vous générez une instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche une boîte de dialogue dans laquelle vous spécifiez la configuration de celle-ci, notamment les séparateurs et l'identificateur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3c320-113">When you generate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration used in that instance, including separators and the syntax identifier.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3c320-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3c320-114">Prerequisites</span></span>  
 <span data-ttu-id="3c320-115">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-115">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-generate-an-instance-of-a-batched-interchange"></a><span data-ttu-id="3c320-116">Pour générer une instance d'un échange par lot</span><span class="sxs-lookup"><span data-stu-id="3c320-116">To generate an instance of a batched interchange</span></span>  
  
1.  <span data-ttu-id="3c320-117">Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="3c320-118">Ajoutez un schéma de message au projet dans l'Explorateur de solutions pour chaque type de document informatisé que vous voulez dans l'instance de message.</span><span class="sxs-lookup"><span data-stu-id="3c320-118">Add a message schema to the project in Solution Explorer for each type of transaction set that you want in the message instance.</span></span> <span data-ttu-id="3c320-119">Ajoutez le schéma de lot pour le type de codage au projet : Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd.</span><span class="sxs-lookup"><span data-stu-id="3c320-119">Add the batch schema for the type of encoding to the project: either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-120">Les schémas de lot sont situés dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span><span class="sxs-lookup"><span data-stu-id="3c320-120">The batch schemas are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-121">Il est inutile de créer le projet pour générer une instance.</span><span class="sxs-lookup"><span data-stu-id="3c320-121">You do not have to build the project to generate an instance.</span></span>  
  
2.  <span data-ttu-id="3c320-122">Cliquez sur le schéma de lot dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3c320-122">Right-click the batch schema in Solution Explorer, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3c320-123">Dans le **propriétés** , configurez **Type sortie générer l’Instance** à **natif** ou **XML**.</span><span class="sxs-lookup"><span data-stu-id="3c320-123">In the **Properties** window, set **Generate Instance Output Type** to **Native** or **XML**.</span></span> <span data-ttu-id="3c320-124">En sélectionnant **natif** vous invite à la génération d’un fichier plat avec une extension .txt.</span><span class="sxs-lookup"><span data-stu-id="3c320-124">Selecting **Native** will prompt generation of a flat file with a .txt extension.</span></span> <span data-ttu-id="3c320-125">En sélectionnant **XML** vous invite à la génération d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3c320-125">Selecting **XML** will prompt generation of an XML file.</span></span>  
  
4.  <span data-ttu-id="3c320-126">Pour **nom de fichier de sortie Instance**, entrez un nom ou accédez à un fichier et sélectionnez le fichier.</span><span class="sxs-lookup"><span data-stu-id="3c320-126">For **Output Instance Filename**, enter a name or browse to a file and select the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-127">Si vous n'entrez pas de valeur pour le nom de fichier d'instance de sortie, le système en choisit une à votre place.</span><span class="sxs-lookup"><span data-stu-id="3c320-127">If you do not enter a value for the output instance filename, one will be chosen for you.</span></span> <span data-ttu-id="3c320-128">Le nom de fichier s'affiche dans la fenêtre Sortie de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-128">The filename will be displayed in the Output window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-129">Si vous sélectionnez un fichier existant, son contenu est remplacé par celui généré par cette opération.</span><span class="sxs-lookup"><span data-stu-id="3c320-129">If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.</span></span>  
  
5.  <span data-ttu-id="3c320-130">Cliquez sur le schéma de lot, puis sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="3c320-130">Right-click the batch schema and then click **Generate Instance**.</span></span>  
  
6.  <span data-ttu-id="3c320-131">Dans le **propriétés de l’Instance EDI** boîte de dialogue, sélectionnez les séparateurs, les identificateurs et les autres configuration options à être utilisé dans cette instance, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3c320-131">In the **EDI Instance Properties** dialog box, select the separators, identifiers, and other configuration options to be used in that instance, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3c320-132">Vérifiez que l’opération a fonctionné le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3c320-132">Verify that the operation worked in the **Output** window.</span></span>  
  
8.  <span data-ttu-id="3c320-133">Pour afficher le fichier, appuyez sur **contrôle** et cliquez sur le lien dans le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3c320-133">To view the file, press **Control** and click the link in the **Output** window.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="3c320-134">Affiche le contenu du fichier dans la fenêtre de l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3c320-134"> will display the contents of the file in the BizTalk Editor window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-135">Lorsque vous générez une instance qui contient un 837I, 837d ou 837p, la valeur de GS08 est incorrectement définie sur 00401.</span><span class="sxs-lookup"><span data-stu-id="3c320-135">When generating an instance that contains an 837I, 837D, or 837P, the value of GS08 will be incorrectly set to 00401.</span></span> <span data-ttu-id="3c320-136">Pour plus d’informations, consultez [problèmes connus avec les outils de XML utilisés avec les Solutions EDI](../core/known-issues-with-xml-tools-used-with-edi-solutions.md).</span><span class="sxs-lookup"><span data-stu-id="3c320-136">For more information, see [Known Issues with XML Tools Used with EDI Solutions](../core/known-issues-with-xml-tools-used-with-edi-solutions.md).</span></span>  
  
### <a name="to-generate-an-instance-of-a-transaction-set"></a><span data-ttu-id="3c320-137">Pour générer une instance d'un document informatisé</span><span class="sxs-lookup"><span data-stu-id="3c320-137">To generate an instance of a transaction set</span></span>  
  
1.  <span data-ttu-id="3c320-138">Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-138">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="3c320-139">Ajoutez le schéma pour le type de document informatisé pour lequel vous voulez générer une instance.</span><span class="sxs-lookup"><span data-stu-id="3c320-139">Add the schema for the type of transaction set that you want to generate an instance for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-140">Il est inutile d'ajouter le schéma de lot au projet pour générer une instance d'un document informatisé.</span><span class="sxs-lookup"><span data-stu-id="3c320-140">You do not have to add the batch schema to the project to generate an instance of a transaction set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-141">Il est inutile de créer le projet pour générer une instance.</span><span class="sxs-lookup"><span data-stu-id="3c320-141">You do not have to build the project to generate an instance.</span></span>  
  
2.  <span data-ttu-id="3c320-142">Cliquez sur le schéma de message dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3c320-142">Right-click the message schema in Solution Explorer, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3c320-143">Dans la fenêtre Propriétés, définissez **Type sortie générer l’Instance** à **natif** ou **XML**.</span><span class="sxs-lookup"><span data-stu-id="3c320-143">In the Properties window, set **Generate Instance Output Type** to **Native** or **XML**.</span></span> <span data-ttu-id="3c320-144">En sélectionnant **natif** vous invite à la génération d’un fichier plat avec une extension .txt.</span><span class="sxs-lookup"><span data-stu-id="3c320-144">Selecting **Native** will prompt generation of a flat file with a .txt extension.</span></span> <span data-ttu-id="3c320-145">En sélectionnant **XML** vous invite à la génération d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3c320-145">Selecting **XML** will prompt generation of an XML file.</span></span>  
  
4.  <span data-ttu-id="3c320-146">Pour **nom de fichier de sortie Instance**, entrez un nom ou accédez à un fichier et sélectionnez le fichier.</span><span class="sxs-lookup"><span data-stu-id="3c320-146">For **Output Instance Filename**, enter a name or browse to a file and select the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-147">Si vous n'entrez pas de valeur pour le nom de fichier d'instance de sortie, le système en choisit une à votre place.</span><span class="sxs-lookup"><span data-stu-id="3c320-147">If you do not enter a value for the output instance filename, one will be chosen for you.</span></span> <span data-ttu-id="3c320-148">Le nom de fichier s’affichera dans le **sortie** fenêtre de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c320-148">The filename will be displayed in the **Output** window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c320-149">Si vous sélectionnez un fichier existant, son contenu est remplacé par celui généré par cette opération.</span><span class="sxs-lookup"><span data-stu-id="3c320-149">If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.</span></span>  
  
5.  <span data-ttu-id="3c320-150">Cliquez sur le schéma de message, puis sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="3c320-150">Right-click the message schema and then click **Generate Instance**.</span></span>  
  
6.  <span data-ttu-id="3c320-151">Dans le **propriétés de l’Instance EDI** boîte de dialogue, sélectionnez les options de configuration que vous souhaitez, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3c320-151">In the **EDI Instance Properties** dialog box, select the configuration options that you want, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3c320-152">Vérifiez qu’il existe un message dans le **sortie** fenêtre, indiquant que l’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="3c320-152">Verify that there is a message in the **Output** window indicating that the operation succeeded.</span></span>  
  
8.  <span data-ttu-id="3c320-153">Pour afficher le fichier, appuyez sur **contrôle** et cliquez sur le lien dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="3c320-153">To view the file, press **Control** and click the link in the Output window.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c320-154">Affiche le contenu du fichier dans la fenêtre de l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3c320-154"> will display the contents of the file in the BizTalk Editor window.</span></span>  
  
9. <span data-ttu-id="3c320-155">Pour créer un message EDI opérationnel, dans l'éditeur de texte, ajoutez les en-têtes d'échange et de groupe au message.</span><span class="sxs-lookup"><span data-stu-id="3c320-155">To make a functional EDI message, add the interchange and group headers to the message in a text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c320-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c320-156">See Also</span></span>  
 <span data-ttu-id="3c320-157">[À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3c320-157">[Using Design-Time XML Tools](../core/using-design-time-xml-tools.md) </span></span>  
 [<span data-ttu-id="3c320-158">Validation d’une Instance (EDI)</span><span class="sxs-lookup"><span data-stu-id="3c320-158">Validating an Instance (EDI)</span></span>](../core/validating-an-instance-edi.md)