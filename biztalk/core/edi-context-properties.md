---
title: "Propriétés de contexte EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a408af-daf5-4e9e-afb3-9fd1795e8c16
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36e2f9fcc839625cc0b1ac01ec6e70b53eb2a6e2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="edi-context-properties"></a>Propriétés de contexte EDI
Les propriétés de contexte de message du schéma de propriété global EDI étant exposées publiquement, vous pouvez les utiliser pour le routage des messages. Elles sont définies dans le fichier PropertySchema.xsd dans l'assembly Microsoft.BizTalk.Edi.BaseArtifacts. L'espace de noms de ces propriétés est `http://schemas.microsoft.com/ Edi/PropertySchema`. Si elles sont promues, ces propriétés de contexte du message sont disponibles en tant que Edi. \< *Nom de la propriété* \> dans les **filtres** page de la **boîte de dialogue Propriétés de Port d’envoi** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].


## <a name="context-properties-list"></a>Liste des propriétés de contexte  
 Les propriétés de contexte EDI sont également disponibles dans une orchestration, tant qu’une référence à l’assembly Microsoft.BizTalk.Edi.BaseArtifacts a été ajoutée au projet d’orchestration.
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|AK901|chaîne|Indique si le groupe fonctionnel identifié dans le segment AK1 de l'accusé de réception a été accepté ou rejeté (accusé de réception X12 997 uniquement).|  
|AttachmentId|Chaîne|ID de la pièce jointe du message.|  
|AgreementID|int|Écrit par le pipeline de réception EDI. Spécifie l'ID de l'accord vers lequel le message entrant est résolu. Pour un accord de secours, cette valeur est 0.|  
|AgreementName|Chaîne|Écrit par le pipeline de réception EDI. Spécifie le nom de l'accord vers lequel le message entrant est résolu. Pour un accord de secours, cette valeur est **BTSGuestParty**.|  
|AgreementNameForSend|Chaîne|Utilisé par le pipeline d'envoi EDI pour résoudre l'accord pour le document sortant.|  
|AgreementPartIDForSend|int|Utilisé par le pipeline d'envoi EDI pour résoudre l'accord pour le document sortant. Cette valeur est écrite par l'orchestration de traitement par lot.|  
|AgreementPartIDOnReceive|int|Écrit par le pipeline de réception EDI. Spécifie l'ID de l'accord unidirectionnel de l'accord vers lequel le message entrant est résolu. Pour un accord de secours, cette valeur est 0.|  
|BatchElementValidationFailure|boolean|Indique qu'une erreur a été promue par le système de traitement par lot lorsque la validation d'un élément du lot a échoué.|  
|BatchEncodingType|chaîne|Type de codage que BizTalk Server doit utiliser pour encoder un échange traité par lot sortant.|  
|BatchId|int|ID de lot de la configuration de lot à utiliser lors du traitement de ce document, si celui-ci ne correspond qu'à un seul filtre par lot.|  
|BatchIds|Chaîne|Liste des ID de lot du filtre par lot correspondant, définie si le document correspond à plusieurs filtres par lot.|  
|BatchingError|chaîne|Description de l'erreur promue par le système de traitement par lot lorsqu'un élément du lot est suspendu.|  
|BatchName|Chaîne|Nom de la configuration de lot à utiliser lors du traitement de ce document.|  
|CodePage|chaîne|Page de codes à utiliser pour valider l'échange.|  
|CONTRL_UCI4|chaîne|Champ Code d'action d'un accusé de réception CONTRL, indiquant si l'échange à été accepté (valeur de « 8 ») ou rejeté à cause d'une erreur dans le segment UNA ou UNB (valeur de « 4 ») (accusé de réception EDIFACT CONTRL uniquement).|  
|DestinationPartyID (déconseillé dans BizTalk Server)|int|ID du tiers de destination à qui le message doit être envoyé.|  
|DestinationPartyName (déconseillé dans BizTalk Server)|chaîne|Nom du tiers de destination à qui le message doit être envoyé.|  
|DestinationPartyReceiver<br />Identificateur|chaîne|Identificateur du tiers de destination à qui le message doit être envoyé. Cette propriété peut être promue dans un composant personnalisé pour permettre la résolution du tiers dans le pipeline d'envoi.|  
|DestinationPartyReceiver<br />Qualificateur|chaîne|Qualificateur du tiers de destination à qui le message doit être envoyé. Cette propriété peut être promue dans un composant personnalisé pour permettre la résolution du tiers dans le pipeline d'envoi.|  
|DestinationPartySender<br />Identificateur|chaîne|Identificateur du tiers qui a envoyé le message au tiers de destination. Cette propriété peut être promue dans un composant personnalisé pour permettre la résolution du tiers dans le pipeline d'envoi.|  
|DestinationPartySender<br />Qualificateur|chaîne|Qualificateur du tiers qui a envoyé le message au tiers de destination. Cette propriété peut être promue dans un composant personnalisé pour permettre la résolution du tiers dans le pipeline d'envoi.|  
|EncodingType|short|Type de codage que BizTalk Server doit utiliser pour encoder un message sortant.|  
|ErrorDescription|chaîne|Contient une copie du message d'erreur pour un message interrompu (semblable au message dans EventViewer).|  
|GS_Segment|chaîne|Segment GS (groupe fonctionnel) complet (X12).<br /><br /> Le pipeline de réception EDI écrit cette propriété au contexte lorsque l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.|  
|GS01|chaîne|Code d'identificateur fonctionnel (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|GS02|chaîne|Code de l'expéditeur de l'application (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|GS03|chaîne|Le Code de récepteur d’Application (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|GS07|chaîne|Entité responsable (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|GS08|chaîne|Code identificateur de la version, de la version finale, de l'activité (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ISA_Segment|chaîne|Segment ISA (Interchange Control Header, en-tête de contrôle de l'échange) complet (X12).<br /><br /> BizTalk Server écrit cette propriété au contexte quand l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.<br /><br /> Cette propriété contient des informations de sécurité ou d'autorisation (ISA2, informations d'autorisation, et ISA4, informations de sécurité) qui peuvent entraîner une divulgation d'informations. Vous pouvez utiliser la propriété masquer les informations de sécurité / d’autorisation/mot de passe (dans le **Validation et génération de l’accusé de réception** page) pour remplacer chaque caractère dans les champs ISA2 et ISA4 par un caractère « # ». Il s’agit d’un processus à sens unique : les caractères « # » ne peut pas être reconvertis en caractères réels.<br /><br /> Le pipeline de réception EDI écrit cette propriété au contexte lorsque l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.|  
|ISA05|chaîne|Qualificateur d'expéditeur des échanges (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ISA06|chaîne|ID de l'expéditeur des échanges (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ISA07|chaîne|Qualificateur de récepteur des échanges (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ISA08|chaîne|ID du récepteur des échanges (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ISA15|chaîne|Indicateur d'utilisation (X12)<br /><br /> Le pipeline de réception EDI promeut cette propriété au contexte (si l'échange n'est pas un échange traité par lot conservé).|  
|IsResendControlMessage|int|Utilisé par le moteur AS2 pour indiquer qu'un message AS2 envoyé doit être retransmis, lorsqu'aucune réponse MDN n'a été reçue au cours de la durée configurée.|  
|IsSystemGeneratedACK|boolean|Indique que le message est un accusé de réception (X12 TA1 ou 997, ou EDIFACT CONTRL) généré par le système. Peut être défini sur True ou False.<br /><br /> Il s’agit d’une propriété de contexte de message qui est disponible en tant que EDI. IsSystemGeneratedACK dans les **filtres** page de la **propriétés de Port d’envoi** boîte de dialogue.|  
|ReceiverPartyName|Chaîne|Écrit par le pipeline de réception EDI. Spécifie le nom du partenaire de destination fourni dans l'accord vers lequel le message est résolu. Pour un accord de secours, cette valeur est **RECEIVE-PARTNER**.|  
|ReceiverPartyNameForSend|Chaîne|Utilisé par le pipeline d'envoi EDI pour résoudre l'accord pour les documents sortants.|  
|ReuseEnvelope|boolean|Indique si un échange est préservé ou fractionné. Si l'échange est préservé, BizTalk Server va réutiliser l'enveloppe lors du traitement de l'échange pour l'envoi.|  
|SenderPartyName|Chaîne|Écrit par le pipeline de réception EDI. Spécifie le nom du partenaire source fourni dans l'accord vers lequel le message entrant est résolu. Pour un accord de secours, cette valeur doit être **BTS-SENDER**.|  
|SenderPartyNameForSend|Chaîne|Utilisé par le pipeline d'envoi EDI pour résoudre l'accord pour les documents sortants.|  
|ST01|chaîne|Code d'identificateur du document informatisé (X12)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|ST03|chaîne|Code identificateur de la version, de la version finale, de l'activité (X12)<br /><br /> Vous pouvez écrire et promouvoir cette propriété pour le contexte et l'utiliser pour le routage des messages.|  
|TA1_TA104|chaîne|Champ Comportement du moteur d'un accusé de réception TA104, indiquant si l'échange est accepté (valeur « A »), accepté avec des erreurs (valeur « E ») ou rejeté/suspendu (valeur « R ») (accusés de réception X12 TA1 uniquement).|  
|ToBeBatched|boolean|Indique si le message doit être traité par lot avec les autres messages par l'orchestration de traitement par lot.<br /><br /> Après avoir traité un échange par lot, l'orchestration de traitement par lot définit cette propriété sur « False ».|  
|ToBeRouted|boolean|Indique que le message doit être récupéré par l'orchestration de routage, qui créé autant de copies de l'élément du lot qu'il y a d'abonnement à cet élément, puis route les copies vers la MessageBox.|  
|UNA_Segment|chaîne|Segment UNA (options de l'échange) complet (EDIFACT)<br /><br /> Le pipeline de réception EDI écrit cette propriété au contexte lorsque l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.|  
|UNB_Segment|chaîne|Segment UNB (en-tête de contrôle de l'échange) complet (EDIFACT)<br /><br /> Le pipeline de réception EDI écrit cette propriété au contexte lorsque l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.<br /><br /> Cette propriété contient des informations de sécurité ou d'autorisation (UNB6.1 et UNB6.2) qui peuvent entraîner une divulgation d'informations. Vous pouvez utiliser la propriété Masquer les informations de sécurité/d'autorisation/de mot de passe pour remplacer les valeurs des champs UNB6.1 et UNB6.2 par des caractères « # ». Remarque : les caractères « #  » ne peuvent pas être reconvertis en leur forme initiale.|  
|UNB11|chaîne|Indicateur d'utilisation (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNB2_1|chaîne|ID de l'expéditeur des échanges (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNB2_2|chaîne|Code du qualificateur d'expéditeur des échanges (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNB2_3|chaîne|Adresse de routage inverse (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNB3_1|chaîne|ID du destinataire de l'échange (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNB3_2|chaîne|Code du qualificateur du destinataire de l'échange (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNG_Segment|chaîne|Segment UNG (groupe fonctionnel) complet (X12).<br /><br /> Le pipeline de réception EDI écrit cette propriété au contexte lorsque l'échange est divisé en documents informatisés, et non pas lorsqu'il est conservé.|  
|UNG1|chaîne|Identification du groupe fonctionnel (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNG2_1|chaîne|Identification de l’expéditeur de l’Application (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNG3_1|chaîne|Identification du destinataire de l'application (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNH2_1|chaîne|Type de message (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNH2_2|chaîne|Numéro de version du message (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
|UNH2_3|chaîne|Numéro de version finale du message (EDIFACT)<br /><br /> Réception d’EDI pipeline promeut cette propriété au contexte (si l’échange n’est pas un échange par lot conservé).|  
  
## <a name="extracting-individual-fields-from-the-segment-context-properties"></a>Extraction de champs individuels des propriétés de contexte du segment  
 Certaines propriétés ne sont pas écrites ou promues pour le contexte du message par les pipelines de réception EDI en tant que propriétés individuelles, mais uniquement en tant que chaînes d'un segment. Cette opération est effectuée pour des raisons de performances, car la promotion des propriétés a des conséquences sur les performances. Par exemple, les champs ISA ISA5, ISA6, ISA7, ISA8 et ISA15 du segment ISA sont promus par les pipelines de réception en tant que propriétés individuelles, mais le reste des champs ISA sont uniquement écrits dans le contexte du message en tant que propriétés ISA_Segment. Ces propriétés sont écrites ou promues uniquement lorsque **ReuseEnvelope** n’est pas définie sur True, indiquant qu’un échange traité par lot reçu n’est pas conservé.  
  
 Si le champ de l'un des segments (ISA, GS, UNB, UNG ou UNA) doit être écrit dans le contexte du message, mais que ce champ n'est pas écrit dans le contexte par défaut, vous devez écrire un composant personnalisé pour qu'il écrive ce champ dans le contexte du message. Ce composant personnalisé doit analyser les champs du segment et écrire un champ individuel dans le contexte du message.  
  
 L'exemple d'enrichissement de message décrit l'utilisation d'un analyseur pour extraire des champs d'un segment et les écrire dans le contexte. Cet exemple est inclus dans le \<lecteur\>: \Program Files\Microsoft BizTalk Server\SDK\Samples\EDI\MessageEnrichment. Pour plus d’informations, consultez [exemple d’enrichissement de Message (exemple BizTalk Server)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et configuration de solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)