---
title: "Comment détecter les problèmes de Configuration d’un fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32afc333-934c-4ffb-b1b5-61af07157200
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 322a97aba4ec5e02cf754106df30b0c9f0088e1b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-detect-configuration-issues-for-a-functoid"></a><span data-ttu-id="4e431-102">Détection des problèmes de configuration d'un fonctoid</span><span class="sxs-lookup"><span data-stu-id="4e431-102">How to Detect Configuration Issues for a Functoid</span></span>
<span data-ttu-id="4e431-103">Vous pouvez rencontrer des problèmes de configuration d'un fonctoid et/ou d'un lien dans le cadre de l'utilisation des mappages.</span><span class="sxs-lookup"><span data-stu-id="4e431-103">While working with maps, you might encounter issues with configuration of a functoid and/or link.</span></span> <span data-ttu-id="4e431-104">Le Mappeur BizTalk utilise un mécanisme de visualisation facilitant l'identification rapide des problèmes associés à la configuration d'un fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4e431-104">The BizTalk Mapper uses a visualization mechanism to help quickly identify problems associated with a functoid configuration.</span></span> <span data-ttu-id="4e431-105">Cette indication visuelle est rendu sous la forme d’une annotation d’avertissement sur l’icône du fonctoid (pour par exemple, ![Functoid IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) dans la vue de relation.</span><span class="sxs-lookup"><span data-stu-id="4e431-105">This visual indication renders as a warning annotation on the functoid icon (for e.g. ![Functoid IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) in the relationship view.</span></span> <span data-ttu-id="4e431-106">Cette rubrique fournit des informations sur la détection des problèmes de configuration d'un fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4e431-106">This topic provides information about how to detect the configuration issues for a functoid.</span></span>  
  
 <span data-ttu-id="4e431-107">L'icône d'avertissement apparaît lorsque le Mappeur détecte qu'un fonctoid n'est pas correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="4e431-107">The warning status icon appears when the Mapper detects that a functoid is not properly configured.</span></span> <span data-ttu-id="4e431-108">Déplacer le curseur de la souris sur le fonctoid affiche également des informations succinctes sur le problème identifié par le Mappeur.</span><span class="sxs-lookup"><span data-stu-id="4e431-108">Moving the mouse over the functoid also displays brief information of the issue identified by the Mapper.</span></span> <span data-ttu-id="4e431-109">Par exemple, si un fonctoid ne possède pas le nombre minimal d'entrées valides, l'info-bulle associée mentionne le nombre de paramètres d'entrée requis.</span><span class="sxs-lookup"><span data-stu-id="4e431-109">For example, if a functoid does not have minimum number of valid inputs, the tooltip for the functoid mentions the number of input parameters required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e431-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4e431-110">Prerequisites</span></span>  
 <span data-ttu-id="4e431-111">Cette opération nécessite l'exécution du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4e431-111">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-detect-configuration-issues-for-a-functoid"></a><span data-ttu-id="4e431-112">Pour détecter les problèmes de configuration d'un fonctoid</span><span class="sxs-lookup"><span data-stu-id="4e431-112">To detect configuration issues for a functoid</span></span>  
  
1.  <span data-ttu-id="4e431-113">Faites glisser le fonctoid requis de la barre d'outils sur la page de grille.</span><span class="sxs-lookup"><span data-stu-id="4e431-113">Drag the required functoid from the toolbox onto the grid page.</span></span> <span data-ttu-id="4e431-114">Le fonctoid est affiché avec une icône d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="4e431-114">You see the functoid with a warning icon.</span></span>  
  
2.  <span data-ttu-id="4e431-115">Vous pouvez effectuer l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4e431-115">You can do one of the following:</span></span>  
  
    -   <span data-ttu-id="4e431-116">déplacer le pointeur de la souris sur le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4e431-116">Move the mouse pointer on the functoid.</span></span> <span data-ttu-id="4e431-117">L'info-bulle affiche des informations sur l'erreur et sur ce que vous devez faire.</span><span class="sxs-lookup"><span data-stu-id="4e431-117">The tooltip displays information about the error and what you need to do.</span></span>  
  
         <span data-ttu-id="4e431-118">La figure suivante montre une info-bulle avec des informations d'erreur lors de la configuration du fonctoid « Addition ».</span><span class="sxs-lookup"><span data-stu-id="4e431-118">The following figure displays a tooltip with error information while configuring the functoid “Addition.”</span></span>  
  
         <span data-ttu-id="4e431-119">![Détection d’erreur dans la configuration du fonctoid](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")</span><span class="sxs-lookup"><span data-stu-id="4e431-119">![Error detection in functoid configuration](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")</span></span>  
  
    -   <span data-ttu-id="4e431-120">double-cliquer sur le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4e431-120">Double-click the functoid.</span></span> <span data-ttu-id="4e431-121">Le **configurer \<fonctoid > fonctoid** boîte de dialogue affiche des icônes d’avertissement sur les paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4e431-121">The **Configure \<Functoid> Functoid** dialog box displays warning icons against the input parameters.</span></span> <span data-ttu-id="4e431-122">Ceci indique que les paramètres d'entrée du fonctoid sélectionné ne sont pas configurés.</span><span class="sxs-lookup"><span data-stu-id="4e431-122">This indicates that the input parameters of the selected functoid are not configured.</span></span>  
  
         <span data-ttu-id="4e431-123">La figure suivante affiche des informations d'erreur sur les paramètres d'entrée du fonctoid « Addition ».</span><span class="sxs-lookup"><span data-stu-id="4e431-123">The following figure displays error information about input parameters for the “Addition” functoid.</span></span>  
  
         <span data-ttu-id="4e431-124">![Avertissement affiché lorsque le fonctoid n’est pas configuré](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")</span><span class="sxs-lookup"><span data-stu-id="4e431-124">![Warning displayed when functoid is not configured](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e431-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e431-125">See Also</span></span>  
 [<span data-ttu-id="4e431-126">À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="4e431-126">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)