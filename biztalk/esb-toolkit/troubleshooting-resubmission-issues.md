---
title: "Résolution des problèmes de nouvelle soumission | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b60ad45-d793-4de6-b9bc-3e8ef34f2b61
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1a143924b97117a708caea3006f74db6e029ca4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-resubmission-issues"></a><span data-ttu-id="6d3ae-102">Résolution des problèmes de nouvelle soumission</span><span class="sxs-lookup"><span data-stu-id="6d3ae-102">Troubleshooting Resubmission Issues</span></span>
<span data-ttu-id="6d3ae-103">Si vous rencontrez des problèmes de la soumettre à nouveau des messages, vérifiez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="6d3ae-103">If you have problems resubmitting messages, check the following:</span></span>  
  
-   <span data-ttu-id="6d3ae-104">Avez-vous accès à l’emplacement de réception via votre navigateur ?</span><span class="sxs-lookup"><span data-stu-id="6d3ae-104">Can you access the receive location through your browser?</span></span> <span data-ttu-id="6d3ae-105">Si vous essayez de renvoyer le WCF rampe d’entrée ou le SOAP rampe d’entrée, l’URL doit être de la forme http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc ou http://localhost/ESB.OnRampServices/ProcessItinerary.asmx.</span><span class="sxs-lookup"><span data-stu-id="6d3ae-105">If you are trying to resubmit to the WCF on-ramp or the SOAP on-ramp, the URL should be of the form http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc or http://localhost/ESB.OnRampServices/ProcessItinerary.asmx.</span></span> <span data-ttu-id="6d3ae-106">Si vous essayez de renvoyer à un emplacement de réception HTTP, vous pouvez utiliser votre navigateur Internet pour déterminer si l’emplacement de réception fonctionne correctement en ajoutant un exemple de message à la chaîne de requête, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6d3ae-106">If you are trying to resubmit to an HTTP receive location, you can use your Internet browser to determine whether the receive location is functioning properly by appending a sample message to the query string, as shown in the following example.</span></span>  
  
    ```  
    http://localhost/HTTPOnRamp/BTSHttpReceive.dll?<SampleMessage>Sample Message Content</SampleMessage>  
    ```  
  
-   <span data-ttu-id="6d3ae-107">Vérifiez que la réception HTTP BizTalk adaptateur est configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="6d3ae-107">Verify that the BizTalk HTTP receive adapter is properly configured.</span></span>