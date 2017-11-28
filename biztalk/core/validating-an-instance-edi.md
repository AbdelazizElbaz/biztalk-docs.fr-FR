---
title: "Validation d’une Instance (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fe4e87-5ab4-41e4-8ceb-8f6cf40cae0b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cceea8afe67f7e69b3ee842198d9a5373a972d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-an-instance-edi"></a><span data-ttu-id="5623a-102">Validation d'une instance (EDI)</span><span class="sxs-lookup"><span data-stu-id="5623a-102">Validating an Instance (EDI)</span></span>
<span data-ttu-id="5623a-103">Vous pouvez valider une instance par rapport à son schéma EDI pendant la phase de conception.</span><span class="sxs-lookup"><span data-stu-id="5623a-103">You can validate an instance against its EDI schema at design time.</span></span> <span data-ttu-id="5623a-104">Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5623a-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="5623a-105">L'instance que vous validez peut être un document informatisé unique (sans en-tête d'échange et de groupe), un échange comprenant un seul document informatisé (avec en-têtes d'échange et de groupe) ou un échange traité par lot complet comprenant plusieurs documents informatisés (avec en-têtes d'échange et de groupe).</span><span class="sxs-lookup"><span data-stu-id="5623a-105">The instance that you validate can be a single transaction set (without interchange and group headers), an interchange with a single transaction set (with interchange and group headers), or a complete batched interchange with multiple transaction sets (with interchange and group headers).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5623a-106">La validation d'un échange conservé XML n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="5623a-106">Validation of an XML preserved interchange is not supported.</span></span> <span data-ttu-id="5623a-107">En revanche, celle d'un échange conservé EDI l'est.</span><span class="sxs-lookup"><span data-stu-id="5623a-107">However, validation of an EDI preserved interchange is supported.</span></span>  
  
 <span data-ttu-id="5623a-108">L'opération de validation de l'instance effectue la validation EDI et XSD.</span><span class="sxs-lookup"><span data-stu-id="5623a-108">The validate-instance operation performs both EDI and XSD validation.</span></span>  
  
 <span data-ttu-id="5623a-109">Lorsque vous validez une instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche une boîte de dialogue dans laquelle vous spécifiez la configuration à valider dans celle-ci, notamment les séparateurs et l'identificateur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5623a-109">When you validate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration to be validated in that instance, including separators and the syntax identifier.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5623a-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5623a-110">Prerequisites</span></span>  
 <span data-ttu-id="5623a-111">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5623a-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-an-instance-against-its-schema"></a><span data-ttu-id="5623a-112">Pour valider une instance par rapport à son schéma</span><span class="sxs-lookup"><span data-stu-id="5623a-112">To validate an instance against its schema</span></span>  
  
1.  <span data-ttu-id="5623a-113">Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5623a-113">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span>  
  
2.  <span data-ttu-id="5623a-114">Dans l'Explorateur de solutions, ajoutez au projet tous les schémas requis pour l'instance du message.</span><span class="sxs-lookup"><span data-stu-id="5623a-114">In Solution Explorer, add to the project all schemas required for the message instance.</span></span>  
  
    1.  <span data-ttu-id="5623a-115">Si vous validez un document informatisé unique sans en-tête d'échange et de groupe, ajoutez le schéma de document correspondant à ce document informatisé.</span><span class="sxs-lookup"><span data-stu-id="5623a-115">If you are validating a single transaction set without interchange and group headers, add the document schema for that transaction set.</span></span>  
  
    2.  <span data-ttu-id="5623a-116">Si vous validez un échange comprenant un seul document informatisé, ajoutez au projet le schéma du document informatisé, ainsi que le schéma de lot correspondant au type de codage utilisé pour le message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span><span class="sxs-lookup"><span data-stu-id="5623a-116">If you are validating an interchange with a single transaction set, add to the project the schema for the transaction and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5623a-117">Le schéma de lot est requis pour valider l'enveloppe de l'instance.</span><span class="sxs-lookup"><span data-stu-id="5623a-117">The batch schema is required to validate the envelope of the instance.</span></span> <span data-ttu-id="5623a-118">Si vous n'utilisez que le schéma du message, l'enveloppe n'est pas validée.</span><span class="sxs-lookup"><span data-stu-id="5623a-118">If you were to use only the message schema, the envelope would not be validated.</span></span>  
  
    3.  <span data-ttu-id="5623a-119">Si vous validez un échange traité par lot comprenant plusieurs documents informatisés, ajoutez au projet le schéma de chaque groupe de documents informatisés de l'instance du message, ainsi que le schéma de lot correspondant au type de codage utilisé pour le message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span><span class="sxs-lookup"><span data-stu-id="5623a-119">If you are validating a batched interchange with multiple transaction sets, add to the project the schemas for each transaction set group in the message instance, and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5623a-120">Si vous avez personnalisé le schéma de service, vous devez inclure le schéma de service personnalisé dans le projet BizTalk, en complément du ou des schémas de document (informatisé) et, si nécessaire, le schéma de lot.</span><span class="sxs-lookup"><span data-stu-id="5623a-120">If you have customized the service schema, you will have to include the custom service schema in the BizTalk project, in addition to the document (transaction set) schema(s) and if necessary, the batch schema.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5623a-121">Il est inutile de créer le projet pour valider une instance.</span><span class="sxs-lookup"><span data-stu-id="5623a-121">You do not have to build the project to validate an instance.</span></span>  
  
