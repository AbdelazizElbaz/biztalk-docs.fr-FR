---
title: "Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange
- how to, retrieve metadata
- retrieving metadata
ms.assetid: 29f85963-ac7f-4e13-96b8-bc2c94a9fcae
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae33fd76725abf15f12d95be39997fc29e67403e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-using-ws-metadata-exchange-in-sap"></a><span data-ttu-id="c8632-102">Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans SAP</span><span class="sxs-lookup"><span data-stu-id="c8632-102">Get Metadata Using WS-Metadata Exchange in SAP</span></span>
<span data-ttu-id="c8632-103">Comme un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] une liaison personnalisée, la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose un point de terminaison WS-MEX (Metadata Exchange) que vous pouvez utiliser pour récupérer des métadonnées pour des opérations spécifiques à partir de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8632-103">As a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding, the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes a WS-Metadata Exchange (MEX) endpoint that you can use to retrieve metadata for specific operations from the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
 <span data-ttu-id="c8632-104">WCF fournit une infrastructure riche d’exportation, de publication, la récupération et l’importation de métadonnées sur un service.</span><span class="sxs-lookup"><span data-stu-id="c8632-104">WCF provides a rich infrastructure for exporting, publishing, retrieving and importing metadata about a service.</span></span> <span data-ttu-id="c8632-105">Les services WCF, telles que l’adaptateur, utilisent des métadonnées pour décrire l’interaction avec les points de terminaison de service afin que les outils, tels que svcutil.exe, peuvent générer automatiquement le code de client pour consommer le service.</span><span class="sxs-lookup"><span data-stu-id="c8632-105">WCF services, like the adapter, use metadata to describe how to interact with the service endpoints so that tools, like svcutil.exe, can automatically generate client code for consuming the service.</span></span> <span data-ttu-id="c8632-106">WCF représente les métadonnées pour un service sous la forme d’une instance de la **MetadataSet** type, qui est fortement associée au format de sérialisation de métadonnées défini dans WS-MEX (Metadata Exchange).</span><span class="sxs-lookup"><span data-stu-id="c8632-106">WCF represents the metadata for a service as an instance of the **MetadataSet** type, which is strongly tied to the metadata serialization format defined in WS-Metadata Exchange (MEX).</span></span> <span data-ttu-id="c8632-107">Vous pouvez créer un **MetadataSet** pour les opérations ciblées sur la carte en utilisant un **MetadataExchangeClient**.</span><span class="sxs-lookup"><span data-stu-id="c8632-107">You can create a **MetadataSet** for targeted operations on the adapter by using a **MetadataExchangeClient**.</span></span>  
  
 <span data-ttu-id="c8632-108">WCF prend en charge pour l’échange de métadonnées est un sujet vaste et dépasse le cadre de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="c8632-108">WCF support for metadata exchange is an expansive topic and beyond the scope of this documentation.</span></span> <span data-ttu-id="c8632-109">Pour plus d’informations sur la prise en charge des métadonnées dans WCF, consultez « Métadonnées » dans la documentation WCF à [http://go.microsoft.com/fwlink/?LinkId=105634](http://go.microsoft.com/fwlink/?LinkId=105634).</span><span class="sxs-lookup"><span data-stu-id="c8632-109">For more information about support for metadata in WCF, see "Metadata" in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=105634](http://go.microsoft.com/fwlink/?LinkId=105634).</span></span> <span data-ttu-id="c8632-110">Pour obtenir une description particulièrement de l’architecture, classes et les espaces de noms WCF expose des métadonnées, consultez « Présentation de l’Architecture métadonnées » au [http://go.microsoft.com/fwlink/?LinkId=105635](http://go.microsoft.com/fwlink/?LinkId=105635).</span><span class="sxs-lookup"><span data-stu-id="c8632-110">For a particularly good description of the architecture, classes, and namespaces that WCF exposes for metadata, see "Metadata Architecture Overview" at [http://go.microsoft.com/fwlink/?LinkId=105635](http://go.microsoft.com/fwlink/?LinkId=105635).</span></span> <span data-ttu-id="c8632-111">Vous devez vous familiariser avec le contenu associé à la récupération de métadonnées à partir d’un service WCF dans ces rubriques WCF avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c8632-111">You should familiarize yourself with the content related to retrieving metadata from a WCF service in these WCF topics before proceeding.</span></span>  
  
 <span data-ttu-id="c8632-112">Les rubriques suivantes contiennent des informations sur la façon d’utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8632-112">The following topics contain information about how to use a **MetadataExchangeClient** to retrieve metadata from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a><span data-ttu-id="c8632-113">À l’aide d’un MetadataExchangeClient pour récupérer des métadonnées</span><span class="sxs-lookup"><span data-stu-id="c8632-113">Using a MetadataExchangeClient to Retrieve Metadata</span></span>  
 <span data-ttu-id="c8632-114">Pour utiliser un **MetadataExchangeClient** vous devez spécifier un URI de connexion et une liaison (**SAPBinding**).</span><span class="sxs-lookup"><span data-stu-id="c8632-114">To use a **MetadataExchangeClient** you must specify a connection URI and a binding (**SAPBinding**).</span></span> <span data-ttu-id="c8632-115">L’URI de connexion identifie les opérations pour lesquelles vous souhaitez récupérer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c8632-115">The connection URI identifies the operations for which you want to retrieve metadata.</span></span>  
  
 <span data-ttu-id="c8632-116">Les sections suivantes contiennent des informations sur la façon de spécifier l’URI de connexion, les propriétés de liaison important et comment utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c8632-116">The following sections contain information about how to specify the connection URI, important binding properties, and how to use a **MetadataExchangeClient** to retrieve metadata from the adapter.</span></span>  
  
### <a name="the-connection-uri"></a><span data-ttu-id="c8632-117">L’URI de connexion</span><span class="sxs-lookup"><span data-stu-id="c8632-117">The Connection URI</span></span>  
 <span data-ttu-id="c8632-118">Pour utiliser le **MetadataExchangeClient** vous devez fournir une URI qui spécifie un point de terminaison MEX et l’ou les opérations pour lesquelles vous souhaitez récupérer les métadonnées de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="c8632-118">To use the **MetadataExchangeClient** you must supply a SAP connection URI that specifies a MEX endpoint and the operation or operations for which you want to retrieve metadata.</span></span> <span data-ttu-id="c8632-119">Vous spécifiez un point de terminaison et cible les opérations MEX dans l’URI de connexion de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="c8632-119">You specify a MEX endpoint and target operations in the connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="c8632-120">Vous devez inclure le paramètre « wsdl » dans la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="c8632-120">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="c8632-121">S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?).</span><span class="sxs-lookup"><span data-stu-id="c8632-121">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="c8632-122">Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="c8632-122">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="c8632-123">Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ».</span><span class="sxs-lookup"><span data-stu-id="c8632-123">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="c8632-124">Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’action du message (ID de nœud) d’une opération de cible.</span><span class="sxs-lookup"><span data-stu-id="c8632-124">Each "op" parameter is preceded by an ampersand (&) and specifies the message action (node ID) of a target operation.</span></span>  
  
 <span data-ttu-id="c8632-125">Par exemple, l’URI de connexion suivant cible l’opération d’envoi pour l’IDOC SALESORDER_CREATEFROMDAT201 et l’IDOC SALESORDER_CREATEFROMDAT202.</span><span class="sxs-lookup"><span data-stu-id="c8632-125">For example, the following connection URI targets the Send operation for the SALESORDER_CREATEFROMDAT201 IDOC and the SALESORDER_CREATEFROMDAT202 IDOC.</span></span> <span data-ttu-id="c8632-126">Les paramètres « wsdl » et « op » sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="c8632-126">The "wsdl" and "op" parameters are highlighted.</span></span>  
  
