---
title: "Avertissement : XSLT personnalisé, mais aucun XML avec extensions personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.warning.customXsltButNoCustomExtensionXML
ms.assetid: af008ac2-e9ae-4753-a5ba-bf4dbb711a4e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b67591e0e0dbb6b3ecac9aee1566c3245c9969a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-xslt-but-no-custom-extension-xml"></a><span data-ttu-id="c5517-102">Avertissement : XSLT personnalisé, mais aucun XML avec extensions personnalisées</span><span class="sxs-lookup"><span data-stu-id="c5517-102">Warning - Custom XSLT but No Custom Extension XML</span></span>
<span data-ttu-id="c5517-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="c5517-103">**Error Code**</span></span>  
  
 <span data-ttu-id="c5517-104">btm1034</span><span class="sxs-lookup"><span data-stu-id="c5517-104">btm1034</span></span>  
  
 <span data-ttu-id="c5517-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="c5517-105">**Explanation**</span></span>  
  
 <span data-ttu-id="c5517-106">Le **chemin du XSLT personnalisé** propriété a été remplacée, mais pas les **XML avec extensions personnalisées** propriété substituée.</span><span class="sxs-lookup"><span data-stu-id="c5517-106">The **Custom XSLT Path** property has been overridden without the **Custom Extension XML** property being overridden.</span></span> <span data-ttu-id="c5517-107">Si cela est intentionnel, ne tenez pas compte de cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="c5517-107">If this is intentional, you can ignore this warning.</span></span>  
  
 <span data-ttu-id="c5517-108">Mappeur BizTalk va utiliser l’élément XSLT défini par le **chemin du XSLT personnalisé** propriété et générer un fichier de mappage XML avec extensions factice.</span><span class="sxs-lookup"><span data-stu-id="c5517-108">BizTalk Mapper will use the XSLT specified by the **Custom XSLT Path** property and generate a dummy Extension XML mapping file.</span></span> <span data-ttu-id="c5517-109">Si vous appelez des assemblys externes depuis l’élément XSLT personnalisé fourni, vous devez spécifier un fichier en utilisant le **XML avec extensions personnalisées** propriété qui contient le préfixe de mappage de nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="c5517-109">If you make calls to external assemblies from within the provided custom XSLT, you must specify a file using the **Custom Extension XML** property that contains the prefix to assembly name mapping.</span></span>  
  
 <span data-ttu-id="c5517-110">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="c5517-110">**User Action**</span></span>  
  
 <span data-ttu-id="c5517-111">Si la condition indiquée par cet avertissement n’est pas intentionnelle, vous devez attribuer une valeur compatible à la **XML avec extensions personnalisées** propriété ou supprimez la valeur de remplacement pour le **chemin du XSLT personnalisé** propriété.</span><span class="sxs-lookup"><span data-stu-id="c5517-111">If the condition indicated by this warning was not intentional, either provide a compatible value for the **Custom Extension XML** property or remove the override value for the **Custom XSLT Path** property.</span></span>