---
title: "Présentation de l’architecture de l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture of Siebel adapter
- Siebel COM Data Control
- adapters, architecture
ms.assetid: b048937f-207b-4c64-8837-7bfeecedfa03
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d78bf2104d5383f3c8aa34984a5781fa8f4dbfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-siebel-ebusiness-applications"></a>Présentation de l’architecture de l’adaptateur BizTalk pour Siebel eBusiness Applications
Décrit l’architecture des solutions de bout en bout qui utilisent la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour fonctionner sur un système Siebel, ainsi que l’architecture interne de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 Comprendre les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] architecture peut vous aider à :  
  
-   Comprendre la relation entre la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].  
  
-   Comprendre les limites de sécurité, afin que vous pouvez améliorer la sécurité des données dans votre solution.  
  
-   Comprendre les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] propriétés de liaison.  
  
-   Résoudre les problèmes d’installation.  

## <a name="adapter-architecture-overview"></a>Présentation de l’architecture adaptateur
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et s’exécute sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] moment de l’exécution. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure de framework et les outils logiciels qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] emploie pour fournir un ensemble complet de fonctionnalités aux utilisateurs et aux clients de la carte.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est une liaison WCF personnalisée. Cette liaison contient un élément de liaison de transport personnalisé unique qui permet la communication avec un système Siebel. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est encapsulée par la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] temps d’exécution et est exposé à des applications via le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal.  
  
