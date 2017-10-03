---
title: "Publication de Services Web avec des en-têtes SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, pipelines
- SOAP headers, BizTalk Web Services Publishing Wizard
- pipelines, SOAP headers
- orchestrations, SOAP headers
ms.assetid: c362caff-b75f-4c1b-9013-d2b9c74f5c65
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7baf6af0e4505e448a854fe6def372614bfdaa49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-web-services-with-soap-headers"></a>Publication de Services Web avec des en-têtes SOAP
Vous ajoutez des en-têtes SOAP à vos services Web lors de l'exécution de l'Assistant Publication de services Web BizTalk. Lorsque vous publiez un service Web qui prend en charge les en-têtes SOAP, les en-têtes deviennent disponibles pour les orchestrations et les composants de pipeline en tant que propriétés de contexte qui contiennent des représentations sous forme de chaîne des en-têtes SOAP.  
  
## <a name="defined-soap-headers"></a>En-têtes SOAP définis  
 Lorsque vous ajoutez un en-tête SOAP défini à l'aide de l'Assistant, ce dernier crée une propriété de contexte dotée d'un nom qui correspond à l'élément racine de l'en-tête SOAP. Toutes les propriétés de contexte d’en-tête SOAP défini ont l’espace de noms **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**. Lorsque l'adaptateur SOAP convertit la demande SOAP en message BizTalk, il crée une propriété de contexte d'en-tête SOAP.  
  
 L'exemple suivant illustre une requête SOAP simple :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
       <soap:Header>  
             <OrigDest xmlns="http://SOAPHeaderWS.ItemAvailability">  
                    <Origination>Work</Origination>  
                    <Destination>Home</Destination>  
             </OrigDest>  
       </soap:Header>  
       <soap:Body>  
  
       </soap:Body>  
</soap:Envelope>  
```  
  
 Pour la requête SOAP simple, l’adaptateur SOAP a créé un message BizTalk avec une propriété de contexte d’en-tête SOAP **OrigDest** et la chaîne.  
  
 L'exemple suivant illustre la chaîne créée par l'adaptateur SOAP :  
  
```  
"<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader"><Origination xmlns="">Home</Origination><Destination xmlns="">Work</Destination> </OrigDest>"  
```  
  
## <a name="unknown-soap-headers"></a>En-têtes SOAP inconnus  
 Si vous choisissez de prendre en charge des en-têtes SOAP inconnus dans l’Assistant, l’Assistant crée une propriété de contexte portant le nom **UnknownHeaders** et l’espace de noms **http://schemas.microsoft.com/BizTalk/2003/soap-properties**. Le **UnknownHeaders** propriété de contexte contient tous les en-têtes SOAP inconnus reçus.  
  
 Par exemple, si vous recevez un en-tête SOAP inconnu avec le nom d’élément racine, **CustomerGroup**, le **UnknownHeaders** propriété de contexte contient la chaîne :  
  
```  
"<?xml version="1.0" encoding="utf-16"?><UnknownHeaders><CustomerGroup xmlns="http://SOAPHeaderWS/CustomerGroup"><Id xmlns="">My Customer</Id>  
</CustomerGroup></UnknownHeaders>"  
```  
  
 Pour plus d’informations sur l’ajout de défini en-têtes SOAP ou prenant en charge les en-têtes SOAP inconnus, consultez [publier une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md). Consultez également [publication de schémas comme un Service Web](../core/publishing-schemas-as-a-web-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes SOAP avec les Services Web publiés](../core/soap-headers-with-published-web-services.md)