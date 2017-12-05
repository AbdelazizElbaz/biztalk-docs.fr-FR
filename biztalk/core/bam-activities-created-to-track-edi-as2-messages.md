---
title: "Activités BAM créées pour le suivi des Messages EDI-AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a10ab846-0fbb-46f5-920e-cb2b5be75814
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7da7ac08a8f26e21b2c648670730db136392471
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="bam-activities-created-to-track-edi-as2-messages"></a>Activités BAM créées pour le suivi des Messages EDI-AS2
BizTalk Server inclut les activités BAM qui ont été créées pour les rapports d’état EDI et AS2. Ces activités déterminent les données qui sont affichées dans les rapports d'état. Cette rubrique décrit les activités BAM et les champs qui y sont définis, ainsi que les valeurs d'énumération qui sont définies pour certains champs dans les activités BAM.  
  
 Vous pouvez créer un rapport d'état personnalisé en créant une activité BAM personnalisée. L'activité personnalisée peut reposer sur l'une des activités standard. Vous pouvez aussi afficher le contenu du message dans le rapport d'état personnalisé en interrogeant la table EdiMessageContent dans la base de données BizTalkDTADb. Pour plus d'informations, reportez-vous à la section « Interrogation de la table EdiMessageContent » ci-dessous.  
  
> [!CAUTION]
>  La modification d'une activité BAM peut affecter le traitement des composants d'exécution EDI et AS2 de BizTalk, qui dépendent des activités.  
  
## <a name="bam-activities-used-in-status-reporting"></a>Activités BAM utilisées dans les rapports d'état  
 Les activités BAM créées pour suivre les messages EDI/AS2 sont incluses en tant que vues dans la base de données BAMPrimaryImport. Le tableau suivant répertorie les activités BAM et les colonnes au sein de celles-ci :  
  
|Activité BAM|Champs|  
|------------------|------------|  
|AS2InterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> MessageID<br /><br /> AS2From<br /><br /> AS2To<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MdnActivity|RecordID<br /><br /> ActivityID<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MdnDateTime<br /><br /> MdnDispositionType<br /><br /> DispositionModifierExtType<br /><br /> DispositionModifierExtDescription<br /><br /> MdnEncryptionType<br /><br /> MdnSignatureType<br /><br /> MdnPayloadContentKey<br /><br /> MdnWireContentKey<br /><br /> MdnMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MessageActivity|RecordID<br /><br /> ActivityID<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MessageDateTime<br /><br /> BTSInterchangeID<br /><br /> BTSMessageID<br /><br /> MdnProcessingStatus<br /><br /> MessageEncryptionType<br /><br /> IsMdnExpected<br /><br /> MicAlgorithmType<br /><br /> MessageSignatureType<br /><br /> MessagePayloadContentKey<br /><br /> MessageWireContentKey<br /><br /> MessageMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> IsAS2MessageDuplicate<br /><br /> DaysToCheckDuplicate<br /><br /> FileName<br /><br /> TrackingActivityID<br /><br /> LastModified|  
|BatchingActivity|RecordID<br /><br /> ActivityID<br /><br /> BatchStatus<br /><br /> DestinationPartyID<br /><br /> DestinationPartyName<br /><br /> ActivationTime<br /><br /> BatchOccurrenceCount<br /><br /> EdiEncodingType<br /><br /> BatchType<br /><br /> TargetedBatchCount<br /><br /> ScheduledReleaseTime<br /><br /> BatchElementCount<br /><br /> RejectedBatchElementCount<br /><br /> BatchSize<br /><br /> LastBatchAction<br /><br /> CreationTime<br /><br /> ReleaseTime<br /><br /> BatchReleaseType<br /><br /> BatchServiceID<br /><br /> ActivationMessageID<br /><br /> ReleaseMessageID<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> BatchName<br /><br /> BatchID<br /><br /> LastModified|  
|BatchInterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> LastModified|  
|BusinessMessageJournal|RecordID<br /><br /> ActivityID<br /><br /> MessageTrackingID<br /><br /> ActionType<br /><br /> ContainerActivityID<br /><br /> ContainerType<br /><br /> BTSInterchangeID<br /><br /> BTSMessageId<br /><br /> BTSServiceInstanceId<br /><br /> BTSHostName<br /><br /> RoutedToPartyName<br /><br /> LinkedMessageTrackingID<br /><br /> TimeCreated<br /><br /> LastModified|  
|FunctionalAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> DeliveredTSCount<br /><br /> AcceptedTSCount<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> ErrorCode1<br /><br /> ErrorCode2<br /><br /> ErrorCode3<br /><br /> ErrorCode4<br /><br /> ErrorCode5<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|FunctionalGroupInfo|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> FunctionalIDCode<br /><br /> TSCount<br /><br /> LastModified|  
|InterchangeAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> AckNoteCode1<br /><br /> AckNoteCode2<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> LastModified|  
|InterchangeStatusActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> AckStatusCode<br /><br /> GroupCount<br /><br /> EdiMessageType<br /><br /> PortID<br /><br /> IsInterchangeAckExpected<br /><br /> IsFunctionalAckExpected<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> TsCorrelationId<br /><br /> LastModified|  
|ResendJournalActivity|RecordID<br /><br /> ActivityID<br /><br /> TrackingActivityId<br /><br /> ResendIndex<br /><br /> ResendStatus<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|ResendTrackingActivity|RecordID<br /><br /> ActivityID<br /><br /> CorrelationId<br /><br /> AdapterPrefix<br /><br /> ResendCount<br /><br /> MaxResendCount<br /><br /> ResendInterval<br /><br /> MaxRetryCount<br /><br /> RetryInterval<br /><br /> MessageContentID<br /><br /> ResendTimeout<br /><br /> RetryTimeout<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|TransactionSetActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> Sens<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> Application émettrice<br /><br /> Application réceptrice<br /><br /> GroupDateTime<br /><br /> GroupControlNo<br /><br /> TransactionSetId<br /><br /> DocType<br /><br /> TransactionSetControlNo<br /><br /> AckStatusCode<br /><br /> BatchProcessing<br /><br /> ProcessingDateTime<br /><br /> GroupOrdinal<br /><br /> TransactionSetOrdinal<br /><br /> MessageContentKey<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> TsCorrelationId<br /><br /> LastModified|  
  
