---
title: Glossaire de BizTalk accelerator pour RosettaNet dans BizTalk Server | Documents Microsoft
description: "Termes et définitions de connaître et d’apprendre à utiliser BizTalk Accelerator pour RosettaNet de courantes"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d98a5ed4-adc5-4ca9-b9d9-38ab02a0bda6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd89d75b0d36359fcf59f7edae0bb950a7196ca7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]utilise les termes de glossaire suivants et les définitions.  

  
## <a name="a"></a>Un  
 **adaptateur d’application**  
 Application qui implémente l'interface de l'adaptateur d'application. Le mécanisme de notification lors de l'acceptation d'un message d'action entrant (demande ou réponse) appelle l'adaptateur d'application. Ce dernier implémente deux méthodes : `BeginNotify` et `EndNotify`. Le répondeur public appelle la méthode `BeginNotify` , tandis que le répondeur prédéfini appelle la méthode `EndNotify` . L'appel à la méthode `Notify` signifie que le message a été enregistré dans la table MessagesToLOB.  
  
 **URL d’action**  
 URL du partenaire vers laquelle l'organisation d'origine transmet un message d'action au cours d'un processus asynchrone. Par exemple : http://FabrikamServer/BTARNApp/RNIFReceive.aspx.  
  
## <a name="b"></a>B  
 **BizTalk Accelerator pour RosettaNet**  
 Un produit complémentaire à BizTalk Server qui permet aux organisations de créer le Framework RNIF (RosettaNet Implementation)-solutions conformes.  
  
 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]Administration**  
 Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] application qui vous permet de décrire des modèles de processus et de gérer des accords de partenariat.  
  
 **Éditeur BizTalk**  
 Outil permettant de créer, de modifier et de gérer des spécifications. Grâce à l'Éditeur BizTalk, vous pouvez créer une spécification basée sur un modèle de spécification, un schéma existant, certains types d'instances de document ou une spécification vide.  
  
 **Concepteur d’Orchestration BizTalk**  
 Outil de conception permettant de créer des dessins qui décrivent des processus d'entreprise à long terme, faiblement couplés et exécutables. Le dessin de planification XLANG est compilé dans une planification XLANG qui vous permet d'exécuter le processus d'entreprise automatisé.  
  
 **BizTalk Server**  
 Produit Microsoft permettant d'automatiser les processus d'entreprise et d'intégrer les applications dans les entreprises et entre celles-ci. BizTalk Server fournit un puissant développement basé sur le Web et l’environnement d’exécution qui s’intègre faiblement couplés et longue des processus d’entreprise, à la fois dans et entre les entreprises.  
  
 Les fonctionnalités de BizTalk Server incluent la composition de planifications XLANG nouvelles et existantes ; intégration des applications existantes ; la définition de spécifications de document et de transformations de spécifications analyse et journalisation de l’activité d’exécution.  
  
 Le serveur fournit une passerelle standard pour l'envoi et la réception de documents via Internet. Il offre également une gamme de services garantissant l'intégrité, la remise, la sécurité et la prise en charge des données pour BizTalk Framework et d'autres formats de document clés.  
  
 **BtarnClean**  
 Utilitaire permettant de nettoyer les artefacts BTARN sur un ordinateur.  
  
 **action d’entreprise**  
 Message RosettaNet contenant des informations d'entreprise, par exemple une demande de bon de commande ou une demande de devis. En association avec les signaux d'entreprise, ces actions constituent les éléments nécessaires pour mener à bien l'activité d'entreprise spécifiée par un processus d'interface entre partenaires (PIP) particulier.  
  
 **Business Activity Monitoring (BAM)**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fonctionnalité qui permet aux utilisateurs de l’entreprise une vue en temps réel des processus d’entreprise hétérogènes. ce qui leur facilite la prise de décisions importantes.  
  
 **signal d’entreprise**  
 Message RosettaNet, tel que ReceiptAcknowledgement ou Exception, échangé entre deux applications de réseau RosettaNet pour communiquer certains événements lors de l'exécution d'une instance PIP. En association avec les actions d'entreprise, ces signaux constituent les éléments nécessaires pour mener à bien l'activité d'entreprise spécifiée par un PIP particulier.  
 
  
