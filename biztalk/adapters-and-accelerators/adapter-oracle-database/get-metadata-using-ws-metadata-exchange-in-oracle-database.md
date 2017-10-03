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
# <a name="get-metadata-using-ws-metadata-exchange-in-oracle-database"></a>Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans la base de données Oracle
Comme un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] une liaison personnalisée, la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un point de terminaison WS-MEX (Metadata Exchange) que vous pouvez utiliser pour récupérer des métadonnées pour des opérations spécifiques à partir de la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
 WCF fournit une infrastructure riche d’exportation, de publication, la récupération et l’importation de métadonnées sur un service. Les services WCF, telles que l’adaptateur, utilisent des métadonnées pour décrire l’interaction avec les points de terminaison de service afin que les outils, tels que svcutil.exe, peuvent générer automatiquement le code de client pour consommer le service. WCF représente les métadonnées pour un service sous la forme d’une instance de la **MetadataSet** type, qui est fortement associée au format de sérialisation de métadonnées défini dans WS-MEX (Metadata Exchange). Vous pouvez créer un **MetadataSet** pour les opérations ciblées sur la carte en utilisant un **MetadataExchangeClient**.  
  
 WCF prend en charge pour l’échange de métadonnées est un sujet vaste et dépasse le cadre de cette documentation. Pour plus d’informations sur la prise en charge des métadonnées dans WCF, consultez [métadonnées](https://msdn.microsoft.com/library/ms731823.aspx). Pour obtenir une description particulièrement utile de l’architecture, les classes et les espaces de noms WCF expose des métadonnées, consultez [présentation de l’Architecture métadonnées](https://msdn.microsoft.com/library/ms730243.aspx). Vous devez vous familiariser avec le contenu associé à la récupération de métadonnées à partir d’un service WCF dans ces rubriques WCF avant de continuer.  
  
 Les rubriques suivantes contiennent des informations sur la façon d’utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a>À l’aide d’un MetadataExchangeClient pour récupérer des métadonnées  
 Pour utiliser un **MetadataExchangeClient** vous devez spécifier un URI de connexion et une liaison (**OracleDBBinding**). L’URI de connexion identifie les opérations pour lesquelles vous souhaitez récupérer les métadonnées.  
  
 Les sections suivantes contiennent des informations sur la façon de spécifier l’URI de connexion, les propriétés de liaison important et comment utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de l’adaptateur.  
  
### <a name="the-connection-uri"></a>L’URI de connexion  
 Pour utiliser le **MetadataExchangeClient** vous devez fournir une URI qui spécifie un point de terminaison MEX et l’ou les opérations pour lesquelles vous souhaitez récupérer les métadonnées de connexion Oracle. Vous spécifiez un point de terminaison et cible les opérations MEX dans l’URI de connexion de la manière suivante :  
  
-   Vous devez inclure le paramètre « wsdl » dans la chaîne de requête. S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?). Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).  
  
-   Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ». Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’action du message (ID de nœud) d’une opération de cible.  
  
 Par exemple, l’URI de connexion suivant cible les opérations Insert et Delete pour SCOTT. Table EMP. Les paramètres « wsdl » et « op » sont mis en surbrillance.  
  
```  
"oracledb://ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
```  
  
> [!NOTE]
>  Si vous souhaitez modifier l’espace de noms généré pour l’opération POLLINGSTMT, vous devez spécifier un paramètre PollingId dans la chaîne de requête.  
  
 Comment vous passez cet URI de connexion à la **MetadataExchangeClient** dépend des méthodes surchargées vous permet de créer le client et de récupérer les métadonnées à partir de l’adaptateur.  
  
 Pour plus d’informations sur l’URI de connexion Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
### <a name="binding-properties"></a>Propriétés de liaison  
 Lorsque vous créez le **MetadataExchangeClient**, vous devez spécifier un **OracleDBBinding**.  
  
 Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées. Ces propriétés sont :  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  Si vous souhaitez récupérer des métadonnées pour l’opération POLLINGSTMT, vous devez définir le **PollingStatement** propriété de liaison.  
  
 Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’appeler le **GetMetadata** méthode sur le **MetadataExchangeClient**. Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise un **MetadataExchangeClient** pour créer une description de service (document WSDL) pour le Insert, Update, Delete et les opérations Select sur SCOTT. Table EMP. Le fichier WSDL est enregistré dans un fichier, EmpOperations.wsdl.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées par programme à partir de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)