## <a name="data-enumerations-in-the-bamprimaryimport-database"></a>Énumération de données dans la base de données BAMPrimaryImport  
 Certaines données EDI et AS2 sont enregistrées en tant qu'énumérations dans les tables de la base de données BAMPrimaryImport. Lorsqu'elles sont affichées dans le rapport d'état, les données apparaissent sous forme de texte. Ces valeurs sont les suivantes :  
  
|Champ|Valeurs Enum|  
|-----------|-----------------|  
|AckProcessingStatus|NotExpected = -1<br /><br /> Attendu = 0<br /><br /> Reçu = 1<br /><br /> Envoyé = 2<br /><br /> Généré = 3|  
|AS2PartyRole|Tous les = 0<br /><br /> Récepteur = 1<br /><br /> Expéditeur = 2|  
|BatchAction|Création = 0<br /><br /> Activation = 1<br /><br /> ElementReference = 2<br /><br /> Version = 3<br /><br /> Remplacer = 4<br /><br /> Arrêt = 5<br /><br /> Envoyés = 6<br /><br /> ToBeReleased = 7|  
|BatchStatus|Tous les = -1<br /><br /> Défini  = 0<br /><br /> Actif<br /><br /> Déclenché<br /><br /> Terminé|  
|BatchType|ScheduleBased = 0<br /><br /> MessagesCountInGroup = 1<br /><br /> MessagesCountIn<br />L’échange = 2<br /><br /> CharacterCount = 3<br /><br /> ExternalTrigger = 4|  
|Sens|Tous les = 0<br /><br /> Réception = 1<br /><br /> Envoi = 2|  
|DisplayAckStatusCode|Tous = 100<br /><br /> Accepté = 0<br /><br /> PartiallyAccepted = 1<br /><br /> Rejeté = 1<br /><br /> AckExpected = 500<br /><br /> AckNotExpected = 600|  
|DispositionModifierExt<br /> Description|Aucune valeur = 1<br /><br /> Échec de l'authentification = 2<br /><br /> Échec du déchiffrement = 3<br /><br /> Message insuffisant<br />Sécurité = 4<br /><br /> Échec de la vérification de l'intégrité = 5<br /><br /> Traitement inattendu <br />Erreur = 6|  
|DispositionModifierExt<br />Type|Aucune valeur = 1<br /><br /> Erreur = 2<br /><br /> Avertissement = 3|  
|EdiMessageType|X12,<br /><br /> Edifact,<br /><br /> Unknown|  
|IsMdnExpected|MDN non attendu = 0<br /><br /> MDN attendu = 1|  
|MdnDispositionType|Traité = 1<br /><br /> Échec = 2|  
|MdnProcessingStatus|Tous les = 0<br /><br /> Traité = 1<br /><br /> Échec = 2<br /><br /> Attendu = 3<br /><br /> Non attendu = 4|  
|MessageEncryptionType|Le message n'est pas chiffré = 0<br /><br /> Le message est chiffré = 1|  
|MessageSignatureType|Le message n'est pas signé = 0<br /><br /> Le message est signé = 1|  
|MicAlgorithmType|Type inconnu = 1<br /><br /> SHA1 = 1<br /><br /> MD5 = 2|  
  
## <a name="businessmessagejournal-bam-activity"></a>Activité BAM BusinessMessageJournal  
 L'activité BAM BusinessMessageJournal permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de mettre en corrélation un échange EDI reçu contenant des documents informatisés et un échange par lot sortant qui contient les mêmes documents informatisés. Pour plus d’informations, consultez [corréler un document informatisé entrant avec un lot sortant](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).  
  
##  <a name="BKMK_Query"></a>Interrogation de la Table EdiMessageContent  
 La table EdiMessageContent de la base de données BizTalkDTADb stocke la charge du message, ainsi que les métadonnées du message. À partir d'un rapport d'état personnalisé, vous pouvez interroger la table EdiMessageContent pour afficher le contenu du message. Cette opération est semblable à celle qui permet à certains rapports d'état du produit d'afficher le contenu du message, par exemple, à celle qui permet au rapport Message AS2 et état MDN corrélé d'afficher le message au format câble.  
  
 Vous pouvez lier une activité BAM personnalisée à la table EdiMessageContent en utilisant les colonnes de clé dans l'activité BAM qui correspondent à la colonne ContentKey dans la table EdiMessageContent. Par exemple, pour lier l'activité BAM AS2MessageActivity à la table EdiMessageContent, vous pouvez utiliser la colonne MessagePayloadContentKey ou la colonne MessageWireContentKey pour une liaison avec la colonne ContentKey.  
  
|Table|Columns|  
|-----------|-------------|  
|EdiMessageContent<br /><br /> (dans la base de données BizTalkDTADb)|ContentKey<br /><br /> MessageFormat<br /><br /> ContentType<br /><br /> Charset<br /><br /> TimeCreated<br /><br /> TimeInserted<br /><br /> IsOrphaned<br /><br /> ContentBinary|  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [Mise en corrélation d’un document informatisé entrant avec un lot sortant](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)