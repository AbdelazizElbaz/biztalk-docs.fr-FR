---
title: Forum aux questions sur BizTalk Adapter Pack | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cdaf09a-50fe-4f30-bd9d-60e316351846
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c9d6e28a5839bafb135285b90d8174a3fa18f49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)
Forum aux questions (FAQ) sur le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
 

## <a name="general-questions"></a>Questions générales

### <a name="what-are-the-supported-biztalk-versions-for-the-biztalk-adapter-pack"></a>Quelles sont les versions prises en charge de BizTalk pour BizTalk Adapter Pack ?  
 Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] est inclus avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Installer la version fournie avec votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version. L’installation de le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] d’une autre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version n’est pas prise en charge. 
  
### <a name="in-which-user-context-should-the-setup-be-run"></a>Dans le contexte utilisateur du programme d’installation doit être exécuté ?  
Exécutez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] le programme d’installation à l’aide d’un compte qui est membre du groupe Administrateurs local et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs. 

Liens : [de sécurité minimales](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)

### <a name="how-do-i-get-started-using-the-adapter"></a>Comment commencer à l’aide de la carte ?  
Si vous êtes familiarisé avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], puis installez [BAP 2016](../adapters-and-accelerators/install-the-biztalk-adapter-pack-2016.md) ou [BAP 2013 R2 et 2013](../adapters-and-accelerators/install-biztalk-adapter-pack-2013-r2-and-2013.md)et puis prise en main la la [différents adaptateurs](../adapters-and-accelerators/biztalk-adapter-pack.md).

Si vous êtes novice [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] ou [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], puis examinez la méthode get rubriques et parcourir les didacticiels : 

[Prise en main l’adaptateur BizTalk pour base de données Oracle](../adapters-and-accelerators/adapter-oracle-database/get-started-with-the-oracle-database-adapter.md)  
[Prise en main l’adaptateur BizTalk pour Oracle E-Business Suite](../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)  
[Prise en main l’adaptateur BizTalk pour mySAP Business Suite](../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)  
[Prise en main l’adaptateur BizTalk pour Siebel eBusiness Applications](../adapters-and-accelerators/adapter-siebel/get-started-with-the-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[Prise en main l’adaptateur BizTalk pour SQL](../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)
   
### <a name="does-the-microsoft-biztalk-adapter-pack-support-tracing"></a>Microsoft BizTalk Adapter Pack prend en charge le suivi ?  
Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] permet aux clients d’adaptateur activer le suivi de Windows Communication Foundation (WCF) et le suivi de spécifiques à l’adaptateur. Lorsque vous activez le traçage, vous choisissez également le nom de fichier et le chemin du dossier. Par conséquent, les suivis sont stockés si vous préférez. Pour afficher les traces, utilisez l’outil WCF Service Trace Viewer. Consultez [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et de dépannage](https://msdn.microsoft.com/library/aa751795.aspx).

Pour plus d’informations sur le suivi et d’autres idées de résolution des problèmes, consultez : 

[Dépanner l’adaptateur de base de données Oracle](../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[Dépanner l’adaptateur Oracle eBusiness Suite](../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)  
[Résoudre les problèmes de l’adaptateur SAP](../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)  
[Dépanner l’adaptateur Siebel](../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)  
[Résoudre les problèmes de l’adaptateur SQL](../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)  
  
### <a name="are-performance-counters-available-for-the-adapters"></a>Sont des compteurs de performance disponibles pour les cartes ?  
Oui. Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] fournit un **temps LOB (cumul)** compteur de performance pour mesurer la durée, en millisecondes, la bibliothèque cliente LOB nécessaire pour effectuer une action initiée par l’adaptateur.  Vous pouvez activer les compteurs de performance en définissant le `EnablePerformanceCounters` liaison de propriété **True**. Pour désactiver les compteurs de performances, définissez `EnablePerformanceCounters` à **False** (la valeur par défaut).   

## <a name="biztalk-server-questions"></a>Questions de BizTalk Server

### <a name="which-biztalk-server-tools-are-used-while-working-with-adapters-where-can-i-find-more-information-about-these-tools"></a>Les outils de BizTalk Server sont utilisées lors de l’utilisation de cartes ? Où puis-je trouver plus d’informations sur ces outils ?  
Il existe plusieurs outils qui peuvent aider aux artefacts qui utilisent ces adaptateurs : 
 
 |Outil|Rubriques de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation de base|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]|-   [À l’aide de Visual Studio](../core/using-visual-studio.md) <br />-   [Utilisation des projets BizTalk](../core/working-with-biztalk-projects.md)<br />-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> En savoir plus sur les solutions de Visual Studio, projets et les éléments à [Solutions et projets dans Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).|  
