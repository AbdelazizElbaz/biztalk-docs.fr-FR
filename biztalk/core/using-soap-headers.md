---
title: "Utilisation des en-têtes SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers
- SOAP headers, about SOAP headers
- Web services, SOAP headers
ms.assetid: 816618ff-ecd8-4f12-b9a9-dbe4203411d8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0671dabe7547d3f55b937a1de58241a35cb70b39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers"></a><span data-ttu-id="a7f20-102">Utilisation des en-têtes SOAP</span><span class="sxs-lookup"><span data-stu-id="a7f20-102">Using SOAP Headers</span></span>
<span data-ttu-id="a7f20-103">Microsoft BizTalk Server prend en charge les en-têtes SOAP définis et inconnus.</span><span class="sxs-lookup"><span data-stu-id="a7f20-103">Microsoft BizTalk Server provides support for defined and unknown SOAP headers.</span></span> <span data-ttu-id="a7f20-104">Les en-têtes SOAP définis sont des en-têtes du fichier WSDL (Web Service Description Language) qui sont explicitement indiqués dans le service Web.</span><span class="sxs-lookup"><span data-stu-id="a7f20-104">Defined SOAP headers are headers in the Web Service Description Language (WSDL) that are explicity stated in the Web service.</span></span> <span data-ttu-id="a7f20-105">Les en-têtes SOAP inconnus sont des en-têtes du fichier WSDL qui ne sont pas explicitement indiqués dans le service Web.</span><span class="sxs-lookup"><span data-stu-id="a7f20-105">Unknown SOAP headers are headers that in the WSDL that are not explicity stated in the Web service.</span></span> <span data-ttu-id="a7f20-106">Pour plus d’informations sur l’utilisation des en-têtes SOAP, consultez « Using SOAP Headers » dans la documentation de Microsoft .NET Framework à [http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363).</span><span class="sxs-lookup"><span data-stu-id="a7f20-106">For more information about using SOAP headers, see "Using SOAP Headers" in the Microsoft .NET Framework documentation at [http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363).</span></span>  
  
 <span data-ttu-id="a7f20-107">BizTalk Server crée une propriété de contexte pour chaque en-tête SOAP défini dans le service Web.</span><span class="sxs-lookup"><span data-stu-id="a7f20-107">BizTalk Server creates a context property for each defined SOAP header in the Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7f20-108">Les services Web utilisés prennent uniquement en charge les en-têtes SOAP définis. Vous ne pouvez pas définir d'en-têtes inconnus lors de l'utilisation de services Web.</span><span class="sxs-lookup"><span data-stu-id="a7f20-108">Consumed Web services support only defined SOAP headers.You cannot set unknown headers when consuming Web services.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7f20-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a7f20-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a7f20-110">En-têtes SOAP avec les Services Web utilisés</span><span class="sxs-lookup"><span data-stu-id="a7f20-110">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)  
  
-   [<span data-ttu-id="a7f20-111">En-têtes SOAP avec les Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="a7f20-111">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)