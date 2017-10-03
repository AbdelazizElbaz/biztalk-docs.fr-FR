---
title: "AS2 Événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9de140d-8961-4c19-a2e5-14631016541f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 824fda0d49ddfd9c5d6f6c12a379568775b8d160
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-events"></a>Événements AS2
Le tableau suivant répertorie les messages d'événement susceptibles d'être publiés dans le journal des événements lors du traitement AS2.  
  
> [!NOTE]
>  Pour plus d’informations sur les erreurs AS2 répertoriées dans le tableau suivant, consultez [événements EDI et AS2](../core/edi-and-as2-events.md).  
  
|Code d'erreur|Condition|  
|----------------|---------------|  
|AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError|Le décodeur AS2 n'a pas réussi à localiser l'en-tête HTTP Disposition-Notification-Options requis pour la création du MDN.|  
|SynchronousMdnRequestedOnOneWayReceivePortError|Erreur de configuration.  MDN synchrone demandé sur un port de réception HTTP unidirectionnel.|  
|SynchronousMdnRequestedOnOneWaySendPortError|Erreur de configuration.  Port d’envoi MDN synchrone demandé sur HTTP unidirectionnel.|  
|EncryptionCertNotConfiguredError|L'empreinte de certificat n'a pas été configurée pour le tiers AS2.  AS2-à partir de : {0} AS2-pour : {1}|  
|AS2DecoderPartySigningConfigurationError|Erreur de configuration.  La signature du message ne correspond pas à la valeur attendue.  Contactez le partenaire émetteur et vérifiez l'utilisation de la signature.  AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
|AS2DecoderExceptionEncounteredDuringProcessing|Le décodeur AS2 a rencontré une exception durant le traitement.  Détails du message et de l’exception sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » MessageType : « {3} » (Exception) : « \ {4\} »|  
|AS2DecoderMdnMicFailureDuringProcessing|Le décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN de traitement.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
|AS2DecoderMdnSigningMismatchFailureDuringProcessing|Le traitement du décodeur AS2 a échoué car la signature du MDN ne correspondait pas à notre demande.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
|AS2DecoderMdnProcessingFailureReturned|Le traitement du décodeur AS2, car le MDN a indiqué que le message AS2 le traitement a échoué.  Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »|  
|AS2InvalidQuotedStringHeaderError|En-tête HTTP entre guillemets non valide rencontré.  Détails sont les suivants : nom d’en-tête : valeur d’en-tête « {0} » : « {{1} »|  
|AS2MicDataStoreDuplicateMicError|L'entrée d'erreur MIC existe déjà.|  
|AS2StreamingNonSeekableStreamError|Ceci est un flux non identifiable.|  
|AS2StreamingSetLengthError|La longueur de ce flux n'est pas définie.|  
|AS2StreamingWriteToReadonlyStreamError|Ceci est un flux en lecture seule.|  
|AS2StreamingMethodNotImplementedError|La méthode ou l'opération n'est pas implémentée.|  
|BtsMimeExceptionEncounteredDuringMessageDecoding|Une erreur BTS MIME a été détectée lors de la tentative de décodage d'un message AS2.  AS2-à partir de : {0}, AS2-pour : {1}, MessageId : {2}, erreur : {3}|  
|AS2DecoderPartyEncryptionConfigurationError|Erreur de configuration.  Le chiffrement du message ne correspondait pas à la valeur attendue.  Contactez le partenaire émetteur et vérifiez l'utilisation du chiffrement.  AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
|AS2DecoderPartySignatureError|Erreur de configuration.  La signature du message ne correspond pas à la signature configurée pour ce tiers.  Contactez le partenaire émetteur et vérifiez le certificat utilisé.  AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »|  
|InvalidAgreementAS2FromName|Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-From.|  
|InvalidAgreementAS2ToName|Le tiers pour cet échange AS2 doit contenir une valeur pour AS2-de.|  
|UnsupportedAS2HashAlgorithmError|L'algorithme de hachage spécifié dans le message AS2 n'est pas pris en charge.|  
|UnableToLocateAS2PartyError|Impossible d’accéder au tiers avec qualificateur : {0} tiers : {1}.  Erreur : {{2}|  
|UnableToLocateAS2PartyByPartyNameError|Impossible d’accéder au tiers avec tiers : {0}.|  
|UnableToLocateAS2PartyBySendPortNameError|Impossible d’accéder au tiers avec port d’envoi : {0} d’erreur : {{1}.|  
|InvalidAS2FromNameConfiguredError|AS2 non valide-nom configuré pour le tiers : {0} valeur : {1}|  
|InvalidAS2ToNameConfiguredError|AS2 non valide-au nom configuré pour le tiers : {0} valeur : {1}|  
|InvalidAS2FromNameHeaderReceivedError|En-tête AS2-From non valide reçu.  Valeur : {0}|  
|InvalidAS2ToNameHeaderReceivedError|AS2 non valide-pour l’en-tête reçu.  Valeur : {0}|  
|MissingAS2FromHeaderError|Un message AS2 ne contenant pas l'en-tête AS2-From a été reçu.|  
|MissingAS2ToHeaderError|Réception d’un message AS2 ne contenant pas AS2-à l’en-tête.|  
|InvalidDispositionNotificationOptionToError|Valeur de disposition-Notification-Option : « {0} » n’est pas valide.  {1}|  
|InvalidReceiptDeliveryOptionError|Valeur de Receipt-Delivery-Option : « {0} » n’est pas valide.  {1}|  
|InvalidOrMissingASN1DataLengthHeader|Champ Longueur des données ASN.1 rencontré lors de la décompression.|  
|InvalidOrMissingASN1TrailingBytes|Octets de structure compressée ASN.1 CMS de fin manquants ou non valides lors de la décompression.|  
|InvalidASN1CompressedStructureEncountered|Structure compressée ASN.1 non valide rencontrée durant la décompression.|  
|InvalidOrMissingDataHeaderEncountered|En-tête compressé ASN.1 non valide ou manquant lors de la décompression.|  
|InvalidOptionalZLibFieldEncountered|Champ de compression ASN.1 ZLib non valide rencontré lors de la décompression.|  
|InvalidOrMissingDataOIDEncountered|OID de données ASN.1 non valide ou manquant rencontré lors de la décompression.|  
|InvalidOrMissingZLibOIDEncountered|OID ASN.1 ZLib non valide ou manquant rencontré lors de la décompression.|  
|InvalidOrMissingCompressedDataOIDEncountered|Non valide ou manquante compressé données OID ASN.1 rencontré lors du traitement de la décompression.|  
|InvalidAdler32ChecksumInCompressedMessageError|Total de contrôle Adler32 non valide rencontré.|  
|UnsupportedOctetStringLengthEncountered|Longueur de chaîne Octet non prise en charge rencontrée.  La longueur d'octet maximale prise en charge est 4.|  
|DecompressionFailedError|Échec de la décompression lors du traitement d'un message AS2 compressé.  Erreur : {0}|  
|DecryptionFailedError|Une erreur s'est produite lors du déchiffrage d'un message AS2.|  
|IntegrityCheckFailedError|Une erreur s'est produite lors de la validation d'un message AS2.  Assurez-vous que les certificats utilisés n'ont pas dépassé le délai de temporisation ou été révoqués.|  
|EncryptionCertificateHasBeenRevokedError|Le certificat utilisé pour chiffrer un message a été révoqué. Empreinte numérique du certificat : {0}|  
|DecryptionCertificateHasBeenRevokedError|Le certificat utilisé pour déchiffrer un message a été révoqué. Empreinte numérique du certificat : {0}|  
|SigningCertificateHasBeenRevokedError|Le certificat utilisé pour signer un message a été révoqué. Empreinte numérique du certificat : {0}|  
|SignatureCertificateHasBeenRevokedError|Le certificat utilisé pour signer un message a été révoqué. Empreinte numérique du certificat : {0}|  
|CertificateMissingError|Impossible de trouver le certificat utilisé pour signer un message dans le magasin de certificats local. Empreinte numérique du certificat : {0}|  
|EmptyContentOnAS2MessageEncountered|Un message AS2 vide a été reçu.  Le message sera interrompu.|  
|AS2FromMatchesAS2ToError|La valeur AS2-From correspond à la valeur AS2-To.|  
|GenericEdiIntException|Une exception EDIINT s'est produite.|  
|BtsMimeExceptionEncounteredDuringMessageEncoding|Une erreur BTS MIME a été détectée lors de la tentative de codage d'un message.  Erreur : {0}, HResult : \ {1\\}|  
|BtsMimeGeneralExceptionEncounteredDuringMessageEncoding|Une erreur BTS MIME a été détectée lors de la tentative de codage d'un message.  Erreur : {0}|  
|AS2StatusReportingExceptionEncountered|Une erreur a été détectée lors de la tentative de création d'un rapport d'état AS2.  Erreur : {0}|