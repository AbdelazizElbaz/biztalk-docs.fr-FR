---
title: "Fonctionne de l’exemple de Service de programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33b5f886-ec54-4b2b-b09d-fb4c47ad43a5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af9f90bf80435b00a0d39e83d2b2293595f6f200
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-the-resolver-service-sample-works"></a>Fonctionne de l’exemple de Service de programme de résolution
L’exemple de Service de résolution instancie le service de résolution et transmet le message spécifié à ce dernier pour le traitement. L’exemple d’application cliente Service de résolution utilise le premier paramètre en tant que le chemin d’accès au fichier ResolverList.xml, qui contient plusieurs demandes de programme de résolution et envoie ces demandes au service de programme de résolution. Par exemple, voici la requête XPATH utilisée dans l’exemple.  
  
```  
  
//XPATH  
<Resolver>  
  <name>XPATHWithFILE</name>   
  <Content>![CDATA[XPATH:\\TransportLocation=/*[local-name()='OrderDoc'   
    and namespace-uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/']/*[local-name()='ID' and namespace-  
    uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/'];TargetNamespace=;  
    MessageExchangePattern=;EndpointConfig=;JaxRpcResponse=;TransportType=;  
    Action=;TransformType=]]  
  </Content>   
  <body>  
    ![CDATA[   
    <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
      <ns0:customerName>Microsoft</ns0:customerName>  
  
<ns0:ID>FILE://C:\Projects\Microsoft.Practices.ESB\Source\Samples  
    \DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml</ns0:ID>   
      <ns0:requestType>10</ns0:requestType>   
    </ns0:OrderDoc>  
    ]]   
  </body>  
</Resolver>  
```  
  
> [!NOTE]
>  Le contenu réel de la  **\<contenu\>**  élément ne contient pas les caractères d’espace blanc utilisés pour encapsuler les lignes dans la liste précédente.  
  
 La liste précédente montre que la demande contient la chaîne de connexion de configuration de programme de résolution au sein d’un  **\<contenu\>**  élément. Le  **\<corps\>**  élément contient le corps du message.  
  
 Le service de programme de résolution utilise le **ResolverMgr** classe à instancier une instance concrète du programme de résolution appropriée, définie par le type de programme de résolution dans la chaîne de connexion. Dans le cas de la requête XPATH, il s’agit de l’outil de résolution XPATH.  
  
 Ensuite, l’infrastructure crée une instance de la **ResolveProvider** classe nommée ESB. Resolver.XPath pour traiter la demande. L’application cliente écrit le message de réponse du service de résolution dans le dossier nommé \Source\Samples\ResolverService\Output. La liste suivante répertorie le contenu de la réponse.  
  
```  
  
//XPATH  
Resolver.Action =   
Resolver.ActionField =   
Resolver.DocumentSpecName =   
Resolver.DocumentSpecStrongName =   
Resolver.EndpointConfig =   
Resolver.EpmRRCorrelationToken =   
Resolver.FixJaxRpc = False  
Resolver.InboundTransportLocation =   
Resolver.InboundTransportType =   
Resolver.InterchangeId =   
Resolver.IsRequestResponse =   
Resolver.MessageExchangePattern =   
Resolver.MessageType =   
Resolver.MethodName =   
Resolver.OutboundTransportCLSID =   
Resolver.ReceiveLocationName =   
Resolver.ReceivePortName =   
Resolver.Success = False  
Resolver.TargetNamespace =   
Resolver.TransformType =   
Resolver.TransportLocation = FILE://C:\Projects\Microsoft.  
    Practices.ESB\Source\Samples  
\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml  
Resolver.TransportNamespace =   
Resolver.TransportType = FILE  
Resolver.WindowUserField =  
```