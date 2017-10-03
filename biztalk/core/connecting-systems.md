---
title: "Connexion de systèmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c4895e5-7272-415f-a0de-905256fa0a43
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67d042d067fa68c6d54d95f3b0e658c20db4961d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connecting-systems"></a>Connexion des systèmes
L'échange efficace de messages entre divers logiciels installés sur des ordinateurs différents est une condition absolument requise pour l'intégration. Étant donné la diversité des styles de communication existants, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] doit prendre en charge une variété de protocoles et de formats de message. Comme décrit ci-après, une part importante du moteur est dédiée au fonctionnement de cette communication. Il est toutefois important de garder à l'esprit que le moteur fonctionne uniquement avec des documents XML en interne. Quel que soit le format d'un message entrant, il doit être converti en un document XML après sa réception. De même, si un document ne peut pas être accepté par son destinataire au format XML, le moteur le convertit dans le format attendu par la cible.  
  
## <a name="sending-and-receiving-messages-adapters"></a>Envoyer et recevoir des Messages : cartes  
 Comme [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] doit communiquer avec des logiciels variés, il s'appuie sur des adaptateurs. Un adaptateur est une implémentation d'un mécanisme de communication, tel qu'un protocole particulier. Un développeur détermine les adaptateurs à utiliser dans une situation donnée. Il peut choisir l'un des adaptateurs intégrés proposés par [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], par exemple, ou utiliser un adaptateur créé pour un produit populaire, tel que Windows SharePoint Services, voire créer un adaptateur personnalisé. Dans chacun des cas, l'adaptateur est créé sur une base standard, nommée l'infrastructure d'adaptateurs. Cette infrastructure offre un moyen commun de créer et d'exécuter des adaptateurs et prend en charge les mêmes outils utilisés pour gérer tous les types d'adaptateur.  
  
 Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] inclut les adaptateurs natifs suivants :  
  
-   Adaptateur file : prend en charge la lecture et écriture aux fichiers dans le système de fichiers Windows. Comme les applications impliquées dans un processus d'entreprise peuvent souvent accéder au même système de fichiers, localement ou sur un réseau, l'échange de messages via des fichiers peut s'avérer pratique.  
  
-   L’adaptateur FTP : prend en charge d’envoyer et recevoir des informations entre un serveur de Transport protocole FTP (File) et le serveur BizTalk.  
  
-   Adaptateur HTTP : prend en charge d’envoyer et recevoir des informations à l’aide de HTTP. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] expose une ou plusieurs URL pour permettre à d'autres applications de lui envoyer des données et il peut utiliser cet adaptateur pour envoyer des données à d'autres URL.  
  
-   L’adaptateur MSMQ : prend en charge d’envoyer et recevoir des messages à l’aide de Microsoft Message Queuing (MSMQ).  
  
-   Adaptateur WebSphere MQ : prend en charge d’envoyer et recevoir des messages à l’aide WebSphere MQ d’IBM (anciennement MQSeries).  
  
-   L’adaptateur POP3 : prend en charge la réception de messages électroniques et leurs pièces jointes à l’aide de la version 3 du Post Office Protocol (POP3).  
  
-   Adaptateur SMTP : prend en charge l’envoi de messages à l’aide de SMTP. Les adresses de messagerie standard sont utilisées pour identifier les tiers.  
  
-   Adaptateur SOAP : prend en charge d’envoyer et recevoir des demandes de service Web pour permettre à BizTalk Server pour se connecter aux Services Web.  
  
-   Adaptateurs WCF : prend en charge d’envoyer et recevoir des informations à l’aide de Windows Communication Foundation.  
  
-   L’adaptateur Windows SharePoint Services (WSS) : prend en charge l’accès et la publication des documents stockés dans des bibliothèques de documents Microsoft Windows SharePoint.  
  
 Des adaptateurs pour les logiciels professionnels couramment utilisés sont également disponibles auprès de Microsoft, notamment :  
  
-   Adaptateur Microsoft BizTalk pour JD Edwards OneWorld  
  
