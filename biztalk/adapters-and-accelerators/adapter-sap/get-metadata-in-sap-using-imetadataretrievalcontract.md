---
title: "Obtient les métadonnées de SAP à l’aide de IMetadataRetrievalContract | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, search metadata
- searching metadata
- how to, browse metadata
- browsing metadata
ms.assetid: 0944fc39-9ee5-4702-8b52-e0bc87f202c6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa36eee26dd9467a71f7e8dd4d28d2e37e26606
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-in-sap-using-imetadataretrievalcontract"></a>Obtient les métadonnées de SAP à l’aide de IMetadataRetrievalContract
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose un **IMetadataRetrievalContract**point de terminaison que vous pouvez utiliser pour parcourir et rechercher les artefacts du système SAP et pour récupérer des métadonnées sous la forme d’un document Web Services Description Language (WSDL) pour opérations.  
  
 Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournit des fonctionnalités de navigation, recherche et la récupération de métadonnées. Outre la **IMetadataRetrievalContract** interface, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] expose le **MetadataRetrievalClient** classe qui implémente l’interface. Vous pouvez utiliser un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour manipuler les métadonnées ; les méthodes exposées à parcourir, rechercher et récupérer les métadonnées sont les mêmes dans chaque cas.  
  
 Les sections suivantes fournissent des informations sur l’utilisation de la **IMetadataRetrievalContract** interface.  
  
## <a name="the-imetadataretrievalcontract-interface"></a>L’Interface IMetadataRetrievalContract  
 Le tableau suivant fournit des informations sur les classes importantes qui sont utilisées lorsque vous travaillez avec le **IMetadataRetrievalContract** interface.  
  
|Classe ou Interface| Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract** interface<br /><br /> (Microsoft.ServiceModel.Channels)|Définit le **Parcourir**, **recherche**, et **GetMetadata** méthodes. Vous appelez ces méthodes à l’aide d’un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour travailler avec les métadonnées de l’adaptateur.|  
|**MetadataRetrievalClient** classe<br /><br /> (Microsoft.ServiceModel.Channels)|Implémente le **IMetadataRetrievalContract** interface. Vous pouvez créer une instance de cette classe et configuration de votre système SAP en fournissant un **SAPBinding** et un **EndpointAddress**. Ensuite, vous pouvez appeler ses méthodes pour travailler avec des métadonnées.|  
|**MetadataRetrievalNode** classe<br /><br /> (Microsoft.ServiceModel.Channels)|Représente un nœud de métadonnées sur la carte. Le **Parcourir** et **recherche** méthodes retournent des nœuds de ce type et le **GetMetadata** méthode accepte les nœuds de ce type en tant que paramètre.|  
|**ServiceDescription** classe<br /><br /> (System.Web.Services.Description)|Fournit un moyen de la création et la mise en forme d’un fichier de document WSDL valide. Le **GetMetadata** méthode retourne un **ServiceDescription** objet.|  
  
 Pour plus d’informations sur la **IMetadataRetrievalContract** interface, le **MetadataRetrievalClient** (classe) et le **MetadataRetrievalNode** classe ; consultez la  **Microsoft.ServiceModel.Channels** gérés référence à l’adresse [http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566).  
  
### <a name="metadata-node-ids"></a>ID de nœud de métadonnées  
 L’adaptateur organise ses métadonnées sous forme d’arborescence hiérarchique de nœuds. Dans l’arborescence, il existe deux types de nœuds de métadonnées :  
  
-   **Nœuds d’opération** représentent des opérations qui met en évidence l’adaptateur sur les artefacts SAP. Nœuds d’opération sont les feuilles de l’arborescence.  
  
