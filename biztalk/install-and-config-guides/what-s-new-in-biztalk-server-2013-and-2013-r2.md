---
title: "Nouveautés de BizTalk Server 2013 et 2013 R2 | Documents Microsoft"
description: "Liste complète des nouvelles fonctionnalités et modifications dans BizTalk Server 2013 R2 et 2013"
caps.latest.revision: "67"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 2017-08-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdb841f7-4aa9-45c9-a6f1-d527089fcc09
ms.author: mandia
ms.openlocfilehash: 49a4e668f1c5e23169464fdbc4b4f0464a062628
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="whats-new-in-biztalk-server-2013-and-2013-r2"></a>Nouveautés de BizTalk Server 2013 et 2013 R2
Découvrez les fonctionnalités nouvelles et celles déconseillées dans [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013.
  
##  <a name="BKMK_NewR2"></a> Nouveautés de BizTalk Server 2013 R2  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Prise en charge des nouvelles versions de SE Windows, SQL Server et Visual Studio|Consultez [Configurations logicielle et matérielle pour BizTalk Server 2013 et 2013 R2](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md).|  
|Prise en charge de JSON|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend désormais en charge l’envoi et la réception de messages JSON. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comprend un assistant pour générer un schéma XSD à partir d’une instance JSON, et un composant encodeur et décodeur à utiliser avec les pipelines personnalisés. Pour plus d’informations, consultez [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md).|  
|Mises à jour de l'adaptateur SB-Messaging|L’adaptateur SB Messaging a été amélioré pour prendre en charge l’authentification basée sur SAP (Signature d’Accès Partagé), en plus d’ACS.  Avec cette nouvelle amélioration, BizTalk Server peut désormais interagir également avec l’édition locale de Service Bus. Pour plus d’informations, consultez la rubrique [Adaptateur SB-Messaging](../core/sb-messaging-adapter.md).|  
|Mises à jour de l'adaptateur SFTP|L'adaptateur SFTP prend maintenant en charge l'authentification à deux facteurs et fournit une option permettant de spécifier un dossier temporaire lors du téléchargement de fichiers volumineux. Vous pouvez aussi sélectionner une valeur de chiffrement (Encryption) spécifique pour votre serveur cible. Pour plus d’informations, consultez la rubrique [Adaptateur SFTP](../core/sftp-adapter.md).|  
|Mises à jour de HL7 Accelerator|L'accélérateur HL7 prend maintenant en charge ce qui suit :<br /><br /> - Il permet d’inclure des données en texte libre dans le cadre des messages pouvant être traités par les pipelines HL7.<br /><br /> - Il fournit une prise en charge 64 bits pour l’hébergement de l’adaptateur Hl7.<br /><br /> Consultez la rubrique [Nouveautés de BizTalk Accelerator pour HL7](http://msdn.microsoft.com/library/ee409458\(v=bts.80\).aspx).|  
|BizTalk Health Monitor|BizTalk Health Monitor est un nouveau composant logiciel enfichable BizTalk qui permet d'analyser le fonctionnement de votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce composant logiciel enfichable peut être ajouté à la console Administration de BizTalk existante ou être exécuté de façon individuelle. BizTalk Health Monitor offre les fonctionnalités suivantes :<br /><br /> - Générer et afficher un rapport d’intégrité<br /><br /> - Afficher le tableau de bord relatif au fonctionnement global de l’environnement BizTalk<br /><br /> - Envoyer des notifications par e-mail<br /><br /> - Planifier la collecte des rapports<br /><br /> - Intégrer l’analyseur des performances avec des compteurs de performances basés sur des scénarios préchargés<br /><br /> - Analyser plusieurs environnement BizTalk<br /><br /> - Gestion des rapports<br /><br /> Pour plus d’informations sur BizTalk Health Monitor, consultez [Bien démarrer avec BizTalk Health Monitor](http://go.microsoft.com/fwlink/?LinkId=403315) et [Présentation de BizTalk Health Monitor](http://go.microsoft.com/fwlink/?LinkId=403316).|  
  
### <a name="deprecated-list"></a>Liste des composants supprimés  
  
|Programme|État|Remplacement|  
|-------------|------------|-----------------|  
|RFID Mobile|Supprimé|Aucun|  
|RFID Server|Déprécié|Aucun|  
|Adaptateur SharePoint SSOM/Web Service|Déprécié|Utilisez l'option CSOM (Client Side Object Model).<br /><br /> [Adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter.md)<br /><br /> [Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)|  
|adaptateur SOAP|Déprécié|[Adaptateur WCF-BasicHttp](../core/wcf-basichttp-adapter.md)|  
|Ancien adaptateur SQL|Déprécié|Adaptateur SQL basé sur WCF dans [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]|  
|UDDI|Déprécié|Aucun|  
  
> [!IMPORTANT]
>  Certaines de ces fonctionnalités déconseillées peuvent apparaître dans les versions plus récentes de BizTalk. Dans ces scénarios, considérez les points suivants :  
>   
>  -   La fonctionnalité est peut-être utilisée en interne dans BizTalk et n'est pas destinée à être utilisée par les solutions des clients. Elle n'est pas prise en charge dans les solutions des clients.  
> -   Les interfaces ont peut-être été modifiées par Microsoft et ne sont peut-être pas publiquement disponibles.  
  
##  <a name="BKMK_New"></a> Nouveautés de BizTalk Server 2013  
 Les fonctionnalités suivantes ont été ajoutées dans BizTalk Server 2013.  
  
 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur Azure IaaS**  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un [!INCLUDE[vm](../includes/vm-md.md)][!INCLUDE[winazure](../includes/winazure-md.md)]|Consultez [Création d’une machine virtuelle BizTalk dans Windows Azure](http://msdn.microsoft.com/library/jj572843.aspx).|  
|Créer un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un [!INCLUDE[vm](../includes/vm-md.md)][!INCLUDE[winazure](../includes/winazure-md.md)]|Consultez [Créer les conditions préalables à un groupe BizTalk](http://msdn.microsoft.com/library/jj248711.aspx) et [Configuration du groupe BizTalk](http://msdn.microsoft.com/library/jj572845.aspx).|  
  
 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur site**  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Par modèle de licence par cœur|BizTalk Server 2013 est par cœur. SQL Server 2012 est également par cœur. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 et les versions précédentes sont par processeur.<br /><br /> Lors de l’exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur des processeurs dotés de quatre cœurs ou moins, le coût de la licence reste cohérent par rapport à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010. Le prix des licences par cœur représente le quart de celui d’une licence par processeur. Lors de l’exécution de serveurs équipés de processeurs de plus grande capacité, les coûts des licences augmentent en raison de la puissance accrue du matériel.<br /><br /> Pour aider à déterminer le nombre de licences dont vous pourriez avoir besoin, une applet de commande PowerShell est disponible dans *C:\Program Files (x86)\Microsoft BizTalk Server 20xx\SDK\Utilities\LicenseUsageTracking*.<br /><br /> Liens utiles :<br /><br /> [Tarification et éditions de BizTalk Server 2013](http://www.microsoft.com/biztalk/pricing.aspx)<br /><br /> [Comprendre la politique des licences de BizTalk Server 2013](http://blogs.biztalk360.com/understand-biztalk-server-2013-licensing/)|  
|Prise en charge pour les nouveaux adaptateurs|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit de nouveaux adaptateurs pour étendre la connectivité des applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à [!INCLUDE[winazure](../includes/winazure-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit également des mises à jour pour l’adaptateur SharePoint qui permettent aux utilisateurs de choisir entre le modèle objet côté client ou côté serveur pour la connexion à un serveur SharePoint. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un nouvel adaptateur pour envoyer et recevoir des messages à partir d’un serveur SFTP.|  
|Suivi des dépendances entre artefacts|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] met à jour la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour offrir une expérience pilotée par l'interface utilisateur afin d'observer les effets de dépendance entre différents artefacts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tels que les orchestrations, les ports d'envoi, les emplacements de réception, etc. Pour plus d’informations, consultez la rubrique [Suivi des dépendances entre les artefacts dans une application BizTalk Server](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md).|  
|ESB Toolkit intégré|ESB Toolkit est désormais intégré dans le cadre de l'installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. D'autre part, l'expérience de configuration d'ESB Toolkit est simplifiée pour offrir aux utilisateurs un démarrage rapide plus facile. Pour plus d’informations, consultez la rubrique [Installer et configurer Microsoft BizTalk ESB Toolkit](../esb-toolkit/install-and-configure-the-microsoft-biztalk-esb-toolkit.md).|  
|Prise en charge des nouvelles versions de SE Windows, SQL Server et Visual Studio|Consultez la rubrique [Configurations logicielle et matérielle pour BizTalk Server 2013 et 2013 R2](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md).|  
|Mises à jour vers les schémas EDI pris en charge|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] introduit la prise en charge des schémas EDI suivants :<br /><br /> -                     **X12** – 5040, 5050, 6020, 6030<br /><br /> - **EDIFACT** – D06A, D06B, D07A, D07B, D08A, D08B, D09A, D09B, D10A, D10B<br /><br /> -                     **HL7** – 2.51 prise en charge des messages ajoutée<br /><br /> -                     **SWIFT** – 2012 Message Pack<br /><br /> Les schémas sont inclus dans le package d'installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez télécharger le package d’installation à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=258228](http://go.microsoft.com/fwlink/p/?LinkId=258228).|  
|Le Mappeur utilise XSLCompiledTransform|Le Mappeur utilise la classe XSLCompiledTransform. Les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisaient la classe XslTransform (désormais obsolète). La classe XSLCompiledTransform améliore les performances, notamment :<br /><br /> - Une fois la méthode Load correctement exécutée, la méthode Transform peut être appelée simultanément à partir de plusieurs threads.<br /><br /> - Le nouveau processeur XSLT compile la feuille de style XSLT dans un format intermédiaire commun. Une fois compilée, la feuille de style peut être mise en cache et réutilisée.<br /><br /> Plus d’informations dans [What the Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) et [Classe XslCompiledTransform](https://msdn.microsoft.com/library/system.xml.xsl.xslcompiledtransform.aspx).|  
|Gestionnaire du port d'envoi dynamique configurable|Lors de la création d’un port d’envoi dynamique, un gestionnaire d’envoi d’adaptateur peut être configuré pour *chaque* adaptateur installé. Inclut à la fois un port d'envoi unidirectionnel et un port d'envoi dynamique avec sollicitation-réponse. Dans les versions précédentes de BizTalk, un ports d'envoi dynamique utilise l'hôte par défaut de l'adaptateur.<br /><br /> La rubrique [Le gestionnaire du port d’envoi dynamique est configurable](../core/dynamic-send-port-handler-is-configurable.md) fournit des informations supplémentaires.|  
|livraison chronologique des messages (éventuellement en anglais)|Dans les versions précédentes de BizTalk avec des scénarios où la livraison chronologique utilise plusieurs points de terminaison, le type d'adaptateur le plus lent correspond à la vitesse maximale. Ce comportement impacte directement les solutions HL7. Lors de l'utilisation de l'adaptateur MLLP, des accusés de réception (ACK) sont nécessaires. Les retards peuvent survenir en raison d'un accusé de réception qui doit être reçu avant l'envoi du prochain message.<br /><br /> Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le prochain message peut être envoyé sans attendre un accusé de réception du message précédent. Lorsque l'accusé de réception arrive, il est corrélé/connecté de façon interne avec son message.|  
|Outils de support|Les outils de support sont automatiquement installés avec BizTalk : *C:\Program Files (x86)\Microsoft BizTalk Server 20xx\SDK\Utilities\Support Tools*.<br /><br /> Les outils inclus sont les suivants :<br /><br /> - BizTalk Assembly Checker<br /><br /> - MsgBox Viewer<br /><br /> - PSSDiagForBizTalk<br /><br /> - Raccourci Internet pour télécharger BizTalk Terminator|  
|Fournisseur PowerShell|Le fournisseur PowerShell [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se trouve dans *C:\Program Files (x86)\Microsoft BizTalk Server 2013\SDK\Utilities\PowerShell*.<br /><br /> Pour les versions antérieures de BizTalk, un fournisseur PowerShell CodePlex est disponible à l’adresse [http://psbiztalk.codeplex.com/](http://psbiztalk.codeplex.com/).|  
|Alertes BAM|Si BizTalk Server 2013 utilise [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], Database Mail est nécessaire pour utiliser les alertes BAM. Si BizTalk Server utilise SQL Server 2008 R2, SQL Server Notification Services est nécessaire pour utiliser les alertes BAM.<br /><br /> La rubrique [Alertes BAM](../install-and-config-guides/prepare-your-computer-for-installation.md#BKMK_BAMAlerts) fournit plus d’informations.|  
  
> [!IMPORTANT]
>  Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts, MS DTC (Microsoft Distributed Transaction Coordinator) gère les transactions entre les ordinateurs. Par conséquent, la fonctionnalité [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn n’est pas prise en charge avec [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)] et 2013. À partir de [!INCLUDE[bts2016](../includes/bts2016-md.md)], la fonctionnalité AlwaysOn **est** prise en charge. Pour plus d’informations, consultez [Nouveautés de BizTalk Server 2016](../install-and-config-guides/what-s-new-in-biztalk-server-2016.md).  
  
### <a name="known-issues"></a>Problèmes connus  
 [Problèmes connus dans BizTalk Server 2013](http://support.microsoft.com/kb/2954101)