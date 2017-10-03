---
title: Comment ajouter des mappages existants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbeaea05-016e-488c-90f3-af8c6b9a3d84
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a61fb0faf5f4eed614257361b00cea781db2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-existing-maps"></a><span data-ttu-id="d9529-102">Ajout de mappages existants</span><span class="sxs-lookup"><span data-stu-id="d9529-102">How to Add Existing Maps</span></span>
<span data-ttu-id="d9529-103">Il peut arriver que vous vouliez ajouter un mappage existant à un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d9529-103">There may be times when you want to add an existing map to a BizTalk project.</span></span> <span data-ttu-id="d9529-104">Pour ce faire, vous devez d’abord vous assurer que les schémas source et de destination du mappage sont inclus dans le projet BizTalk auquel vous ajoutez le mappage ou qu’ils sont référencés par l’assembly .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="d9529-104">Before doing so, you must ensure that the source and destination schemas of the map are included in the BizTalk project to which you are adding the map; or, referenced by the corresponding .NET assembly.</span></span>  
  
### <a name="to-add-an-existing-map-to-a-biztalk-project"></a><span data-ttu-id="d9529-105">Pour ajouter un mappage existant à un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="d9529-105">To add an existing map to a BizTalk project</span></span>  
  
1.  <span data-ttu-id="d9529-106">Cliquez sur un projet BizTalk dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="d9529-106">Right-click a BizTalk project in Solution Explorer, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="d9529-107">Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier contenant le mappage à ajouter, sélectionnez-le, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d9529-107">In the **Add Existing Item** dialog box, browse to the folder containing the map to be added, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="d9529-108">Le mappage s'ouvre dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d9529-108">The map opens in BizTalk Mapper.</span></span> <span data-ttu-id="d9529-109">Le mappage ajouté apparaît également en tant qu’enfant du projet BizTalk actuel dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="d9529-109">The newly added map also appears as a child of the current BizTalk project in Solution Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9529-110">Si vous avez accédé à un dossier différent de celui du projet BizTalk, une copie du mappage ajouté a été créée dans le dossier du projet et c’est cette copie qui a été ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="d9529-110">If you browsed to a folder other than the BizTalk project folder, a copy of the map you added was created in the project folder, and it was this copy of the map that was added to the project.</span></span> <span data-ttu-id="d9529-111">Les modifications ultérieures du mappage sont apportées à cette copie et non au mappage original contenu dans l’autre dossier.</span><span class="sxs-lookup"><span data-stu-id="d9529-111">Subsequent changes to the map are made to this copy, not to the original map in the other folder.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d9529-112">Les mappages BizTalk peuvent uniquement être ouverts par le Mappeur BizTalk, qui est hébergé dans le shell Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9529-112">BizTalk maps can only be opened by BizTalk Mapper, which is hosted within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="d9529-113">Si vous double-cliquez sur un mappage dans l’Explorateur Windows, une nouvelle instance de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] s’ouvrira et le mappage sera ouvert par le Mappeur BizTalk, à condition que les schémas correspondants soient correctement chargés.</span><span class="sxs-lookup"><span data-stu-id="d9529-113">If you double-click a map in Windows Explorer, a new instance of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will be opened, and then the map will be opened by BizTalk Mapper, provided the corresponding schemas are loaded properly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9529-114">Si le mappage existant contient des fonctoids personnalisés, alors les DLL correspondants doivent être copiés dans le dossier « %BTSINSTALLPATH%\Developer Tools\Mapper Extensions ».</span><span class="sxs-lookup"><span data-stu-id="d9529-114">If the existing map contains custom functoids, then the corresponding DLLs must be copied to the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”.</span></span> <span data-ttu-id="d9529-115">Si cela n'est pas fait, le mappage ne se chargera pas et lèvera une erreur suite à l'échec de chargement des fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d9529-115">Else, the map will not load and throws an error because of failure to load custom functoids.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9529-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9529-116">See Also</span></span>  
 <span data-ttu-id="d9529-117">[La gestion des mappages dans des projets](../core/managing-maps-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="d9529-117">[Managing Maps Within Projects](../core/managing-maps-within-projects.md) </span></span>  
 [<span data-ttu-id="d9529-118">Développement de fonctoids personnalisés</span><span class="sxs-lookup"><span data-stu-id="d9529-118">Developing Custom Functoids</span></span>](../core/developing-custom-functoids.md)