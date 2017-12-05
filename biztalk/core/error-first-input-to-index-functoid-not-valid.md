---
title: "Erreur - première entrée du fonctoid Index n’est pas valide. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputToIndexNotValid
ms.assetid: f7dbe9cc-9cfa-4fc7-af3e-1241cb2b50a9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163de330945cc085648188dffcb75821c11ec5d6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---first-input-to-index-functoid-not-valid"></a><span data-ttu-id="69362-102">Erreur - première entrée du fonctoid Index n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="69362-102">Error - First Input to Index Functoid Not Valid</span></span>
<span data-ttu-id="69362-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="69362-103">**Error Code**</span></span>  
  
 <span data-ttu-id="69362-104">btm1015</span><span class="sxs-lookup"><span data-stu-id="69362-104">btm1015</span></span>  
  
 <span data-ttu-id="69362-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="69362-105">**Explanation**</span></span>  
  
 <span data-ttu-id="69362-106">Le premier paramètre d’entrée pour le fonctoid **Index** fonctoid ne provient pas d’un **champ** nœud au sein d’un bouclage **enregistrement** nœud dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="69362-106">The first input parameter to the indicated **Index** functoid is not from a **Field** node within a looping **Record** node in the source schema.</span></span>  
  
 <span data-ttu-id="69362-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="69362-107">**User Action**</span></span>  
  
 <span data-ttu-id="69362-108">Créer le lien d’entrée approprié en faisant glisser entre un **champ** nœud au sein d’un bouclage **enregistrement** nœud dans le schéma source et le fonctoid **Index** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="69362-108">Create the appropriate input link by dragging between a **Field** node within a looping **Record** node in the source schema and the indicated **Index** functoid.</span></span> <span data-ttu-id="69362-109">Il peut être nécessaire ouvrir le **configurer \<fonctoid\> fonctoid** boîte de dialogue en sélectionnant le fonctoid **Index** fonctoid et en cliquant sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés afin de garantir que le lien créé est le premier paramètre d’entrée pour le fonctoid **Index** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="69362-109">It may be necessary to open the **Configure \<Functoid\> Functoid** dialog box by selecting the indicated **Index** functoid and clicking the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window in order to ensure that the newly created link is the first input parameter to the indicated **Index** functoid.</span></span>