---
title: "Cycle de vie d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, orchestrations
- messages, host instances
- messages, receive locations
- send ports, about send ports
- processing, messages
- messages, processing
- host instances, about host instances
- receive locations, about receive locations
- hosts, about hosts
- messages, lifecycle
- MessageBox database, about MessageBox database
- receive ports, about receive ports
- send port groups, about send port groups
- messages, hosts
- messages, send port groups
- messages, receive ports
- orchestrations, about orchestrations
- messages, send ports
ms.assetid: d2374f86-9b5f-404f-ba7b-9cab69873fa8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e05aca3ec819fb8615552c5ed57114032d7ea60b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lifecycle-of-a-message"></a>Cycle de vie d'un message
L'illustration suivante fournit une vue d'ensemble détaillée de l'architecture BizTalk Server au niveau messagerie.  
  
 ![Architecture de messagerie BizTalk Server](../core/media/arch-messaging-01.gif "arch_messaging_01")  
  
 Dans cette vue simplifiée, un message est reçu par le biais d'un emplacement de réception défini dans un port de réception donné. Ce message est traité par l'emplacement de réception, puis publié dans la base de données MessageBox, le principal mécanisme de persistance et de routage de BizTalk Server. Le MessageBox évalue les abonnements actifs, puis achemine le message aux orchestrations et ports d'envoi disposant d'abonnements correspondants. Les orchestrations peuvent traiter le message et publier des messages via le MessageBox sur un port d'envoi à partir duquel il sera poussé vers sa destination finale.  
  
 Les composants clés suivants sont impliqués dans le traitement des messages BizTalk Server.  
  
## <a name="receive-ports-and-receive-locations"></a>Ports de réception et emplacements de réception  
 A *port de réception* est une collection d’un ou plusieurs emplacements de réception qui définissent les points d’entrée spécifiques de BizTalk Server. A *emplacement de réception* est la configuration d’un seul point de terminaison (URL) pour recevoir des messages. L'emplacement contient des informations de configuration pour un adaptateur de réception et un pipeline de réception. Le *adaptateur* est responsable de la partie de transport et de communication de la réception d’un message. En guise d'exemple, on peut citer les adaptateurs FILE et SOAP, chacun recevant des messages de différents types de sources. Le pipeline de réception se charge de préparer le message en vue de sa publication dans le MessageBox. A *pipeline* est une série de composants qui sont exécutées dans l’ordre, chacun appliquant un traitement spécifique à un message de chiffrement/déchiffrement, l’analyse ou la validation. Pour plus d’informations sur les pipelines, des ports, de réception et emplacements de réception, consultez [artefacts](../core/artifacts.md).  
  
## <a name="send-ports-and-send-port-groups"></a>Ports d'envoi et groupes de ports d'envoi  
 A *port d’envoi* est la combinaison d’un pipeline d’envoi et un adaptateur d’envoi. Un groupe de ports d'envoi regroupe des ports d'envoi et fonctionne comme une liste de distribution de courrier électronique. Un message envoyé à un groupe de ports d'envoi sera envoyé à tous les ports de ce groupe. Le pipeline d'envoi sert à préparer un message provenant de BizTalk Server en vue de sa transmission à un autre service. L'adaptateur d'envoi se charge d'envoyer réellement le message à l'aide d'un protocole spécifique comme SOAP ou FTP. Pour plus d’informations sur les ports d’envoi et groupes de ports d’envoi, consultez [artefacts](../core/artifacts.md).  
  
## <a name="orchestrations"></a>Orchestrations  
 Les orchestrations peuvent s'abonner à des messages (réception) et les publier (envoi) via le MessageBox. Les orchestrations peuvent en outre construire de nouveaux messages. Les messages sont reçus par le biais du mécanisme d'abonnement et de routage présenté précédemment. Lorsque des abonnements sont définis pour les orchestrations, une nouvelle instance est activée et le message est remis, ou, dans le cas d'abonnements d'instance, l'instance est réalimentée si nécessaire et le message est ensuite remis. Lorsque des messages sont envoyés à partir d'une orchestration, ils sont publiés dans la base de données MessageBox de la même manière qu'un message qui arrive sur un emplacement de réception avec les propriétés appropriées et qui est inséré dans la base de données pour être utilisé dans le routage. Pour plus d’informations sur les orchestrations, consultez [artefacts](../core/artifacts.md).  
  
## <a name="messagebox-database"></a>Base de données MessageBox  
 Le cœur du moteur de publication/d'abonnement dans BizTalk Server est la base de données MessageBox. MessageBox est constitué de deux composants : un ou plusieurs bases de données Microsoft SQL Server et l’Agent des messages. La base de données SQL Server assure le stockage permanent de nombreuses choses comme les messages, les propriétés des messages, les abonnements, les états des orchestrations, les données de suivi et les files d'attente hôte pour le routage. Pour plus d’informations sur la base de données MessageBox, consultez [la base de données MessageBox](../core/the-messagebox-database.md).  
  
## <a name="hosts-and-host-instances"></a>Hôtes et instance d'hôte  
 A *hôte* est une représentation logique d’un processus de Microsoft Windows qui exécute des artefacts BizTalk Server comme ports d’envoi et orchestrations. A *instance d’hôte* est la représentation physique d’un ordinateur hôte sur un serveur spécifique. Un hôte peut être de type In-process, ce qui signifie qu'il est possédé et géré par BizTalk Server, ou être un hôte isolé, c'est-à-dire que le code BizTalk Server s'exécute dans un processus qui n'est pas contrôlé par BizTalk Server. Les services Internet (IIS), qui hébergent la fonctionnalité de réception des adaptateurs HTTP et SOAP, illustrent parfaitement ce qu'est un hôte isolé. Les hôtes sont définis pour un groupe BizTalk Server entier, c'est-à-dire un ensemble de serveurs BizTalk Server partageant une même configuration, des MessageBoxes, des ports, etc. Pour plus d’informations sur les hôtes et les instances d’hôte, consultez [entités](../core/entities.md).  
  
## <a name="saving-a-message-body"></a>Enregistrement d'un corps de message  
 Trois méthodes permettent d'enregistrer un corps de message.  
  
### <a name="from-the-admin-mmc-group-hub-page-queries"></a>À partir des requêtes de la page Hub du groupe de la console MMC d'administration  
 Cette méthode s'applique aux messages de la base de données MessageBox uniquement.  
  
-   Affichez une instance de service.  
  
-   Ouvrez le **détails de l’Instance Service** boîte de dialogue.  
  
-   Cliquez sur le **onglet Messages** pour afficher la liste de messages associés à cette instance.  
  
-   Soit le message d’avec le bouton droit, puis cliquez sur **enregistrer**.  
  
     -ou-  
  
-   Double-cliquez sur le message pour l’ouvrir dans le **l’Afficheur des messages**, puis cliquez sur **enregistrer**.  
  
### <a name="from-the-operations-om"></a>À partir du modèle OM (Operations object model)  
  
-   Utilisez **GetInstance** pour récupérer un objet de l’Instance de Service.  
  
-   Utilisez **[] de Instance.Messages** pour énumérer tous les messages qui fait actuellement référence à l’instance de service.  
  
-   Utilisez les méthodes sur l’objet de message telles que **Message.BodyPart []** et **Message.Context []** d’accès et l’enregistrer.  
  
### <a name="from-the-dta"></a>À partir de DTA  
  
-   Récupérer des messages à partir de DTA à l’aide du **GetTrackedInstance** et **GetTrackedmessage** appels d’API.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)