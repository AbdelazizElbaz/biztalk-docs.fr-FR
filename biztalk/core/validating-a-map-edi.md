---
title: "Validation d’un mappage (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caf58ecf-ed10-4c13-8d7d-e007b9158b0e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 028a152be285bb79f3cd0899b2143e99ef2b6042
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-map-edi"></a><span data-ttu-id="343ea-102">Validation d'un mappage (EDI)</span><span class="sxs-lookup"><span data-stu-id="343ea-102">Validating a Map (EDI)</span></span>
<span data-ttu-id="343ea-103">Vous pouvez valider un mappage lors de la phase de conception.</span><span class="sxs-lookup"><span data-stu-id="343ea-103">You can validate a map at design time.</span></span> <span data-ttu-id="343ea-104">Pour ce faire, vous utilisez les extensions de l’outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="343ea-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="343ea-105">Cette opération a pour effet de générer un fichier contenant le XSLT sous-jacent du mappage ainsi qu'un autre fichier contenant les objets d'extension.</span><span class="sxs-lookup"><span data-stu-id="343ea-105">This operation generates a file containing the underlying XSLT of the map and a file containing extension objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="343ea-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="343ea-106">Prerequisites</span></span>  
 <span data-ttu-id="343ea-107">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="343ea-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-a-map"></a><span data-ttu-id="343ea-108">Pour valider un mappage</span><span class="sxs-lookup"><span data-stu-id="343ea-108">To validate a map</span></span>  
  
1.  <span data-ttu-id="343ea-109">Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="343ea-109">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="343ea-110">Dans l'Explorateur de solutions, ajoutez le mappage que vous souhaitez valider ainsi que les schémas de messages entrant et sortant.</span><span class="sxs-lookup"><span data-stu-id="343ea-110">To the project in Solution Explorer, add the map that you want to validate and its input and output message schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="343ea-111">Ces derniers se trouvent dans le sous-dossier approprié, sous le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span><span class="sxs-lookup"><span data-stu-id="343ea-111">The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span> <span data-ttu-id="343ea-112">Pour plus d’informations sur l’installation des fichiers de schéma, consultez [comment installer les fichiers de schéma EDI](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span><span class="sxs-lookup"><span data-stu-id="343ea-112">For more information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="343ea-113">Il est inutile de générer un projet pour valider un mappage.</span><span class="sxs-lookup"><span data-stu-id="343ea-113">You do not have to build the project to validate a map.</span></span>  
  
2.  <span data-ttu-id="343ea-114">Avec le bouton droit de la carte dans l’Explorateur de solutions, puis cliquez sur **valider le mappage**.</span><span class="sxs-lookup"><span data-stu-id="343ea-114">Right-click the map in Solution Explorer, and then click **Validate Map**.</span></span>  
  
3.  <span data-ttu-id="343ea-115">Vérifiez qu'il y a un message dans la fenêtre Sortie indiquant que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="343ea-115">Verify that there is a message in the Output window indicating that the operation succeeded.</span></span>  
  
4.  <span data-ttu-id="343ea-116">Notez les avertissements qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a validé dans le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="343ea-116">Note any warnings that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has posted in the **Output** window.</span></span>  
  
5.  <span data-ttu-id="343ea-117">Dans le **sortie** fenêtre, notez le nom et le chemin d’accès de la sortie XSLT.</span><span class="sxs-lookup"><span data-stu-id="343ea-117">In the **Output** window, note the name and path of the output XSLT.</span></span> <span data-ttu-id="343ea-118">Ce fichier XSL possède le même nom que le fichier de mappage, mais avec une extension XSL.</span><span class="sxs-lookup"><span data-stu-id="343ea-118">This XSL file will be given the same name as the map file, but with an XSL extension.</span></span> <span data-ttu-id="343ea-119">Vous pouvez appuyer sur CTRL et cliquer sur le lien pour afficher le fichier XSL dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="343ea-119">You can press CTRL and click the link to display the XSL file in the BizTalk Editor.</span></span>  
  
6.  <span data-ttu-id="343ea-120">Dans le **sortie** fenêtre, notez le nom et le chemin d’accès de l’objet d’extension XML.</span><span class="sxs-lookup"><span data-stu-id="343ea-120">In the **Output** window, note the name and path of the extension object XML.</span></span> <span data-ttu-id="343ea-121">Vous pouvez appuyer sur CTRL et cliquer sur le lien pour afficher le fichier XSL dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="343ea-121">You can press CTRL and click the link to display the XSL file in the BizTalk Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343ea-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="343ea-122">See Also</span></span>  
 [<span data-ttu-id="343ea-123">À l’aide d’outils au moment du Design XML</span><span class="sxs-lookup"><span data-stu-id="343ea-123">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)