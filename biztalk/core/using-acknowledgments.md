---
title: "À l’aide des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, publishing
- messages, acknowledgements
- BTS.AckSendPortID property
- BTS.AckSendPortName property
- BTS.AckType property
- BTS.AckFailureCode property
- BTS.AckID property
- acknowledgements, positive
- SOAP fault
- BTS.AckReceivePortID property
- BTS.AckReceivePortName property
- BTS.AckInboundTransportLocation property
- BTS.AckOutboundTransportLocation property
- messages, successful transmission
- BTS.AckDescription property
- orchestrations, messages
- acknowledgements, negative
- BTS.CorrelationToken property
- BTS.AckFailureCategory property
- positive acknowledgements (ACK)
- BTS.AckOwnerID property
ms.assetid: 2e5986d4-9633-4b7b-8ff3-fa3da93c5400
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c3a5363ee70a67c5882088af9fa3d2f4b805823
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-acknowledgments"></a>Utilisation des accusés de réception
Le moteur de messagerie BizTalk génère des accusés de réception positifs (ACK) et négatifs (NACK) en réponse aux conditions rencontrées pendant le traitement d'un message via un port. BizTalk Server émet un accusé de réception positif pour indiquer qu’un message a été correctement transmis et un accusé de réception négatif pour indiquer que la transmission a échoué et que le message est suspendu.  
  
## <a name="why-use-acknowledgments"></a>Pourquoi utiliser des accusés de réception ?  
 Les accusés de réception positifs et négatifs constituent un important retour d’informations vous permettant de déterminer si un message est arrivé à destination ou s'il a rencontré des problèmes au cours de la transmission. Par exemple, les accusés de réception sont utiles lorsque :  
  
-   vous souhaitez surveiller un port de réception associé à un nouveau partenaire commercial pour une validation de schéma ou la recherche d'erreurs ;  
  
-   vous voulez marquer l'état d’une demande de prêt envoyée pour approbation comme étant « en cours de traitement » si l'envoi à un partenaire pour approbation a abouti ou comme « échec » si la transmission a échoué (par exemple, si le serveur du partenaire est arrêté) ;  
  
-   vous traitez les échanges contenant plusieurs bons de commande et voulez suivre le nombre de commandes ayant été transmises ou dont la transmission a échoué.  
  
 Pour réaliser chacun de ces scénarios, vous pouvez vous servir des accusés de réception et du routage basé sur le contenu utilisant des filtres.  
  
## <a name="routing-acknowledgments"></a>Acheminement des accusés de réception  
 Lorsqu'un ACK ou un NACK est publié, toutes les propriétés de contexte de message provenant du message ayant provoqué l'accusé ACK/NACK sont rétrogradées. Aucune propriété promue n'est transmise à l'accusé de réception. Pour acheminer un accusé de réception, créer un filtre utilisant les propriétés suivantes à partir de la **BTS** espace de noms :  
  
|Nom de la propriété|Type de données| Description|  
|-------------------|---------------|-----------------|  
|BTS.AckFailureCategory|xs:int|Identifie la **ErrorCategory**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.AckFailureCode|xs:string|Identifie la **ErrorCode**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.AckType|xs:string|La valeur est ACK pour un accusé de réception positif et NACK pour un accusé de réception négatif.|  
|BTS.AckID|xs:string|Identifie la **MessageID** du message d’origine.|  
|BTS.AckOwnerID|xs:string|Identifie l'ID d'instance du message d'origine.|  
|BTS.CorrelationToken|xs:string|Identifie le jeton de corrélation du message d'origine s’il en existe un.|  
|BTS.AckDescription|xs:string|Identifie la **ErrorDescription**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.AckSendPortID|xs:string|Identifie la **SendPortID** à partir du message d’origine.|  
|BTS.AckSendPortName|xs:string|Identifie la **SendPortName** à partir du message d’origine.|  
|BTS.AckOutboundTransportLocation|xs:string|Identifie la **OutboundTransportLocation** à partir du message d’origine.|  
|BTS.AckReceivePortID|xs:string|Identifie la **ReceivePortID** à partir du message d’origine.|  
|BTS.AckReceivePortName|xs:string|Identifie la **ReceivePortName** du message d’origine.|  
|BTS.AckInboundTransportLocation|xs:string|Identifie la **InboundTransportLocation** du message d’origine.|  
  
> [!NOTE]
>  Les propriétés contenant des informations sur l'erreur ne figurent pas dans les accusés ACK, car ces derniers signalent une remise positive.  
  
## <a name="negative-acknowledgment-message-body"></a>Corps de message d'accusé de réception négatif  
 Une grande partie des informations importantes concernant l’accusé de réception positif ou négatif figurent dans les propriétés de contexte. Outre les propriétés de contexte, les accusés NACK contiennent également un corps de message comportant une erreur SOAP. Le format de l’erreur SOAP est le suivant :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
  <SOAP:Body>  
    <SOAP:Fault>  
      <faultcode>Microsoft BizTalk Server Negative Acknowledgment </faultcode>  
      <faultstring>An error occurred while processing the message, refer to the details section for more information </faultstring>  
      <faultactor>C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml</faultactor>  
      <detail>  
        <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
          <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
          <ErrorCode>0xc0c01658</ErrorCode>  
          <ErrorCategory>0</ErrorCategory>  
          <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".  </ErrorDescription>  
        </ns0:NACK>  
      </detail>  
    </SOAP:Fault>  
  </SOAP:Body>  
</SOAP:Envelope>  
```  
  
 Le message d'exception déclenché par l’adaptateur se trouve dans la section relative aux détails SOAP de l'élément ErrorDescription.  
  
### <a name="accessing-the-message-body-from-an-orchestration"></a>Accès au corps de message à partir d’une orchestration  
 Si un port d'orchestration nécessite un accusé de réception, l'exception DeliveryFailureException émise en cas d'échec de transmission est désérialisée de l'erreur SOAP contenue dans le corps du message NACK. Pour accéder à la chaîne du message d'exception depuis votre orchestration, convertissez l'exception DeliveryFailureException en une exception SoapException, puis accédez à InnerXml comme indiqué dans le code suivant :  
  
```  
// Cast the DeliveryFailureException to a SoapException…  
System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
//e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
//object type created in an Exception handler  
```  
  
 L'échantillon de code précédent renvoie un fragment XML semblable à ce qui suit :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
  <ErrorCode>0xc0c01658</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".</ErrorDescription>  
</ns0:NACK>  
```  
  
## <a name="when-is-an-acknowledgment-published"></a>À quel moment un accusé de réception est-il publié ?  
 Les accusés de réception positifs (ACK) et négatifs (NACK) sont publiés dans la base de données MessageBox au moment de l'échec, à condition qu'il existe au moins un abonnement correspondant. Par exemple, si BizTalk Server ne peut pas trouver de schéma correspondant pour un message lu depuis un port de réception, et qu'il n'existe aucun abonnement NACK, le message est suspendu (si le routage des messages ayant échoué n’a pas été activé) et aucun NACK n’est publié.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs](../core/error-handling.md)   
 [À l’aide de routage des messages ayant échoué](../core/using-failed-message-routing.md)