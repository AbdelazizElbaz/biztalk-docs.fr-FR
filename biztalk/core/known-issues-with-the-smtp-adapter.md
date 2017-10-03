---
title: "Problèmes connus avec l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b530e39e-c4e7-4b98-be0b-4d02eb2e8dc7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8691da466c2915cee4b8746e20a0d5a96d82d81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-smtp-adapter"></a>Problèmes connus avec l'adaptateur SMTP
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="error-in-the-biztalk-server-application-log-if-emailbodytextcharset-is-not-defined"></a>Erreur dans le journal de l'application BizTalk Server si EmailBodyTextCharset n'est pas défini.  
  
##### <a name="problem"></a>Problème  
 Des erreurs, similaires à celle indiquée ci-après, sont générées dans le journal de l'application BizTalk Server si EmailBodyTextCharset n'est pas défini :  
  
```  
Event Type:Error  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:5754  
Date:9/1/2006  
Time:10:50:11 AM  
User:N/A  
Computer:TEST2006  
Description:  
A message sent to adapter "SMTP" on send port "TIE Test_1.0.0.0_TIE_Test.TieRespTest_Email_Port_4f4f8f4101d5615a" with URI "mailto:approver@BTS2006.com" is suspended.   
Error details: Unknown Error Description   
MessageId: {3F12EBE1-1CDA-44FE-85FE-C2CB8228F287}  
InstanceID: {0616E750-22FF-4380-B413-C94718421340}  
```  
  
##### <a name="cause"></a>Cause  
 Une valeur doit être définie pour le **EmailBodyTextCharset** paramètre.  
  
##### <a name="resolution"></a>Résolution  
 Spécifiez une valeur pour le **EmailBodyTextCharset** paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’adaptateur SMTP](../core/troubleshooting-the-smtp-adapter.md)