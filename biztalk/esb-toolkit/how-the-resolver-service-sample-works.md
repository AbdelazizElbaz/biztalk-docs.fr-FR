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
ms.openlocfilehash: 6c44677d4d488a4770c540ef94c0922579be3184
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-resolver-service-sample-works"></a><span data-ttu-id="cde1d-102">Fonctionne de l’exemple de Service de programme de résolution</span><span class="sxs-lookup"><span data-stu-id="cde1d-102">How the Resolver Service Sample Works</span></span>
<span data-ttu-id="cde1d-103">L’exemple de Service de résolution instancie le service de résolution et transmet le message spécifié à ce dernier pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="cde1d-103">The Resolver Service sample instantiates the Resolver service and passes the message you specify to it for processing.</span></span> <span data-ttu-id="cde1d-104">L’exemple d’application cliente Service de résolution utilise le premier paramètre en tant que le chemin d’accès au fichier ResolverList.xml, qui contient plusieurs demandes de programme de résolution et envoie ces demandes au service de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="cde1d-104">The Resolver Service sample client application uses the first parameter as the path to the ResolverList.xml file, which contains multiple resolver requests, and sends these requests to the Resolver service.</span></span> <span data-ttu-id="cde1d-105">Par exemple, voici la requête XPATH utilisée dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="cde1d-105">For example, the following is the XPATH request used in the sample.</span></span>  
  
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
>  <span data-ttu-id="cde1d-106">Le contenu réel de la  **\<contenu >** élément ne contient pas les caractères d’espace blanc utilisés pour encapsuler les lignes dans la liste précédente.</span><span class="sxs-lookup"><span data-stu-id="cde1d-106">The actual content of the **\<Content>** element does not contain the white space characters used to wrap the lines in the preceding listing.</span></span>  
  
 <span data-ttu-id="cde1d-107">La liste précédente montre que la demande contient la chaîne de connexion de configuration de programme de résolution au sein d’un  **\<contenu >** élément.</span><span class="sxs-lookup"><span data-stu-id="cde1d-107">The preceding listing shows that the request contains the resolver configuration connection string within a **\<Content>** element.</span></span> <span data-ttu-id="cde1d-108">Le  **\<corps >** élément contient le corps du message.</span><span class="sxs-lookup"><span data-stu-id="cde1d-108">The **\<body>** element contains the message body.</span></span>  
  
 <span data-ttu-id="cde1d-109">Le service de programme de résolution utilise le **ResolverMgr** classe à instancier une instance concrète du programme de résolution appropriée, définie par le type de programme de résolution dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="cde1d-109">The Resolver service uses the **ResolverMgr** class to instantiate a concrete instance of the appropriate resolver, defined by the resolver type in the connection string.</span></span> <span data-ttu-id="cde1d-110">Dans le cas de la requête XPATH, il s’agit de l’outil de résolution XPATH.</span><span class="sxs-lookup"><span data-stu-id="cde1d-110">In the case of the XPATH request, this is the XPATH resolver.</span></span>  
  
 <span data-ttu-id="cde1d-111">Ensuite, l’infrastructure crée une instance de la **ResolveProvider** classe nommée ESB. Resolver.XPath pour traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="cde1d-111">Next, the framework creates an instance of the **ResolveProvider** class named ESB.Resolver.XPath to process the request.</span></span> <span data-ttu-id="cde1d-112">L’application cliente écrit le message de réponse du service de résolution dans le dossier nommé \Source\Samples\ResolverService\Output.</span><span class="sxs-lookup"><span data-stu-id="cde1d-112">The client application writes the response message from the Resolver service into the folder named \Source\Samples\ResolverService\Output.</span></span> <span data-ttu-id="cde1d-113">La liste suivante répertorie le contenu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="cde1d-113">The following listing shows the contents of the response.</span></span>  
  
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