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
# <a name="soap-headers-with-published-wcf-services"></a><span data-ttu-id="ff98e-102">En-têtes SOAP avec les services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="ff98e-102">SOAP Headers with Published WCF Services</span></span>
<span data-ttu-id="ff98e-103">Adaptateurs de réception WCF peuvent copier toutes les valeurs d’en-tête SOAP dans les messages entrants vers le **InboundHeaders** propriété, ou ils peuvent écrire ou promouvoir les valeurs spécifiées dans le contexte de message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ff98e-103">The WCF receive adapters can copy all the SOAP header values in the inbound messages to the **InboundHeaders** property, or they can write or promote specified values to the BizTalk message context.</span></span> <span data-ttu-id="ff98e-104">Les adaptateurs peuvent utiliser les en-têtes SOAP personnalisés et les en-têtes SOAP standard utilisés par l'infrastructure WCF, tels que WS-Addressing, WS-Security et WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="ff98e-104">The adapters can work with both custom SOAP headers and standard SOAP headers that the WCF infrastructure uses, such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="ff98e-105">Le **InboundHeaders** propriété de contexte est dans l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**et contient les représentations sous forme de chaîne de SOAP valeurs d’en-tête dans les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="ff98e-105">The **InboundHeaders** context property is in the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**, and contains string representations of the SOAP header values in inbound messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff98e-106">Si vous souhaitez promouvoir les valeurs d'en-tête SOAP que vous avez spécifiées, un schéma de propriété correspondant à ces valeurs doit être déployé dans votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ff98e-106">If you are going to promote the SOAP header values you specified, there must be a deployed property schema in your BizTalk project that corresponds to the values you are promoting.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff98e-107">Ces propriétés promues peuvent inclure jusqu'à 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="ff98e-107">The promoted properties cannot be longer than 256 characters.</span></span>  
  
 <span data-ttu-id="ff98e-108">Les données XML suivantes montrent un exemple de la représentation sous forme de chaîne des en-têtes SOAP pour le **InboundHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="ff98e-108">The following XML data shows an example of the string representation of the SOAP headers for the **InboundHeaders** property.</span></span> <span data-ttu-id="ff98e-109">Transmises par le client, elles sont envoyées à l'emplacement de réception BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ff98e-109">This comes from the client and is sent to the BizTalk receive location.</span></span>  
  
```  
<headers>  
<a:Action s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">Operation_1</a:Action>  
<SalesAgent xmlns="Microsoft.Samples.BizTalk.WCF.CustomSoapHeaderPipeline">Contoso</SalesAgent>  
<a:MessageID xmlns:a="http://www.w3.org/2005/08/addressing">urn:uuid:26e6720f-5a82-4ef2-b597-6ef077bab92e</a:MessageID>  
<a:ReplyTo xmlns:a="http://www.w3.org/2005/08/addressing"><a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address></a:ReplyTo>  
<a:To s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">net.tcp://localhost:9990/NetTcpOrderProcess</a:To>  
</headers>  
```  
  
 <span data-ttu-id="ff98e-110">Pour écrire ou promouvoir des valeurs d'en-tête SOAP dans le contexte du message BizTalk, vous devez placer un ensemble de paires de valeurs constituées d'un nom de propriété et d'un espace de noms dans le message WCF afin que les adaptateurs WCF reconnaissent que les valeurs d'en-tête doivent être écrites ou promues.</span><span class="sxs-lookup"><span data-stu-id="ff98e-110">To write or promote SOAP header values to the BizTalk message context, you need to put a collection of value pairs that consist of property name and namespace into the WCF message so that the WCF adapters will recognize that the header values are to be written or promoted.</span></span> <span data-ttu-id="ff98e-111">Un adaptateur WCF attend les propriétés suivantes dans les messages WCF pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk :</span><span class="sxs-lookup"><span data-stu-id="ff98e-111">A WCF adapter expects the following message properties in the WCF messages for writing or promoting SOAP header values to the BizTalk message context:</span></span>  
  
