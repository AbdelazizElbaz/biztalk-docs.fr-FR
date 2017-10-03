---
title: "Fonctions de contrôle du moteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rules Engine, functions
ms.assetid: a7900e59-c52c-4a6d-9ca3-ee4ec659f9b5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 033a4213a6552319f44a98e23562d7e8703fdd42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="engine-control-functions"></a><span data-ttu-id="7c01d-102">Fonctions de contrôle de moteur</span><span class="sxs-lookup"><span data-stu-id="7c01d-102">Engine Control Functions</span></span>
<span data-ttu-id="7c01d-103">Cette section décrit les comportements associés à plusieurs fonctions de contrôle du moteur des règles d'entreprise qui permettent à une application ou à une stratégie de contrôler les faits dans la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="7c01d-103">This section explains the behaviors associated with several Business Rule engine control functions that allow an application or policy to control the facts in the rule engine's working memory.</span></span> <span data-ttu-id="7c01d-104">La présence de faits dans la mémoire de travail détermine les conditions qui sont évaluées et les actions qui sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="7c01d-104">The presence of facts in the working memory drives the conditions that are evaluated and the actions that are executed.</span></span>  
  
 <span data-ttu-id="7c01d-105">Cette section examine le **Assert**, **retrait**, **RetractByType**, **redéclarer**, et **mise à jour** fonctions pour différents faits : objets .NET, **TypedXmlDocument**, **DataConnection**, et **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="7c01d-105">This section examines the **Assert**, **Retract**, **RetractByType**, **Reassert**, and **Update** functions for different facts: .NET objects, **TypedXmlDocument**, **DataConnection**, and **TypedDataTable**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c01d-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7c01d-106">In This Section</span></span>  
  
-   [<span data-ttu-id="7c01d-107">Assert</span><span class="sxs-lookup"><span data-stu-id="7c01d-107">Assert</span></span>](../core/assert.md)  
  
-   [<span data-ttu-id="7c01d-108">Retrait</span><span class="sxs-lookup"><span data-stu-id="7c01d-108">Retract</span></span>](../core/retract.md)  
  
-   [<span data-ttu-id="7c01d-109">RetractByType</span><span class="sxs-lookup"><span data-stu-id="7c01d-109">RetractByType</span></span>](../core/retractbytype.md)  
  
-   [<span data-ttu-id="7c01d-110">Redéclarer</span><span class="sxs-lookup"><span data-stu-id="7c01d-110">Reassert</span></span>](../core/reassert.md)  
  
-   [<span data-ttu-id="7c01d-111">Update</span><span class="sxs-lookup"><span data-stu-id="7c01d-111">Update</span></span>](../core/update1.md)  
  
-   [<span data-ttu-id="7c01d-112">Arrêter</span><span class="sxs-lookup"><span data-stu-id="7c01d-112">Halt</span></span>](../core/halt.md)