-   Adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne  
  
-   Adaptateur Microsoft BizTalk pour PeopleSoft Enterprise  
  
-   Adaptateur Microsoft BizTalk pour TIBCO Rendezvous  
  
-   Adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service  
  
 Pour plus d’informations sur ces adaptateurs, consultez [adaptateurs dans BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
 Quel que soit l'adaptateur utilisé pour recevoir des données, les messages qu'il reçoit doivent généralement être traités avant qu'ils ne soient accessibles à une orchestration. De même, les messages sortants produits par une orchestration doivent souvent être traités avant leur envoi par un adaptateur.  
  
## <a name="processing-messages-pipelines"></a>Le traitement des Messages : Pipelines  
 Les applications sous-jacentes d’un processus d’entreprise communiquent en échangeant des différents types de documents : comme des bons de commande et des factures. Pour qu'une application [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] exécute un processus d'entreprise, elle doit pouvoir gérer correctement les messages contenus dans ces documents. Ce traitement pouvant impliquer plusieurs étapes, il est effectué par un pipeline de messages. Les messages entrants sont traités par l'intermédiaire d'un pipeline de réception, tandis que les messages sortants passent par un pipeline d'envoi.  
  
 Par exemple, même si de plus en plus d'applications sont conçues pour comprendre des documents XML, nombre d'entre elles (probablement la majorité actuellement) ne le peuvent pas. Comme [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] fonctionne uniquement avec des documents XML en interne, il doit proposer un moyen de convertir d'autres formats depuis et vers le format XML. D'autres services peuvent également être requis, notamment l'authentification de l'expéditeur d'un message. Pour traiter ces tâches et d'autres encore de manière modulaire, mais personnalisable, un pipeline est créé à partir d'un certain nombre d'étapes, chacune contenant un ou plusieurs composants .NET ou COM (Component Object Model). Chaque composant gère une partie donnée du traitement des messages. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] propose plusieurs composants standard qui couvrent les situations les plus courantes. Si toutefois ils ne suffisent pas, les développeurs peuvent également créer des composants personnalisés pour les pipelines de réception et d'envoi.  
  
 ![](../core/media/understandingbts-05-pipelinereceive.gif "UnderstandingBTS_05_PipelineReceive")  
  
 Le schéma ci-avant illustre les étapes dans un pipeline de réception, ainsi que les composants standard fournis par chacune d'elles. Ces étapes et leurs composants associés sont les suivants :  
  
-   Décoder : [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] fournit un seul composant standard pour cette étape, le décodeur MIME/SMIME. Ce composant peut gérer des messages et leurs pièces jointes, au format MIME ou S/MIME (Secure MIME). Il convertit ces deux types de message en XML et peut décrypter les messages S/MIME et vérifier leur signature numérique.  
  
-   Désassembler : Trois composants standard sont fournies. Le composant Désassembleur de fichier plat transforme des fichiers plats en documents XML. Ces fichiers peuvent être positionnels (chaque enregistrement a les mêmes longueur et structure) ou délimités (un caractère désigné sert à séparer les enregistrements dans le fichier). Le deuxième composant standard, le Désassembleur XML, analyse les messages entrants qui sont déjà décrits à l'aide de XML. Le troisième composant standard, peu utilisé à l'heure actuelle, est le Désassembleur BizTalk Framework. Il accepte des messages envoyés à l’aide du mécanisme de messagerie fiable défini par BizTalk Framework, qui a été implémenté dans BizTalk Server 2000.  
  
-   Valider : [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] fournit un composant valideur XML pour cette étape. Comme son nom l'indique, ce composant valide un document XML, produit à l'étape Désassembler, par rapport à un schéma ou groupe de schémas spécifié, en renvoyant une erreur si le document n'est pas conforme à l'un de ces schémas.  
  