```  
"sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"  
```  
  
> [!NOTE]
>  <span data-ttu-id="c8632-127">Il n’est pas nécessaire d’inclure des paramètres de l’écouteur dans l’URI de connexion pour les opérations entrantes.</span><span class="sxs-lookup"><span data-stu-id="c8632-127">It is not necessary to include listener parameters in the connection URI for inbound operations.</span></span> <span data-ttu-id="c8632-128">L’adaptateur se connecte en tant que client pour récupérer des métadonnées à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="c8632-128">The adapter connects as a client to retrieve metadata from the SAP system.</span></span>  
  
 <span data-ttu-id="c8632-129">Vous pouvez également utiliser l’une des constantes définies au `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` pour vous aider à spécifier les opérations lorsque vous créez un URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c8632-129">You can also use the constants defined at `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` to help you specify operations when you create a connection URI.</span></span> <span data-ttu-id="c8632-130">Cela est illustré dans l’exemple de code à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c8632-130">This is demonstrated in the code example at the end of this topic.</span></span>  
  
 <span data-ttu-id="c8632-131">Comment vous passez cet URI de connexion à la **MetadataExchangeClient** dépend des méthodes surchargées vous permet de créer le client et de récupérer les métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c8632-131">How you pass this connection URI to the **MetadataExchangeClient** depends on which of the overloaded methods you use to create the client and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="c8632-132">Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="c8632-132">For more information about the SAP connection URI, see [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="c8632-133">Propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="c8632-133">Binding Properties</span></span>  
 <span data-ttu-id="c8632-134">Lorsque vous créez le **MetadataExchangeClient**, vous devez spécifier un **SAPBinding**.</span><span class="sxs-lookup"><span data-stu-id="c8632-134">When you create the **MetadataExchangeClient**, you must specify an **SAPBinding**.</span></span>  
  
 <span data-ttu-id="c8632-135">Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c8632-135">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="c8632-136">Ces propriétés sont :</span><span class="sxs-lookup"><span data-stu-id="c8632-136">These properties are:</span></span>  
  