## <a name="c"></a>C  
 **CertWizard**  
 Utilitaire permettant d'importer un certificat de signature ou de chiffrement à partir d'un fichier .pfx (.p12) ou .cer (.der) dans une banque de données privée ou publique en vue d'une utilisation avec BTARN. Un fichier .pfx (aussi appelé « échange d'informations personnelles » ou PKCS #12) contient une clé privée utilisée pour la signature ou le déchiffrement. Il est généralement protégé par un mot de passe. Un fichier .cer (fichier de certificat) conserve la clé publique pour le chiffrement et la validation de la signature.  
  
 **Chimiques normes de données Exchange (CHEMICAL) chem**  
 Normes uniformes d'échange de données développées spécifiquement pour l'achat, la vente et la livraison de produits chimiques. Ces normes sont basées sur les normes universelles d'échange de données électroniques (XML). BTARN prend en charge les normes Chem eStandards CIDX.  
  
 **cluster**  
 Groupe de processus d'entreprise de haut niveau, comme la gestion des commandes, la gestion des stocks, ou l'assistance et le support technique. Les clusters adressés par RosettaNet représentent les principaux processus d'entreprise dans le secteur de la logistique.  
  
## <a name="d"></a>D  
 **Nombre de Universal Numbering System (D-U-N-S) de données**  
 Numéro à neuf chiffres généré de manière séquentielle qui identifie de manière unique les emplacements de l'entreprise. Son étendue est globale.  
  
 **en-tête de remise**  
 Partie d'un message RosettaNet. L'en-tête de remise est un document XML qui identifie l'expéditeur du message, le destinataire et les informations d'instance du message.  
  
 **organisation de destination**  
 Organisation désignée dans un port d'échanges comme la destination des documents.  
  
 **algorithmes numériques**  
 Algorithme qui accepte un message comme entrée et produit un hachage ou digest de celui-ci. Cet ensemble de bits de longueur fixe très complexe dépend du contenu du message. Lors de la conception, vous devez faire en sorte qu'il soit extrêmement difficile pour quelqu'un de contrefaire un digest ou de modifier un message sans changer son digest. Les applications qui utilisent généralement des algorithmes digest reposent sur des schémas de signature numérique et d'authentification des messages. Parmi les algorithmes largement utilisés, citons MD5 et SHA1. BTARN prend en charge MD5 et SHA1 pour les messages entrants et uniquement SHA1 pour les messages sortants.  
  
 **définition de document**  
 Ensemble de propriétés représentant un document spécifique. Les propriétés de définition de document incluent un pointeur vers une spécification de document et peuvent inclure des champs de suivi global et des critères de sélection.  
  
 **instance de document**  
 Une représentation des données réelles qui sont envoyées à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Une instance de document diffère d'une spécification de document en ce sens que la spécification définit la structure des données, tandis qu'une instance de document est une représentation des données spécifiques contenues dans une structure.  
  
 **définition de type de document (DTD)**  
 Définition standard qui spécifie d'une part les éléments et les attributs qui peuvent être présents dans d'autres éléments et attributs et, d'autre part, les contraintes relatives à leur classement, leur fréquence et leur contenu.  
  
 **transaction double action**   
 Processus lors duquel un initiateur envoie une action de demande, puis reçoit un signal suivi d'une action de réponse du récepteur. L'initiateur termine le processus en envoyant un signal à l'action de réponse.  
  
## <a name="e"></a>E  
 **Extensible Markup Language (XML)**  
 Spécification développée par le World Wide Web Consortium (W3C) qui permet aux concepteurs de créer des balises personnalisées au-delà des capacités du code HTML standard. Bien que le langage HTML utilise des balises prédéfinies pour décrire les éléments de la page, le langage XML permet au développeur de la page de définir des balises. Les balises de n'importe quel élément de données, tel qu'un produit ou un montant dû, peuvent être utilisées pour des applications spécifiques. Les pages web peuvent ainsi fonctionner en tant qu'enregistrements de base de données.  
  
 **Feuille de style XSL (Extensible Language)**  
 Format de feuille de style pour les documents XML. XSL est utilisé pour définir l'affichage du langage XML, au même titre que les feuilles de style en cascade (CSS) sont utilisées pour définir l'affichage du langage HTML. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]utilise XSL comme langage de conversion entre deux spécifications.  
  
## <a name="g"></a>G  
 **Global Business Identification GBI)**  
 Identificateur unique permettant d'identifier des partenaires commerciaux. RosettaNet utilise le système de numérotation Dun and Bradstreet à neuf chiffres (DUNS) en tant que GBI.  
  
## <a name="h"></a>H  
 **organisation d’origine**   
 Alias identifiant votre organisation.  
  
## <a name="i"></a>I  
 **initiateur**  
 Rôle d'une organisation dans un processus de transaction ou de notification qui initie un processus à un partenaire commercial.  
  