|Concepteur d'orchestration|[Création d’orchestrations à l’aide du Concepteur d’orchestration](../core/creating-orchestrations-using-orchestration-designer.md)|  
|Concepteur de pipeline| [Création de pipelines à l’aide du Concepteur de pipeline](../core/creating-pipelines-using-pipeline-designer.md)|  
|Mappeur BizTalk| [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)|  
|Console d’Administration de BizTalk Server|[Utilisation de la console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md)|  
  
### <a name="can-i-reuse-bindings-of-a-biztalk-application-how"></a>Puis-je réutiliser les liaisons d’une application BizTalk ? Comment ?  
Oui. Une liaison crée un mappage entre un point de terminaison logique, par exemple un port d’orchestration ou un lien de rôle et un point de terminaison physique, par exemple un envoi et le port de réception. Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer. Les informations de liaison sont stockées dans un fichier XML qui contient des informations de liaison pour chaque orchestration BizTalk dans l’étendue d’un assembly BizTalk, une application ou un groupe. Vous pouvez exporter les liaisons d’un assembly, une application ou un groupe BizTalk et puis la réutiliser en important dans n’importe quel autre application BizTalk ou groupe. Pour plus d'informations, consultez 

[Réutiliser les liaisons de carte de base de données Oracle](../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)  
[Réutiliser les liaisons de l’adaptateur Oracle eBusiness Suite](../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)  
[Réutiliser les liaisons de l’adaptateur SAP](../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)  
[Réutiliser les liaisons de l’adaptateur Siebel](../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)  
[Réutiliser les liaisons de l’adaptateur SQL](../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)
  
### <a name="what-is-the-transaction-isolation-level-how-can-i-configure-it"></a>Qu’est « Transaction Isolation Level » ? Comment puis-je configurer il ?  
 Le niveau d’isolation de transaction détermine le degré auquel une transaction est isolée des modifications de données effectuées par d’autres transactions. Il définit le comportement de verrouillage des commandes Transact-SQL émises par une connexion au système de métier (LOB). 
  
Cela est configurable pour certaines des cartes. Consultez : 

[Base de données Oracle : Configurer le niveau d’isolation de transaction et le délai d’attente de transaction](../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)  
[Oracle E-Business Suite : Configurer le niveau d’isolation de transaction et le délai d’attente de transaction](../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)  
[SQL : Configurer le niveau d’Isolation de Transaction et le délai d’attente de Transaction](../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)

