---
title: "Appeler des méthodes de Service d’entreprise avec des objets d’intégration à l’aide de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- integration objects
- how to, invoke business service methods with integration objects
- business service methods, invoking with integration objects
ms.assetid: ac0fa80a-3451-436e-8a1a-b6b5e93081e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132c269d347f67cbad3038bcbbb8e62d29112b6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-business-service-methods-with-integration-objects-using-the-siebel-adapter"></a><span data-ttu-id="35c5d-102">Appeler des méthodes de Service d’entreprise avec des objets d’intégration à l’aide de l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="35c5d-102">Invoke Business Service Methods with Integration Objects using the Siebel adapter</span></span>
<span data-ttu-id="35c5d-103">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur appeler des méthodes de service d’entreprise qui fonctionnent avec les objets d’intégration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to invoke business service methods that work with integration objects.</span></span> <span data-ttu-id="35c5d-104">Ces services professionnels ont généralement IN, OUT, ou dans les paramètres de données de « hiérarchie » de type pour envoyer ou recevoir des données d’objet intégration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-104">These business services typically have IN, OUT, or IN OUT parameters of "hierarchy" data type to send or receive integration object data.</span></span>  
  
 <span data-ttu-id="35c5d-105">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose ces types hiérarchiques sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="35c5d-105">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes these hierarchical types as strings.</span></span> <span data-ttu-id="35c5d-106">Ces valeurs de chaîne sont essentiellement une chaîne XML est encapsulée dans une section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="35c5d-106">These string values are essentially an XML string encapsulated in an XML CDATA section.</span></span> <span data-ttu-id="35c5d-107">La chaîne XML est compatible avec le schéma XML de l’objet d’intégration que le client de l’adaptateur tente d’envoyer ou recevoir.</span><span class="sxs-lookup"><span data-stu-id="35c5d-107">The XML string is compatible with the XML schema of the integration object the adapter client is trying to send or receive.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="35c5d-108">Exemple basé sur cette rubrique</span><span class="sxs-lookup"><span data-stu-id="35c5d-108">Sample Based On This Topic</span></span>  
 <span data-ttu-id="35c5d-109">Un exemple, SiebelAdapterIntegrationObjects, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35c5d-109">A sample, SiebelAdapterIntegrationObjects, based on this topic is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="35c5d-110">Pour plus d’informations, consultez [exemples pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="35c5d-110">For more information, see [Samples for the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).</span></span>
  
