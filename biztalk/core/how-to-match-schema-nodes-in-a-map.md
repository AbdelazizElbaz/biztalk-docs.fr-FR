---
title: "Mise en correspondance des nœuds de schéma dans un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 584f85d2-6198-4ef3-90d9-a322f1457d9a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e2ce880489ca49b0b55d2e6f45b9e887d719a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-match-schema-nodes-in-a-map"></a><span data-ttu-id="8f465-102">Mise en correspondance des nœuds de schémas à un mappage</span><span class="sxs-lookup"><span data-stu-id="8f465-102">How to Match Schema Nodes in a Map</span></span>
<span data-ttu-id="8f465-103">Il peut être difficile de mapper des éléments lorsque les schémas source et de destination sont complexes.</span><span class="sxs-lookup"><span data-stu-id="8f465-103">When the source or destination schemas are complex, it can be difficult to map the elements.</span></span> <span data-ttu-id="8f465-104">Le Mappeur BizTalk introduit le **de correspondance indicatives :** fonctionnalité, qui vous permet de mapper des éléments de schéma complexes en suggérant les meilleures correspondances possibles.</span><span class="sxs-lookup"><span data-stu-id="8f465-104">The BizTalk Mapper introduces the **Indicative Match** feature, which enables you to map complex schema elements by suggesting the best possible matches.</span></span> <span data-ttu-id="8f465-105">Cette rubrique fournit les informations vous permettant d'effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="8f465-105">This topic provides information about how to perform this operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f465-106">Le Mappeur BizTalk suggère les correspondances possibles pour un nœud de schéma.</span><span class="sxs-lookup"><span data-stu-id="8f465-106">The BizTalk Mapper suggests possible matches for a schema node.</span></span> <span data-ttu-id="8f465-107">Actuellement, cette fonctionnalité prend uniquement en charge les noms anglais.</span><span class="sxs-lookup"><span data-stu-id="8f465-107">This feature is currently supported only for English names.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f465-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8f465-108">Prerequisites</span></span>  
 <span data-ttu-id="8f465-109">Les instructions suivantes requièrent l'exécution du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f465-109">These instructions require that the BizTalk Mapper is running.</span></span>  
  
### <a name="to-match-relevant-schema-nodes"></a><span data-ttu-id="8f465-110">Pour mettre en correspondance des nœuds de schéma</span><span class="sxs-lookup"><span data-stu-id="8f465-110">To match relevant schema nodes</span></span>  
  
1.  <span data-ttu-id="8f465-111">Sélectionnez et cliquez sur l’élément de schéma pour lequel vous avez besoin connaître les meilleures correspondances, puis cliquez sur **indiquer les correspondances**.</span><span class="sxs-lookup"><span data-stu-id="8f465-111">Select and right-click the schema element for which you need to know the best matches, and then click **Indicate Matches**.</span></span> <span data-ttu-id="8f465-112">Le Mappeur BizTalk indique les meilleures correspondances (limitées à sept) en sélectionnant la correspondance optimale.</span><span class="sxs-lookup"><span data-stu-id="8f465-112">The BizTalk Mapper highlights the best matches (restricted to seven), with the most optimum match selected.</span></span>  
  
     <span data-ttu-id="8f465-113">Vous pouvez également sélectionner **indiquer les correspondances** à partir du menu BizTalk, ou appuyez sur MAJ + touches de l’espace.</span><span class="sxs-lookup"><span data-stu-id="8f465-113">Alternatively, you can select **Indicate Matches** from the BizTalk menu, or press SHIFT + SPACE keys.</span></span>  
  
     <span data-ttu-id="8f465-114">La figure suivante illustre les correspondances suggérées pour le nœud sélectionné dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="8f465-114">The following figure shows suggestive matches for the selected node in destination schema.</span></span>  
  
     <span data-ttu-id="8f465-115">![Mappage suggéré](../core/media/suggestive-mapping.gif "Suggestive_Mapping")</span><span class="sxs-lookup"><span data-stu-id="8f465-115">![Suggestive mapping](../core/media/suggestive-mapping.gif "Suggestive_Mapping")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f465-116">Maintenez appuyée la touche MAJ pour parcourir la liste des correspondances suggérées.</span><span class="sxs-lookup"><span data-stu-id="8f465-116">Hold down the SHIFT key to traverse among the suggestive matches.</span></span>  
  
2.  <span data-ttu-id="8f465-117">Vous pouvez maintenant effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f465-117">You can now do the following:</span></span>  
  
    -   <span data-ttu-id="8f465-118">appuyer sur ENTRÉE pour valider la (meilleure) correspondance en surbrillance ;</span><span class="sxs-lookup"><span data-stu-id="8f465-118">Press ENTER to confirm the highlighted (best possible) match.</span></span>  
  
    -   <span data-ttu-id="8f465-119">utiliser les flèches HAUT et BAS pour parcourir les correspondances en surbrillance dans l'ordre de préférence.</span><span class="sxs-lookup"><span data-stu-id="8f465-119">Use the UP/DOWN ARROW keys to cycle through the highlighted matches in the order of preference.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f465-120">Appuyez sur la flèche BAS pour accéder à la meilleure correspondance suivante et sur la touche HAUT pour mettre en surbrillance la meilleure correspondance précédente.</span><span class="sxs-lookup"><span data-stu-id="8f465-120">Press the DOWN ARROW key to traverse to the next best match, and the UP ARROW key highlights the previous best match.</span></span>  
  
    -   <span data-ttu-id="8f465-121">Appuyez sur la touche DÉBUT pour retourner à la première correspondance.</span><span class="sxs-lookup"><span data-stu-id="8f465-121">Press the HOME key to return to the top match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f465-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f465-122">See Also</span></span>  
 [<span data-ttu-id="8f465-123">À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8f465-123">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)