## <a name="siebel-com-data-control"></a>Contrôle de données Siebel COM  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] se connecte avec le système Siebel via la bibliothèque de contrôle de données Siebel COM (sstchca.dll) et la bibliothèque Microsoft.Adapters.Siebel.SiebelBusinessObjectInterface.dll. Le contrôle de données Siebel COM est un composant du Client Web Siebel. 
  
 Les interfaces de contrôle de données Siebel COM permettent à un client externe, comme le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour se connecter et de communiquer avec un gestionnaire d’objets Siebel Application sur un serveur d’entreprise Siebel. Le Gestionnaire d’objets Siebel et serveur d’entreprise Siebel ainsi que les autres paramètres de connexion sont spécifiés dans le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] URI de connexion. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion du système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
 La figure suivante illustre l’architecture de bout en bout pour les solutions sont développées à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 ![Bout Siebel &#45; à &#45; Architecture de fin](../../adapters-and-accelerators/adapter-siebel/media/1ae1955e-b7d7-44a0-80c1-1e835edab356.gif "1ae1955e-b7d7-44a0-80c1-1e835edab356")  
  
## <a name="consuming-the-adapter"></a>Utilisation de l’adaptateur  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose le système Siebel en tant qu’un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service pour les applications clientes. Pour effectuer des opérations et accéder aux données sur le système Siebel, les applications clientes échangent des messages SOAP avec le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] via [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux. L’illustration précédente montre quatre façons dans lequel le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peuvent être utilisés.  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]application du modèle de canal. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de canal effectue des opérations sur le système Siebel à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal pour échanger SOAP des messages directement avec le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour plus d’informations sur le développement de solutions pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal, consultez [applications SQL de développer à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application du modèle de service. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application de modèle de service appelle des méthodes sur un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour effectuer des opérations sur le système Siebel. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client modélise les opérations exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] en tant que méthodes de .NET. Vous pouvez utiliser la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client à partir des métadonnées exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Pour plus d’informations sur la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [applications SQL de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).  
  
-   Via un BizTalk emplacement de réception ou port d’envoi qui est configuré pour utiliser l’adaptateur Microsoft BizTalk WCF-Custom. L’adaptateur WCF-Custom permet d’utiliser [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fonctionnalités d’extensibilité. À l’aide de l’adaptateur WCF-Custom, vous pouvez sélectionner et configurer la liaison de Siebel et le comportement de l’emplacement de réception ou port d’envoi. Transactions BizTalk sont pris en charge par le BizTalk en couche canal élément de liaison qui peut être chargé en définissant une propriété de liaison sur la liaison de Siebel. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solutions, consultez [développer vos Applications BizTalk](../../core/develop-your-biztalk-applications.md).
  
-   Grâce à un service Web hébergé par IIS. Dans ce scénario, un proxy de service WCF généré à l’aide de l’adaptateur est hébergé dans IIS à l’aide de la liaison de Http de WCF standard. Cela expose le contrat de service comme service Web aux utilisateurs externes. IIS héberge automatiquement l’adaptateur au moment de l’exécution, ce qui, à son tour, communique avec le système Siebel.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et le contrôle de données COM Siebel bibliothèque sont toujours hébergé in-process avec l’application ou le service qui utilise l’adaptateur.  
  
## <a name="siebel-adapter-and-wcf"></a>L’adaptateur Siebel et WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]présente un modèle de programmation basé sur l’échange de messages SOAP sur les canaux entre les clients et services. Ces messages sont envoyés entre les points de terminaison exposés par un client et un service de communication. Un point de terminaison se compose de :  
  
-   Un *adresse de point de terminaison*, qui spécifie l’emplacement auquel les messages sont reçus.  
  
-   A *liaison*, qui spécifie les protocoles de communication qui sont utilisés pour échanger des messages.  
  
-   A *contrat*, qui spécifie les types d’opérations et les données qui sont exposées par le point de terminaison.  
  
 Une liaison se compose d’un ou plusieurs éléments de liaison s’empilent autres pour définir la manière dont les messages sont échangés avec le point de terminaison. Au minimum, une liaison doit spécifier le transport et encodage qui sont utilisés pour échanger des messages avec le point de terminaison. Échange de messages entre points de terminaison se produit sur une pile de canaux qui se compose d’un ou plusieurs canaux. Chaque canal est une implémentation concrète de l’un des éléments de liaison dans la liaison est configurée pour le point de terminaison. Le [documentation WCF](http://go.microsoft.com/fwlink/?LinkID=196850) comprend plus de détails sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de programmation.  
  
 Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison personnalisée, la liaison de Siebel (**Microsoft.Adapters.Siebel.SiebelBinding**). Par défaut, cette liaison contient un élément de liaison de transport personnalisé unique, l’élément de liaison de l’adaptateur Siebel (**Microsoft.Adapters.Siebel.SiebelAdapter**), ce qui permet des opérations sur un système Siebel. Lorsque vous utilisez le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], que vous pouvez définir le **EnableBizTalkCompatibilityMode** liaison de propriété pour charger un élément de liaison personnalisé : l’élément de liaison BizTalk en couche canal : au-dessus de l’adaptateur Siebel Élément de liaison. L’élément de liaison BizTalk en couche canal est implémentée en interne par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et n’est pas exposée à l’extérieur de la liaison de Siebel.  
  
 **Microsoft.Adapters.Siebel.SiebelBinding** (la liaison Siebel) et **Microsoft.Adapters.Siebel.SiebelAdapter** (le Siebel adaptateur élément de liaison) sont des classes publiques et sont également exposées à la configuration système. Étant donné que l’élément de liaison de l’adaptateur Siebel est exposée publiquement, vous pouvez créer vos propres [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons permettant d’étendre les fonctionnalités de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Par exemple, vous pouvez implémenter une liaison personnalisée pour prendre en charge Enterprise Single Sign-on (SSO) dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] de canal ou de programmation du modèle de service. Les raisons de cette opération sont à :  
  
-   Opérations d’agrégation de la base de données en une seule opération multifonction.  
  
-   Effectuer la transformation de schéma entre les opérations qui sont implémentées par une application personnalisée et les opérations sur le système Siebel.  

## <a name="siebel-adapter-and-wcf-lob-adapter-sdk"></a>L’adaptateur Siebel et WCF LOB Adapter SDK

Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] implémente un ensemble de composants qui :  
  
-   Tirer parti des fonctionnalités fournies par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].  
  
-   Fournir la connectivité au système Siebel via la bibliothèque de contrôle de données Siebel COM (sstchca.dll).  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est la couche logicielle par le biais duquel le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] interfaces avec WCF ; Contrôle de données Siebel COM est la couche par le biais duquel le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] interfaces avec le système Siebel. L’illustration suivante montre les relations entre les composants internes de le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et entre ces composants et le contrôle de données COM Siebel.  
  
 ![Architecture interne de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/media/e4accea7-86b2-4f2a-937a-edff7e1100ec.gif "e4accea7-86b2-4f2a-937a-edff7e1100ec")
   
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)  
 [Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)