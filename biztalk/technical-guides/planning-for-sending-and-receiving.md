---
title: Planification pour envoyer et recevoir | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d67e5f7-5127-4c1d-be20-8d8dbb538286
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2b87964266b77629f7fa1d1156ace3cd048e7f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="planning-for-sending-and-receiving"></a>Planification pour envoyer et recevoir
Presque chaque document traité par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est reçu par un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] l’adaptateur de réception et envoyés à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] l’adaptateur d’envoi. Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes figurant donc en évidence dans les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, il est important de planifier déterminer les cartes ou les accélérateurs, vous allez utiliser et la configuration de ces adaptateurs et/ou les accélérateurs.  
  
## <a name="determining-which-adapters-and-accelerators-you-will-use"></a>Déterminer les adaptateurs et les accélérateurs, vous allez utiliser  
 Discutez avec vos partenaires commerciaux à l’avance afin de déterminer les adaptateurs et les accélérateurs, vous devrez facilitent l’envoi et réception de documents entre votre organisation et vos partenaires commerciaux et entre vos applications BizTalk et internes applications d’entreprise. Conception de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture pour être suffisamment flexibles pour prendre en charge l’ajout de cartes supplémentaires ou des accélérateurs dans le cas où vous établissez des relations avec les commerciaux supplémentaires aux partenaires à l’avenir.  
  
## <a name="functionality-supported-by-biztalk-adapters"></a>Fonctionnalités prises en charge par les adaptateurs BizTalk  
 Le tableau de cette section répertorie le principal avantage de chaque adaptateur natif et indique si l’adaptateur fournit les fonctionnalités suivantes :  
  
