---
title: Samples3 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SDK samples
- examples, developing
- developing, examples
ms.assetid: b940111e-4f71-494b-b7a3-d2e8310bea51
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba22559730a458a3c1968c991008c67ac0e4f5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="samples"></a>Exemples
Cette section décrit les exemples inclus dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel (SDK). Cette section fournit des informations détaillées sur chaque échantillon, y compris comment générer l’exemple, à l’exécution et aux résultats attendus.  
  
 Les exemples sont inclus dans le \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\ dossier.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   Dossier d’exemples de carte  
  
    -   [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md). Montre comment inclure un mécanisme de notification de message.  
  
    -   [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md). Montre comment exécuter des règles de validation spéciales sur un message.  
  
-   Dossier d’exemples de messagerie  
  
    -   [Exemple de FileTransport](../../adapters-and-accelerators/accelerator-rosettanet/filetransport-sample.md). Montre comment configurer BTARN pour utiliser les ports du fichier.  
  
    -   [Exemple de GetMessages](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md). Montre comment récupérer des messages à partir d’une des tables des non répudiation ou l’une des tables de métier (LOB).  
  
    -   [Exemple de soumission ASPX de message](../../adapters-and-accelerators/accelerator-rosettanet/message-submission-aspx-sample.md). Fournit des exemples de code .aspx pour l’envoi de contenu de service à un processus privé. Fournit également des HTML pour l’envoi d’un message d’action de processus PIP (Partner Interface) pour le contenu de ce service.  
  
    -   [Exemple de suivi](../../adapters-and-accelerators/accelerator-rosettanet/tracking-sample.md). Fournit des exemples de code .aspx pour afficher l’état des messages envoyés et reçus avec BTARN.  
  
-   Dossier d’exemples d’orchestration  
  
    -   [Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md). Montre comment automatiser un processus d’entreprise impliquant des PIP à l’aide d’un mappage de transformation d’un message de demande à un message de réponse.  
  
    -   [Double Orchestration Action PIPAutomation](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md). Montre comment automatiser un processus d’entreprise avec détermination automatique du type de message de réponse en fonction du type de message entrant.  
  
    -   [Demande de 3A2 d’exemple de mappage de réponse 3A2](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md). Montre comment mapper un schéma de demande 3A2 à un schéma de réponse 3A2.  
  
    -   [Demande de 3 a 4 pour un exemple de mappage de réponse 3 a 4](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md). Montre comment mapper un schéma de demande de 3 a 4 à un schéma de réponse 3 a 4.  
  
    -   [Exemple de PrivateInitiator](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md). Montre comment créer une orchestration de processus privé initiateur.  
  
    -   [Exemple de PrivateResponder](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md). Montre comment créer une orchestration de processus privé répondeur.  
  
    -   [Exemple HubScenario](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md). Montre comment transformer un message envoyé à un hub intermédiaire, dans un message à envoyer au destinataire final.  
  
-   Dossier d’exemples de pipeline  
  
    -   [Pipeline d’envoi](../../adapters-and-accelerators/accelerator-rosettanet/send-pipeline.md). Montre comment traiter les messages XML sortants dans les messages RNIF équivalentes à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines.  
  
    -   [Pipeline de réception](../../adapters-and-accelerators/accelerator-rosettanet/receive-pipeline.md). Montre comment traiter les messages RNIF entrants dans les messages XML équivalents à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines.  
  
    -   [Exemple de Pipeline message Editor](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-sample.md). Montre comment créer un composant de pipeline personnalisé pour modifier les messages entrants.  
  
-   Dossier d’exemples de schéma  
  
    -   [Exemples de schémas](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md). Décrit les schémas de l’exemple fournis dans le Kit de développement, y compris les schémas XML du PIP, les schémas de nouvelle génération de RosettaNet et schémas RNIF. Les pointeurs vers les procédures d’utilisation de ces schémas.  
  
-   Dossier exemple d’Application Web  
  
    -   [RNIFSend](../../adapters-and-accelerators/accelerator-rosettanet/rnifsend.md). Montre comment personnaliser la page ASPX qui envoie des messages RNIF à partir de l’initiateur au répondeur.  
  
    -   [RNIFReceive](../../adapters-and-accelerators/accelerator-rosettanet/rnifreceive.md). Montre comment personnaliser la page ASPX qui reçoit les messages RNIF au répondeur.  
  
-   [L’arrêt et démarrage des Orchestrations, Ports d’envoi et emplacements de réception par programmation](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md). Montre comment arrêter et démarrer toutes les orchestrations, ports d’envoi et emplacements de réception en tant que groupe ou individuellement.