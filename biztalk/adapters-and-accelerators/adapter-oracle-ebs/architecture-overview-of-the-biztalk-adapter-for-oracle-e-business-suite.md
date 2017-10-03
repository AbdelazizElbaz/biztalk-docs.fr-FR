---
title: "Présentation de l’architecture de l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f840ff23-4d68-4bd3-b115-aa87bc4c99f2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39c2353448a05747d94ae3128968182f428739ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-oracle-e-business-suite"></a>Présentation de l’architecture de l’adaptateur BizTalk pour Oracle E-Business Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Cette liaison contient un élément de liaison de transport personnalisé unique qui permet la communication avec un Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est encapsulée par la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] runtime et est exposé à des applications via le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] communique avec Oracle E-Business Suite via le fournisseur de données Oracle pour .NET (ODP.NET) et le client Oracle, qui font partie d’Oracle données accès composants (ODAC) pour Windows.  
  
 La figure suivante illustre l’architecture de bout en bout pour les solutions sont développées à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 ![Diagramme d’architecture de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/967bc4a5-852b-479e-8ef0-941773f5991f.gif "967bc4a5-852b-479e-8ef0-941773f5991f")  
  
## <a name="consuming-the-adapter"></a>Utilisation de l’adaptateur  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose Oracle E-Business Suite comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service pour les applications clientes. Pour effectuer des opérations et accéder aux données d’Oracle E-Business Suite, les applications clientes échangent des messages SOAP avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] via [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux. L’illustration précédente montre quatre façons dans lequel le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peuvent être utilisés. Celles-ci sont les suivantes :   
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de canal. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de canal effectue des opérations sur Oracle E-Business Suite à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal pour échanger SOAP des messages directement avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de service. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de service appelle des méthodes sur un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour effectuer des opérations sur Oracle E-Business Suite. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client modélise les opérations exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en tant que méthodes de .NET. Vous pouvez utiliser la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ou le WCF Service Model Metadata Utility Tool (svcutil.exe) pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client à partir des métadonnées exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   Via un BizTalk emplacement de réception ou port d’envoi qui est configuré pour utiliser l’adaptateur Microsoft BizTalk WCF-Custom. L’adaptateur WCF-Custom permet d’utiliser [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fonctionnalités d’extensibilité. À l’aide de l’adaptateur WCF-Custom, vous pouvez sélectionner et configurer la liaison de Oracle eBusiness Suite et le comportement de l’emplacement de réception ou port d’envoi. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solutions, consultez [BizTalk de développer les applications à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md).  
  
-   Grâce à un service Web hébergé par IIS. Dans ce scénario, un proxy de service WCF généré à l’aide de l’adaptateur est hébergé dans IIS à l’aide de la liaison WCF basicHttpBinding. Cela expose le contrat de service comme service Web aux utilisateurs externes. IIS héberge automatiquement l’adaptateur lors de l’exécution, ce qui, à son tour, communique avec Oracle E-Business Suite.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et ODAC se trouvent toujours in-process avec l’application ou le service qui utilise l’adaptateur.  
  
## <a name="oracle-ebs-adapter-and-wcf"></a>Adaptateur Oracle eBusiness Suite et WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]présente un modèle de programmation basé sur l’échange de messages SOAP sur les canaux entre les clients et services. Ces messages sont envoyés entre les points de terminaison exposés par un client et un service de communication. Un point de terminaison se compose de :  
  
-   Un *adresse de point de terminaison*, qui spécifie l’emplacement de réception des messages  
  
-   A *liaison*, qui spécifie les protocoles de communication utilisés pour échanger des messages  
  
-   A *contrat*, qui spécifie les types d’opérations et les données exposées par le point de terminaison.  
  
 Une liaison se compose d’un ou plusieurs éléments de liaison s’empilent autres pour définir la manière dont les messages sont échangés avec le point de terminaison. Au minimum, une liaison doit spécifier le transport et encodage qui sont utilisés pour échanger des messages avec le point de terminaison. Échange de messages entre points de terminaison se produit sur une pile de canaux qui se compose d’un ou plusieurs canaux. Chaque canal est une implémentation concrète de l’un des éléments de liaison dans la liaison configurée pour le point de terminaison. Le [documentation WCF](http://go.microsoft.com/fwlink/?LinkID=196850) comprend plus de détails sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de programmation.  
  
 Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison personnalisée, la liaison de Suite Oracle E-Business (**Microsoft.Adapters.OracleEBS.OracleEBSBinding**). Par défaut, cette liaison contient un élément de liaison de transport personnalisé unique, l’élément de liaison de l’adaptateur Oracle E-Business Suite (**Microsoft.Adapters.OracleEBS.OracleEBSAdapter**), ce qui permet des opérations sur Oracle E-Business Suite.  
  
 **Microsoft.Adapters.OracleEBS.OracleEBSBinding** (le Oracle E-Business Suite liaison) et **Microsoft.Adapters.OracleEBS.OracleEBSAdapter** (l’Oracle E-Business Suite adaptateur élément de liaison) sont publics classes et sont également exposées au système de configuration. Étant donné que l’élément de liaison de l’adaptateur Oracle E-Business Suite est exposée publiquement, vous pouvez créer vos propres [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons permettant d’étendre les fonctionnalités de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Par exemple, vous pouvez implémenter une liaison personnalisée pour prendre en charge Enterprise Single Sign-on (SSO) dans un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de canal ou de service. Les raisons de cette opération serait d’opérations d’agrégation de la base de données en une seule opération multifonction ou pour effectuer la transformation de schéma entre les opérations implémentées par une application personnalisée et les opérations sur Oracle E-Business Suite.  

## <a name="oracle-ebs-adapter-and-the-wcf-lob-sdk"></a>Adaptateur Oracle eBusiness Suite et le Kit de développement WCF LOB
 
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]et s’exécute sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime. 


Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure de framework et les outils logiciels qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise pour fournir un ensemble complet de fonctionnalités aux utilisateurs et aux clients de la carte.  Il sert également de la couche du logiciel par le biais duquel le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] interagissant avec le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. ODP.NET sert de la couche par le biais duquel le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] interfaces avec la base de données Oracle. 

