---
title: 'Erreur : aucune classe pour le fonctoid script | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.noClassForScriptingFunctoid
ms.assetid: c02504d4-4e13-42dc-9446-869c9dca513a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1668f4d29dc5748290e24b85a6f1a2623393e1b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---no-class-for-scripting-functoid"></a><span data-ttu-id="b1a69-102">Erreur : aucune classe pour le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="b1a69-102">Error - No Class for Scripting Functoid</span></span>
<span data-ttu-id="b1a69-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="b1a69-103">**Error Code**</span></span>  
  
 <span data-ttu-id="b1a69-104">btm1008</span><span class="sxs-lookup"><span data-stu-id="b1a69-104">btm1008</span></span>  
  
 <span data-ttu-id="b1a69-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="b1a69-105">**Explanation**</span></span>  
  
 <span data-ttu-id="b1a69-106">Le **classe du Script** propriété du fonctoid **script** fonctoid n’a pas été défini même si le **le Type de Script** propriété indique qu’un assembly externe contient le script pour cette **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="b1a69-106">The **Script Class** property of the indicated **Scripting** functoid has not been set even though the **Script Type** property indicates that an external assembly contains the script for this **Scripting** functoid.</span></span>  
  
 <span data-ttu-id="b1a69-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="b1a69-107">**User Action**</span></span>  
  
 <span data-ttu-id="b1a69-108">Sélectionnez le **script** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **Script** propriété dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis définissez les valeurs appropriées dans le **configurer le Script du fonctoid** boîte de dialogue y compris le **classe du Script** propriété.</span><span class="sxs-lookup"><span data-stu-id="b1a69-108">Select the indicated **Scripting** functoid, click the ellipsis (**...**) button associated with the **Script** property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then set the appropriate values in the **Configure Functoid Script** dialog box, including the **Script Class** property.</span></span>