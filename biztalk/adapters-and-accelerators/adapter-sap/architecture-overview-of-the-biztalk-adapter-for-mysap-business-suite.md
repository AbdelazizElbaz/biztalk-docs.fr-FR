---
title: "Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture of SAP adapter
- adapters, architecture
ms.assetid: 1b45edb0-2476-427b-b6cd-41e38ed815e0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d571cdd3beea2bc9a57ec7ad15f865e7ef51e53a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite"></a>Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] implémente un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée, qui contient un élément de liaison de transport personnalisé unique qui permet la communication avec un système SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est encapsulée par la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] runtime et est exposé à des applications via le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] architecture de canal. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] communique avec le système SAP via la version 64 bits ou 32 bits du SDK RFC Unicode SAP (librfc32u.dll). 

La figure suivante illustre l’architecture de bout en bout pour les solutions sont développées à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 ![Fin SAP &#45; à &#45; Architecture de fin](../../adapters-and-accelerators/adapter-sap/media/9ba0c31f-90df-444d-8192-42743c893d51.gif "9ba0c31f-90df-444d-8192-42743c893d51")  
  
## <a name="consuming-the-adapter"></a>Utilisation de l’adaptateur  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose le système SAP comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service pour les applications clientes. Les applications clientes échangent des messages SOAP avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canaux pour effectuer des opérations et accéder aux données sur le système SAP. L’illustration précédente montre quatre façons dans lequel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peuvent être utilisés.  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] application qui effectue des opérations sur le système SAP à l’aide de canaux le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal pour échanger SOAP des messages directement avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur le développement de solutions pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à l’aide de [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] programmation de modèle de canal, consultez [développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).  
  
-   Via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service d’application de modèle qui appelle des méthodes sur un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client pour effectuer des opérations sur le système SAP. A [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client modélise les opérations exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en tant que méthodes de .NET. Vous pouvez utiliser la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ou l’outil svcutil.exe pour créer un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] classe de client à partir des métadonnées exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] programmation de modèle de service et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
-   Via un port BizTalk qui est configuré pour utiliser l’adaptateur BizTalk WCF-Custom avec la liaison SAP configurés en tant que la liaison pour le type de transport WCF-Custom dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application. L’adaptateur BizTalk WCF-Custom permet la communication entre un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application et un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service. Prend en charge de l’adaptateur BizTalk WCF-Custom personnalisé [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] type, qui vous permet de configurer les liaisons grâce à son WCF-Custom du transport [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison exposé au système de configuration en tant que la liaison utilisée par l’adaptateur BizTalk WCF-Custom. Pour plus d’informations sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solutions, consultez [BizTalk de développer des applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md). Transactions BizTalk sont pris en charge par l’élément de liaison de canal de superposées BizTalk qui peut être chargée en définissant une propriété de liaison sur la liaison de SAP.  
  
-   Grâce à un service Web hébergé par IIS. Dans ce scénario, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est exposée via un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] proxy de Service, qui est hébergé dans IIS à l’aide d’un de la norme [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons HTTP.  
  
-   Via le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] s’exécute sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et fournit une interface ADO.NET à un système SAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et la bibliothèque SAP RFC se trouvent toujours in-process avec l’application ou le service qui utilise l’adaptateur.  
  
## <a name="sap-adapter-and-wcf"></a>WCF et l’adaptateur SAP  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]présente un modèle de programmation basé sur l’échange de messages SOAP sur les canaux entre les clients et services. Ces messages sont envoyés entre les points de terminaison exposés par un client et un service de communication.  
  
 Un point de terminaison se compose d’un *adresse de point de terminaison* qui spécifie l’emplacement de réception des messages, un *liaison* qui spécifie les protocoles de communication utilisés pour échanger des messages et un *contrat* qui spécifie les types d’opérations et les données exposées par le point de terminaison. Une liaison se compose d’un ou plusieurs éléments de liaison s’empilent autres pour définir la manière dont les messages sont échangés avec le point de terminaison.  
  
 Au minimum, une liaison doit spécifier le transport et encodage utilisé pour échanger des messages avec le point de terminaison. Échange de messages entre points de terminaison se produit sur une pile de canaux qui se compose d’un ou plusieurs canaux. Chaque canal est une implémentation concrète de l’un des éléments de liaison dans la liaison configurée pour le point de terminaison.  
  