[Niveaux d’isolation dans le moteur de base de données SQL](https://technet.microsoft.com/library/ms189122.aspx) décrit les différents niveaux dans SQL. 

## <a name="wcf-based-adapter-faqs"></a>Adaptateur WCF Foire aux questions

### <a name="what-is-wcf"></a>Nouveautés WCF
 WCF est l’acronyme Windows Communication Foundation. WCF est une infrastructure de programmation développée par Microsoft pour la création d’applications orientées service. WCF fait partie du .NET framework et permet aux développeurs de créer des solutions sécurisées, fiables et transactionnelles qui s’intègrent à plusieurs plateformes et interagissent avec les investissements existants.  
  
Liens : [présentation de Windows Communication Foundation](https://msdn.microsoft.com/library/ms731082.aspx)  
  
### <a name="what-is-wcf-lob-adapter-sdk"></a>Nouveautés WCF LOB Adapter SDK  
 WCF LOB Adapter SDK est un ensemble d’outils et composants qui fournissent un cadre cohérent pour le développement d’adaptateurs réutilisables et riches en métadonnées pour les systèmes de line-of-business. Adaptateurs écrits à l’aide de WCF LOB Adapter SDK sont signalées en tant que liaisons WCF personnalisées et peuvent être consommés par un client compatible WCF. 
 
Liens : [WCF ligne d’entreprise adaptateur documentation du SDK](../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md) 

### <a name="what-is-the-wcf-service-model"></a>Qu’est le modèle de service WCF ?  
 Le modèle de service WCF est un modèle de programmation fourni par WCF dans lequel le système métier (par exemple, Oracle ou SAP) est exposé comme service WCF. Le contrat de service qui existe entre un client et un service est représenté comme une interface .NET, et les opérations sont représentées en tant que méthodes sur cette interface. Le modèle de service WCF génère une classe proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations et les données à l’aide de l’adaptateur de réception. 
 
 Toutes les cartes dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] prend en charge le modèle de service WCF.
 
 ### <a name="what-is-the-wcf-channel-model"></a>Qu’est le modèle de canal WCF ?  
 Le modèle de canal WCF est une abstraction de l’échange de messages SOAP entre les clients et les services de bas niveau. Il fournit des interfaces et des types qui vous permettent d’envoyer et recevoir des messages à l’aide d’une pile de protocole en couche appelée une pile de canaux. Chaque couche de la pile est composé d’un canal, et chaque canal est créé à partir d’une liaison WCF. Chaque adaptateur est une liaison de transport personnalisé WCF qui expose le système métier en tant que service WCF. 
 
  Toutes les cartes dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] prennent en charge le modèle de canal WCF.
  
### <a name="when-should-i-use-the-wcf-service-model-or-the-wcf-channel-model"></a>Quand dois-je utiliser le modèle de service WCF ou le modèle de canal WCF ?  
 Le modèle de service WCF présente un modèle familier aux programmeurs .NET et masque la complexité sous-jacente d’échange de messages SOAP sur un canal. En outre, le plug-in d’Ajouter adaptateur Service référence est intégré à l’expérience de conception de Visual Studio et présente une interface standard de Microsoft Windows qui fournit de puissantes de navigation et de recherche avancées sur les opérations exposées par l’adaptateur. Par conséquent, le modèle de service WCF est souvent le meilleur choix pour développer des solutions de programmation pour les cartes basé sur WCF.  

 Vous souhaitez utiliser le modèle de canal WCF via le service WCF de modèle lorsque :  
  
-   Le modèle de canal WCF fournit un contrôle plus affiné sur les opérations que vous effectuez sur le système métier, car dans le modèle de canal WCF, vous contrôlez directement le contenu des messages que vous envoyez sur le canal.  
  
-   Le modèle de canal WCF fourni la prise en charge plus complète de bout en bout pour la diffusion en continu des types de données LOB (large object) que le modèle de service WCF. Il s’agit, car dans le modèle de canal WCF, vous contrôlez directement comment vous fournissez le corps du message sur les messages sortants et le mode de traitement du corps du message sur les messages entrants. 
  
### <a name="how-do-i-get-started-with-the-wcf-service-model"></a>Comment pour démarrer avec le modèle de service WCF ?  
 Vous pouvez utiliser des outils suivants fournis par le modèle de service WCF pour générer une classe de client WCF ou d’un contrat de service WCF et d’assistance associées, le code à partir des métadonnées de service exposées par chaque carte :  
  
-   Le service Model Metadata Utility Tool (svcutil.exe), qui est fourni avec WCF.  
  
-   L’ajouter adaptateur Service référence Visual Studio plug-in, qui est fourni avec le [!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)].  
  
### <a name="how-do-i-get-started-with-the-wcf-channel-model"></a>Comment pour démarrer avec le modèle de canal WCF ?  
 À l’aide du modèle de canal WCF, vous pouvez appeler des opérations et les résultats d’une requête d’interrogation de réception en échangeant des messages SOAP avec l’adaptateur sur un canal WCF. Pour commencer, vous devez créer sortant (client) et les canaux entrants (service).
  
## <a name="see-also"></a>Voir aussi  
[Pack d’adaptateurs BizTalk](../adapters-and-accelerators/biztalk-adapter-pack.md)