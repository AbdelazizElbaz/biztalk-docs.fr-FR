---
title: "Définir la justification des chaînes dans l’adaptateur JD Edwards OneWorld | Documents Microsoft"
description: "Mettre à jour le fichier jdearglist pour utiliser l’adaptateur JD Edwards OneWorld dans une orchestration BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b32d0106d95a1970b480e32dfa47a81ebf98ca
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="set-string-justification-in-jdearglist"></a><span data-ttu-id="57c75-103">Définir la chaîne de la Justification dans Jdearglist</span><span class="sxs-lookup"><span data-stu-id="57c75-103">Set string Justification in Jdearglist</span></span>

## <a name="overview"></a><span data-ttu-id="57c75-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="57c75-104">Overview</span></span>
<span data-ttu-id="57c75-105">Pour configurer certains arguments de chaîne de sorte qu'ils soient alignés à droite (et remplis à gauche) dans le fichier JD Edwards OneWorld jdearglist.txt, vous devez déterminer la fonction d'entreprise à laquelle vous souhaitez accéder et les champs associés que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="57c75-105">To configure certain string arguments as right-justified (and left padded) in the JD Edwards OneWorld jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.</span></span>  
  
 <span data-ttu-id="57c75-106">Vous devez mettre à jour le fichier jdearglist.txt avant de générer les liaisons (schémas) dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="57c75-106">You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration.</span></span> <span data-ttu-id="57c75-107">Les instructions de mise à jour le fichier jdearglist.txt sont décrites dans [gestion des valeurs de chaîne](../core/handling-string-values1.md).</span><span class="sxs-lookup"><span data-stu-id="57c75-107">The instructions for updating the jdearglist.txt file are outlined in [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
 <span data-ttu-id="57c75-108">Si un message d'avertissement est consigné dans le journal d'audit, il vous informe que le fichier jdearglist.txt est manquant.</span><span class="sxs-lookup"><span data-stu-id="57c75-108">If you receive a jdearglist.txt warning message in the audit log, it informs you that the jdearglist.txt is missing.</span></span> <span data-ttu-id="57c75-109">Si vous exécutez la fonction d'entreprise SalesOrder ou PurchaseOrder, le fichier doit être situé au niveau de votre chemin d'accès, sans quoi elle ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="57c75-109">If you run the SalesOrder or PurchaseOrder business functions, you must have the file in your PATH, or it will not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c75-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57c75-110">See Also</span></span>  
[<span data-ttu-id="57c75-111">Utiliser la gestion des exceptions BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="57c75-111">Use BizTalk Server Exception Handling</span></span>](using-biztalk-server-exception-handling1.md)