L’illustration suivante montre les relations entre les composants internes de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]et ODP.NET :  
  
 ![Oracle E &#45; Architecture interne de l’adaptateur métier](../../adapters-and-accelerators/adapter-oracle-ebs/media/bts-oracleebs-architecture-internalc.gif "bts_OracleEBS_Architecture_Internalc")  
  
## <a name="odpnet"></a>ODP.NET  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] se connecte avec Oracle E-Business Suite via le ODP.NET et le client Oracle. Deux de ces composants font partie d’Oracle données accès composants (ODAC).  
  
 ODP.NET implémente un fournisseur de données pour Oracle E-Business Suite est cohérente avec l’interface ADO.NET. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les classes exposées par ODP.NET pour fonctionner sur Oracle E-Business Suite.  
  
 Le client Oracle fournit la connectivité à Oracle E-Business Suite. Vous établissez une connexion à un Oracle E-Business Suite en fournissant un URI de connexion à la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Vous pouvez spécifier l’URI de connexion de deux manières :  
  
-   **À l’aide de tnsnames.ora**. Dans cette approche, l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau spécifié dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion telles que le nom du serveur, nom du service, numéro de port, etc. à partir de l’entrée de nom de service réseau dans le fichier. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
-   **Sans utiliser de tnsnames.ora**. Dans cette approche, les clients de l’adaptateur spécifient les paramètres de connexion directement dans l’URI de connexion. Cela ne nécessite pas le nom de service réseau d’être présents dans le fichier tnsnames.ora sur l’ordinateur client. Cette approche ne nécessite pas le fichier tnsnames.ora se trouvent sur l’ordinateur client.  
  
 Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).  
  
## <a name="next"></a>Suivant
[Sécuriser vos applications Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)