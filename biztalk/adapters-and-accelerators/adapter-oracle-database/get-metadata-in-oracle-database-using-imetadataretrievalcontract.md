---
title: "Obtient les métadonnées de la base de données Oracle à l’aide de IMetadataRetrievalContract | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving using IMetadataRetrievalContract
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132ad3f64d377a3bfcbf7b1b2303e1c0de0c612f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-in-oracle-database-using-imetadataretrievalcontract"></a>Obtient les métadonnées de la base de données Oracle à l’aide de IMetadataRetrievalContract
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un **IMetadataRetrievalContract**point de terminaison que vous pouvez utiliser pour parcourir et rechercher les artefacts de base de données Oracle et récupérer des métadonnées pour les opérations sous la forme d’une Description langage WSDL (Web Services ) document.  
  
 Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournit des fonctionnalités de navigation, recherche et la récupération de métadonnées. Outre la **IMetadataRetrievalContract** interface, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] expose le **MetadataRetrievalClient** classe qui implémente l’interface. Vous pouvez utiliser un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour manipuler les métadonnées ; les méthodes exposées à parcourir, rechercher et récupérer les métadonnées sont les mêmes dans chaque cas.  
  
 Les sections suivantes fournissent des informations sur l’utilisation de la **IMetadataRetrievalContract** interface.  
  
## <a name="the-imetadataretrievalcontract-interface"></a>L’Interface IMetadataRetrievalContract  
 Le tableau suivant fournit des informations sur les classes importantes qui sont utilisées lorsque vous travaillez avec le **IMetadataRetrievalContract** interface.  
  
|Classe ou Interface| Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract** interface<br /><br /> (Microsoft.ServiceModel.Channels)|Définit le **Parcourir**, **recherche**, et **GetMetadata** méthodes. Vous appelez ces méthodes à l’aide d’un **IMetadataRetrievalContract** canal ou un **MetadataRetrievalClient** pour travailler avec les métadonnées de l’adaptateur.|  
|**MetadataRetrievalClient** classe<br /><br /> (Microsoft.ServiceModel.Channels)|Implémente le **IMetadataRetrievalContract** interface. Vous pouvez créer une instance de cette classe et le configurer pour votre base de données Oracle en fournissant une **OracleDBBinding** et un **EndpointAddress**. Ensuite, vous pouvez appeler ses méthodes pour travailler avec des métadonnées.|  
|**MetadataRetrievalNode** classe<br /><br /> (Microsoft.ServiceModel.Channels)|Représente un nœud de métadonnées sur la carte. Le **Parcourir** et **recherche** méthodes retournent des nœuds de ce type et le **GetMetadata** méthode accepte les nœuds de ce type en tant que paramètre.|  
|**ServiceDescription** classe<br /><br /> (System.Web.Services.Description)|Fournit un moyen de la création et la mise en forme d’un fichier de document WSDL valide. Le **GetMetadata** méthode retourne un **ServiceDescription** objet.|  
  
 
### <a name="metadata-node-ids"></a>ID de nœud de métadonnées  
 L’adaptateur organise ses métadonnées sous forme d’arborescence hiérarchique de nœuds. Dans l’arborescence, il existe deux types de nœuds de métadonnées :  
  
-   **Nœuds d’opération** représentent des opérations qui met en évidence l’adaptateur sur les objets de base de données Oracle. Nœuds d’opération sont les feuilles de l’arborescence.  
  
-   **Les nœuds de catégorie** représentent les artefacts de base de données Oracle et des regroupements d’artefacts de base de données Oracle qui ne correspondent pas directement à une opération sur la carte. Les nœuds de catégorie sont les branches de l’arborescence. elles contiennent des autres nœuds de catégorie et/ou les nœuds de l’opération. Par exemple, les packages et des tables Oracle sont représentées en tant que nœuds de catégorie.  
  
 Chaque nœud de métadonnées exposée par l’adaptateur est identifié par un ID de nœud unique. Pour plus d’informations sur le nœud de métadonnées ID exposées par l’adaptateur, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md). Ces ID de nœud vous permet de spécifier les artefacts de base de données Oracle cible lorsque vous utilisez la **IMetadataRetrievalContract** interface à parcourir, rechercher et récupérer des métadonnées.  
  
### <a name="binding-properties"></a>Propriétés de liaison  
 Si vous utilisez un **IMetadataRetrievalContract** canal ou un **IMetadataRetrievalClient** pour travailler avec des métadonnées, vous devez spécifier un **OracleDBBinding** lorsque vous créer l’instance.  
  
 Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées. Ces propriétés sont :  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  Si vous souhaitez récupérer des métadonnées pour l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison.  
  
 Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’ouvrir l’objet de récupération de métadonnées. Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
### <a name="browsing-metadata-nodes"></a>Parcourir les nœuds de métadonnées  
 Vous utilisez la **Parcourir** méthode pour retourner tous les nœuds de métadonnées qui sont contenus dans un nœud parent. L’exemple suivant recherche les trois premiers schémas sur la base de données Oracle. Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  Vous pouvez uniquement rechercher des nœuds de catégorie ; Impossible de parcourir les nœuds de l’opération.  
  
