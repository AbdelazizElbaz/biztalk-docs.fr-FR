---
title: 'Avertissement : XML avec extensions personnalisées, mais aucun XSLT personnalisé | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.customExtensionXmlButNoCustomXSLT
ms.assetid: 3219c73c-2e58-4fe2-bc6e-2d60348d2415
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b626f8ede3231c04ae74dc0097cbdf524c90522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-extension-xml-but-no-custom-xslt"></a><span data-ttu-id="4b341-102">Avertissement : XML avec extensions personnalisées, mais aucun XSLT personnalisé</span><span class="sxs-lookup"><span data-stu-id="4b341-102">Warning - Custom Extension XML But No Custom XSLT</span></span>
<span data-ttu-id="4b341-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="4b341-103">**Error Code**</span></span>  
  
 <span data-ttu-id="4b341-104">btm1033</span><span class="sxs-lookup"><span data-stu-id="4b341-104">btm1033</span></span>  
  
 <span data-ttu-id="4b341-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="4b341-105">**Explanation**</span></span>  
  
 <span data-ttu-id="4b341-106">Le **XML avec extensions personnalisées** propriété a été remplacée, mais pas les **chemin du XSLT personnalisé** propriété substituée.</span><span class="sxs-lookup"><span data-stu-id="4b341-106">The **Custom Extension XML** property has been overridden without the **Custom XSLT Path** property being overridden.</span></span> <span data-ttu-id="4b341-107">Si cela est intentionnel, ne tenez pas compte de cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="4b341-107">If this is intentional, you can ignore this warning.</span></span>  
  
 <span data-ttu-id="4b341-108">Le Mappeur BizTalk va utiliser l'élément XSLT produit lors de la compilation du mappage, puis va générer l'élément XML avec extensions qui sera ensuite ajouté à l'élément XML avec extensions personnalisées remplacé.</span><span class="sxs-lookup"><span data-stu-id="4b341-108">BizTalk Mapper will use the XSLT produced by compiling the map and will also generate the Extension XML and append it to the custom Extension XML specified by the overridden property.</span></span> <span data-ttu-id="4b341-109">Cela peut être utile lorsque le mappage contient **script** modèles qui effectuent des appels à une ou plusieurs méthodes dans les assemblys externes d’appel de fonctoids qui utilisent inline XSLT ou XSLT inline.</span><span class="sxs-lookup"><span data-stu-id="4b341-109">This can be useful when the map contains **Scripting** functoids that use inline XSLT or inline XSLT call templates that make calls to one or more methods in external assemblies.</span></span> <span data-ttu-id="4b341-110">Dans ce cas, l’utilisateur peut alors affecter le préfixe au mappage de nom d’assembly dans le **XML avec extensions personnalisées** propriété.</span><span class="sxs-lookup"><span data-stu-id="4b341-110">In such cases, the user can then specify the prefix to assembly name mapping in the **Custom Extension XML** property.</span></span>  
  
 <span data-ttu-id="4b341-111">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="4b341-111">**User Action**</span></span>  
  
 <span data-ttu-id="4b341-112">Si la condition indiquée par cet avertissement n’est pas intentionnelle, vous devez attribuer une valeur compatible à la **chemin du XSLT personnalisé** propriété ou supprimez la valeur de remplacement pour le **XML avec extensions personnalisées** propriété.</span><span class="sxs-lookup"><span data-stu-id="4b341-112">If the condition indicated by this warning was not intentional, either provide a compatible value for the **Custom XSLT Path** property or remove the override value for the **Custom Extension XML** property.</span></span>