---
title: "Erreur : aucune méthode pour le fonctoid script | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.noMethodForScriptingFunctiod
ms.assetid: 8e844626-2878-4ac2-9e8e-240bd32921ac
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7b053d58de52a52903eef587bff4e76610c984a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---no-method-for-scripting-functoid"></a><span data-ttu-id="af70c-102">Erreur : aucune méthode pour le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="af70c-102">Error - No Method for Scripting Functoid</span></span>
<span data-ttu-id="af70c-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="af70c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="af70c-104">btm1009</span><span class="sxs-lookup"><span data-stu-id="af70c-104">btm1009</span></span>  
  
 <span data-ttu-id="af70c-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="af70c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="af70c-106">Le **méthode de Script** propriété du fonctoid **script** fonctoid n’a pas été défini même si le **le Type de Script** propriété indique qu’un assembly externe contient le script pour cette **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="af70c-106">The **Script Method** property of the indicated **Scripting** functoid has not been set even though the **Script Type** property indicates that an external assembly contains the script for this **Scripting** functoid.</span></span>  
  
 <span data-ttu-id="af70c-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="af70c-107">**User Action**</span></span>  
  
 <span data-ttu-id="af70c-108">Sélectionnez le **script** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **Script** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis définissez les valeurs appropriées dans le **configurer le Script du fonctoid** boîte de dialogue, y compris le **méthode de Script** propriété.</span><span class="sxs-lookup"><span data-stu-id="af70c-108">Select the indicated **Scripting** functoid, click the ellipsis (**...**) button associated with the **Script** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then set the appropriate values in the **Configure Functoid Script** dialog box, including the **Script Method** property.</span></span>