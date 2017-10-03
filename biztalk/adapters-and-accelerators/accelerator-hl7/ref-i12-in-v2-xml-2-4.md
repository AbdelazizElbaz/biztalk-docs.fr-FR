---
title: REF_I12 dans V2. XML 2.4 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: REF_I12 schema
ms.assetid: 95f40b75-a176-4fc6-b9ad-65721d456ea4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a230611424efb527eec6f75f6fb7623561760e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="refi12-in-v2xml-24"></a><span data-ttu-id="77e2d-102">REF_I12 dans V2. XML 2.4</span><span class="sxs-lookup"><span data-stu-id="77e2d-102">REF_I12 in V2.XML 2.4</span></span>
<span data-ttu-id="77e2d-103">Vous devez modifier manuellement le code suivant dans le schéma REF_I12 V2. 2.4 XML après l’exécution de l’outil Update2XMLSchema :</span><span class="sxs-lookup"><span data-stu-id="77e2d-103">You must manually change the following code in the REF_I12 schema in V2.XML 2.4 after running the Update2XMLSchema tool:</span></span>  
  
```  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
```  
  
 <span data-ttu-id="77e2d-104">Vous devez remplacer le code ci-dessus par le code suivant, afin de résoudre l’ambiguïté due à plusieurs occurrences de la **REF** définition de l’élément :</span><span class="sxs-lookup"><span data-stu-id="77e2d-104">You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **REF** element definition:</span></span>  
  
```  
<xsd:element minOccurs="0" maxOccurs="2" ref="REF_I12.PATIENT_VISIT" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="77e2d-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77e2d-105">See Also</span></span>  
 <span data-ttu-id="77e2d-106">[Mises à jour manuelles requises](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span><span class="sxs-lookup"><span data-stu-id="77e2d-106">[Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span></span>  
 [<span data-ttu-id="77e2d-107">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="77e2d-107">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)