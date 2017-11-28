---
title: XML pour une Session SalesOrder | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SalesOrder sessions
- examples, SalesOrder session
ms.assetid: dddf2424-b9d6-48a9-b7db-df524fafccd0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b0a2b0fd5570a2daee83f07463d4cd67385427
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-for-a-salesorder-session"></a><span data-ttu-id="56171-102">XML pour une session SalesOrder</span><span class="sxs-lookup"><span data-stu-id="56171-102">XML for a SalesOrder Session</span></span>
<span data-ttu-id="56171-103">Les sections suivantes proposent des exemples de code XML pour une session SalesOrder.</span><span class="sxs-lookup"><span data-stu-id="56171-103">The following sections provide samples of XML for a SalesOrder session.</span></span>  
  
## <a name="begindoc-xml-sample"></a><span data-ttu-id="56171-104">Exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="56171-104">BeginDoc XML Sample</span></span>  
  
```  
<ns0:F4211FSBeginDoc xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNumber />  
<ns0:cCMDocAction>A</ns0:cCMDocAction>   
<ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
<ns0:cCMUpdateWriteToWF>2</ns0:cCMUpdateWriteToWF>   
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
<ns0:szOrderType>SO</ns0:szOrderType>   
<ns0:szBusinessUnit>M30</ns0:szBusinessUnit>  
<ns0:szOriginalOrderCo />   
  
<ns0:szOriginalOrderNo />   
<ns0:szOriginalOrderType />   
<ns0:mnAddressNumber>1001</ns0:mnAddressNumber>   
<ns0:jdOrderDate />   
<ns0:szReference />   
<ns0:cApplyFreightYN>Y</ns0:cApplyFreightYN>  
<ns0:szCurrencyCode />   
<ns0:cWKSourceOfData />   
<ns0:cWKProcMode />   
<ns0:mnWKSuppressProcess>0</ns0:mnWKSuppressProcess>  
<ns0:cRetrieveOrderNo>1</ns0:cRetrieveOrderNo>   
<ns0:nSourceOfOrder>0</ns0:nSourceOfOrder>   
  
</ns0:F4211FSBeginDoc>  
  
```  
  
## <a name="editline-xml-sample"></a><span data-ttu-id="56171-105">Exemple XML EditLine</span><span class="sxs-lookup"><span data-stu-id="56171-105">EditLine XML Sample</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
  
<ns0:F4211FSEditLine xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNo>7</ns0:mnCMJobNo>   
<ns0:cCMLineAction>A</ns0:cCMLineAction>   
<ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
<ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>   
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
<ns0:szItemNo>210</ns0:szItemNo>   
<ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>   
<ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
<ns0:szTransactionUOM>EA</ns0:szTransactionUOM>   
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
<ns0:mnProcessID>4092</ns0:mnProcessID>   
<ns0:mnTransactionID>8</ns0:mnTransactionID>  
  
</ns0:F4211FSEditLine>  
  
```  
  
## <a name="enddoc-xml-sample"></a><span data-ttu-id="56171-106">Exemple XML EndDoc</span><span class="sxs-lookup"><span data-stu-id="56171-106">EndDoc XML Sample</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
  
<ns0:F4211FSEndDoc xmlns:ns0=  
"http://schemas.microsoft.com/[JDE://CSALES/B4200310]">   
<ns0:mnCMJobNo>7</ns0:mnCMJobNo>   
<ns0:szCMComputerID>BVISION02</ns0:szCMComputerID>   
  
<ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>   
  
<ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>   
  
<ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
  
<ns0:mnProcessID>4092</ns0:mnProcessID>   
  
<ns0:mnTransactionID>8</ns0:mnTransactionID>  
</ns0:F4211FSEndDoc>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="56171-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56171-107">See Also</span></span>  
 [<span data-ttu-id="56171-108">Annexe a : exemples de fichiers</span><span class="sxs-lookup"><span data-stu-id="56171-108">Appendix A: Sample Files</span></span>](../core/appendix-a-sample-files.md)