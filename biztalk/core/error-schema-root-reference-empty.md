---
title: 'Erreur : référence de racine du schéma vide | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.rootRefEmpty
ms.assetid: 172e6ad8-6118-40db-9451-92808a3a2051
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7217f6f9ea328aff4864cfdf3bee9ea71de3741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-root-reference-empty"></a><span data-ttu-id="0576f-102">Erreur : référence de racine du schéma vide</span><span class="sxs-lookup"><span data-stu-id="0576f-102">Error - Schema Root Reference Empty</span></span>
<span data-ttu-id="0576f-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="0576f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="0576f-104">BEC2005</span><span class="sxs-lookup"><span data-stu-id="0576f-104">BEC2005</span></span>  
  
 <span data-ttu-id="0576f-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="0576f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="0576f-106">Le **référence de racine** propriété de la **schéma** nœud n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="0576f-106">The **Root Reference** property of the **Schema** node is not set.</span></span> <span data-ttu-id="0576f-107">Lorsque le **Standard** propriété de la **schéma** nœud a une valeur autre que **XML**, vous devez définir le **référence de racine** propriété indiquer quel nœud enfant de la **schéma** nœud est destiné à être utilisé en tant que la racine du message défini par ce schéma.</span><span class="sxs-lookup"><span data-stu-id="0576f-107">When the **Standard** property of the **Schema** node is set to a value other than **XML**, you must set the **Root Reference** property to indicate which child node of the **Schema** node is meant to be used as the root of the message defined by this schema.</span></span>  
  
 <span data-ttu-id="0576f-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="0576f-108">**User Action**</span></span>  
  
 <span data-ttu-id="0576f-109">Comme il convient pour votre schéma, soit définir la **Standard** propriété de la **schéma** nœud **XML**, ou définir le **référence de racine** propriété de la **schéma** nœud vers le nœud enfant approprié de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="0576f-109">As appropriate for your schema, either set the **Standard** property of the **Schema** node to **XML**, or set the **Root Reference** property of the **Schema** node to the appropriate child node of the **Schema** node.</span></span> <span data-ttu-id="0576f-110">Les nœuds enfants sont disponibles dans le **référence de racine** liste de propriétés de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="0576f-110">These child nodes are the available in the **Root Reference** property drop-down list.</span></span>