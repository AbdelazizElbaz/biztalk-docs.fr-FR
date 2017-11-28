---
title: "Paramètres d’entrée du fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cca24f93-74a8-460c-b9ab-9aa2c767fe2f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97919e3afcb6277f33aa65e6e8e6370aecb23844
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="functoid-input-parameters"></a><span data-ttu-id="ca409-102">Paramètres d'entrée de fonctoid</span><span class="sxs-lookup"><span data-stu-id="ca409-102">Functoid Input Parameters</span></span>
<span data-ttu-id="ca409-103">La configuration correcte des paramètres d'entrée des fonctoids est un des aspects stratégiques de l'utilisation des fonctoids dans les mappages.</span><span class="sxs-lookup"><span data-stu-id="ca409-103">A critical aspect of using functoids in your maps is properly configuring the input parameters to the functoid.</span></span> <span data-ttu-id="ca409-104">Lors de l’ordre des paramètres d’entrée n’est pas critique pour tous les fonctoids (telles que la **ajout** fonctoid, qui affiche les propriétés associées qu’attend d’une addition), plusieurs fonctoids doivent avoir les paramètres d’entrée spécifié dans l’ordre approprié.</span><span class="sxs-lookup"><span data-stu-id="ca409-104">While the order of input parameters is not critical for all functoids (such as the **Addition** functoid, which displays the same associate properties that one expects from addition), many functoids must have their input parameters specified in the correct order.</span></span>  
  
## <a name="create-input-paramaters"></a><span data-ttu-id="ca409-105">Créer des paramètres d’entrée</span><span class="sxs-lookup"><span data-stu-id="ca409-105">Create input paramaters</span></span>
 <span data-ttu-id="ca409-106">Il existe deux méthodes pour créer les paramètres d'entrée d'un fonctoid :</span><span class="sxs-lookup"><span data-stu-id="ca409-106">There are two ways that input parameters to a functoid can be created:</span></span>  
  
-   <span data-ttu-id="ca409-107">créer des liens dans la partie gauche d'un fonctoid dans la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="ca409-107">By creating links into the left side of a functoid in the displayed grid page.</span></span> <span data-ttu-id="ca409-108">L'ordre dans lequel vous créez les liens est celui dans lequel les paramètres d'entrée associés sont transmis au fonctoid ;</span><span class="sxs-lookup"><span data-stu-id="ca409-108">The order in which you create the links is the order in which the associated input parameters are passed to the functoid.</span></span>  
  
-   <span data-ttu-id="ca409-109">En ouvrant le **configurer \<fonctoid > fonctoid** boîte de dialogue et ajouter de nouveaux paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ca409-109">By opening the **Configure \<Functoid> Functoid** dialog box and adding new input parameters.</span></span> <span data-ttu-id="ca409-110">Cette boîte de dialogue est importante, car elle permet aussi de remettre les paramètres d'entrée d'un fonctoid dans l'ordre approprié.</span><span class="sxs-lookup"><span data-stu-id="ca409-110">This dialog box is also important because it allows you to reorder the input parameters to a functoid so that they are in the correct order.</span></span> <span data-ttu-id="ca409-111">Par exemple, si vous créez des liens avec le fonctoid dans un ordre incorrect, vous pouvez vous servir de cette boîte pour apporter les corrections nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ca409-111">For example, if you create links to the functoid in the incorrect order, you can go to this dialog box and make the necessary corrections.</span></span> <span data-ttu-id="ca409-112">Pour obtenir des instructions sur la configuration des paramètres d’entrée d’un fonctoid, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ca409-112">For step-by-step instructions on configuring the input parameters for a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
  
 <span data-ttu-id="ca409-113">Vous devez utiliser le **configurer \<fonctoid > fonctoid** boîte de dialogue pour créer des paramètres d’entrée qui sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="ca409-113">You must use the **Configure \<Functoid> Functoid** dialog box to create input parameters that are constants.</span></span>  
  
 <span data-ttu-id="ca409-114">Lorsque vous fournissez une étiquette pour un lien ou un fonctoid à l’aide de la **étiquette** propriété dans la fenêtre Propriétés lorsque la liaison ou le fonctoid est sélectionné, cette étiquette sera affichée dans le **configurer \<fonctoid > fonctoid**  boîte de dialogue au lieu du XPath correspondant d’un nœud de schéma, ou le nom d’un fonctoid actuellement utilisé comme paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ca409-114">When you provide a label for a link or functoid using the **Label** property in the Properties window when the link or functoid is selected, that label will be shown in the **Configure \<Functoid> Functoid** dialog box rather than the corresponding XPath of a schema node, or the name of a functoid being used as an input parameter.</span></span> <span data-ttu-id="ca409-115">Avec les étiquettes, il sera beaucoup plus facile de différencier les paramètres et de les mettre dans l'ordre qui convient.</span><span class="sxs-lookup"><span data-stu-id="ca409-115">With labels, it will be much easier to tell which parameter is which, and to get them into the correct order.</span></span>  
  
 <span data-ttu-id="ca409-116">Pour plus d’informations sur l’ordre correct des paramètres d’entrée du fonctoid définitives, consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="ca409-116">For definitive information about the correct order of functoid input parameters, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ca409-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca409-117">See Also</span></span>  
 <span data-ttu-id="ca409-118">[Configurer les paramètres d’entrée de fonctoid](../core/how-to-configure-functoid-input-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="ca409-118">[Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md) </span></span>  
 <span data-ttu-id="ca409-119">[Configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="ca409-119">[Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md) </span></span>  
 [<span data-ttu-id="ca409-120">Configurer le bouclage de Table et de fonctoids Extracteur de Table</span><span class="sxs-lookup"><span data-stu-id="ca409-120">Configure the Table Looping and Table Extractor Functoids</span></span>](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)