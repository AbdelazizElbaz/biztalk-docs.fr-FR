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
# <a name="get-metadata-using-ws-metadata-exchange-in-sap"></a>Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans SAP
Comme un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] une liaison personnalisée, la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose un point de terminaison WS-MEX (Metadata Exchange) que vous pouvez utiliser pour récupérer des métadonnées pour des opérations spécifiques à partir de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
 WCF fournit une infrastructure riche d’exportation, de publication, la récupération et l’importation de métadonnées sur un service. Les services WCF, telles que l’adaptateur, utilisent des métadonnées pour décrire l’interaction avec les points de terminaison de service afin que les outils, tels que svcutil.exe, peuvent générer automatiquement le code de client pour consommer le service. WCF représente les métadonnées pour un service sous la forme d’une instance de la **MetadataSet** type, qui est fortement associée au format de sérialisation de métadonnées défini dans WS-MEX (Metadata Exchange). Vous pouvez créer un **MetadataSet** pour les opérations ciblées sur la carte en utilisant un **MetadataExchangeClient**.  
  
 WCF prend en charge pour l’échange de métadonnées est un sujet vaste et dépasse le cadre de cette documentation. Pour plus d’informations sur la prise en charge des métadonnées dans WCF, consultez « Métadonnées » dans la documentation WCF à [http://go.microsoft.com/fwlink/?LinkId=105634](http://go.microsoft.com/fwlink/?LinkId=105634). Pour obtenir une description particulièrement de l’architecture, classes et les espaces de noms WCF expose des métadonnées, consultez « Présentation de l’Architecture métadonnées » au [http://go.microsoft.com/fwlink/?LinkId=105635](http://go.microsoft.com/fwlink/?LinkId=105635). Vous devez vous familiariser avec le contenu associé à la récupération de métadonnées à partir d’un service WCF dans ces rubriques WCF avant de continuer.  
  
 Les rubriques suivantes contiennent des informations sur la façon d’utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a>À l’aide d’un MetadataExchangeClient pour récupérer des métadonnées  
 Pour utiliser un **MetadataExchangeClient** vous devez spécifier un URI de connexion et une liaison (**SAPBinding**). L’URI de connexion identifie les opérations pour lesquelles vous souhaitez récupérer les métadonnées.  
  
 Les sections suivantes contiennent des informations sur la façon de spécifier l’URI de connexion, les propriétés de liaison important et comment utiliser un **MetadataExchangeClient** pour récupérer des métadonnées à partir de l’adaptateur.  
  
### <a name="the-connection-uri"></a>L’URI de connexion  
 Pour utiliser le **MetadataExchangeClient** vous devez fournir une URI qui spécifie un point de terminaison MEX et l’ou les opérations pour lesquelles vous souhaitez récupérer les métadonnées de connexion SAP. Vous spécifiez un point de terminaison et cible les opérations MEX dans l’URI de connexion de la manière suivante :  
  
-   Vous devez inclure le paramètre « wsdl » dans la chaîne de requête. S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?). Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).  
  
-   Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ». Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’action du message (ID de nœud) d’une opération de cible.  
  
 Par exemple, l’URI de connexion suivant cible l’opération d’envoi pour l’IDOC SALESORDER_CREATEFROMDAT201 et l’IDOC SALESORDER_CREATEFROMDAT202. Les paramètres « wsdl » et « op » sont mis en surbrillance.  
  
```  
"sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"  
```  
  
> [!NOTE]
>  Il n’est pas nécessaire d’inclure des paramètres de l’écouteur dans l’URI de connexion pour les opérations entrantes. L’adaptateur se connecte en tant que client pour récupérer des métadonnées à partir du système SAP.  
  
 Vous pouvez également utiliser l’une des constantes définies au `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` pour vous aider à spécifier les opérations lorsque vous créez un URI de connexion. Cela est illustré dans l’exemple de code à la fin de cette rubrique.  
  
 Comment vous passez cet URI de connexion à la **MetadataExchangeClient** dépend des méthodes surchargées vous permet de créer le client et de récupérer les métadonnées à partir de l’adaptateur.  
  
 Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
### <a name="binding-properties"></a>Propriétés de liaison  
 Lorsque vous créez le **MetadataExchangeClient**, vous devez spécifier un **SAPBinding**.  
  
 Il existe plusieurs propriétés de liaison qui affectent la façon dont l’adaptateur génère des métadonnées. Ces propriétés sont :  
  
-   **GenerateFlatfileCompatibleIdocSchema**  
  
-   **ReceiveIDocFormat**  
  
-   **EnableSafeTyping**  
  
-   **FlatFileSegmentIndicator**  
  
 Vous devez vous assurer que ces propriétés sont définies sur les valeurs requises pour votre application avant d’appeler le **GetMetadata** méthode sur le **MetadataExchangeClient**. Pour plus d’informations sur les propriétés de liaison de l’adaptateur SAP, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise un **MetadataExchangeClient** pour créer une description de service (document WSDL) pour les opérations BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [La récupération des métadonnées par programme à partir de SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)   
 [La récupération des métadonnées dans SAP à l’aide de IMetadataRetrievalContract](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)