## <a name="l"></a>L  
 **Application métier (LOB)**  
 Application qui communique avec BTARN en tant que système principal.  
  
 **Utilitaire de bouclage**  
 Utilitaire permettant aux développeurs de générer automatiquement un accord de bouclage, à savoir une copie miroir d'un accord d'une organisation d'origine à un partenaire. Vous pouvez ainsi effectuer des échanges de messages d'une organisation d'origine à un partenaire et d'un partenaire à une organisation d'origine sur un seul ordinateur.  
  
## <a name="m"></a>M  
 **carte**  
 Fichier XML qui définit les relations de correspondance entre les enregistrements et les champs de deux spécifications. Un mappage contient un fichier XSL feuille de style [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] utilise pour effectuer la transformation décrite dans le mappage. Les mappages sont créés dans le Mappeur BizTalk.
  
 **Mon organisation**  
 Représente votre organisation dans un accord de partenariat commercial.   
  
 **Polyvalent Internet Mail Extensions (MIME)**  
 Extension du protocole de messagerie Internet vous permettant d'utiliser le protocole pour échanger différents types de fichiers de données sur Internet : audio, vidéo, images et programmes d'application.  
  
## <a name="n"></a>N  
 **non répudiation**  
 Moyen permettant de s'assurer, d'une part, que l'expéditeur d'un message ne peut pas nier avoir envoyé le message et, d'autre part, que le destinataire ne peut pas nier avoir reçu le message. La non-répudiation d'un message entrant nécessite que le message soit enregistré par le récepteur et qu'il comporte une signature numérique faisant appel au certificat de signature de l'expéditeur pour garantir son authenticité. La non-répudiation d'un message sortant nécessite l'enregistrement du message d'accusé de réception (message entrant provenant du destinataire du premier message). Par ailleurs, le message doit comporter la signature numérique du digest du message d'origine faisant appel au certificat de signature du destinataire.   
  
 **notification**  
 Type de processus RNIF 1.1 où l'initiateur envoie un seul message pour informer le répondeur. Le répondeur est censé répondre avec un signal d'entreprise comme accusé de réception.  
  
 **Notification d’échec (PIP 0 a 1)**  
 PIP spécial qui indique les échecs de processus inattendus. L'initiateur ou le répondeur peut initier une notification d'échec. Celle-ci fait référence à un processus existant ou précédemment échangé. À la réception d'une notification 0A1, le destinataire s'assure que le processus référencé est considéré comme n'étant pas valide.  
  
## <a name="o"></a>O  
 **organisation**  
 Partenaire commercial ou unité commerciale capable d'effectuer des transactions commerciales.  
  
## <a name="p"></a>P  
 **empaquetage**  
 Processus de conversion d'un message RosettaNet dans sa représentation XML et vice versa.  
  
 **Partner Interface Process (PIP)**  
 Un processus d'interface entre partenaires (PIP) décrit un ensemble de documents commerciaux et les détails de l'accord, y compris des informations sur le contenu du document.  
  
 **Document de spécification PIP**  
 Document contenant des instructions sur les paramètres à utiliser quand vous créez une configuration de processus dans la console de gestion BTARN. Le document de spécifications PIP et le processus PIP sont disponibles en téléchargement sur le site de l'organisation RosettaNet (RosettaNet.org). Document contenant des instructions sur les paramètres à utiliser quand vous créez une configuration de processus dans la console de gestion BTARN. Le document de spécifications PIP et le processus PIP sont disponibles en téléchargement sur le site de l'organisation RosettaNet (RosettaNet.org).  
  
 **en-tête de préambule**  
 Nœud XML qui identifie le nom et la version de la norme à laquelle un message d'entreprise est conforme. Il est empaqueté avec les autres en-têtes pour former un message RosettaNet complet. Aussi appelé « préambule ».  
  
 **processus privé**   
 Processus d'entreprise internes à une organisation. BTARN implémente les processus privés en tant qu'orchestrations BizTalk à long terme.  
  
 **Processus profil de paramètre de Configuration (PC)**  
 Détermine la façon dont un accord de partenariat s'exécute. Utilisez le profil PC pour entrer les détails de configuration d'un processus PIP (Partner Interface Process) RosettaNet. Toutes les valeurs de configuration spécifiées dans une spécification PIP RosettaNet mappent à un élément dans le profil PCS. Vous pouvez utiliser un profil PCS pour plusieurs accords de partenariat.  
  
 **port**  
 Emplacement nommé qui utilise une implémentation spécifique. Dans le concepteur d'orchestration BizTalk, un port est défini par l'emplacement vers lequel les messages sont envoyés ou à partir duquel ces derniers sont reçus. Désigne également la technologie utilisée pour implémenter la communication. Seul le nom du port permet d'identifier l'emplacement.  
  
 **processus public**   
 Processus d'entreprise qui impliquent l'intégration à des partenaires commerciaux en tant que processus publics. BTARN implémente les processus publics en tant qu'orchestrations BizTalk à long terme. Une orchestration de processus publics s'exécute côté initiateur, et une autre côté répondeur. Le programme d'installation de BTARN fournit des versions des orchestrations de processus publics côté initiateur et côté répondeur pour RNIF 1.1 et RNIF 2.01. Ces orchestrations de processus publics implémentent tous les processus RNIF. Les processus publics masquent la complexité de la spécification RNIF du reste des composants. Outre l'application du flux de messages conformes à la spécification RNIF, le processus public détermine aussi les paramètres de suivi par défaut et fournit des informations sur l'état des processus au moment de l'exécution.  
  