Le [documentation WCF](http://go.microsoft.com/fwlink/?LinkID=196850) comprend plus de détails sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]et le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de programmation.  
  
 Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaison personnalisée, la liaison de SAP (**Microsoft.Adapters.SAP.SAPBinding**). Par défaut, cette liaison contient un élément de liaison de transport personnalisé unique, l’élément de liaison de l’adaptateur SAP (**Microsoft.Adapters.SAP.SAPAdapter**), ce qui permet des opérations sur un système SAP. Lorsque vous utilisez la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez définir le **EnableBizTalkCompatibilityMode** liaison de propriété pour charger un élément de liaison personnalisée, le BizTalk en couche canal élément de liaison sur la liaison de l’adaptateur SAP Élément. L’élément de liaison BizTalk en couche canal est implémentée en interne par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et n’est pas exposée à l’extérieur de la liaison de SAP.  
  
 **Microsoft.Adapters.SAP.SAPBinding** (la liaison de SAP) et **Microsoft.Adapters.SAP.SAPAdapter** (la SAP adaptateur élément de liaison) sont des classes publiques et sont également exposées au système de configuration. Étant donné que l’élément de liaison de l’adaptateur SAP est exposée publiquement, vous pouvez créer vos propres [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] liaisons permettant d’étendre les fonctionnalités de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Par exemple, vous pouvez implémenter une liaison personnalisée pour prendre en charge Enterprise Single Sign-On (SSO) dans un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] canal ou un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service la solution de programmation de modèle, à des opérations d’agrégation de la base de données en une seule opération multifonction, ou pour effectuer la transformation de schéma entre les opérations implémentées par une application personnalisée et les opérations sur le système SAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et s’exécute sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une infrastructure de framework et les outils logiciels qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] tire parti pour fournir un ensemble complet de fonctionnalités aux utilisateurs et aux clients de la carte.  

## <a name="sap-adapter-and-the-wcf-lob-adapter-sdk"></a>Adaptateur SAP et WCF LOB Adapter SDK
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] implémente un ensemble de composants qui tirent parti des fonctionnalités fournies par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et fournir une connectivité au système SAP via la bibliothèque de kit de développement logiciel RFC SAP Unicode (librfc32u.dll).  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sert de la couche du logiciel par le biais duquel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] interagissant avec [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)], et le SDK RFC sert de la couche par le biais duquel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] interfaces avec le système SAP. L’illustration suivante montre les relations entre les composants internes de le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et entre ces composants et le SDK RFC.  
  
 ![La relation entre composants d’adaptateur internes](../../adapters-and-accelerators/adapter-sap/media/10f97b95-4e82-4592-ba07-0f58478305c2.gif "10f97b95-4e82-4592-ba07-0f58478305c2")  
  
## <a name="connection-to-the-sap-system"></a>Connexion au système SAP  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte avec le système SAP via la bibliothèque de kit de développement logiciel RFC SAP Unicode (librfc32u.dll). Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge 32 bits et les versions 64 bits du SDK RFC SAP. Le Kit de développement logiciel RFC SAP permet aux programmes externes appeler des fonctions ABAP sur un système SAP.  
  
 Vous établissez une connexion à un système SAP en fournissant un URI de connexion à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les types de connexions à un système SAP suivants :  
  
-   Une connexion basée sur l’hôte d’application (A), dans lequel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte directement à un serveur d’applications SAP.  
  
-   Un équilibrage de la connexion (B), dans laquelle le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte à un serveur de messagerie de SAP.  
  
-   Une destination connexion (D), dans lequel la connexion au système SAP est spécifiée par une destination dans le fichier de configuration saprfc.ini. A, B et R connexions de type sont pris en charge.  
  
-   Une connexion de port d’écoute (R), dans lequel l’adaptateur reçoit RFC, tRFC et IDOC via une Destination RFC sur le système SAP qui est spécifié par un hôte de l’écouteur, un service de passerelle du port d’écoute et un ID de programme écouteur, soit directement dans l’URI de connexion basée sur une R destination dans le fichier de configuration saprfc.ini.  
  
 Pour plus d’informations sur le fichier saprfc.ini, consultez « le SAPRFC. Ini » dans le [documentation SAP](https://help.sap.com/doc/PRODUCTION/saphelp_nwpi711/7.1.1/en-US/48/c4168eca64581de10000000a42189c/frameset.htm).  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte à un système SAP, consultez [créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)