-   Résolution tiers : le seul composant standard pour cette étape, la résolution du tiers, tente de déterminer l’identité de l’expéditeur de ce message. Si le message a été signé numériquement, la signature sert à rechercher une identité Windows dans la base de données de gestion [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] (comme décrit ci-après, cette base de données est également utilisée par les outils de gestion de BizTalk Server). Si le message comporte l'identificateur de sécurité (SID) authentifié d'un utilisateur Windows, cette identité est utilisée. Si aucun mécanisme ne réussit, une identité anonyme par défaut est attribuée à l'expéditeur du message.  
  
 ![](../core/media/understandingbts-06-pipelinesend.gif "UnderstandingBTS_06_PipelineSend")  
  
 Des messages sortants peuvent également passer par plusieurs étapes, comme défini par le pipeline d'envoi utilisé. La figure ci-avant montre les étapes et les composants standard pour un pipeline d'envoi, Celles-ci sont les suivantes :  
  
-   Ne préassembler : Aucun composant standard est fournies. Au lieu de cela, des composants personnalisés peuvent être insérés ici, si nécessaire.  
  
-   Assembler : À l’instar de la phase de désassemblage d’un pipeline de réception, cette étape comporte également trois composants standard. L'Assembleur de fichier plat convertit un message XML en un fichier plat positionnel ou délimité, et l'Assembleur XML prend en charge l'ajout d'une enveloppe et d'autres modifications apportées à un message XML sortant. Le troisième composant, l'Assembleur BizTalk Framework, regroupe des messages pour une transmission fiable, à l'aide de la technologie de messagerie BizTalk Framework.  
  
-   Encoder : [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] définit un seul composant standard pour cette étape, l’encodeur MIME/SMIME. Ce composant regroupe les messages sortants au format MIME ou S/MIME. Si S/MIME est utilisé, le message peut également être signé numériquement et/ou crypté.  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] définit des pipelines par défaut, notamment une simple paire envoi/réception qui peut être utilisée pour gérer des messages déjà exprimés en XML. Un développeur peut également créer des pipelines personnalisés à l'aide du Concepteur de pipeline. Cet outil, exécuté dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dispose d'une interface graphique qui permet au développeur de glisser et déposer des composants pour créer des pipelines au comportement requis.  
  
## <a name="choosing-messages-subscriptions"></a>Choix des Messages : les abonnements  
 Une fois qu'un message est passé par un adaptateur et un pipeline de réception, il convient de déterminer sa destination. Le plus souvent, un message est destiné à une orchestration, mais il se peut qu'un message aille directement à un pipeline d'envoi, permettant à [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] d'être utilisé en tant que système de messagerie pur. Dans les deux cas, cette correspondance de messages avec leurs destinations s'effectue à l'aide d'abonnements.  
  
 Lorsqu'un message est traité par un pipeline de réception, un contexte de message est créé, avec diverses propriétés du message. Une orchestration ou un pipeline d'envoi peut s'abonner aux messages en fonction des valeurs de ces propriétés. Par exemple, une orchestration peut créer un abonnement qui correspond à tous les messages de type « Facture », tous les messages de type « Facture » reçus de QwickBank ou tous les messages de type « Facture » reçus de QwickBank pour un montant supérieur à 10 000 $. Toutefois, il est spécifié qu'un abonnement renvoie à son abonné uniquement les messages qui répondent aux critères définis dans l'abonnement. Un message reçu peut initier un processus d'entreprise en instanciant une orchestration ou activer une autre étape dans un processus d'entreprise déjà en cours. De même, lorsqu'une orchestration reçoit un message, il est mis en correspondance avec un pipeline d'envoi, en fonction d'un abonnement établi par ce pipeline.  
  
-   Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], il est également possible de s'abonner à des conditions d'erreur spécifiques. Un message d'erreur peut être traité d'une manière particulière ou routé vers une destination spécifique, telle qu'un dossier Windows SharePoint Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie BizTalk Server](../core/the-biztalk-server-messaging-engine.md)   
 [Publication et l’abonnement d’Architecture](../core/publish-and-subscribe-architecture.md)   
 [Adaptateurs](../core/adapters.md)   
 [Pipelines](../core/pipelines.md)