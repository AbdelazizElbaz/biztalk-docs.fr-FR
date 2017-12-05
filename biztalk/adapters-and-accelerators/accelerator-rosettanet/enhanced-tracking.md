---
title: "Amélioré suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracking
ms.assetid: 8adf78f0-ab0f-44d4-aa5b-9546e2bdf01f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0212caafb34ca76988e1a863899021b44ac416fb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="enhanced-tracking"></a>Suivi amélioré
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fournit une capacité améliorée pour effectuer le suivi des messages et processus. Les fonctionnalités natives d’analyse BAM (Business Activity) dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] consiste à effectuer le suivi des métadonnées uniquement. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]assure le suivi de message contenu : contenu du service et les en-têtes.  
  
 Le tableau suivant présente la gamme complète des données de suivi des modifications dans [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. Cette rubrique traite des processus et le suivi des messages. Pour plus d’informations sur les données de non-répudiation, consultez [de traitement du Message RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md).  
  
|Informations suivies|Fonctionnalité|Accès utilisateur|  
|-------------------------|-------------|-----------------|  
|Processus de RosettaNet et suivi des messages|Par le composant BAM (avec les tables de base de données et les vues de données) pour les métadonnées et les interfaces propriétaires pour le corps du message|Interface utilisateur BAM ou interface utilisateur personnalisée|  
|Erreurs et événements|Via le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements|Journal des événements|  
|Données de non-répudiation|Par le biais des interfaces propriétaires (formats des messages sont stockés de câble)|Tables MessageStorageIn et MessageStorageOut de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données d’Archive et par le biais du SDK|  
  
## <a name="process-and-message-tracking"></a>Processus et le suivi des messages  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]effectue le suivi de deux activités de base : l’activité de processus et l’activité des messages. L’activité de processus effectue le suivi de traitement des messages dans les orchestrations de processus publics. Le message activité pistes traitement des messages dans envoyer ou recevoir des pipelines.  
  
 L’activité de processus effectue le suivi des métadonnées de la totalité du message. L’activité message effectue le suivi des métadonnées d’activité de processus et le contenu du message.  
  
### <a name="process-activity"></a>Activité de processus  
 Chaque fois qu’une orchestration de processus publics (initiateur ou répondeur) est instanciée, le processus public crée un enregistrement d’activité de processus dans la base de données de suivi BAM. À différents points dans le processus public, l’orchestration enregistre les métadonnées de suivi. L’activité de processus s’arrête lorsque l’orchestration s’arrête.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]assure le suivi terminer les métadonnées pour le processus en deux instances :  
  
-   Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] est un répondeur, et il reçoit un message d’action de demande  
  
