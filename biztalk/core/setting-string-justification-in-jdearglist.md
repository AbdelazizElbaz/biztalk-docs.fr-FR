---
title: "Définition de Justification des chaînes dans Jdearglist | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, setting string justification
- strings, configuring
- strings, right-justified
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daecf4101ebf5dc8964562dc7f385d41279a3401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-string-justification-in-jdearglist"></a><span data-ttu-id="8fdb5-102">Configuration de la justification des chaînes dans Jdearglist</span><span class="sxs-lookup"><span data-stu-id="8fdb5-102">Setting String Justification in Jdearglist</span></span>
<span data-ttu-id="8fdb5-103">Pour configurer certains arguments de chaîne de sorte qu'ils soient alignés à droite (et remplis à gauche) dans le fichier JD Edwards OneWorld jdearglist.txt, vous devez déterminer la fonction d'entreprise à laquelle vous souhaitez accéder et les champs associés que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="8fdb5-103">To configure certain string arguments as right-justified (and left padded) in the JD Edwards OneWorld jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.</span></span>  
  
 <span data-ttu-id="8fdb5-104">Vous devez mettre à jour le fichier jdearglist.txt avant de générer les liaisons (schémas) dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="8fdb5-104">You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration.</span></span> <span data-ttu-id="8fdb5-105">Les instructions de mise à jour le fichier jdearglist.txt sont décrites dans [gestion des valeurs de chaîne](../core/handling-string-values1.md).</span><span class="sxs-lookup"><span data-stu-id="8fdb5-105">The instructions for updating the jdearglist.txt file are outlined in [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
 <span data-ttu-id="8fdb5-106">Si un message d'avertissement est consigné dans le journal d'audit, il vous informe que le fichier jdearglist.txt est manquant.</span><span class="sxs-lookup"><span data-stu-id="8fdb5-106">If you receive a jdearglist.txt warning message in the audit log, it informs you that the jdearglist.txt is missing.</span></span> <span data-ttu-id="8fdb5-107">Si vous exécutez la fonction d'entreprise SalesOrder ou PurchaseOrder, le fichier doit être situé au niveau de votre chemin d'accès, sans quoi elle ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="8fdb5-107">If you run the SalesOrder or PurchaseOrder business functions, you must have the file in your PATH, or it will not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fdb5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fdb5-108">See Also</span></span>  
 [<span data-ttu-id="8fdb5-109">Administration de l’adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="8fdb5-109">Administering BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/administering-biztalk-adapter-for-jd-edwards-oneworld.md)