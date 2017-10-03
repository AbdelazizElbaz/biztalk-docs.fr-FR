---
title: "Foire aux questions de l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7fe4e0-ddd5-402f-bbbc-b320850eaf3b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d576fa5dae04a43daa54f2d99e7f9c14d1341e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="oracle-e-business-suite-adapter-faqs"></a>Foire aux questions de l’adaptateur Oracle E-Business Suite
Les éléments suivants sont Forum aux questions (FAQ) relatives à [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]. Consultez également [Forum aux questions sur BizTalk Adapter Pack](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md).
  

## <a name="how-can-i-use-the-oracle-e-business-adapter-to-communicate-with-oracle-e-business-suite"></a>Comment puis-je utiliser l’adaptateur Oracle E-Business pour communiquer avec Oracle E-Business Suite ?  
 Vous pouvez utiliser la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour communiquer avec Oracle E-Business Suite en développement d’applications BizTalk, à l’aide du modèle de service WCF ou l’aide du modèle de canal WCF. Pour plus d’informations, consultez [vue d’ensemble de l’adaptateur BizTalk pour Oracle E-Business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e).  
  
## <a name="what-interfaces-are-supported-by-the-oracle-e-business-adapter-for-retrieving-metadata"></a>Les interfaces sont prises en charge par l’adaptateur Oracle E-Business pour récupérer des métadonnées ?  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge deux interfaces de récupération des métadonnées :  
  
-   MetadataExchange fournie par WCF. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir des métadonnées à partir d’Oracle E-Business Suite.  
  
-   IMetadataRetrievalContract fournie par le WCF LOB Adapter SDK, qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
## <a name="how-does-the-adapter-connect-to-oracle-e-business-suite"></a>Comment l’adaptateur effectue la connexion à Oracle E-Business Suite ?  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les composants d’accès aux données Oracle pour Client Oracle. [Prise en charge des systèmes métier](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions de client. Pour vous connecter à Oracle E-Business Suite, les clients de l’adaptateur doivent fournir une chaîne de connexion, [connexion identificateur de ressource uniforme (URI)](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md). En interne, l’adaptateur mappe l’URI de connexion à une chaîne de connexion pour se connecter à la base de données sous-jacente dans Oracle E-Business Suite. Consultez [créer une connexion à Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).  
  
## <a name="does-the-oracle-e-business-adapter-provide-a-secure-way-of-communicating-with-the-oracle-e-business-suite--are-there-any-best-practices-to-ensure-data-security"></a>L’adaptateur Oracle E-Business fournit un moyen sécurisé de communication avec Oracle E-Business Suite ?  Existe-t-il des pratiques recommandées pour garantir la sécurité des données ?  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge Enterprise Single Sign-On (SSO) pour l’authentification sur les connexions qu’il établit avec Oracle E-Business Suite. L’authentification unique utilise une base de données et un secret pour chiffrer et stocker les informations d’identification de l’utilisateur. Il fournit également des services pour mapper les comptes Microsoft Windows aux informations d’identification secondaires qui sont utilisées pour accéder à un système principal.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] nécessite également que vous entrez les informations d’identification de nom d’utilisateur et mot de passe pour se connecter à Oracle E-Business Suite. Ces informations d’identification sont utilisées pour authentifier l’utilisateur et fournir ainsi un niveau d’autorisation pour les connexions. L’adaptateur Oracle E-Business fournit différentes méthodes par le biais duquel vous pouvez fournir ces informations d’identification. Pour plus d’informations sur la façon de fournir des informations d’identification Oracle dans les solutions BizTalk en toute sécurité, consultez [sécurité avec l’adaptateur et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md). Pour plus d’informations sur la façon de fournir des informations d’identification Oracle dans des solutions de programmation en toute sécurité, consultez [sécurisée de programmation avec l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-programming-with-the-oracle-ebs-adapter.md).  
  
 Pour plus d'informations, consultez :  
  
-   Sécurité des données dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [sécuriser vos applications Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md).  
  
-   Meilleures pratiques pour garantir la sécurité des données dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [meilleures pratiques de sécurité](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md).  
  
## <a name="is-there-a-gui-provided-by-the-oracle-e-business-adapter-to-view-and-perform-operations-on-the-artifacts-in-oracle-e-business-suite"></a>Existe-t-il une interface graphique utilisateur fournie par l’adaptateur Oracle E-Business pour afficher et effectuer des opérations sur les artefacts dans Oracle E-Business Suite ?  
 Le complément à consommer de projet d’adaptateur Service BizTalk et l’ajouter adaptateur Service référence Visual Studio plug-in de fournissent une boîte de dialogue où vous pouvez afficher et effectuer des opérations sur les artefacts dans Oracle E-Business Suite. Pour plus d’informations sur l’interface utilisateur fournie par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations d’Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
## <a name="what-are-binding-properties-in-the-oracle-e-business-adapter-where-can-i-find-information-about-all-the-binding-properties-in-the-oracle-e-business-adapter"></a>Propriétés de ce que sont liaison dans l’adaptateur Oracle E-Business ? Où puis-je trouver plus d’informations sur les propriétés de liaison dans l’adaptateur Oracle E-Business ?  
 Les clients de carte peuvent utiliser des propriétés de liaison dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour configurer et contrôler le comportement de l’adaptateur. Pour plus d’informations sur les propriétés de liaison exposés dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [fonctionne avec les propriétés de liaison](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## <a name="what-are-inbound-and-outbound-operations-in-the-oracle-e-business-adapter"></a>Quelles sont les opérations entrantes et sortantes dans l’adaptateur Oracle E-Business ?  
 Dans les opérations entrantes, le système métier (Oracle E-Business Suite) est le client et les clients de l’adaptateur sont le service, dans laquelle les transactions provenant d’Oracle E-Business Suite. Par exemple, les opérations d’interrogation et de Notification.  
  
 Dans les opérations sortantes, les clients de l’adaptateur sont le client et le système métier (Oracle E-Business Suite) devient le service, dans laquelle les transactions sont issus les clients de la carte. Par exemple, le Insert, Select, Update et opération Delete sur les tables, l’opération sur les fonctions et procédures stockées et des opérations composites Interface.  
  
## <a name="where-can-i-find-information-about-the-oracle-data-types-that-are-supported-in-the-oracle-e-business-adapter"></a>Où puis-je trouver plus d’informations sur les types de données Oracle qui sont pris en charge dans l’adaptateur Oracle E-Business ?  
 Pour plus d’informations sur les types de données Oracle pris en charge dans les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [des Types de données Oracle base](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md).  
  
## <a name="what-is-applications-context-how-can-i-set-applications-context-for-various-oracle-artifacts-in-the-oracle-e-business-adapter"></a>Qu’est le contexte des applications ? Comment puis-je définir contexte des applications pour différents artefacts Oracle dans l’adaptateur Oracle E-Business ?  
 Pour plus d’informations sur le contexte des applications et comment la définir le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="which-approach-biztalk-server-wcf-service-model-or-wcf-channel-model-can-i-use-to-perform-various-operations-using-the-oracle-e-business-adapter"></a>Quelle approche (BizTalk Server, modèle de service WCF ou modèle de canal WCF) puis-je utiliser pour effectuer diverses opérations à l’aide de l’adaptateur Oracle E-Business ?  
 Pour plus d’informations sur l’approche, vous pouvez utiliser pour effectuer diverses opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [développer vos applications Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
[Forum aux questions pour le Pack d’adaptateurs BizTalk](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)