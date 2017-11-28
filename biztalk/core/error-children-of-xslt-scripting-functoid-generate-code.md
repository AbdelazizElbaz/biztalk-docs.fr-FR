---
title: "Erreur : Code généré par les enfants du fonctoid script XSLT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.xsltScriptingChildrenGenCode
ms.assetid: 9cdac362-177f-445e-904b-aa6a9b1eb46f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 810fe9befecd9bbd1a15468ca714177900450cb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---children-of-xslt-scripting-functoid-generate-code"></a><span data-ttu-id="ce29c-102">Erreur : Code généré par les enfants du fonctoid script XSLT</span><span class="sxs-lookup"><span data-stu-id="ce29c-102">Error - Children of XSLT Scripting Functoid Generate Code</span></span>
<span data-ttu-id="ce29c-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="ce29c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="ce29c-104">btm1063</span><span class="sxs-lookup"><span data-stu-id="ce29c-104">btm1063</span></span>  
  
 <span data-ttu-id="ce29c-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="ce29c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="ce29c-106">Un scénario qui se révèle contradictoire avec l’utilisation d’un **script** fonctoid qui est configuré pour utiliser un modèle d’appel XSLT ou XSLT inline a été trouvé dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="ce29c-106">A scenario that contradicts the use of a **Scripting** functoid that is configured to use inline XSLT or an XSLT Call Template was found in the map.</span></span> <span data-ttu-id="ce29c-107">Dans le schéma de destination, les descendants d’un nœud qui est lié à la sortie d’un **script** fonctoid tentent de générer leur propre code XSLT.</span><span class="sxs-lookup"><span data-stu-id="ce29c-107">In the destination schema, descendent nodes of a node that is linked to the output of such a **Scripting** functoid are attempting to generate XSLT code of their own.</span></span>  
  
 <span data-ttu-id="ce29c-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="ce29c-108">**User Action**</span></span>  
  
 <span data-ttu-id="ce29c-109">Supprimer l’incompatibilité en modifiant l’utilisation de la **script** fonctoid ou modifiez les nœuds enfants, tels qu’ils ne sont plus de générer leur propre code XSLT.</span><span class="sxs-lookup"><span data-stu-id="ce29c-109">Remove the incompatibility by changing the usage of the relevant **Scripting** functoid or changing the child nodes such that they no longer generate XSLT code of their own.</span></span>