## <a name="r"></a>R  
 **répondeur**  
 Rôle d'une organisation dans un processus de transaction ou de notification qui répond à une demande par un partenaire commercial.  
  
 **RosettaNet Implementation Framework (RNIF)**  
 Infrastructure de normes qui fournit des instructions d'implémentation aux entreprises souhaitant créer des composants d'application logicielle interopérables qui exécutent des processus PIP.  
  
 **Message RosettaNet**  
 Regroupement logique de l'en-tête de préambule, de l'en-tête de remise (dans le cas de RNIF 2.0), de l'en-tête de service et du contenu du service.  
  
 **RosettaNet, objet**  
 Message RosettaNet enveloppé pour la remise dans RosettaNet Implementation Framework version 1.1.  
  
## <a name="s"></a>S  
 **schéma**  
 Définition de la structure d'un fichier XML. Un schéma contient des informations sur les propriétés en rapport avec les enregistrements et les champs dans la structure.  
  
 **contenu du service**  
 Composant principal du message RosettaNet. Il s'agit d'un nœud XML qui représente le contenu d'entreprise spécifié par un processus PIP particulier.  
  
 **en-tête de service**  
 Document XML qui identifie les parties d'un message d'entreprise, notamment le processus PIP, l'activité et l'action d'entreprise, l'envoi et la réception de services, les partenaires commerciaux et les rôles.  
  
 **URL de signal**  
 URL vers laquelle l'organisation d'origine transmet un message de signal. Par exemple : http://FabrikamServer/BTARNApp/RNIFReceive.aspx.  
  
 **notification d’action unique**  
 Processus au cours duquel l'initiateur envoie un message d'action unique et le répondeur répond par un message.  
  
 **spécification**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]-schéma XML spécifique. Les spécifications créées dans l'Éditeur BizTalk peuvent reposer sur des normes, telles que EDIFACT, X12 et XML, ou sur des fichiers plats, tels que des fichiers plats délimités, positionnels, ou délimités et positionnels. Le Mappeur BizTalk utilise des spécifications, ouvertes sous forme de spécifications source et de destination, pour créer des mappages.  
  
 **URL de synchronisation**  
 URL utilisée par l'organisation d'origine pour établir des transactions synchrones avec le partenaire. Par exemple : http://FabikamServer/BTARNApp/RNIFReceive.aspx.  
  
 **transaction synchrone**  
 Processus au cours duquel l'initiateur retourne une réponse (action double) ou un signal (action unique) sur le même état HTTP sans fermer la connexion.  
  
## <a name="t"></a>T  
 **partenaire commercial**  
 Organisation externe avec laquelle votre organisation échange des données électroniques.  
  
 **accord de partenariat commercial**  
 Accord entre votre organisation et votre partenaire commercial. Un accord de partenariat commercial fait référence à un profil de paramètre de configuration de processus, à une organisation d'origine et à un partenaire. Il contient les paramètres de configuration spécifiques à l'accord.  
  
 **transaction**  
 Processus RNIF 1.1 où l'initiateur envoie un message RosettaNet, reçoit un signal, reçoit un message RosettaNet comme réponse et envoie un signal d'accusé de réception.  
  
## <a name="v"></a>V  
 **adaptateur de validation**  
 Application qui implémente l'interface de l'adaptateur de validation. Le répondeur public appelle l'adaptateur de validation quand il reçoit un message d'action (demande ou réponse). Il peut inclure n'importe quel ensemble de règles de validation qu'une entreprise peut exiger avant d'accepter un message entrant. BTARN effectue une validation en mode natif dans le pipeline de réception et dans les orchestrations publiques.  
  
## <a name="x"></a>X  
 **Planification XLANG**  
 Langage XML spécifique qui décrit le processus d'entreprise et l'intégration principale. Les processus d'entreprise spécifiques dans BTARN sont exprimés en langage XLANG. Une planification XLANG est enregistrée avec l'extension de nom de fichier .skx.  
  