-   **Prise en charge des transactions** la possibilité d’envoyer et recevoir des documents dans le contexte d’une transaction coordinator (DTC) de transaction distribuée. Cette fonctionnalité est requise pour assurer la livraison chronologique des messages et garantir que les documents ne sont pas dupliqués ou perdus.  
  
    > [!NOTE]  
    >  Si vous rencontrez des problèmes liés à MSDTC, consultez la rubrique [Troubleshooting Problems with MSDTC](http://go.microsoft.com/fwlink/?LinkID=154693) (http://go.microsoft.com/fwlink/?LinkID=154693).  
  
-   **Prise en charge la communication bidirectionnelle (requête-réponse ou sollicitation-réponse)** la possibilité d’envoyer un document et de traiter un message de réponse de la destination ou recevoir un document et envoyer un message de réponse à la source.  
  
-   **Dans l’ordre de réception prise en charge.** La possibilité de publier des documents reçus dans la base de données MessageBox dans l’ordre exact que les documents ont été reçus.  
  
    > [!NOTE]  
    >  Certaines cartes peuvent appliquer remise ordonnée document au niveau de l’emplacement de réception, mais pas les autres adaptateurs. Livraison chronologique des messages peuvent toujours être appliqué au niveau du port d’envoi de ces cartes qui ne gèrent pas la livraison de document au niveau de l’emplacement de réception chronologique mais cela donc risque d’entraîner une baisse des performances. Pour plus d’informations sur la livraison chronologique des messages, consultez la rubrique [classés de remise de Messages](http://go.microsoft.com/fwlink/?LinkId=155751) (http://go.microsoft.com/fwlink/?LinkId=155751).  
  
-   **Authentification unique activée.** capacité à utiliser l'authentification unique dans le cadre de l'envoi ou de la réception de documents avec l'adaptateur.  
  
|Adaptateur|Le principal avantage|Prise en charge des transactions|Prise en charge de la Communication bidirectionnelle|Dans l’ordre de réception prise en charge|Authentification unique activée|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|  
|Fichier|Facile à utiliser|non|Non|Non|non|  
|FTP|Est largement utilisé pour les communications de l’entreprise-entreprise|non|Non|Non|Oui|  
|HTTP(s)|Est largement utilisé pour les communications de l’entreprise-entreprise|non|Requête/réponse et sollicitation/réponse|non|Oui|  
|SOAP|Prend en charge l’utilisation de services Web|non|Requête/réponse et sollicitation/réponse|non|Oui|  
|MSMQ|Prend en charge garantie de remise unique des messages entre BizTalk Server et Microsoft Message Queuing|Oui|Non|Oui|non|  
|MQSeries|Prend en charge garantie de remise unique des messages entre BizTalk Server et IBM WebSphere MQ pour les plateformes Windows|Oui|Non|Oui|Oui|  
|SQL|Prend en charge une communication directe entre les bases de données BizTalk Server et SQL Server|Oui|Sollicitation-réponse uniquement|non|non|  
|Windows SharePoint Services|Permet l’échange de messages XML et binaires entre BizTalk Server et les bibliothèques de documents SharePoint|non|Non|Non|non|  
|POP3|Prend en charge la réception de documents par courrier électronique|non|Non|Non|non|  
|SMTP|Prend en charge l’envoi de documents par courrier électronique|non|Non|Non|non|  
|Routage|Traitement prend en charge des documents commerciaux qui se conforment à la norme EDI|non|Non|Non|non|  
|Custom|Prend en charge de votre système hérité|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|Oui, requiert du code personnalisé.|  
|WCF-WSHttp|Prend en charge WS-* normes via le transport HTTP|Oui, les transactions sont prises en charge sur WsHTTP (WS-transactions uniquement)|Requête/réponse et sollicitation/réponse|non|Oui|  
|WCF-BasicHttp|Communique avec les services Web basés sur ASMX et les clients et autres services conformes à WS-I Basic Profile 1.1 à l’aide de HTTP ou HTTPS|non|Requête/réponse et sollicitation/réponse|non|Oui|  
|WCF-NetTcp|Prend en charge WS-* normes via le transport TCP|Oui|Requête/réponse et sollicitation/réponse|non|Oui|  
|WCF-NetMsmq|Prend en charge queuing en utilisant Microsoft Message Queuing (MSMQ) comme transport|Oui|Non|Oui|Oui|  
|WCF-NetNamedPipe|Fournit un transport rapide pour la communication interprocessus sur le même ordinateur (uniquement pour les applications WCF)|Oui|Requête/réponse et sollicitation/réponse|non|Oui|  
|WCF-Custom|Permet d’utiliser des fonctionnalités d’extensibilité WCF|Oui.|Oui.|Oui, dès lors que la liaison prend en charge cette fonctionnalité.|Oui.|  
|WCF-CustomIsolated|Permet d’utiliser des fonctionnalités d’extensibilité WCF via le transport HTTP|Oui.|Oui.|Non.|Oui.|  
  
## <a name="line-of-business-adapters"></a>Adaptateurs sectoriels  
 La liste suivante répertorie les adaptateurs sectoriels fournis par Microsoft.  
  
> [!NOTE]  
>  À l’exception de Microsoft BizTalk Adapter v2.0 pour mySAP™ Business Suite (l’adaptateur), aucun des adaptateurs métier sont pris en charge sur Windows Vista.  
  
|Adaptateur| Description|Versions prises en charge|  
|-------------|-----------------|------------------------|  
|SAP (également appelée « la carte »)|Permet l’échange de messages d’appel (RFC) de la fonction distante entre BizTalk Server et un système SAP R/3®, BAPI et Intermediate Document (IDOC).|SAP r/3 4.x et r/3 6.20 (Enterprise)|  
|PeopleSoft Enterprise|Permet l'échange de messages d'interface de composant entre BizTalk Server et un système PeopleSoft.|PeopleTools Versions 8.17.02, 8.43, 8.45, 8.46 et 8.48|  
|JD Edwards OneWorld XE|Permet l'échange de messages commerciaux entre BizTalk Server et un système JD Edwards OneWorld.|B7.3.3.3 with SP23 et JDE 8.0 (B7.3.3.4)|  
|JD Edwards EnterpriseOne|Permet l'échange de messages commerciaux entre BizTalk Server et un système JD Edwards EnterpriseOne.|8.10 & 8.11 with Tools Release 8.93, 8.94, 8.95 et 8.96|  
|Adaptateur ODBC pour base de données Oracle|Permet de lire et écrire des informations depuis et vers une base de données du serveur Oracle.|Oracle 8i (8.1.6.0), 9i (9.2.0.1), ou 10g|  
|Siebel eBusiness Applications|Permet l’échange de messages de composants d’entreprise et le Service d’entreprise entre BizTalk Server et une application Siebel eBusiness applications.|7.0, 7.5. *, 7.7. \*et 7.8.\*|  
|TIBCO Rendezvous|Permet l'échange de messages au format de données XML et binaires entre BizTalk Server et TIBCO Rendezvous.|7.3|  
|TIBCO Enterprise Message Service|Permet l'échange de messages au format de données XML et binaires entre BizTalk Server et un serveur TIBCO EMS et fournit une infrastructure d'applications étroitement intégrée et fiable.|4.2|  
|WebSphere MQ|Permet l'échange de messages entre BizTalk Server et IBM WebSphere MQ.|5.3 with Fix Pack 10 ou version ultérieure et 6.0 with Fix Pack 1.1 ou version ultérieure|  
  
 Pour plus d’informations sur les adaptateurs LOB disponibles avec BizTalk Server, consultez [adaptateurs inclus dans BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=152664) (http://go.microsoft.com/fwlink/?LinkId=152664).  
  
## <a name="biztalk-adapter-pack"></a>Module adaptateur de BizTalk  
 Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] contient les adaptateurs WCF pour fournir une connectivité aux applications métier telles que la base de données Oracle, Oracle E-Business Suite, SAP, Siebel et SQL Server. Pour obtenir la liste des adaptateurs disponibles avec [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez [BizTalk Adapter Pack](http://go.microsoft.com/fwlink/?LinkId=152665) (http://go.microsoft.com/fwlink/?LinkId=152665).  
  
> [!IMPORTANT]  
>  Vous pouvez utiliser la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] outil de Migration pour migrer des projets BizTalk pour les adaptateurs LOB aux projets BizTalk pour les adaptateurs LOB de basé sur WCF disponibles avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Vous pouvez télécharger le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] outil de Migration à partir de [outil de Migration BizTalk Adapter Pack](http://go.microsoft.com/fwlink/?LinkID=153328) (http://go.microsoft.com/fwlink/?LinkID=153328). En savoir plus sur les adaptateurs LOB migration vers adaptateurs LOB de basé sur WCF inclus dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], consultez la [livre blanc de Microsoft BizTalk adaptateur 2.0 Migration](http://go.microsoft.com/fwlink/?LinkId=158848) (http://go.microsoft.com/fwlink/?LinkId=158848).  
  
## <a name="biztalk-accelerators"></a>Accélérateurs BizTalk  
 Alors que les adaptateurs BizTalk adapter envoyer et recevoir des documents avec un protocole spécifique, les accélérateurs BizTalk sont conçus pour prendre en charge l’échange de documents conformément à une norme industrielle particulière. Pour obtenir la liste les accélérateurs BizTalk disponibles, consultez [accélérateurs de Microsoft BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=103609) (http://go.microsoft.com/fwlink/?LinkId=103609).  
  
##  <a name="BKMK_InternetTrans"></a> Configuration de votre domaine lors de l’exposition des Transports à Internet  
 Afin de faciliter l’envoi et la réception de documents entre votre organisation et les partenaires externes, il peut être nécessaire d’exposer des transports sur un site exposés au public qui est accessible à partir d’Internet. Dans ces circonstances, la configuration de domaine suivante est recommandée :  
  
-   **Utiliser un domaine de réseau de périmètre, (également appelé zone démilitarisée (DMZ) ou sous-réseau filtré), aux serveurs de maison pour fournir d’Internet services pour votre organisation associés**  
  
     Le domaine de réseau de périmètre doit contenir des serveurs qui hébergent l’emplacement physique où les transports côté Internet acheminer des documents entre des ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et vos partenaires commerciaux. Le pare-feu de réseau de périmètre doit ouvrir uniquement les ports requis pour autoriser les communications vers et depuis Internet faisant face à des transports. Il ne doit y avoir aucun ordinateur en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Single Sign-On les ordinateurs serveur ou des emplacements de réception dans le domaine de réseau de périmètre. Documents envoyés/reçus de transports dans le domaine de réseau de périmètre doivent être routés le pare-feu protégeant le domaine de traitement à l’aide d’Internet Security and Acceleration Server (ISA) Server Web Publishing du pare-feu connecté à Internet et Publication de serveur. Pour plus d’informations sur l’utilisation de Web ISA Server et le serveur de publication, consultez [publication Concepts dans ISA Server 2006](http://go.microsoft.com/fwlink/?LinkID=86359) (http://go.microsoft.com/fwlink/?LinkID=86359).  
  
    > [!NOTE]  
    >  Comme une mesure supplémentaire de sécurité, tenez compte à l’aide de certificats numériques d’infrastructure à clé publique (PKI) à des fins de chiffrement de document et le déchiffrement, signature de documents et vérification (non-répudiation) pour les documents envoyés ou reçus des commerciaux partenaires via Internet faisant face à des transports dans ce domaine.  
  
     Les transports suivants sont généralement utilisés sur le domaine de réseau de périmètre est accessible à partir d’Internet :  
  
    -   FTP - pour recevoir des documents à l’aide du protocole FTP  
  
    -   SMTP - envoyer des documents à l’aide du protocole SMTP  
  
    -   HTTP - pour recevoir des documents à l’aide du protocole HTTP  
  
    -   SOAP - pour recevoir des documents à l’aide de SOAP  
  
    -   POP3 - pour recevoir le document à l’aide du protocole POP3  
  
-   **Utiliser un domaine de traitement pour héberger les serveurs qui contiennent le serveur BizTalk Server recevoir et envoyer des gestionnaires et un serveur du portail BAM**  
  
     Flux de documents entre les transports en vis-à-vis externes dans le domaine de périmètre et les adaptateurs BizTalk dans le domaine de traitement doit être routé via un pare-feu entre ces domaines. Le domaine de traitement doit héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] recevoir des ports, emplacements, des pipelines, des mappages, des schémas et assemblys utilisés pour recevoir, Router et envoyer des messages. Le domaine de traitement doit également contenir des serveurs pour le portail BAM. Le nombre d’ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le domaine de traitement sera dépend du nombre d’ordinateurs hôtes et instances requises pour répondre aux besoins de performances de votre organisation de l’hôte.  
  
    > [!IMPORTANT]  
    >  Vérifiez que vous créez des instances d’hôte isolé suffisantes dans le domaine de traitement pour prendre en charge le trafic entre les transports HTTP et SOAP dans le domaine de périmètre et les adaptateurs HTTP et SOAP dans le domaine de traitement. Si une grande partie du trafic entre votre organisation et vos partenaires commerciaux document transite par les transports HTTP et SOAP, le domaine de traitement pour gérer le flux de document doit être suffisamment de bande passante du traitement.  
  
-   **Utiliser des domaines supplémentaires pour fournir des couches d’isolement et de sécurité supplémentaires pour votre environnement**  
  
     Ces domaines doivent inclure :  
  
    -   Un domaine qui est approuvé par le domaine de traitement et qui est nécessaire pour traiter correctement les messages des services. En général, les serveurs dans le domaine des services exécutent les orchestrations BizTalk, des pipelines, des services Enterprise Single Sign-On (SSO), le moteur de règles d’entreprise et peuvent inclure les autres processus d’entreprise.  
  
    -   Un domaine de données pour les ordinateurs exécutant SQL Server utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   Un domaine d’entreprise pour les serveurs et ordinateurs de bureau pour fournir des services aux travailleurs de votre organisation.  
  
     Pour plus d’informations sur les topologies de domaine recommandée pour les divers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architectures, consultez [exemples d’architecture BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=155750) (http://go.microsoft.com/fwlink/?LinkId=155750).  
  
## <a name="high-availability-considerations"></a>Considérations relatives à la haute disponibilité  
 Haute disponibilité peut être fournie pour la plupart des cartes en exécutant des instances du Gestionnaire d’adaptateur hôte sur plusieurs serveurs BizTalk Server dans un groupe BizTalk. De cette façon, si une instance d’hôte de gestionnaire de carte échoue, une autre instance hôte Gestionnaire d’adaptateur est disponible pour poursuivre le traitement. Toutefois, il existe des exceptions à cette opération. Dans certains cas en cours d’exécution carte à plusieurs instances d’hôte de gestionnaire peut entraîner les problèmes de contention. Par exemple des problèmes de contention peuvent se produire lors de l’exécution de plusieurs instances des adaptateurs POP3 et FTP. Dans ces circonstances, haute disponibilité peut être fournie pour l’adaptateur en exécutant l’instance de gestionnaire d’adaptateur hôte dans un hôte BizTalk en cluster.  
  
 Pour plus d’informations sur la fourniture de haute disponibilité pour une instance d’hôte d’adaptateur gestionnaire par le biais de cluster hôte, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](http://go.microsoft.com/fwlink/?LinkID=151284) (http://go.microsoft.com/fwlink/?LinkID=151284). Pour plus d’informations sur la fourniture de haute disponibilité pour les hôtes BizTalk, consultez [haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md).  
  
## <a name="performance-considerations"></a>Considérations relatives aux performances  
 **Considérations de performances de l’adaptateur SOAP**  
  
 Pour plus d’informations sur l’optimisation des performances de l’adaptateur SOAP, consultez [les paramètres de Configuration qui affectent les performances carte](http://go.microsoft.com/fwlink/?LinkID=154200) (http://go.microsoft.com/fwlink/?LinkID=154200).  
  
 **Considérations sur les performances d’adaptateur MQSeries**  
  
 **Désactiver la prise en charge des transactions et la livraison chronologique des messages si ce n’est pas requis pour MQSeries carte des emplacements de réception** lors de la réception d’un adaptateur MQSeries emplacement est configuré avec le **prise en charge des transactions** lavaleurd’option **Oui**, ou **commandé** option définie sur **classer avec arrêt**, puis chaque message récupéré par l’emplacement de réception sera traitée dans le contexte d’un Microsoft Distributed Transaction Transaction Coordinator (MSDTC). Étant donné que supplémentaires surcharge système générée lors du traitement des messages dans le contexte d’une transaction MSDTC, ces options de ne doivent pas être activées si la livraison chronologique des messages ou de prise en charge de la transaction n’est pas requis pour le MQSeries adaptateur emplacement de réception.  
  
## <a name="planning-for-ordered-message-delivery"></a>Planification de la livraison chronologique des messages  
 Livraison chronologique des messages garantit que les messages qui sont publiées dans la base de données MessageBox dans un ordre donné sont remis à chaque abonné correspondant dans le même ordre. Les considérations suivantes s’appliquent lors de l’implémentation de livraison chronologique des messages :  
  
 **Configuration de livraison chronologique des messages**  
  
 La livraison chronologique des messages peut être configurée aux deux emplacements suivants :  
  
-   Forme réception dans une orchestration  
  
-   Emplacement de réception pour certaines cartes  
  
-   Port d'envoi  
  
 **Livraison avec Transports existants chronologique**  
  
 Les protocoles sous-jacents de certains transports tels que FILE et HTTP ne sont pas cohérents avec la notion de livraison chronologique des messages. Toutefois, même avec de tels transports, si le port lié au transport est programmé pour une livraison chronologique des messages, BizTalk Server applique la livraison chronologique de force en faisant en sorte que le transport ne reçoive pas le message sortant suivant tant que l'envoi du message en cours n'a pas abouti. Pour ce faire, BizTalk Server transmet chaque message à l’adaptateur de transport dans un lot unique et attend jusqu'à ce que l’adaptateur a supprimé le message à partir de la base de données MessageBox avant de remettre le message suivant, dans un autre traitement, à l’adaptateur.  
  
 **Livraison chronologique des messages pour les adaptateurs personnalisés**  
  
 Pour une personnalisée de réception pour conserver l’ordre des messages lors de leur envoi à BizTalk Server, l’adaptateur doit être développé avec les fonctionnalités suivantes :  
  
-   Après avoir soumis un lot de messages, recevoir votre carte doit attendre l’appel de BatchComplete depuis BizTalk Server avant de soumettre le lot suivant. Pour plus d’informations, consultez [Interfaces pour un adaptateur de réception Batch-Supported](http://go.microsoft.com/fwlink/?LinkId=155752) (http://go.microsoft.com/fwlink/?LinkId=155752).  
  
-   Si un message échoue dans le pipeline, il doit être suspendu, de préférence sans reprise possible. Utilisez le BTS. Propriété de contexte de message SuspendAsNonResumable dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour marquer le message de manière appropriée.  
  
    > [!NOTE]  
    >  La chronologie des messages peut être rompue si un message suspendu est repris plus tard. Si vous ne souhaitez pas ce comportement, suspendre les messages ayant échoué sans reprise possible.  
  
 **Conditions de bout en bout commandé le traitement des messages**  
  
 Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :  
  
-   Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server. MSMQ et MQSeries sont des exemples de ces adaptateurs dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En outre, les adaptateurs HTTP ou SOAP permettent de soumettre des messages dans l'ordre, mais dans ce cas, le client HTTP ou SOAP doit appliquer l’ordre de force en soumettant les messages un par un.  
  
-   Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option définie sur **True**.  
  
-   Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de l’environnement pour BizTalk Server](../technical-guides/planning-the-environment-for-biztalk-server.md)