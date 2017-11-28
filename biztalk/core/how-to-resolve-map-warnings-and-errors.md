---
title: "Comment résoudre les erreurs et avertissements de la carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a3e7f3-c96c-4d3d-9f7c-d2bfd9ace4fd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2983a53bb47aa66d1564772d0f8e033132e5a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resolve-map-warnings-and-errors"></a><span data-ttu-id="a122e-102">Résolution des avertissements et des erreurs liés aux mappages</span><span class="sxs-lookup"><span data-stu-id="a122e-102">How to Resolve Map Warnings and Errors</span></span>
<span data-ttu-id="a122e-103">Lors de la compilation d’un mappage, il se peut que le processus donne lieu à des avertissements et des erreurs.</span><span class="sxs-lookup"><span data-stu-id="a122e-103">When you compile a map, you may find that warnings and errors result from the compilation process.</span></span>  
  
## <a name="resolve-warnings-and-errors-when-building-a-map"></a><span data-ttu-id="a122e-104">Résoudre les erreurs et des avertissements lors de la création d’un mappage</span><span class="sxs-lookup"><span data-stu-id="a122e-104">Resolve warnings and errors when building a map</span></span>  
  
1.  <span data-ttu-id="a122e-105">Pour les erreurs de liaison et de fonctoid, dans le **liste d’erreurs** fenêtre, double-cliquez sur n’importe quelle description.</span><span class="sxs-lookup"><span data-stu-id="a122e-105">For link and functoid errors, in the **Error List** window, double-click any description.</span></span>  
  
     <span data-ttu-id="a122e-106">La liaison, le fonctoid ou le nœud de schéma associé à l’erreur apparaît en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="a122e-106">The link, functoid, or the schema node associated with the error is highlighted.</span></span> <span data-ttu-id="a122e-107">Procédez à la résolution du problème.</span><span class="sxs-lookup"><span data-stu-id="a122e-107">Resolve the issue.</span></span>  
  
2.  <span data-ttu-id="a122e-108">Examinez le **Description** zone dans le **liste d’erreurs** fenêtre afin d’identifier les erreurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="a122e-108">Review the **Description** area in the **Error List** window to determine additional errors.</span></span>  
  
3.  <span data-ttu-id="a122e-109">Cliquez sur le **sortie** onglet de fenêtre pour afficher les informations de message avertissement et d’erreur supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="a122e-109">Click the **Output** window tab to view additional warning and error message information.</span></span>  
  
4.  <span data-ttu-id="a122e-110">Une fois que vous avez résolu tous les problèmes, cliquez sur le nom de fichier de mappage dans l’Explorateur de solutions, puis cliquez sur **Test Map** ou **générer la Solution**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="a122e-110">After you have resolved all issues, right-click the map file name in Solution Explorer, and then click **Test Map** or **Build Solution**, as the case may be.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a122e-111">Si un avertissement s’affiche, le problème risque d’exister sur plusieurs pages de grille.</span><span class="sxs-lookup"><span data-stu-id="a122e-111">If a warning appears, the problem might exist over several grid pages.</span></span> <span data-ttu-id="a122e-112">Par exemple, vous disposez de la page de grille 1 avec un enregistrement (nommé **élément**) dans l’arborescence des schémas sources liée à un enregistrement (nommé **numéro**) dans l’arborescence de schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="a122e-112">For example, you have grid page 1 with a record (named **Item**) in the source schema tree linked to a record (named **Number**) in the destination schema tree.</span></span> <span data-ttu-id="a122e-113">Sur la page de grille 2 vous disposez d’un enregistrement (nommé **produit**) dans l’arborescence du schéma source lié à la même **nombre** enregistrement dans l’arborescence de schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="a122e-113">On grid page 2 you have a record (named **Product**) in the source schema tree linked to the same **Number** record in the destination schema tree.</span></span> <span data-ttu-id="a122e-114">Dans ce scénario, un message d’avertissement est généré indiquant que vous disposez de plusieurs entrées pour le même enregistrement.</span><span class="sxs-lookup"><span data-stu-id="a122e-114">In this scenario, a warning message is generated stating that you have multiple inputs to the same record.</span></span> <span data-ttu-id="a122e-115">Toutefois, si vous affichez la page de grille 1, vous voyez uniquement une seule entrée dans le **nombre** enregistrement.</span><span class="sxs-lookup"><span data-stu-id="a122e-115">However if you view grid page 1, you see only one input into the **Number** record.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="a122e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a122e-116">See Also</span></span>  
 <span data-ttu-id="a122e-117">[La compilation et test des mappages](../core/compiling-and-testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="a122e-117">[Compiling and Testing Maps](../core/compiling-and-testing-maps.md) </span></span>  
 <span data-ttu-id="a122e-118">[Erreurs du Mappeur BizTalk](../core/biztalk-mapper-errors.md) </span><span class="sxs-lookup"><span data-stu-id="a122e-118">[BizTalk Mapper Errors](../core/biztalk-mapper-errors.md) </span></span>  
 [<span data-ttu-id="a122e-119">Résolution des problèmes de mappages</span><span class="sxs-lookup"><span data-stu-id="a122e-119">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)