-   <span data-ttu-id="c8632-137">**GenerateFlatfileCompatibleIdocSchema**</span><span class="sxs-lookup"><span data-stu-id="c8632-137">**GenerateFlatfileCompatibleIdocSchema**</span></span>  
  
-   <span data-ttu-id="c8632-138">**ReceiveIDocFormat**</span><span class="sxs-lookup"><span data-stu-id="c8632-138">**ReceiveIDocFormat**</span></span>  
  
-   <span data-ttu-id="c8632-139">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="c8632-139">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="c8632-140">**FlatFileSegmentIndicator**</span><span class="sxs-lookup"><span data-stu-id="c8632-140">**FlatFileSegmentIndicator**</span></span>  
  
 <span data-ttu-id="c8632-141">Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’appeler le **GetMetadata** méthode sur le **MetadataExchangeClient**.</span><span class="sxs-lookup"><span data-stu-id="c8632-141">You should ensure that these binding properties are set to the values required for your application before you invoke the **GetMetadata** method on the **MetadataExchangeClient**.</span></span> <span data-ttu-id="c8632-142">Pour plus d’informations sur les propriétés de liaison de l’adaptateur SAP, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c8632-142">For more information about the SAP adapter binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="c8632-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8632-143">Example</span></span>  
 <span data-ttu-id="c8632-144">L’exemple suivant utilise un **MetadataExchangeClient** pour créer une description de service (document WSDL) pour les opérations BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK.</span><span class="sxs-lookup"><span data-stu-id="c8632-144">The following example uses a **MetadataExchangeClient** to create a service description (WSDL document) for the BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK operations.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Collections.ObjectModel;  
  
// Needed for WCF and SAP adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
// Needed for MetadataExchangeClient class  
using System.ServiceModel.Description;  
// Needed for ServiceDescription class  
using System.Web.Services;  
  
namespace SapMetadataExchangeClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //Create a binding  
            SAPBinding binding = new SAPBinding();  
  
            //Create a metadata exchange client that will retrieve metadata according to the WS-MEX standard.  
            MetadataExchangeClient client = new MetadataExchangeClient(binding);  
            client.SoapCredentials.UserName.UserName = "YourUserName";  
            client.SoapCredentials.UserName.Password = "YourPassword";  
  
            //Set up an endpoint address and specify the operation for which we want metadata.  
            string connectionUri = "sap://Client=800;lang=EN@A/YourSAPHost/00?wsdl&op="  
                + Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix  
                + "BAPI_TRANSACTION_COMMIT"  
                + "&op="  
                + Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix  
                + "BAPI_TRANSACTION_ROLLBACK";  
  
            EndpointAddress address = new EndpointAddress(connectionUri);  
  
            //Get the metadata.  
            MetadataSet ms = client.GetMetadata(address);  
  
            // Check for the metadata set size.   
            Collection<MetadataSection> documentCollection = ms.MetadataSections;  
            if (documentCollection != null && documentCollection.Count > 0)  
            {  
                //Get the WSDL from the metadata set  
                System.Web.Services.Description.ServiceDescription wsdl = (System.Web.Services.Description.ServiceDescription)documentCollection[0].Metadata;  
  
                //Save the WSDL to a file.  
                wsdl.Write("BapiTx.wsdl");    
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8632-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8632-145">See Also</span></span>  
 <span data-ttu-id="c8632-146">[La récupération des métadonnées par programme à partir de SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md) </span><span class="sxs-lookup"><span data-stu-id="c8632-146">[Retrieving Metadata Programmatically from SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md) </span></span>  
 [<span data-ttu-id="c8632-147">La récupération des métadonnées dans SAP à l’aide de IMetadataRetrievalContract</span><span class="sxs-lookup"><span data-stu-id="c8632-147">Retrieving Metadata in SAP using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)