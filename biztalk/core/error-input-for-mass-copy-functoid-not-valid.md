---
title: 'Erreur : entrée de fonctoid copie de masse n’est pas valide. | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.massCopyInputNotValid
ms.assetid: 141c45cd-79da-4f99-abb0-60a88dfcab76
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 903954fabb99520ce5b4a8e20c0296165944053a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---input-for-mass-copy-functoid-not-valid"></a><span data-ttu-id="bc486-102">Erreur : entrée de fonctoid copie de masse non valide</span><span class="sxs-lookup"><span data-stu-id="bc486-102">Error - Input for Mass Copy Functoid Not Valid</span></span>
<span data-ttu-id="bc486-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="bc486-103">**Error Code**</span></span>  
  
 <span data-ttu-id="bc486-104">btm1069</span><span class="sxs-lookup"><span data-stu-id="bc486-104">btm1069</span></span>  
  
 <span data-ttu-id="bc486-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="bc486-105">**Explanation**</span></span>  
  
 <span data-ttu-id="bc486-106">Le paramètre d’entrée pour le **copie de masse** fonctoid n’est pas valide ou trop de paramètres d’entrée pour le **copie de masse** ont été spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bc486-106">The input parameter for the relevant **Mass Copy** functoid is not valid or too many input parameters for the relevant **Mass Copy** functoid have been specified.</span></span> <span data-ttu-id="bc486-107">**Copie de masse** fonctoids doivent avoir une seule entrée : une liaison entre un **enregistrement** nœud dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="bc486-107">**Mass Copy** functoids must have exactly one input: a link from a **Record** node in the source schema.</span></span>  
  
 <span data-ttu-id="bc486-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="bc486-108">**User Action**</span></span>  
  
 <span data-ttu-id="bc486-109">Redéfinissez le **copie de masse** fonctoid telles qu’il possède un seul paramètre d’entrée une **enregistrement** nœud dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="bc486-109">Reconfigure the relevant **Mass Copy** functoid such that it has a single input parameter from a **Record** node in the source schema.</span></span>