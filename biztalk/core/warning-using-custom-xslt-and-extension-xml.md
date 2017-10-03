---
title: "Avertissement : utilisation de XML avec extensions et XSLT personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.warning.usingCustomXsltAndExtensionXML
ms.assetid: b86da5fb-6435-4e3b-89b6-d9d036b5152b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90644aec738345e3a36286cc62aaa7a355e04348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---using-custom-xslt-and-extension-xml"></a><span data-ttu-id="280a7-102">Avertissement : utilisation de XML avec extensions et XSLT personnalisés</span><span class="sxs-lookup"><span data-stu-id="280a7-102">Warning - Using Custom XSLT and Extension XML</span></span>
<span data-ttu-id="280a7-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="280a7-103">**Error Code**</span></span>  
  
 <span data-ttu-id="280a7-104">btm1035</span><span class="sxs-lookup"><span data-stu-id="280a7-104">btm1035</span></span>  
  
 <span data-ttu-id="280a7-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="280a7-105">**Explanation**</span></span>  
  
 <span data-ttu-id="280a7-106">Les valeurs de remplacement pour le **chemin du XSLT personnalisé** et **XML avec extensions personnalisées** contrôle les messages d’instance de sortie générés par ce mappage, en ignorant les mappages de propriétés spécifié entre les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="280a7-106">The presence of override values for the **Custom XSLT Path** and **Custom Extension XML** properties is controlling the output instance messages produced by this map, completely ignoring any mappings specified between the source and destination schemas.</span></span> <span data-ttu-id="280a7-107">Si cela est intentionnel, ne tenez pas compte de cet avertissement.</span><span class="sxs-lookup"><span data-stu-id="280a7-107">If this is intentional, you can ignore this warning.</span></span>  
  
 <span data-ttu-id="280a7-108">Un scénario dans lequel il est valide consiste à utiliser le Mappeur BizTalk pour générer un XSLT préliminaire pour le mappage, modifiez ce XSLT manuellement pour répondre aux exigences supplémentaires spécifiques, puis spécifiez le fichier modifié en tant que la valeur de la **cheminduXSLTpersonnalisé** propriété, remplaçant ainsi le XSLT préliminaire lors des opérations de mappage ultérieures.</span><span class="sxs-lookup"><span data-stu-id="280a7-108">One scenario in which this is valid is to use BizTalk Mapper to generate preliminary XSLT for the mapping, modify this XSLT by hand to meet specific additional requirements, and then specify the modified file as the value of the **Custom XSLT Path** property, thereby overriding the preliminary XSLT during subsequent mapping operations.</span></span>  
  
 <span data-ttu-id="280a7-109">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="280a7-109">**User Action**</span></span>  
  
 <span data-ttu-id="280a7-110">Si vous ne souhaitez pas remplacer le mappage spécifié dans ce mappage, supprimez les valeurs de remplacement pour le **chemin du XSLT personnalisé** propriété et la **XML avec extensions personnalisées** propriété, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="280a7-110">If you do not intend to override the mapping specified within this map, remove the override values for the **Custom XSLT Path** property and the **Custom Extension XML** property, as appropriate.</span></span>