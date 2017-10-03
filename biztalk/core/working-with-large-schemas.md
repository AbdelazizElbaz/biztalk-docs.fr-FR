---
title: "Utilisation de grands schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8348036d-6edb-46a3-badd-0223cfe0a92f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c5ef679070009b5dfb5fdd403d238cfe243cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-large-schemas"></a><span data-ttu-id="ff51f-102">Utilisation de grands schémas</span><span class="sxs-lookup"><span data-stu-id="ff51f-102">Working with Large Schemas</span></span>
<span data-ttu-id="ff51f-103">Si vos schémas deviennent très volumineux, vous constaterez que l'actualisation de la vue XSD prend de plus en plus de temps et éventuellement que la réponse d'autres aspects de l'interface utilisateur est affectée.</span><span class="sxs-lookup"><span data-stu-id="ff51f-103">When your schemas become very large, you may find that refreshing the XSD view is increasingly slow and that the response of other aspects of the user interface can be impacted as well.</span></span> <span data-ttu-id="ff51f-104">La solution à ce problème consiste à désactiver la fonctionnalité d’actualisation automatique, mais plutôt le manuel **Actualiser** lien dans la vue XSD pour actualiser périodiquement la vue XSD.</span><span class="sxs-lookup"><span data-stu-id="ff51f-104">The solution to this issue is to turn off the auto-refresh feature and instead use the manual **Refresh** link in the XSD view to periodically refresh the XSD view.</span></span> <span data-ttu-id="ff51f-105">Pour activer des instructions détaillées sur la façon la fonctionnalité d’actualisation automatique sur un arrêt, voir la procédure « pour activer et désactiver la l’actualisation automatique de la vue XSD » dans [la gestion de la vue XSD](../core/how-to-manage-the-xsd-view.md).</span><span class="sxs-lookup"><span data-stu-id="ff51f-105">For step-by-step instructions about how turn the auto-refresh feature on an off, see the procedure "To turn automatic refresh of the XSD view on and off" in [Managing the XSD View](../core/how-to-manage-the-xsd-view.md).</span></span>  
  
 <span data-ttu-id="ff51f-106">Performances peuvent également être lentes dans les grands schémas avec plusieurs racines attachés à la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="ff51f-106">Performance may also be slow in large schemas with multiple roots attached to the **schema** node.</span></span> <span data-ttu-id="ff51f-107">Définition de la **référence de racine** propriété peut améliorer les performances de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ff51f-107">Setting the **Root Reference** property may increase performance in the user interface.</span></span> <span data-ttu-id="ff51f-108">Paramètre **référence de racine** améliore les performances car le compilateur crée des classes c# pour tous les schémas racine.</span><span class="sxs-lookup"><span data-stu-id="ff51f-108">Setting **Root Reference** improves performance because the compiler creates C# classes for all root schemas.</span></span> <span data-ttu-id="ff51f-109">Une racine unique implique la création d'un nombre moins important de classes.</span><span class="sxs-lookup"><span data-stu-id="ff51f-109">A single root means the creation of fewer classes.</span></span>  
  
 <span data-ttu-id="ff51f-110">**Valider l’Instance** semble lent dans l’interface utilisateur, car une validation est toujours effectuée sur le schéma avant la validation de l’instance.</span><span class="sxs-lookup"><span data-stu-id="ff51f-110">**Validate Instance** may appear slow in the user interface because a validation is always done on the schema before validating the instance.</span></span> <span data-ttu-id="ff51f-111">La validation de schémas n'a lieu que dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ff51f-111">Schema validation occurs only in the user interface.</span></span> <span data-ttu-id="ff51f-112">Définition de la **référence de racine** propriété améliore également les performances de l’interface utilisateur dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="ff51f-112">Setting the **Root Reference** property also improves user interface performance in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff51f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff51f-113">See Also</span></span>  
 [<span data-ttu-id="ff51f-114">À l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="ff51f-114">Using BizTalk Editor</span></span>](../core/using-biztalk-editor.md)