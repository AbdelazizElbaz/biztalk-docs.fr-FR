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
# <a name="troubleshooting-resubmission-issues"></a>Résolution des problèmes de nouvelle soumission
Si vous rencontrez des problèmes de la soumettre à nouveau des messages, vérifiez les points suivants :  
  
-   Avez-vous accès à l’emplacement de réception via votre navigateur ? Si vous essayez de renvoyer le WCF rampe d’entrée ou le SOAP rampe d’entrée, l’URL doit être de la forme http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc ou http://localhost/ESB.OnRampServices/ProcessItinerary.asmx. Si vous essayez de renvoyer à un emplacement de réception HTTP, vous pouvez utiliser votre navigateur Internet pour déterminer si l’emplacement de réception fonctionne correctement en ajoutant un exemple de message à la chaîne de requête, comme illustré dans l’exemple suivant.  
  
    ```  
    http://localhost/HTTPOnRamp/BTSHttpReceive.dll?<SampleMessage>Sample Message Content</SampleMessage>  
    ```  
  
-   Vérifiez que la réception HTTP BizTalk adaptateur est configuré correctement.