-   Lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] est un initiateur et reçoit un message de demande à partir de l’application de métier (LOB).  
  
 Chaque fois que [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoie ou reçoit un message, le processus public met à jour l’état de l’activité de processus.  
  
### <a name="message-activity"></a>Activité de message  
 L’activité de message assure le suivi des messages via l’envoi et les pipelines de réception. Chaque fois qu’un envoi ou pipeline de réception traite un message, le pipeline crée une activité de message. Le pipeline crée un enregistrement d’activité de message dans le suivi de base de données et un enregistrement du message dans BAM le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données de l’Archive.  
  
 L’activité des messages enregistre le contenu du message, y compris les en-têtes et le contenu de service. Dans le pipeline de réception, si le décodeur MIME réussit, l’activité enregistre les quatre parties du contenu du message au format XML au format de texte dans la colonne ContentXml de la table le MessageContent. Si le décodeur MIME échoue, l’activité enregistre le contenu du message au format binaire dans la colonne ContentBinary de la table le MessageContent.  
  
### <a name="use-of-tracking-data-in-correlation"></a>Utilisation de données de corrélation de suivi  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]suit les informations requises pour mettre en corrélation chaque processus pour tous les messages échangés pour un PIP spécifique (positifs ou négatifs de signaux et les signaux de demande et de réponse). Il suit également les informations utilisées pour mettre en corrélation un message 0 a 1, si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoie une Notification d’échec pour ce PIP. La combinaison de l’ID d’instance PIP, nom du tiers initiateur et nom de tiers de destination déterminent les messages liés à une activité.  
  
### <a name="tracking-databases"></a>Bases de données de suivi  
 Les activités de processus et de message enregistrement le suivi des métadonnées dans le BAMPrimaryImport [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données. Dans cette base de données, tables dont les noms commencent par le préfixe « bam_Process » stockent les données de suivi des activités de processus et tables dont les noms commencent par le préfixe « bam_Message » stockent les données de suivi d’activité d’un message. Chaque processus distinct ou l’activité du message a un seul enregistrement correspondant dans les tables. Informations sur les deux activités et le suivi des métadonnées, sont incluses dans les tables de métadonnées dont le nom commence par le préfixe « bam_Metadata ».  
  
 Vous pouvez utiliser les données dans la base de données de suivi BAMPrimaryImport à l’aide des vues suivantes. Celles-ci et autres vues sont disponibles dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nœud de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.  
  
|Mode de suivi|data|  
|-------------------|----------|  
|bam_Process_AllInstances|État du processus RosettaNet défini par le PIP|  
|bam_Message_AllInstances|États de tous les messages|  
|bam_Process_CompletedInstances|État des processus terminés|  
  
 L’activité des messages enregistre le contenu du message dans la table le MessageContent de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données de l’Archive. Vous pouvez examiner le contenu en exécutant une requête sur la table le MessageContent, à l’aide de l’identificateur unique pour le message. L’activité stocke l’identificateur unique dans la colonne ContentKey de l’activité message tables de suivi, avec le préfixe « bam_Message.  
  
> [!IMPORTANT]
>  L’activité message partage le contenu du message en texte clair dans la table le MessageContent de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données de l’Archive. Ceci se produit dans tous les scénarios de suivi, y compris celles figurant dans lequel les messages sont chiffrés ou signés. Si vous êtes inquiet de l’accessibilité du contenu du message, vous pouvez restreindre l’accès à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données de l’Archive.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise le suivi API BAM pour enregistrer les données de suivi.  
  
### <a name="status-codes"></a>Codes d’état  
 Les tables bam_Process_Active et bam_Process_Completed dans la base de données inclus une colonne d’état qui indique l’état du processus. Le tableau suivant montre les valeurs pour chaque code d’état.  
  
|Code de l'état|État du processus|  
|-----------------|-------------------|  
|-1000|ActivityNotPresentFatalError|  
|-500|UnexpectedFatalError|  
|-100|Initiated0A1|  
|-99|TerminatedOnError<br /> (N’importe quel autre fin que terminé par 0 a 1)|  
|-85|TerminatedBy0A1|  
|-75|TimedOutOnResponseSignal|  
|-50|TimedOutOnResponse|  
|-25|TimedOutOnActionSignal|  
|0|RegisteredActivity|  
|1|ActivityToBeInitiated|  
|10|ReceivedAction ou SentAction|  
|25|ReceivedActionSignal ou SentActionSignal|  
|35|ReceivedActionSignal2 ou SentActionSignal2<br /> (Signal 2 est destinée à être RNIF v11)|  
|50|ReceivedResponse ou SentResponse|  
|75|ReceivedResponseSignal ou SentResponseSignal|  
|85 %|ReceivedResponseSignal2 ou SentResponseSignal2<br /> (Signal 2 est destinée à être RNIF v11)|  
|100|ActivityCompleted|  
  
### <a name="activity-definition-file"></a>Fichier de définition d’activité  
 Le fichier de définition d’activité définit les champs que vous suivez dans l’analyse BAM, et comment les afficher. Pour plus d’informations sur ce fichier, consultez [fonctionne avec le fichier de définition de suivi des activités](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md).  
  
 Pour plus d’informations sur BAM, consultez « analyse BAM (Business Activity) » dans l’aide de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation avec le fichier de définition des activités de suivi](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md)   
 [Ce qu’apporte BizTalk Accelerator pour RosettaNet à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)