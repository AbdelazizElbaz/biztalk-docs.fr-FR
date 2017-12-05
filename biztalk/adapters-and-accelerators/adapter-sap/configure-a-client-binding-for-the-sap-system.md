---
title: "Configurer un client de liaison pour le système SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxy programming, creating a proxy
- creating a proxy
- how to, create a proxy
ms.assetid: bceef132-29ff-4207-a37d-bf94fab484dd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e9a4f84dbf98a17b2c1a918e30ab85b8e86c13
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configure-a-client-binding-for-the-sap-system"></a>Configurer un client de liaison pour le système SAP
Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]. Pour plus d’informations sur la génération de la classe d’assistance et de code de client WCF pour les opérations qui les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
 Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison. L’adresse de point de terminaison doit contenir un URI de connexion SAP valide, et la liaison doit être une instance d’une liaison de SAP (**SAPBinding**). Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
 Vous pouvez spécifier la liaison de SAP et de l’adresse de point de terminaison dans votre code ou dans un fichier de configuration. Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet. Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté au système SAP avec la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a>Spécification de la liaison et l’adresse de point de terminaison dans le Code  
 Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans le code. Il est conseillé de spécifier les informations d’identification du système SAP à l’aide de la **ClientCredentials** propriété du client WCF, plutôt que dans l’URI fourni pour l’adresse de point de terminaison de connexion.  
  
```  
// A WCF client that targets an RFC is created  
// by using a binding object and endpoint address  
SAPBinding sapBinding = new SAPBinding();  
EndpointAddress sapAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00");  
  
RfcClient rfcClient = new RfcClient(sapBinding, sapAddress);  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a>Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration  
 Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.  
  
```  
// A WCF client that targets an RFC is created  
// by specifying the client endpoint information in app.config  
RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
 Le code XML suivant montre le fichier de configuration créé pour la table EMP par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" receiveIdocFormat="Typed"  
                    generateFlatFileCompatibleIdocSchema="true" maxConnectionsPerSystem="50"  
                    enableConnectionPooling="true" idleConnectionTimeout="00:15:00"  
                    flatFileSegmentIndicator="SegmentDefinition" enablePerformanceCounters="false"  
                    autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false" padReceivedIdocWithSpaces="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="Rfc"  
                name="SAPBinding_Rfc" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration. Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et les artefacts du système SAP cible (par exemple, Rfc et Trfc) ; par exemple, « SAPBinding_Rfc ». Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion. Ces entrées de configuration de liaison seront nommées de la manière suivante : SAPBinding1, SAPBinding2, et ainsi de suite. Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.  
  
> [!IMPORTANT]
>  Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence les artefacts SAP différentes du même type (par exemple, RFC, TRFC et IDOC) en tant qu’opérations différentes du même contrat de service. Par exemple, deux RFC différents, RFC_EXAMPLE_A et RFC_EXAMPLE_B, seront à la fois visible sous le même contrat de service (« Rfc »). Cela signifie que les deux documents RFC seront appelés par la même classe de client WCF, **RfcClient**, et que les paramètres pour les deux documents RFC seront déclarés dans le même espace de noms. Par conséquent, vous devez générer le client WCF pour les deux documents RFC pendant la même [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] session (connexion) pour éviter de rencontrer une collision d’espace de noms lorsque vous générez votre solution.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [Générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)   
 [Créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)