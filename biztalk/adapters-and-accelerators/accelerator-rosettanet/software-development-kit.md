---
title: "Kit de développement logiciel pour l’accélérateur RosettaNet dans BizTalk Server | Documents Microsoft"
description: Liste des utilitaires et des exemples dans le SDK de BTARN pour BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36a1b283-26e1-407e-afc4-8879ef0d1672
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81bf0f7f0947875540d835ced3726224525f23a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="software-development-kit"></a>Kit de développement logiciel
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] inclut un kit de développement logiciel (SDK) qui inclut la référence et le guide du programmeur complète. En outre, le SDK inclut des utilitaires et des exemples qui peuvent simplifier vos opérations et l’intégration back-end.  
  
## <a name="utilities"></a>Utilitaires  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut les exemples suivants :  
  
|Utilitaire|Utiliser|  
|-------------|---------|  
|[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md)|Pour annuler le déploiement de tous les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] artefacts à partir de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe de l’ordinateur hôte|  
|[BtarnConfig](../../adapters-and-accelerators/accelerator-rosettanet/btarnconfig.md)|Pour importer ou exporter des données de configuration|  
|[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)|Pour importer un certificat|  
|[LOBApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)|Pour envoyer un message d’action ou d’une réponse à un partenaire commercial|  
|[LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)|Pour envoyer un message d’action ou d’une réponse à partir d’une page ASPX à un partenaire commercial|  
|[Bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)|Pour générer un accord de bouclage, paramètre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configurer sur un seul ordinateur|  
|[Composant de Pipeline message Editor](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-component.md)|Pour modifier automatiquement n’importe quelle partie d’un message à parties multiples dans un envoi ou le pipeline de réception|  
|[Message Inspector Pipeline Component](../../adapters-and-accelerators/accelerator-rosettanet/message-inspector-pipeline-component.md)|Pour examiner toutes les parties d’un message à parties multiples et le contexte du message|  
|[SchemaValidator](../../adapters-and-accelerators/accelerator-rosettanet/schemavalidator.md)|Pour résoudre les problèmes liés à une instance de message|  
|[TestCrypto](../../adapters-and-accelerators/accelerator-rosettanet/testcrypto.md)|Pour résoudre les échecs de déchiffrement des messages|  
  
## <a name="samples"></a>Exemples  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut les exemples suivants :  
  
|Exemple|Montre|  
|------------|------------------|  
|[ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)|Comment envoyer des notifications quand un message est arrivé.|  
|[ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)|Comment exécuter des règles de validation spéciales sur un message reçu par l’orchestration du partenaire commercial|  
|[Exemple de FileTransport](../../adapters-and-accelerators/accelerator-rosettanet/filetransport-sample.md)|Comment utiliser des ports de fichier, au lieu des ports SQL|  
|[Exemple de GetMessages](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md)|Comment récupérer des messages à partir d’une des tables non répudiation ou une des tables dans un format lisible LOB|  
|[Exemple ASPX d’envoi de message](../../adapters-and-accelerators/accelerator-rosettanet/message-submission-aspx-sample.md)|Comment envoyer du contenu de service à un processus privé|  
|[Exemple de suivi](../../adapters-and-accelerators/accelerator-rosettanet/tracking-sample.md)|Comment afficher l’état actuel de messages et de processus|  
|[Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)|Comment implémenter un processus privé répondeur incorporant une règle d’entreprise|  
|[Orchestration Action PIPAutomation double](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)|Comment implémenter une orchestration pour générer automatiquement des réponses pour les processus d’Interface double action partenaires (PIP)|  
|[Demande de 3A2 d’exemple de mappage de réponse 3A2](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)|Comment mapper une demande 3A2 à une réponse 3A2|  
|[Demande de 3 a 4 pour un exemple de mappage de réponse 3 a 4](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)|Comment mapper une demande de 3 a 4 à une réponse 3 a 4|  
|[Exemple de PrivateInitiator](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)|Comment implémenter le processus privé initiateur|  
|[Exemple de PrivateResponder](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)|Comment implémenter le processus privé répondeur|  
|[Exemple HubScenario](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md)|Comment gérer la transmission des messages dans un scénario de concentrateur|  
|[Pipeline d’envoi](../../adapters-and-accelerators/accelerator-rosettanet/send-pipeline.md)|L’implémentation d’un pipeline d’envoi|  
|[Pipeline de réception](../../adapters-and-accelerators/accelerator-rosettanet/receive-pipeline.md)|L’implémentation d’un pipeline de réception|  
|[Exemple de Pipeline message Editor](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-sample.md)|Comment modifier le contenu d’un message entrant|  
|[Exemples de schémas](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)|Comment modifier des schémas|  
|[RNIFSend](../../adapters-and-accelerators/accelerator-rosettanet/rnifsend.md)|Comment préparer un message pour le traitement RNIF et envoyer le message à la page RNIFReceive.aspx au répondeur|  
|[RNIFReceive](../../adapters-and-accelerators/accelerator-rosettanet/rnifreceive.md)|Comment recevoir un message RNIF et le préparer pour le traitement par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus public|  
|[L’arrêt et démarrage des Orchestrations, Ports d’envoi et emplacements de réception par programmation](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)|Comment arrêter et démarrer ces artefacts dynamiquement|  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [Exemples](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)