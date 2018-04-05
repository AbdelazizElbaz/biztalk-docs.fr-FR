---
title: 'Erreur : aucun Assembly pour le fonctoid script | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.noAssemblyForScriptingFunctoid
ms.assetid: db8fa41c-904c-4789-9522-f3107dbeb087
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8e8f6cfcb0f75529c1c677dfe6d5ce388881e5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---no-assembly-for-scripting-functoid"></a><span data-ttu-id="f81a1-102">Erreur : aucun Assembly pour le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="f81a1-102">Error - No Assembly for Scripting Functoid</span></span>
<span data-ttu-id="f81a1-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f81a1-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f81a1-104">btm1007</span><span class="sxs-lookup"><span data-stu-id="f81a1-104">btm1007</span></span>  
  
 <span data-ttu-id="f81a1-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f81a1-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f81a1-106">Le **Assembly du Script** propriété du fonctoid **script** fonctoid n’a pas été défini même si le **le Type de Script** indique qu’un assembly externe contient le script pour ce **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="f81a1-106">The **Script Assembly** property of the indicated **Scripting** functoid has not been set even though the **Script Type** property indicates that an external assembly contains the script for this **Scripting** functoid.</span></span>  
  
 <span data-ttu-id="f81a1-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f81a1-107">**User Action**</span></span>  
  
 <span data-ttu-id="f81a1-108">Sélectionnez le **script** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **Script** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis définissez les valeurs appropriées dans le **configurer le Script du fonctoid** boîte de dialogue, y compris le **Assembly du Script** propriété.</span><span class="sxs-lookup"><span data-stu-id="f81a1-108">Select the indicated **Scripting** functoid, click the ellipsis (**...**) button associated with the **Script** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then set the appropriate values in the **Configure Functoid Script** dialog box, including the **Script Assembly** property.</span></span>