-   **Les nœuds de catégorie** représentent les artefacts SAP et les regroupements d’artefacts SAP qui ne correspondent pas directement à une opération sur la carte. Les nœuds de catégorie sont les branches de l’arborescence. elles contiennent des autres nœuds de catégorie et/ou les nœuds de l’opération. Par exemple, les groupes fonctionnels RFC ou les objets métiers SAP sont représentées en tant que nœuds de catégorie.  
  
 Chaque nœud de métadonnées exposée par l’adaptateur est identifié par un ID de nœud unique. Pour plus d’informations sur le nœud de métadonnées ID exposées par l’adaptateur, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md). Ces ID de nœud vous permet de spécifier les artefacts SAP cible lorsque vous utilisez la **IMetadataRetrievalContract** interface à parcourir, rechercher et récupérer des métadonnées. Vous pouvez utiliser l’une des constantes définies dans `Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants` et `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` pour vous aider à construire des ID de nœud de métadonnées.  
  
### <a name="binding-properties"></a>Propriétés de liaison  
 Si vous utilisez un **IMetadataRetrievalContract** canal ou un **IMetadataRetrievalClient** pour travailler avec des métadonnées, vous devez spécifier un **SAPBinding** lorsque vous créez le instance.  
  
 Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées. Ces propriétés sont :  
  
-   **GenerateFlatfileCompatibleIdocSchema**  
  
-   **ReceiveIDocFormat**  
  
-   **EnableSafeTyping**  
  
-   **FlatFileSegmentIndicator**  
  
 Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’ouvrir l’objet de récupération de métadonnées. Pour plus d’informations sur les propriétés de liaison de l’adaptateur SAP, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
### <a name="browsing-metadata-nodes"></a>Parcourir les nœuds de métadonnées  
 Vous utilisez la **Parcourir** méthode pour retourner tous les nœuds de métadonnées qui sont contenus dans un nœud parent. L’exemple suivant recherche les trois premiers groupes fonctionnels RFC sur le système SAP. Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
```  
  
> [!IMPORTANT]
>  Vous pouvez uniquement rechercher des nœuds de catégorie ; Impossible de parcourir les nœuds de l’opération.  
  
### <a name="searching-for-metadata-nodes"></a>Recherche de noeuds de métadonnées  
 Vous utilisez la **recherche** méthode pour effectuer une recherche pour les nœuds contenus dans un nœud parent. Vous pouvez spécifier l’astérisque (\*) caractère générique. Ce caractère correspond à zéro ou plusieurs caractères. L’exemple suivant montre une recherche de tous les documents RFC qui contiennent la chaîne « BAPI ». Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.  
  
```  
// Search for all nodes that contain "BAPI" under the RFC node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI*", int.MaxValue);  
```  
  
> [!IMPORTANT]
>  La recherche est uniquement pris en charge sur un ensemble limité de nœuds. Pour plus d’informations sur les nœuds sur lesquels recherche est prise en charge et sur le caractère générique pris en charge dans les expressions de recherche, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a>La récupération de métadonnées (WSDL) pour les opérations  
 Vous utilisez la **GetMetadata** pour récupérer une description de service (document WSDL) pour un groupe de nœuds de l’opération. L’exemple suivant récupère une description de service pour le document RFC BAPI_TRANSACTION_COMMIT. Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**. Notez que l’ID de nœud pour un nœud d’opération est équivalente à l’action du message pour cette opération.  
  
```  
// Get a WSDL document that specifies a contract that contains the  
// BAPI_TRANSACTION_COMMIT operation.  
MetadataRetrievalNode[] nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
nodes[0].IsOperation = true;  
  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
