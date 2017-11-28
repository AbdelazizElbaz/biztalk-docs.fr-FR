---
title: "Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange, retrieving metadata
- metadata, retrieving using WS-Metadata Exchange
ms.assetid: 6ff34438-7260-489d-a5f0-6e53f8fe43be
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be3f829d41b77dc7897d7b3f4300d82e7a3c100
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-using-ws-metadata-exchange-in-oracle-database"></a><span data-ttu-id="2e4dc-102">Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="2e4dc-102">Get Metadata Using WS-Metadata Exchange in Oracle Database</span></span>
<span data-ttu-id="2e4dc-103">Comme un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] une liaison personnalisée, la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un point de terminaison WS-MEX (Metadata Exchange) que vous pouvez utiliser pour récupérer des métadonnées pour des opérations spécifiques à partir de la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4dc-103">As a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding, the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes a WS-Metadata Exchange (MEX) endpoint that you can use to retrieve metadata for specific operations from the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
 <span data-ttu-id="2e4dc-104">WCF fournit une infrastructure riche d’exportation, de publication, la récupération et l’importation de métadonnées sur un service.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-104">WCF provides a rich infrastructure for exporting, publishing, retrieving and importing metadata about a service.</span></span> <span data-ttu-id="2e4dc-105">Les services WCF, telles que l’adaptateur, utilisent des métadonnées pour décrire l’interaction avec les points de terminaison de service afin que les outils, tels que svcutil.exe, peuvent générer automatiquement le code de client pour consommer le service.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-105">WCF services, like the adapter, use metadata to describe how to interact with the service endpoints so that tools, like svcutil.exe, can automatically generate client code for consuming the service.</span></span> <span data-ttu-id="2e4dc-106">WCF représente les métadonnées pour un service sous la forme d’une instance de la **MetadataSet** type, qui est fortement associée au format de sérialisation de métadonnées défini dans WS-MEX (Metadata Exchange).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-106">WCF represents the metadata for a service as an instance of the **MetadataSet** type, which is strongly tied to the metadata serialization format defined in WS-Metadata Exchange (MEX).</span></span> <span data-ttu-id="2e4dc-107">Vous pouvez créer un **MetadataSet** pour les opérations ciblées sur la carte en utilisant un **MetadataExchangeClient**.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-107">You can create a **MetadataSet** for targeted operations on the adapter by using a **MetadataExchangeClient**.</span></span>  
  
 <span data-ttu-id="2e4dc-108">WCF prend en charge pour l’échange de métadonnées est un sujet vaste et dépasse le cadre de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-108">WCF support for metadata exchange is an expansive topic and beyond the scope of this documentation.</span></span> <span data-ttu-id="2e4dc-109">Pour plus d’informations sur la prise en charge des métadonnées dans WCF, consultez [métadonnées](https://msdn.microsoft.com/library/ms731823.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-109">For more information about support for metadata in WCF, see [Metadata](https://msdn.microsoft.com/library/ms731823.aspx).</span></span> <span data-ttu-id="2e4dc-110">Pour obtenir une description particulièrement utile de l’architecture, les classes et les espaces de noms WCF expose des métadonnées, consultez [présentation de l’Architecture métadonnées](https://msdn.microsoft.com/library/ms730243.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-110">For a particularly good description of the architecture, classes, and namespaces that WCF exposes for metadata, see [Metadata Architecture Overview](https://msdn.microsoft.com/library/ms730243.aspx).</span></span> <span data-ttu-id="2e4dc-111">Vous devez vous familiariser avec le contenu associé à la récupération de métadonnées à partir d’un service WCF dans ces rubriques WCF avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-111">You should familiarize yourself with the content related to retrieving metadata from a WCF service in these WCF topics before proceeding.</span></span>  
  
 <span data-ttu-id="2e4dc-112">Les rubriques suivantes contiennent des informations sur la façon d’utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e4dc-112">The following topics contain information about how to use a **MetadataExchangeClient** to retrieve metadata from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a><span data-ttu-id="2e4dc-113">À l’aide d’un MetadataExchangeClient pour récupérer des métadonnées</span><span class="sxs-lookup"><span data-stu-id="2e4dc-113">Using a MetadataExchangeClient to Retrieve Metadata</span></span>  
 <span data-ttu-id="2e4dc-114">Pour utiliser un **MetadataExchangeClient** vous devez spécifier un URI de connexion et une liaison (**OracleDBBinding**).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-114">To use a **MetadataExchangeClient** you must specify a connection URI and a binding (**OracleDBBinding**).</span></span> <span data-ttu-id="2e4dc-115">L’URI de connexion identifie les opérations pour lesquelles vous souhaitez récupérer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-115">The connection URI identifies the operations for which you want to retrieve metadata.</span></span>  
  
 <span data-ttu-id="2e4dc-116">Les sections suivantes contiennent des informations sur la façon de spécifier l’URI de connexion, les propriétés de liaison important et comment utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-116">The following sections contain information about how to specify the connection URI, important binding properties, and how to use a **MetadataExchangeClient** to retrieve metadata from the adapter.</span></span>  
  
### <a name="the-connection-uri"></a><span data-ttu-id="2e4dc-117">L’URI de connexion</span><span class="sxs-lookup"><span data-stu-id="2e4dc-117">The Connection URI</span></span>  
 <span data-ttu-id="2e4dc-118">Pour utiliser le **MetadataExchangeClient** vous devez fournir une URI qui spécifie un point de terminaison MEX et l’ou les opérations pour lesquelles vous souhaitez récupérer les métadonnées de connexion Oracle.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-118">To use the **MetadataExchangeClient** you must supply an Oracle connection URI that specifies a MEX endpoint and the operation or operations for which you want to retrieve metadata.</span></span> <span data-ttu-id="2e4dc-119">Vous spécifiez un point de terminaison et cible les opérations MEX dans l’URI de connexion de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="2e4dc-119">You specify a MEX endpoint and target operations in the connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="2e4dc-120">Vous devez inclure le paramètre « wsdl » dans la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-120">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="2e4dc-121">S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-121">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="2e4dc-122">Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-122">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="2e4dc-123">Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ».</span><span class="sxs-lookup"><span data-stu-id="2e4dc-123">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="2e4dc-124">Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’action du message (ID de nœud) d’une opération de cible.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-124">Each "op" parameter is preceded by an ampersand (&) and specifies the message action (node ID) of a target operation.</span></span>  
  
 <span data-ttu-id="2e4dc-125">Par exemple, l’URI de connexion suivant cible les opérations Insert et Delete pour SCOTT. Table EMP.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-125">For example, the following connection URI targets the Insert and Delete operations for the SCOTT.EMP table.</span></span> <span data-ttu-id="2e4dc-126">Les paramètres « wsdl » et « op » sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-126">The "wsdl" and "op" parameters are highlighted.</span></span>  
  
```  
"oracledb://ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
```  
  
> [!NOTE]
>  <span data-ttu-id="2e4dc-127">Si vous souhaitez modifier l’espace de noms généré pour l’opération POLLINGSTMT, vous devez spécifier un paramètre PollingId dans la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-127">If you want to modify the namespace generated for the POLLINGSTMT operation you should specify a PollingId parameter in the query string.</span></span>  
  
 <span data-ttu-id="2e4dc-128">Comment vous passez cet URI de connexion à la **MetadataExchangeClient** dépend des méthodes surchargées vous permet de créer le client et de récupérer les métadonnées à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-128">How you pass this connection URI to the **MetadataExchangeClient** depends on which of the overloaded methods you use to create the client and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="2e4dc-129">Pour plus d’informations sur l’URI de connexion Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-129">For more information about the Oracle connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="2e4dc-130">Propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="2e4dc-130">Binding Properties</span></span>  
 <span data-ttu-id="2e4dc-131">Lorsque vous créez le **MetadataExchangeClient**, vous devez spécifier un **OracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-131">When you create the **MetadataExchangeClient**, you must specify an **OracleDBBinding**.</span></span>  
  
 <span data-ttu-id="2e4dc-132">Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-132">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="2e4dc-133">Ces propriétés sont :</span><span class="sxs-lookup"><span data-stu-id="2e4dc-133">These properties are:</span></span>  
  
-   <span data-ttu-id="2e4dc-134">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="2e4dc-134">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="2e4dc-135">**UseSchemaInNamespace**</span><span class="sxs-lookup"><span data-stu-id="2e4dc-135">**UseSchemaInNamespace**</span></span>  
  
-   <span data-ttu-id="2e4dc-136">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="2e4dc-136">**PollingStatement**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e4dc-137">Si vous souhaitez récupérer des métadonnées pour l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-137">If you want to retrieve metadata for the POLLINGSTMT operation you must set the **PollingStatement** binding property.</span></span>  
  
 <span data-ttu-id="2e4dc-138">Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’appeler le **GetMetadata** méthode sur le **MetadataExchangeClient**.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-138">You should ensure that these binding properties are set to the values required for your application before you invoke the **GetMetadata** method on the **MetadataExchangeClient**.</span></span> <span data-ttu-id="2e4dc-139">Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2e4dc-139">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e4dc-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e4dc-140">Example</span></span>  
 <span data-ttu-id="2e4dc-141">L’exemple suivant utilise un **MetadataExchangeClient** pour créer une description de service (document WSDL) pour le Insert, Update, Delete et les opérations Select sur SCOTT. Table EMP.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-141">The following example uses a **MetadataExchangeClient** to create a service description (WSDL document) for the Insert, Update, Delete, and Select operations on the SCOTT.EMP table.</span></span> <span data-ttu-id="2e4dc-142">Le fichier WSDL est enregistré dans un fichier, EmpOperations.wsdl.</span><span class="sxs-lookup"><span data-stu-id="2e4dc-142">The WSDL is saved to a file, EmpOperations.wsdl.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Collections.ObjectModel;  
  
// Needed for WCF and Oracle Adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Needced for MetadataExchangeClient class  
using System.ServiceModel.Description;  
// Needed for ServiceDescription class  
using System.Web.Services;  
  
namespace OracleMetadataExchange  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            OracleDBBinding binding = new OracleDBBinding();  
  
            //create a metadata exchange client that will retrieve metadata according to the WS-MEX standard  
            MetadataExchangeClient client = new MetadataExchangeClient(binding);  
            client.SoapCredentials.UserName.UserName = "SCOTT";  
            client.SoapCredentials.UserName.Password = "TIGER";  
  
            //set up an endpoint address and specifies the operations for which we want metadata  
            string connectionUri = "oracledb://ADAPTER?wsdl"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select";  
  
            EndpointAddress address = new EndpointAddress(connectionUri);  
  
            //get the metadata  
            MetadataSet ms = client.GetMetadata(address);  
  
            // Check for the metadata set size   
            Collection<MetadataSection> documentCollection = ms.MetadataSections;  
            if (documentCollection != null && documentCollection.Count > 0)  
            {  
                //get the wsdl from the metadata set  
                System.Web.Services.Description.ServiceDescription wsdl = (System.Web.Services.Description.ServiceDescription)documentCollection[0].Metadata;  
  
                //save the wsdl to a file  
                wsdl.Write("EmpOperations.wsdl");  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e4dc-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e4dc-143">See Also</span></span>  
 [<span data-ttu-id="2e4dc-144">Obtenir les métadonnées par programme à partir de la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="2e4dc-144">Get Metadata Programmatically from the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)