3.  <span data-ttu-id="5623a-122">Affichez la page des propriétés associée au schéma dans l'Explorateur de solutions en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="5623a-122">Display the property page for the schema in Solution Explorer, as follows:</span></span>  
  
    1.  <span data-ttu-id="5623a-123">Si vous validez un document informatisé unique, cliquez sur le schéma de document pour ce jeu de transactions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5623a-123">If you are validating a single transaction set, right-click the document schema for that transaction set, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="5623a-124">Si vous validez un échange avec un document informatisé unique ou un échange par lot avec plusieurs jeux de transactions, cliquez sur le schéma de lot (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd schéma), puis cliquez sur **depropriétés**.</span><span class="sxs-lookup"><span data-stu-id="5623a-124">If you are validating an interchange with a single transaction set or a batched interchange with multiple transaction sets, right-click the batch schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd schema), and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5623a-125">Dans la fenêtre Propriétés pour le schéma, pour **nom d’Instance d’entrée** Entrez le nom et le chemin d’accès de l’instance de message que vous souhaitez valider, ou accédez au fichier, sélectionnez-le, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5623a-125">In Properties window for the schema, for **Input Instance Filename** enter the name and path of the message instance that you want to validate, or browse to the file, select it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="5623a-126">Pour **Type valider l’entrée d’Instance**, entrez le type de fichier à valider : **natif** pour un fichier EDI ou **XML** pour un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="5623a-126">For **Validate Instance Input Type**, enter the type of the file to be validate: **Native** for a EDI file or **XML** for an XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5623a-127">La validation d'un échange conservé XML n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="5623a-127">Validation of an XML preserved interchange is not supported.</span></span> <span data-ttu-id="5623a-128">Si vous sélectionnez XML pour le **Type valider l’entrée d’Instance** propriété lors de la validation d’un échange conservé, l’opération échoue et rien n’est renvoyé.</span><span class="sxs-lookup"><span data-stu-id="5623a-128">If you select XML for the **Validate Instance Input Type** property when validating a preserved interchange, the operation will fail and nothing will be returned.</span></span> <span data-ttu-id="5623a-129">Toutefois, si vous sélectionnez **natif** pour le **Type valider l’entrée d’Instance** lorsque vous validez un échange conservé, l’opération réussira.</span><span class="sxs-lookup"><span data-stu-id="5623a-129">However, if you select **Native** for the **Validate Instance Input Type** when validating a preserved interchange, the operation will succeed.</span></span>  
  
6.  <span data-ttu-id="5623a-130">Cliquez sur le schéma du message (Edifact_BatchSchema.xsd ou X12_BatchSchema.xsd si la validation d’un échange avec un document informatisé unique ou un échange par lot), puis sur **valider l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="5623a-130">Right-click the message schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd if validating an interchange with a single transaction set or a batched interchange) and then click **Validate Instance**.</span></span>  
  
7.  <span data-ttu-id="5623a-131">Dans le **propriétés de l’Instance EDI** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5623a-131">In the **EDI Instance Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="5623a-132">Si l’instance doit utiliser un séparateur de répétition, sélectionnez **séparateur de répétition**.</span><span class="sxs-lookup"><span data-stu-id="5623a-132">If your instance should use a repetition separator, select **Repetition separator**.</span></span>  
  
    2.  <span data-ttu-id="5623a-133">Si l’instance doit utiliser des délimiteurs de fin, sélectionnez **Oui** pour **utiliser les délimiteurs de fin**.</span><span class="sxs-lookup"><span data-stu-id="5623a-133">If your instance should use trailing delimiters, select **Yes** for **Use trailing delimiters**.</span></span>  
  
    3.  <span data-ttu-id="5623a-134">Si l’instance doit utiliser un caractère autre que **base**, sélectionnez **étendue** ou **Unicode** dans **identificateur de syntaxe**.</span><span class="sxs-lookup"><span data-stu-id="5623a-134">If your instance should use a character set other than **Basic**, select **Extended** or **Unicode** in **Syntax identifier**.</span></span>  
  
    4.  <span data-ttu-id="5623a-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5623a-135">Click **OK**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5623a-136">Le **propriétés de l’Instance EDI** boîte de dialogue peut apparaître une deuxième fois, une fois que vous avez cliqué sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5623a-136">The **EDI Instance Properties** dialog box might appear a second time after you have clicked **OK**.</span></span> <span data-ttu-id="5623a-137">Dans ce cas, cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="5623a-137">If so, click **OK** again.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5623a-138">Le **propriétés de l’Instance EDI** boîte de dialogue contiendra les mêmes valeurs dans la dernière opération de validation de l’instance qui a été exécutée pour le même utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="5623a-138">The **EDI Instance Properties** dialog box will be populated with the same values used in the last validate-instance operation that was run for the same logged-in user.</span></span>  
  
8.  <span data-ttu-id="5623a-139">Vérifiez qu’il existe un message dans le **sortie** fenêtre, indiquant que l’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="5623a-139">Verify that there is a message in the **Output** window indicating that the operation succeeded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5623a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5623a-140">See Also</span></span>  
 <span data-ttu-id="5623a-141">[À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5623a-141">[Using Design-Time XML Tools](../core/using-design-time-xml-tools.md) </span></span>  
 [<span data-ttu-id="5623a-142">Génération d’une Instance (EDI)</span><span class="sxs-lookup"><span data-stu-id="5623a-142">Generating an Instance (EDI)</span></span>](../core/generating-an-instance-edi.md)