### <a name="searching-for-metadata-nodes"></a>Recherche de noeuds de métadonnées  
 Vous utilisez la **recherche** méthode pour effectuer une recherche pour les nœuds contenus dans un nœud parent. L’adaptateur prend en charge les caractères génériques dans les expressions de recherche ; par exemple, vous pouvez spécifier le pourcentage (%) caractère générique pour faire correspondre zéro ou plusieurs caractères. L’exemple suivant montre une recherche de toutes les tables dans le schéma SCOTT qui contiennent la chaîne « EMP ». Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  La recherche est uniquement pris en charge sur un ensemble limité de nœuds. Pour plus d’informations sur les nœuds sur lesquels recherche est prise en charge et sur les caractères génériques pris en charge dans les expressions de recherche, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a>La récupération de métadonnées (WSDL) pour les opérations  
 Vous utilisez la **GetMetadata** pour récupérer une description de service (document WSDL) pour un groupe de nœuds de l’opération. L’exemple suivant récupère une description de service qui contient toutes les opérations que l’adaptateur met en évidence pour SCOTT. Table EMP en spécifiant son ID de nœud. Dans cet exemple, **client** est une instance de **MetadataRetrievalClient**.  
  
```  
// Get a service description that contains all of the operations   
// surfaced for the SCOTT.EMP table. The IsOperation  
// property is set false because this is a category node.  
nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
nodes[0].IsOperation = false;  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
  
```  
  
> [!IMPORTANT]
>  Le **IsOperation** propriété doit avoir la valeur false pour les nœuds de catégorie et de la valeur true pour les nœuds de l’opération.  
  
### <a name="using-a-metadataretrievalclient"></a>À l’aide d’un MetadataRetrievalClient  
 Création et utilisation d’un **MetadataRetrievalClient** est quasiment identique comme tout autre client WCF. Vous créez le client en spécifiant un point de terminaison et une instance de **OracleDBBinding**. Vous ce faire de façon déclarative dans la configuration ou impérativement dans votre code. Vous appelez ensuite les méthodes de la **MetadataRetrievalClient** pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur.  
  
 L’exemple suivant montre comment utiliser un **MetadataRetrievalClient** pour parcourir, rechercher et récupérer des métadonnées à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. L’exemple montre :  
  
-   Navigation sur le nœud racine de l’arborescence de métadonnées pour les schémas de base de données Oracle.  
  
-   Recherchez les tables dans le schéma SCOTT avec des noms qui contiennent la chaîne « EMP ».  
  
-   Récupération des métadonnées pour toutes les opérations prises en charge pour SCOTT. Table EMP en passant d’un nœud de catégorie pour le **GetMetadata** (méthode).  
  
-   Récupération des métadonnées pour l’opération POLLINGSTMT en passant le nœud d’opération POLLINGSTMT à la **GetMetadata** méthode...  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace OracleMetadataRetrieval  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //write all the nodes returned to the console.  
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
            MetadataRetrievalClient client = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // create a binding and   
                // set the PollingStatement binding property if you want to  
                // return metadata for the POLLINGSTMT operation  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.PollingStatement = "SELECT * FROM EMP";  
  
                // Set PollingId parameter if you want to alter the namespace of the POLLINGSTMT operation  
                EndpointAddress address = new EndpointAddress("oracledb://ADAPTER?PollingId=1");  
  
                client = new MetadataRetrievalClient(binding, address);  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
                client.Open();  
  
                // Browse for the first 3 (schema) nodes directly under the root  
                // The parameters are the parent Node ID, the start index, and the maximum number  
                // of nodes to return  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Search for first 3 tables that contain "EMP" in the SCOTT schema  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return  
                nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
                nodeWriter.Write(String.Format("Search results for \"%EMP%\" under {0} node:", "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table"), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // surfaced for the SCOTT.EMP table. The IsOperation property is set false  
                // because this is a category node.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
                nodes[0].IsOperation = false;  
                System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
                description.Write("EmpTableContract.wsdl");  
  
                // Get a WSDL document that specifies a contract that contains the   
                // the POLLINGSTMT operation. The IsOperation property is set true  
                // because this is an operation node.  
                // Note that the operation NodeId is equivalent to the message action.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT";  
                nodes[0].IsOperation = true;  
                description = client.GetMetadata(nodes);  
                description.Write("PollingContract.wsdl");  
  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 Voici la sortie de ce programme sur la console. Vous pouvez voir la structure des nœuds de récupération de métadonnées retournées par chaque méthode. Le programme écrit également deux documents WSDL à des fichiers.  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTERTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTERTEST  
        Description = Owned By ADAPTERTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTEST  
        Description = Owned By ADAPTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADMIN123  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADMIN123  
        Description = Owned By ADMIN123  
  
Search results for "%EMP%" under http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/AEMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = AEMP  
        Description = Table.AEMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP  
        Description = Table.EMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP1  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP1  
        Description = Table.EMP1  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a>À l’aide d’un canal IMetadataRetrievalContract  
 Vous pouvez également créer un **IMetadataRetrievalContract** puis utiliser ce canal pour parcourir, rechercher et récupérer les métadonnées à partir de l’adaptateur et de canal. (Les signatures de méthode sont les mêmes que pour les **MetadataRetrievalClient** classe.) L'exemple suivant montre comment effectuer cette opération.  
  
```  
…  
//Create a binding and endpoint address.  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER/");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées par programme à partir de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)