```  
  
> [!IMPORTANT]
>  Vous devez spécifier uniquement les nœuds d’opération dans le **GetMetadata** (méthode).  
  
### <a name="using-a-metadataretrievalclient"></a>À l’aide d’un MetadataRetrievalClient  
 Création et utilisation d’un **MetadataRetrievalClient** est quasiment identique comme tout autre client WCF. Vous créez le client en spécifiant un point de terminaison et une instance de **SAPBinding**. Vous ce faire de façon déclarative dans la configuration ou impérativement dans votre code. Vous appelez ensuite les méthodes de la **MetadataRetrievalClient** pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur.  
  
 L’exemple suivant montre comment utiliser un **MetadataRetrievalClient** pour parcourir, rechercher et récupérer des métadonnées à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace SapMetaDataBrowseClient  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console.  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //Write all the nodes returned to the console.  
            foreach (MetadataRetrievalNode node in nodes)  
            {  
                Console.WriteLine("NodeId = " + node.NodeId);  
                Console.WriteLine("\tDirection   = " + node.Direction.ToString());  
                Console.WriteLine("\tIsOperation = " + node.IsOperation.ToString());  
                Console.WriteLine("\tDisplayName = " + node.DisplayName);  
                Console.WriteLine("\tDescription = " + node.Description);  
            }  
            Console.WriteLine();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            MetadataRetrievalClient browser = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // Create a binding  
                SAPBinding binding = new SAPBinding();  
  
                EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
                browser = new MetadataRetrievalClient(binding, address);  
                browser.ClientCredentials.UserName.UserName = "YourUserName";  
                browser.ClientCredentials.UserName.Password = "YourPassword";  
                browser.Open();  
  
                // Return the nodes directly under the root.  
                // The parameters are the parent node ID, the start index, and the maximum number  
                // of nodes to return.  
                MetadataRetrievalNode[] nodes = browser.Browse(MetadataRetrievalNode.Root.NodeId, 0, int.MaxValue);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Return first 3 RFC group nodes.  
                nodes = browser.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
                nodeWriter.Write(String.Format("Browse results for the first {1} nodes of {0}:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, nodes.Length), nodes);  
  
                // Search for first 3 nodes that begin with "BAPI_TRANSACTION" under the RFC node.  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return.  
                nodes = browser.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI_TRANSACTION*", 3);  
                nodeWriter.Write(String.Format("Search results for \"*BAPI_TRANSACTION*\" under {0} node:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // found in the search and write it to a file.  
                // You could explicitly specify operations as in the following:  
                //    nodes[0] = new MetadataRetrievalNode();  
                //    nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
                //    nodes[0].IsOperation = true;  
                // Note that the operation NodeId is equivalent to the message action.  
                System.Web.Services.Description.ServiceDescription description = browser.GetMetadata(nodes);  
                description.Write("SampleContract.wsdl");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (browser != null)  
                {  
                    if (browser.State == CommunicationState.Opened)  
                        browser.Close();  
                    else  
                        browser.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 Voici la sortie de ce programme sur la console. Vous pouvez voir la structure des nœuds de récupération de métadonnées retourné pour chaque méthode. Le programme écrit également un document WSDL qui décrit un contrat de service comprenant les nœuds retournés par la recherche dans un fichier. (Pour la plupart des installations SAP, la description du service contient les opérations BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK.)  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/BAPISECTION/000001  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = BAPI  
        Description = BAPI  
NodeId = http://Microsoft.LobServices.Sap/2007/03/IDOCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = IDOC  
        Description = IDOC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = RFC  
        Description = RFC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/TRFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = TRFC  
        Description = TRFC  
  
Browse results for the first 3 nodes of http://Microsoft.LobServices.Sap/2007/03  
/RFCSECTION/:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/A  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Asset Accounting  
        Description = Asset Accounting  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/S  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Basis  
        Description = Basis  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/B  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Business Information Warehouse  
        Description = Business Information Warehouse  
  
Search results for "*BAPI_TRANSACTION*" under http://Microsoft.LobServices.Sap/2  
007/03/RFCSECTION/ node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_COMMIT  
        Description = Execute external Commit when using BAPIs  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_ROLLBACK  
        Description = Execute external Rollback when using BAPIs  
  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a>À l’aide d’un canal IMetadataRetrievalContract  
 Vous pouvez également créer un **IMetadataRetrievalContract** puis utiliser ce canal pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur et de canal. (Les signatures de méthode sont les mêmes que pour les **MetadataRetrievalClient** classe.) L'exemple suivant montre comment effectuer cette opération.  
  
```  
…  
//Create a binding and endpoint address.  
SAPBinding binding = new SAPBinding();  
EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "BAPI_TRANSACTION*", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a>Voir aussi  
 [La récupération des métadonnées par programme à partir de SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)