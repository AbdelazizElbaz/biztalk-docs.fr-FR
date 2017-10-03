---
title: "L’adaptateur SQL FAQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25369e6b-d1f2-4abc-9ffc-4cb9aef1d3fb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dee4b402e548f55dd8eab4583215d879c98186b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-adapter-faqs"></a>Forum aux questions sur l’adaptateur SQL
Les éléments suivants sont Forum aux questions (FAQ) relatives à [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] et [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] en général.  
  
## <a name="how-can-i-use-the-sql-adapter-to-communicate-with-the-sql-server-database"></a>Comment puis-je utiliser l’adaptateur SQL pour communiquer avec la base de données SQL Server ?  
 Vous pouvez utiliser l’adaptateur SQL pour communiquer avec la base de données SQL Server en développement d’applications BizTalk, à l’aide du modèle de service WCF ou l’aide du modèle de canal WCF. Pour plus d’informations, consultez [vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md).  
  
## <a name="what-interfaces-are-supported-by-the-sql-adapter-for-retrieving-metadata"></a>Les interfaces sont prises en charge par l’adaptateur SQL pour la récupération des métadonnées ?  
 L’adaptateur SQL prend en charge deux interfaces de récupération des métadonnées :  
  
-   MetadataExchange fournie par WCF. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir des métadonnées à partir de la base de données SQL Server.  
  
-   IMetadataRetrievalContract fournie par le WCF LOB Adapter SDK, qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
## <a name="how-does-the-sql-adapter-support-high-availability-of-data"></a>Comment l’adaptateur SQL prend en charge une haute disponibilité des données ?  
 Lors de la spécification du [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md) pour vous connecter à une base de données SQL Server, l’adaptateur SQL vous permet de spécifier le nom de base de données de basculement SQL Server pour se connecter à if de la base de données SQL Server principal n’est pas disponible. La base de données de basculement SQL Server est spécifié à l’aide d’un paramètre facultatif, FailoverPartner, dans l’URI de connexion.  
  
## <a name="can-i-migrate-biztalk-projects-created-using-the-previous-version-of-the-sql-adapter-to-use-the-wcf-based-sql-adapter-how"></a>Puis-je migrer des projets BizTalk créés à l’aide de la version précédente de l’adaptateur SQL pour utiliser l’adaptateur SQL de basé sur WCF ? Comment ?  
 Oui. Pour connaître les étapes de migration des projets BizTalk créés à l’aide de la version précédente de l’adaptateur SQL pour utiliser l’adaptateur SQL de basé sur WCF, voir [didacticiels de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md).  
  
## <a name="does-the-sql-adapter-provide-a-secure-way-of-communicating-with-the-sql-server-database--are-there-any-best-practices-to-ensure-security-of-data"></a>L’adaptateur SQL fournit un moyen sécurisé de communiquer avec la base de données SQL Server ?  Existe-t-il des pratiques recommandées pour garantir la sécurité des données ?  
 L’adaptateur SQL prend en charge Enterprise Single Sign-On (SSO) et la sécurité intégrée pour l’authentification sur les connexions qu’il établit avec la base de données SQL Server. Avec l’authentification unique, les informations d’identification sont chiffrées et stockées dans le Registre. Le système utilise ces informations d’identification pour déterminer l’accès au lieu de demander l’utilisateur à entrer les où ils peuvent être détectés par les acteurs non autorisés. La sécurité intégrée utilise les informations d’identification de l’utilisateur connecté pour accéder au serveur SQL. Cela évite également aux utilisateurs d’entrer des informations d’identification. L’administrateur de base de données doit configurer SQL pour accepter les informations d’identification des utilisateurs pour la sécurité intégrée fonctionner correctement.  
  
 L’adaptateur SQL ne permet pas d’entrer les informations d’identification de l’utilisateur dans l’URI de connexion pour la base de données SQL Server lors de l’utilisation de l’ajouter adaptateur Service référence Visual Studio du plug-in et consommer adaptateur Service BizTalk Project Add-in pour empêcher informations d’identification d’apparaître en texte clair. En outre, le mot de passe n’est pas écrite pour le fichier de configuration (généré par l’ajouter adaptateur Service référence Visual Studio plug-in) et le fichier de liaison (générés par le complément à consommer de projet d’adaptateur Service BizTalk).  
  
 Pour plus d’informations sur :  
  
-   Sécurité des données dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).  
  
-   Meilleures pratiques pour garantir la sécurité des données dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [meilleures pratiques pour sécuriser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md).  
  
## <a name="is-there-a-gui-provided-by-the-sql-adapter-to-view-and-perform-operations-on-the-artifacts-in-my-underlying-sql-server-database"></a>Existe-t-il une interface graphique utilisateur fournie par l’adaptateur SQL pour afficher et effectuer des opérations sur les artefacts dans ma base de données SQL Server sous-jacent ?  
 Le complément à consommer de projet d’adaptateur Service BizTalk et l’ajouter adaptateur Service référence Visual Studio plug-in de fournissent une boîte de dialogue où vous pouvez afficher et effectuer des opérations sur les artefacts dans la base de données SQL Server. Pour plus d’informations sur l’interface utilisateur fournie par l’adaptateur SQL, consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md).  
  
## <a name="what-are-binding-properties-in-the-sql-adapter-where-can-i-find-information-about-all-the-binding-properties-in-sql-adapter"></a>Propriétés de ce que sont liaison dans l’adaptateur SQL ? Où puis-je trouver plus d’informations sur les propriétés de liaison dans l’adaptateur SQL ?  
 Les clients de carte peuvent utiliser des propriétés de liaison dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour configurer et contrôler le comportement de l’adaptateur. Pour plus d’informations sur les propriétés de liaison exposés dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
## <a name="what-is-msdtc-do-i-need-to-bother-about-it-before-using-sql-adapter"></a>Nouveautés MSDTC Je dois il vous souciez avant d’utiliser l’adaptateur SQL  
 MSDTC acronyme de Microsoft Distributed Transaction Coordinator. MSDTC coordonne les transactions différentes entre plusieurs gestionnaires de ressources tels que les bases de données, les systèmes de fichiers et les files d’attente. Pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez activer MSDTC. Pour plus d’informations sur la configuration de MSDTC, consultez [configurer le MSDTC sur un client SQL Server et de la carte](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md).  
  
## <a name="where-can-i-find-information-about-the-sql-server-data-types-that-are-supported-in-the-sql-adapter"></a>Où puis-je trouver plus d’informations sur les types de données SQL Server sont prises en charge dans l’adaptateur SQL ?  
 Pour connaître les types de données SQL Server sont prises en charge dans l’adaptateur SQL, consultez [base SQL Server Data Types](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md).  
  
## <a name="which-approach-biztalk-server-wcf-service-model-or-wcf-channel-model-can-i-use-to-perform-various-operations-using-the-sql-adapter"></a>Quelle approche (BizTalk Server, modèle de service WCF ou modèle de canal WCF) puis-je utiliser pour effectuer diverses opérations à l’aide de l’adaptateur SQL ?  
 Pour connaître l’approche que vous pouvez utiliser pour effectuer diverses opérations à l’aide de l’adaptateur SQL, consultez [développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md).  
  
 
## <a name="see-also"></a>Voir aussi  
 [Forum aux Questions](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)
 