---
title: "Fonctionnalités de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TIBCO Enterprise adapters, message delivery
- architecture, TIBCO Enterprise adapters
- TIBCO Enterprise adapters, architecture
- TIBCO Enterprise adapters, data validation
ms.assetid: ede748ce-3f28-4942-b2bd-e38e5f1b0f54
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffa789837973f8c8c7bb6c5bd428e36c562df96c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-features"></a>Fonctionnalités de l’adaptateur
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service permet la publication et l'abonnement aux files d'attentes et aux rubriques gérées par TIBCO EMS à l'aide de BizTalk Server et du Kit de développement logiciel TIBCO. L'adaptateur intègre les messages TIBCO EMS de manière rapide, simple et fiable. Il échange des formats de données XML entre les serveurs TIBCO EMS et Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour fournir une infrastructure d'applications étroitement intégrée et fiable. Il fournit des opérations d'intégration d'adaptateur de réception et de transmission offrant une gestion des processus d'entreprise de bout en bout à l'aide de schémas XML.  
  
## <a name="data-validation"></a>Validation des données  
 L'adaptateur BizTalk pour TIBCO EMS s'exécute de façon in-process avec l'hôte BizTalk Server en tant qu'adaptateur natif, étroitement intégré, et valide la configuration du port au moment de la configuration. Il valide les données autant que possible, par exemple, nom valide, numéro valide, plage valide. Il n'essaie pas d'établir une connexion. Par conséquent, l'hôte, la destination du port, l'utilisateur et le mot de passe ne sont pas validés tant qu'il y a un appel au moment de l'exécution, auquel cas une erreur est consignée.  
  
## <a name="message-delivery"></a>Remise des messages  
 L'adaptateur BizTalk pour TIBCO EMS garantit la remise unique des messages. Les messages qui n'atteignent pas EMS sont marqués comme autorisant une nouvelle tentative lors de l'interruption. Il peut y avoir des exceptions, par exemple, lorsqu'une configuration du port invalide existe au moment de l'exécution.  
  
 L’adaptateur accepte les types de messages EMS texte.  L’adaptateur prend en charge les transactions pour les messages envoyés à EMS, et la prise en charge des transactions est contrôlée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  La connexion entre l'adaptateur BizTalk pour TIBCO EMS et le serveur EMS n'est pas sécurisée. Elle n'est pas prise en charge par le Kit de développement logiciel TIBCO EMS fourni.  
  
 L'adaptateur prend en charge toutes les propriétés JMS standard et les extensions EMS. Ces propriétés sont placées dans le contexte du message BizTalk afin d'être disponibles pour une orchestration.  
  
## <a name="general-adapter-features"></a>Fonctionnalités générales de l'adaptateur  
 L'adaptateur BizTalk pour TIBCO EMS constitue un moyen d'échanger des données commerciales en temps réel entre les systèmes TIBCO EMS et BizTalk Server. L’adaptateur permet de l’interaction entre une application XML et les TIBCO EMS. Il permet aux applications XML le traitement entrant et sortant avec TIBCO EMS.  
  
 L'adaptateur accepte les messages XML qui permettent aux applications BizTalk Server de communiquer avec TIBCO EMS à l'aide d'un des éléments suivants :  
  
-   Adaptateur de transmission qui utilise un port d'envoi unidirectionnel statique pour envoyer un message à TIBCO EMS  
  
-   Adaptateur de réception qui utilise un port de réception unidirectionnel statique pour recevoir des messages de TIBCO EMS  
  
### <a name="transmit-adapter-architecture-send--static-one-way"></a>Architecture de l'adaptateur de transmission : envoi – unidirectionnel statique  
 Dans le scénario d'envoi unidirectionnel, le port d'envoi est configuré pour envoyer des messages à une file d'attente / rubrique. L'adaptateur BizTalk pour TIBCO Enterprise Message Service transmet la demande au serveur TIBCO EMS sur la file d'attente / rubrique spécifiée. L'adaptateur envoie le message au système TIBCO EMS à l'aide du protocole de communication TIBCO EMS. Le système TIBCO EMS reçoit les demandes et exécute la logique d'entreprise. Pour effectuer des appels dans TIBCO EMS, vous devez fournir l'adaptateur avec les informations de configuration permettant d'accéder au serveur TIBCO EMS.  
  
 L'image suivante illustre l'opération d'envoi unidirectionnel de l'adaptateur.  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
### <a name="receive-adapter-architecture-receive--static-one-way"></a>Architecture de l'adaptateur de réception : réception – unidirectionnel statique  
 Dans le scénario de réception unidirectionnelle, l'emplacement de réception est configuré pour recevoir des messages sur une file d'attente / rubrique EMS. L'adaptateur BizTalk pour TIBCO EMS écoute les messages sur une file d'attente / rubrique spécifiée et envoie les messages reçus à BizTalk Server.  
  
 L'image suivante illustre l'opération de réception unidirectionnelle de l'adaptateur.  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’Applications](../core/developing-applications5.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)