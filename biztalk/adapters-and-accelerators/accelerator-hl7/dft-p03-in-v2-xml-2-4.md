---
title: DFT_P03 dans V2. XML 2.4 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DFT_P03 schema
ms.assetid: 6735685a-2aac-4481-87d1-202b2178aeb5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7e35c52c38d5e9738b557118a3caf1d03344ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dftp03-in-v2xml-24"></a><span data-ttu-id="c4d35-102">DFT_P03 dans V2. XML 2.4</span><span class="sxs-lookup"><span data-stu-id="c4d35-102">DFT_P03 in V2.XML 2.4</span></span>
<span data-ttu-id="c4d35-103">Vous devez modifier manuellement le code suivant dans le schéma DFT_P03 V2. 2.4 XML après l’exécution de l’outil Update2XMLSchema :</span><span class="sxs-lookup"><span data-stu-id="c4d35-103">You must manually change the following code in the DFT_P03 schema in V2.XML 2.4 after running the Update2XMLSchema tool:</span></span>  
  
```  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
<xsd:element ref="PV1" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="PV2" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="ROL" minOccurs="0" maxOccurs="unbounded" />  
```  
  
 <span data-ttu-id="c4d35-104">Vous devez remplacer le code ci-dessus par le code suivant, afin de résoudre l’ambiguïté due à plusieurs occurrences de la **rôle** définition de l’élément :</span><span class="sxs-lookup"><span data-stu-id="c4d35-104">You must replace the above code with the following, in order to fix the ambiguity caused by multiple occurrences of the **ROL** element definition:</span></span>  
  
```  
<xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
  <xsd:choice minOccurs="0" maxOccurs="1">  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV1" />  
      <xsd:element minOccurs="0" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
    <xsd:sequence>  
      <xsd:element minOccurs="1" maxOccurs="1" ref="PV2" />  
      <xsd:element minOccurs="0" maxOccurs="unbounded" ref="ROL" />  
    </xsd:sequence>  
  </xsd:choice>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4d35-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4d35-105">See Also</span></span>  
 <span data-ttu-id="c4d35-106">[Mises à jour manuelles requises](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span><span class="sxs-lookup"><span data-stu-id="c4d35-106">[Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) </span></span>  
 [<span data-ttu-id="c4d35-107">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="c4d35-107">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)