---
title: "En-têtes SOAP avec les Services WCF publiés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, SOAP headers [WCF services]
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: 5564a57e-e241-4595-a959-4289c8502410
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78f36e778930a781ac797e18308240ecb4bef667
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="soap-headers-with-published-wcf-services"></a>En-têtes SOAP avec les services WCF publiés
Adaptateurs de réception WCF peuvent copier toutes les valeurs d’en-tête SOAP dans les messages entrants vers le **InboundHeaders** propriété, ou ils peuvent écrire ou promouvoir les valeurs spécifiées dans le contexte de message BizTalk. Les adaptateurs peuvent utiliser les en-têtes SOAP personnalisés et les en-têtes SOAP standard utilisés par l'infrastructure WCF, tels que WS-Addressing, WS-Security et WS-AtomicTransaction. Le **InboundHeaders** propriété de contexte est dans l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**et contient les représentations sous forme de chaîne de SOAP valeurs d’en-tête dans les messages entrants.  
  
> [!NOTE]
>  Si vous souhaitez promouvoir les valeurs d'en-tête SOAP que vous avez spécifiées, un schéma de propriété correspondant à ces valeurs doit être déployé dans votre projet BizTalk.  
  
> [!NOTE]
>  Ces propriétés promues peuvent inclure jusqu'à 256 caractères.  
  
 Les données XML suivantes montrent un exemple de la représentation sous forme de chaîne des en-têtes SOAP pour le **InboundHeaders** propriété. Transmises par le client, elles sont envoyées à l'emplacement de réception BizTalk.  
  
```  
<headers>  
<a:Action s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">Operation_1</a:Action>  
<SalesAgent xmlns="Microsoft.Samples.BizTalk.WCF.CustomSoapHeaderPipeline">Contoso</SalesAgent>  
<a:MessageID xmlns:a="http://www.w3.org/2005/08/addressing">urn:uuid:26e6720f-5a82-4ef2-b597-6ef077bab92e</a:MessageID>  
<a:ReplyTo xmlns:a="http://www.w3.org/2005/08/addressing"><a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address></a:ReplyTo>  
<a:To s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">net.tcp://localhost:9990/NetTcpOrderProcess</a:To>  
</headers>  
```  
  
 Pour écrire ou promouvoir des valeurs d'en-tête SOAP dans le contexte du message BizTalk, vous devez placer un ensemble de paires de valeurs constituées d'un nom de propriété et d'un espace de noms dans le message WCF afin que les adaptateurs WCF reconnaissent que les valeurs d'en-tête doivent être écrites ou promues. Un adaptateur WCF attend les propriétés suivantes dans les messages WCF pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk :  
  
-   Pour promouvoir les valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** et la valeur **liste\< KeyValuePair\<XmlQualifiedName, objet\>\>**.  
  
     À l’aide de cette paire, les adaptateurs extraient l’espace de noms, le nom et la valeur de la **XmlQualifiedName** de l’objet et les utilisent pour promouvoir les valeurs d’en-tête.  
  
-   Pour écrire, mais pas la promotion des valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** et la valeur  **Liste\<KeyValuePair\<XmlQualifiedName, objet\>\>**.  
  
     À l'aide de cette paire, les adaptateurs WCF écrivent les valeurs dans le contexte du message.  
  
 Le code suivant illustre la méthode utilisée pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk :  
  
```  
const string PropertiesToPromoteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote";  
const string PropertiesToWriteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext";  
  
XmlQualifiedName PropName1=new XmlQualifiedName("Destination", "http://tempuri.org/2007/sample-properties");  
XmlQualifiedName PropName2=new XmlQualifiedName("Source", "http://tempuri.org/2007/sample-properties");  
  
//Create a List of KeyValuePairs that indicate properties to be promoted to BizTalk message context.   
//A Property Schema must be deployed and string values have a limit of 256 characters  
List<KeyValuePair<XmlQualifiedName, object>> promoteProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
promoteProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName1, "Property value"));  
wcfMessage.Properties[PropertiesToPromoteKey]=promoteProps;  
  
//Create a List of KeyValuePairs that indicate properties to be written to BizTalk message context  
List<KeyValuePair<XmlQualifiedName, object>> writeProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
writeProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName2, "Property value"));  
wcfMessage.Properties[PropertiesToWriteKey]=writeProps;  
```  
  
 L'Assistant Publication de services WCF BizTalk n'inclut pas de définitions d'en-tête SOAP personnalisées dans les métadonnées générées. Pour publier des métadonnées pour les services WCF à l'aide d'en-têtes SOAP personnalisés, vous devez créer manuellement un fichier WSDL (Web Services Description Language). Vous pouvez utiliser la **externalMetadataLocation** attribut de la [ \<serviceMetadata\> ](http://go.microsoft.com/fwlink/?LinkId=89121) élément dans le fichier Web.config généré par l’Assistant pour spécifier l’emplacement de la Fichier WSDL. Ce dernier est renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX (Metadata Exchange), au lieu du fichier WSDL généré automatiquement.  
  
 Les données XML suivantes montrent un exemple de la partie du fichier WSDL qui définit les en-têtes SOAP personnalisés :  
  
```  
<wsdl:operation name="Request">  
  <soap12:operation soapAction="http://Microsoft.Samples.BizTalk.NetTcpAdapter/OrderProcess/IOrderProcess/Request" style="document" />   
   <wsdl:input name="Order">  
     <soap12:header message="i0:Order_Headers" part="SalesAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:input>  
   <wsdl:output name="OrderConfirmation">  
     <soap12:header message="i0:OrderConfirmation_Headers" part="PaymentAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:output>  
</wsdl:operation>  
```  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Accès aux en-têtes SOAP dans les messages WCF avec des orchestrations](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [Accès aux en-têtes SOAP dans les messages WCF avec des composants de pipeline](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En-têtes SOAP avec les services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md)