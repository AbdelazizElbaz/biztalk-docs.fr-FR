---
title: SchemaValidator | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, SchemaValidator utility
- validating, SchemaValidator utility
- SchemaValidator utility
- schemas, SchemaValidator utility
ms.assetid: 3bd61a03-d81e-4fd1-802c-f801000002d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9e3921b8bf83e3e7e775efef77a029bfda2e7e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="schemavalidator"></a><span data-ttu-id="2e9b3-102">SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2e9b3-102">SchemaValidator</span></span>
<span data-ttu-id="2e9b3-103">Vous utilisez l’utilitaire SchemaValidator pour résoudre les problèmes liés à une instance de message.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-103">You use the SchemaValidator utility to troubleshoot problems with a message instance.</span></span> <span data-ttu-id="2e9b3-104">Si vous recevez un message dont la validation échoue, vous pouvez exécuter l’utilitaire SchemaValidator pour déterminer la source de l’échec.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-104">If you receive a message that fails validation, you can run the SchemaValidator utility to determine the source of the failure.</span></span>  
  
 <span data-ttu-id="2e9b3-105">Vous utilisez cet utilitaire si vous utilisez un assembly qui inclut un fichier de schéma, et vous n’avez pas d’un fichier .xsd de schéma.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-105">You use this utility if you are using an assembly that includes a schema .dll file, and you do not have a schema .xsd file.</span></span> <span data-ttu-id="2e9b3-106">L’utilitaire SchemaValidator vous permet de valider à l’aide du fichier .dll de schéma.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-106">The SchemaValidator utility lets you validate using the schema .dll file.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="2e9b3-107">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="2e9b3-107">Location in SDK</span></span>  
 <span data-ttu-id="2e9b3-108">\<*lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2e9b3-108">\<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator</span></span>  
  
## <a name="building-and-running-schemavalidator"></a><span data-ttu-id="2e9b3-109">Génération et exécution SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2e9b3-109">Building and Running SchemaValidator</span></span>  
  
#### <a name="to-build-the-schemavalidator-utility"></a><span data-ttu-id="2e9b3-110">Pour générer l’utilitaire SchemaValidator</span><span class="sxs-lookup"><span data-stu-id="2e9b3-110">To build the SchemaValidator utility</span></span>  
  
1.  <span data-ttu-id="2e9b3-111">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-111">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2e9b3-112">Déplacer vers \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-112">Move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator.</span></span>  
  
3.  <span data-ttu-id="2e9b3-113">À l’invite de commandes, tapez **sn -k SchemaValidator.snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-113">At the command prompt, type **sn -k SchemaValidator.snk**, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="2e9b3-114">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-114">Start **Microsoft Visual Studio 2012**.</span></span>  
  
5.  <span data-ttu-id="2e9b3-115">Sur le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **ouvrir une Solution**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-115">On the **File** menu, point to **Open**, and then click **Open Solution**.</span></span>  
  
6.  <span data-ttu-id="2e9b3-116">Déplacer vers \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator, sélectionnez **SchemaValidator.sln** , puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-116">Move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator, select **SchemaValidator.sln**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="2e9b3-117">Dans l’Explorateur de solutions, cliquez sur **SchemaValidator**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-117">In Solution Explorer, right-click **SchemaValidator**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="2e9b3-118">Dans la page **Propriété de MessageInspector**  , cliquez sur l'onglet **Signature** , puis cochez la case **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="2e9b3-118">In the **MessageInspector Property**  page, click **Signing** tab, and then click **Sign the assembly** checkbox.</span></span> <span data-ttu-id="2e9b3-119">Sélectionnez **SchemaValidator.snk** dans **choisir un fichier de clé de nom fort**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-119">Select **SchemaValidator.snk** in **Choose a strong name key file**.</span></span>  
  
9. <span data-ttu-id="2e9b3-120">Cliquez sur **SchemaValidator.cs**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-120">Click **SchemaValidator.cs**.</span></span>  
  
10. <span data-ttu-id="2e9b3-121">Tapez le chemin d’instance de message approprié dans la ligne de code existante suivante `Main`:</span><span class="sxs-lookup"><span data-stu-id="2e9b3-121">Type the appropriate message instance path in the following existing line of code in `Main`:</span></span>  
  
    ```  
    const string xmlInstancePath = @"..\..\Sample3A4.xml";  
    ```  
  
11. <span data-ttu-id="2e9b3-122">Remplacez la ligne suivante existante du code dans `Main` avec une référence à l’assembly RNPIPs, puis sélectionnez le schéma approprié :</span><span class="sxs-lookup"><span data-stu-id="2e9b3-122">Replace the following existing line of code in `Main` with a reference to the RNPIPs assembly, and then select the appropriate schema:</span></span>  
  
    ```  
    _3A4_MS_V02_02_PurchaseOrderRequest BTSSchema = new _3A4_MS_V02_02_PurchaseOrderRequest();  
    ```  
  
12. <span data-ttu-id="2e9b3-123">Avec le bouton droit **SchemaValidator**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-123">Right-click **SchemaValidator**, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="2e9b3-124">Modifier l’instance de message pour que vous souhaitez tester en supprimant le \< \!DOCTYPE... \> balise en spécifiant le fichier DTD à partir de l’en-tête de l’instance XML.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-124">Modify the message instance to you want to test by removing the \<\!DOCTYPE …\> tag specifying the DTD file from the header of the XML instance.</span></span>  
  
14. <span data-ttu-id="2e9b3-125">Dans le nœud racine de l’instance de message, ajoutez un espace de noms XML du schéma que vous allez valider par rapport à.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-125">In the root node of the message instance, add an XML namespace of the schema that you will validate against.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e9b3-126">Pour obtenir un exemple d’un schéma prêt à être validée par l’utilitaire SchemaValidator, consultez Sample3A4.xml dans \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator pour RosettaNet\SDK\SchemaValidator.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-126">For an example of a schema ready to be validated by the SchemaValidator utility, see Sample3A4.xml in \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator.</span></span>  
  
15. <span data-ttu-id="2e9b3-127">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **SchemaValidator.cs**, puis appuyez sur CTRL et sur F5 pour exécuter l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-127">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **SchemaValidator.cs**, and then press CTRL and F5 to run the utility.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9b3-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2e9b3-128">Remarks</span></span>  
 <span data-ttu-id="2e9b3-129">Étant donné que le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut le code SchemaValidator, vous pouvez ajouter une logique à l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-129">Because the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes the SchemaValidator code, you can add logic to the utility.</span></span> <span data-ttu-id="2e9b3-130">Par exemple, vous pouvez rendre un utilitaire de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2e9b3-130">For example, you can make it a command-line utility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9b3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e9b3-131">See Also</span></span>  
 [<span data-ttu-id="2e9b3-132">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="2e9b3-132">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)