## <a name="creating-an-orchestration-to-invoke-business-service-methods-with-integration-objects"></a><span data-ttu-id="35c5d-111">Création d’une Orchestration pour appeler des méthodes de Service d’entreprise avec des objets d’intégration</span><span class="sxs-lookup"><span data-stu-id="35c5d-111">Creating an Orchestration to Invoke Business Service Methods with Integration Objects</span></span>  
 <span data-ttu-id="35c5d-112">Création d’une orchestration pour appeler une méthode de service d’entreprise qui utilise des paramètres de l’objet d’intégration est similaire à l’orchestration à appeler n’importe quel autre service d’entreprise, comme décrit dans [appeler Business Service méthodes à l’aide de BizTalk Server et l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="35c5d-112">Creating an orchestration to invoke a business service method that takes integration object parameters is similar to the orchestration to invoke any other business service, as described in [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span></span>  
  
 <span data-ttu-id="35c5d-113">La différence réside dans le message de demande que vous déposez pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-113">The difference lies in the request message that you drop for the orchestration.</span></span> <span data-ttu-id="35c5d-114">Cela s’explique par le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="35c5d-114">This difference is because of the following:</span></span>  
  
-   <span data-ttu-id="35c5d-115">Le schéma du message de requête est différent, car vous appelez un service d’entreprise différents.</span><span class="sxs-lookup"><span data-stu-id="35c5d-115">The schema for the request message is different because you invoke a different business service.</span></span>  
  
-   <span data-ttu-id="35c5d-116">Le message de demande contient la chaîne XML de l’objet d’intégration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-116">The request message contains the XML string for the integration object.</span></span> <span data-ttu-id="35c5d-117">Ce code XML est encapsulé dans une section CDATA.</span><span class="sxs-lookup"><span data-stu-id="35c5d-117">This XML is encapsulated in a CDATA section.</span></span> <span data-ttu-id="35c5d-118">Vous devez tout d’abord générer le schéma pour l’objet d’intégration et ensuite créer un document XML conforme au schéma.</span><span class="sxs-lookup"><span data-stu-id="35c5d-118">You must first generate the schema for the integration object and then create an XML that conforms to the schema.</span></span> <span data-ttu-id="35c5d-119">Ce document XML doit être passé au sein de la section CDATA du message de demande envoyée à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="35c5d-119">This XML must be passed within the CDATA section of the request message sent to the adapter.</span></span>  
  
 <span data-ttu-id="35c5d-120">Une fois que vous avez généré le code XML qui est conforme au schéma d’objet intégration et inclus dans le message de demande, vous devez supprimer le message de demande à un emplacement de fichier, exactement comme vous le feriez pour n’importe quel autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-120">After you have generated the XML that conforms to the integration object schema and included it in the request message, you must drop the request message at a FILE location, just like you do for any other orchestration.</span></span> <span data-ttu-id="35c5d-121">Recherchez le message de réponse dans l’autre emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="35c5d-121">Look for the response message in the other FILE location.</span></span>  
  
## <a name="request-and-response-messages-for-invoking-business-service-with-integration-objects"></a><span data-ttu-id="35c5d-122">Messages de demande et réponse pour l’appel de Service d’entreprise avec des objets d’intégration</span><span class="sxs-lookup"><span data-stu-id="35c5d-122">Request and Response Messages for Invoking Business Service with Integration Objects</span></span>  
 <span data-ttu-id="35c5d-123">Comme mentionné précédemment, la seule différence pour appeler un service d’entreprise qui utilise des paramètres de l’objet d’intégration est le message de demande envoyé à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="35c5d-123">As mentioned before, the only difference for invoking a business service that takes integration object parameters is the request message sent to the adapter.</span></span> <span data-ttu-id="35c5d-124">Cette section fournit des instructions sur la procédure à qu'effectuer pour créer le message de demande.</span><span class="sxs-lookup"><span data-stu-id="35c5d-124">This section provides instructions on the steps you must perform to create the request message.</span></span>  
  
 <span data-ttu-id="35c5d-125">Pour mieux comprendre, prenons l’exemple un service d’entreprise Siebel 'EAI l’adaptateur Siebel'.</span><span class="sxs-lookup"><span data-stu-id="35c5d-125">For better understanding, take a Siebel business service 'EAI Siebel Adapter' as an example.</span></span> <span data-ttu-id="35c5d-126">Le service d’entreprise 'EAI l’adaptateur Siebel' fonctionne sur un objet d’intégration de Siebel, « Compte de l’exemple ».</span><span class="sxs-lookup"><span data-stu-id="35c5d-126">The 'EAI Siebel Adapter' business service operates on a Siebel integration object, 'Sample Account'.</span></span> <span data-ttu-id="35c5d-127">Vous devez effectuer les tâches suivantes pour créer le message de demande pour appeler une méthode exposée par le service d’entreprise 'EAI l’adaptateur Siebel' :</span><span class="sxs-lookup"><span data-stu-id="35c5d-127">You must perform the following tasks to create the request message to invoke a method exposed by the 'EAI Siebel Adapter' business service:</span></span>  
  
-   <span data-ttu-id="35c5d-128">**Générer le schéma pour le service d’entreprise EAI l’adaptateur Siebel**.</span><span class="sxs-lookup"><span data-stu-id="35c5d-128">**Generate the schema for the EAI Siebel Adapter business service**.</span></span> <span data-ttu-id="35c5d-129">Vous devez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma.</span><span class="sxs-lookup"><span data-stu-id="35c5d-129">You must use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema.</span></span> <span data-ttu-id="35c5d-130">Une fois que vous générez le schéma, générer le code XML qui est conforme au schéma.</span><span class="sxs-lookup"><span data-stu-id="35c5d-130">Once you generate the schema, generate the XML that conforms to the schema.</span></span>  
  
-   <span data-ttu-id="35c5d-131">**Générer le schéma pour l’objet d’intégration**.</span><span class="sxs-lookup"><span data-stu-id="35c5d-131">**Generate the schema for the integration object**.</span></span> <span data-ttu-id="35c5d-132">Utilisez les outils de Siebel pour générer le schéma d’un objet d’intégration.</span><span class="sxs-lookup"><span data-stu-id="35c5d-132">Use Siebel Tools to generate schema for an integration object.</span></span> <span data-ttu-id="35c5d-133">Dans l’interface Outils Siebel, sélectionnez l’objet d’intégration, par exemple, exemple de compte, puis cliquez sur **générer le schéma**.</span><span class="sxs-lookup"><span data-stu-id="35c5d-133">From the Siebel Tools interface, select the integration object, for example, Sample Account, and click **Generate Schema**.</span></span> <span data-ttu-id="35c5d-134">Lors de la génération du schéma, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="35c5d-134">While generating the schema, make sure:</span></span>  
  
    -   <span data-ttu-id="35c5d-135">Le **sélectionner un Service d’entreprise à partir de la liste** déroulante a la valeur « EAI XML XSD Generator ».</span><span class="sxs-lookup"><span data-stu-id="35c5d-135">The **Select a Business Service from the list** drop-down has the value "EAI XML XSD Generator".</span></span>  
  
    -   <span data-ttu-id="35c5d-136">Le **sélectionnez un type d’enveloppe dans la liste** déroulante a la valeur « Enveloppe de Message Siebel ».</span><span class="sxs-lookup"><span data-stu-id="35c5d-136">The **Select an envelope type from the list** drop-down has the value "Siebel Message Envelope".</span></span>  
  
     <span data-ttu-id="35c5d-137">Pour plus d’informations, consultez la documentation de Siebel.</span><span class="sxs-lookup"><span data-stu-id="35c5d-137">For more information, see the Siebel documentation.</span></span>  
  
-   <span data-ttu-id="35c5d-138">**Créer un message XML conforme au schéma de l’objet d’intégration**.</span><span class="sxs-lookup"><span data-stu-id="35c5d-138">**Create an XML message that conforms to schema of the integration object**.</span></span> <span data-ttu-id="35c5d-139">Un exemple de message XML généré pour l’objet d’intégration 'Exemple compte' ressemble à :</span><span class="sxs-lookup"><span data-stu-id="35c5d-139">A sample XML message generated for the 'Sample Account' integration object looks like:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="UTF-16"?>  
    <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
      <ListOfSampleAccount>  
        <Account>  
          <CurrencyCode>USD</CurrencyCode>  
          <Location>Redmond</Location>  
          <Name>IntegrationObjectTest</Name>  
        </Account>  
      </ListOfSampleAccount>  
    </SiebelMessage>  
    ```  
  
-   <span data-ttu-id="35c5d-140">**Passer ce message XML en tant que la valeur de l’élément CDATA dans le message de demande pour la méthode de service business**.</span><span class="sxs-lookup"><span data-stu-id="35c5d-140">**Pass this XML message as the value for the CDATA element in the request message for the business service method**.</span></span> <span data-ttu-id="35c5d-141">Un exemple de message de demande qui contient le message XML au sein d’un élément CDATA ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="35c5d-141">A sample request message that contains the preceding XML message within a CDATA element looks like the following.</span></span> <span data-ttu-id="35c5d-142">Cet exemple de demande est d’appeler la méthode d’insertion pour le service d’entreprise 'EAI l’adaptateur Siebel'.</span><span class="sxs-lookup"><span data-stu-id="35c5d-142">This sample request is to invoke the Insert method for the 'EAI Siebel Adapter' business service.</span></span>  
  
    ```  
    <Insert xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertRequestRecord />   
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </Insert>  
    ```  
  
     <span data-ttu-id="35c5d-143">La réponse à partir de Siebel pour le message de demande ci-dessus ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="35c5d-143">The response from Siebel for the above request message resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <InsertResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertResult>  
        <ErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">0x0</ErrorCode>   
        <ErrorContextIntComp xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorContextSearchSpec xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <PrimaryRowId xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">1-6SPSJ</PrimaryRowId>   
      </InsertResult>  
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </InsertResponse>  
    ```  
  
 <span data-ttu-id="35c5d-144">À l’aide des fonctionnalités de BizTalk, les clients de l’adaptateur peuvent également effectuer une validation supplémentaire de l’intégration IN et OUT paramètre de l’objet par rapport au schéma d’objet integration (obtenu à partir des outils de Siebel).</span><span class="sxs-lookup"><span data-stu-id="35c5d-144">Using BizTalk features, adapter clients can also perform additional validation of the integration object IN and OUT parameter against the integration object schema (obtained from Siebel Tools.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c5d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35c5d-145">See Also</span></span>  
<span data-ttu-id="35c5d-146">[Développer des Applications BizTalk à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)  </span><span class="sxs-lookup"><span data-stu-id="35c5d-146">[Develop BizTalk Applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)  </span></span>  
[<span data-ttu-id="35c5d-147">Développer vos applications Siebel</span><span class="sxs-lookup"><span data-stu-id="35c5d-147">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)