---
title: 'Erreur : lien de sortie pour le fonctoid script XSLT non valide. | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.outputLinkForXsltNotValid
ms.assetid: cdf8e779-6cf6-4d9c-8655-f8b406498fb7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd597a3953db76087086c7ea9038e9fa1fd87eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---output-link-for-xslt-scripting-functoid-not-valid"></a><span data-ttu-id="d498b-102">Erreur : lien de sortie pour le fonctoid script XSLT non valide</span><span class="sxs-lookup"><span data-stu-id="d498b-102">Error - Output Link For XSLT Scripting Functoid Not Valid</span></span>
<span data-ttu-id="d498b-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="d498b-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d498b-104">btm1075</span><span class="sxs-lookup"><span data-stu-id="d498b-104">btm1075</span></span>  
  
 <span data-ttu-id="d498b-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="d498b-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d498b-106">Le lien de sortie de la **script** configuré pour utiliser un modèle d’appel XSLT ou XSLT inline ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="d498b-106">The output link of the relevant **Scripting** functoid configured to use inline XSLT or an XSLT Call Template is not valid.</span></span> <span data-ttu-id="d498b-107">La sortie de ces **script** fonctoids doivent être connectés directement à un nœud dans le schéma de destination (et non à un autre fonctoid, par exemple).</span><span class="sxs-lookup"><span data-stu-id="d498b-107">The output of such **Scripting** functoids must be connected directly to a node in the destination schema (and not to another functoid, for example).</span></span>  
  
 <span data-ttu-id="d498b-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="d498b-108">**User Action**</span></span>  
  
 <span data-ttu-id="d498b-109">Vérifiez que vous vous connectez le lien de sortie à partir de la **script** fonctoid directement à un nœud dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="d498b-109">Ensure that you connect the output link from the relevant **Scripting** functoid directly to a node in the destination schema.</span></span>