-   <span data-ttu-id="ff98e-112">Pour promouvoir les valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** et la valeur **liste\< KeyValuePair\<XmlQualifiedName, objet\>\>**.</span><span class="sxs-lookup"><span data-stu-id="ff98e-112">To promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.</span></span>  
  
     <span data-ttu-id="ff98e-113">À l’aide de cette paire, les adaptateurs extraient l’espace de noms, le nom et la valeur de la **XmlQualifiedName** de l’objet et les utilisent pour promouvoir les valeurs d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="ff98e-113">Using this pair, WCF adapters take the namespace, name, and value from the **XmlQualifiedName** object and use them for promoting the header values.</span></span>  
  
-   <span data-ttu-id="ff98e-114">Pour écrire, mais pas la promotion des valeurs d’en-tête SOAP dans le contexte de message BizTalk, les adaptateurs WCF recherchent la paire de clé **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** et la valeur  **Liste\<KeyValuePair\<XmlQualifiedName, objet\>\>**.</span><span class="sxs-lookup"><span data-stu-id="ff98e-114">To write but not promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.</span></span>  
  
     <span data-ttu-id="ff98e-115">À l'aide de cette paire, les adaptateurs WCF écrivent les valeurs dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="ff98e-115">Using this pair, WCF adapters write the values to the message context.</span></span>  
  
 <span data-ttu-id="ff98e-116">Le code suivant illustre la méthode utilisée pour écrire ou promouvoir les valeurs d'en-tête SOAP dans le contexte du message BizTalk :</span><span class="sxs-lookup"><span data-stu-id="ff98e-116">The following code shows how to write or promote the SOAP header values to the BizTalk message context:</span></span>  
  
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
  
 <span data-ttu-id="ff98e-117">L'Assistant Publication de services WCF BizTalk n'inclut pas de définitions d'en-tête SOAP personnalisées dans les métadonnées générées.</span><span class="sxs-lookup"><span data-stu-id="ff98e-117">The BizTalk WCF Service Publishing Wizard does not include custom SOAP header definitions in the generated metadata.</span></span> <span data-ttu-id="ff98e-118">Pour publier des métadonnées pour les services WCF à l'aide d'en-têtes SOAP personnalisés, vous devez créer manuellement un fichier WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="ff98e-118">To publish metadata for WCF services using custom SOAP headers, you should manually create a Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="ff98e-119">Vous pouvez utiliser la **externalMetadataLocation** attribut de la [ \<serviceMetadata\> ](http://go.microsoft.com/fwlink/?LinkId=89121) élément dans le fichier Web.config généré par l’Assistant pour spécifier l’emplacement de la Fichier WSDL.</span><span class="sxs-lookup"><span data-stu-id="ff98e-119">You can use the **externalMetadataLocation** attribute of the [\<serviceMetadata\>](http://go.microsoft.com/fwlink/?LinkId=89121) element in the Web.config file that the wizard generates to specify the location of the WSDL file.</span></span> <span data-ttu-id="ff98e-120">Ce dernier est renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX (Metadata Exchange), au lieu du fichier WSDL généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ff98e-120">The WSDL file is returned to the user in response to WSDL and metadata exchange (MEX) requests instead of the auto-generated WSDL.</span></span>  
  
 <span data-ttu-id="ff98e-121">Les données XML suivantes montrent un exemple de la partie du fichier WSDL qui définit les en-têtes SOAP personnalisés :</span><span class="sxs-lookup"><span data-stu-id="ff98e-121">The following XML data shows an example of a part of the WSDL file defining custom SOAP headers:</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="ff98e-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ff98e-122">In This Section</span></span>  
  
-   [<span data-ttu-id="ff98e-123">Accès aux en-têtes SOAP dans les messages WCF avec des orchestrations</span><span class="sxs-lookup"><span data-stu-id="ff98e-123">Accessing SOAP Headers in WCF Messages with Orchestrations</span></span>](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [<span data-ttu-id="ff98e-124">Accès aux en-têtes SOAP dans les messages WCF avec des composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="ff98e-124">Accessing SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff98e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff98e-125">See Also</span></span>  
 <span data-ttu-id="ff98e-126">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ff98e-126">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="ff98e-127">En-têtes SOAP avec les services WCF utilisés</span><span class="sxs-lookup"><span data-stu-id="ff98e-127">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)