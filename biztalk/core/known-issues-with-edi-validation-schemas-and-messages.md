---
title: "Problèmes connus avec la Validation EDI, les schémas et les Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 417c3e18-9a97-4d59-bc2b-e96a8c33d388
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a508834ff81814b17bc12f1d698984d65748092
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-validation-schemas-and-messages"></a>Problèmes connus avec la validation, les schémas et les messages EDI
Cette rubrique décrit des problèmes de validation connus.  
  
## <a name="message-is-suspended-with-edi-validation-turned-off"></a>Message suspendu avec validation EDI désactivée  
 **Symptôme**  
  
 Suite à la violation d'une règle associée, la validation est désactivée, mais le message est suspendu (le résultat attendu est qu'il soit sérialisé).  
  
 **Cause possible**  
  
 Validation de champ croisé/segment est effectuée, même si **type EDI** propriété est désactivée dans le **Validation et les paramètres de génération de l’accusé de réception** nœud de la **propriétés EDI** boîte de dialogue. La validation a lieu parce qu'elle est activée dans l'annotation de schéma.  
  
 **Résolution**  
  
 Désactivez la validation dans l'annotation de schéma.  
  
## <a name="the-biztalk-service-needs-to-be-restarted-after-a-schema-has-been-edited-and-redeployed"></a>Nécessité de redémarrer le service BizTalk après la modification et le redéploiement d'un schéma  
 **Symptôme**  
  
 BizTalk Server ne traite pas correctement un message valide suite à la modification et au redéploiement d'un schéma  
  
 **Cause possible**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] met en cache des schémas avec des délais d'attente illimités.  
  
 **Résolution**  
  
 Après avoir modifié et redéployé un schéma, redémarrez le service de l'application BizTalk Server. Vous devez également redémarrer l'instance de l'hôte hébergeant le pipeline qui utilise le schéma redéployé.  
  
## <a name="processing-has-been-aborted-for-messages-of-a-single-encoding-type-for-a-single-party"></a>Abandon du traitement de messages d'un type de codage unique pour une partie unique  
 **Symptôme**  
  
 Le traitement de tous les messages d'un type de codage unique (par exemple, X12 ou EDIFACT) pour une partie unique a été abandonné. Le traitement des messages d'un autre type de codage pour la même partie ou de tous les messages pour une autre partie n'est pas affecté.  
  
 **Cause possible**  
  
 La longueur du numéro de contrôle d'échange, de groupe ou de transaction a dépassé la longueur maximale autorisée.  
  
 Pour les messages X12, la longueur maximale d'un numéro de contrôle est de neuf chiffres. Pour les messages EDIFACT, la longueur maximale d'un numéro de contrôle est de 14 chiffres répartis dans trois champs.  
  
 **Résolution**  
  
 Dans la page de propriétés appropriée de la boîte de dialogue Propriétés EDI pour la partie affectée, redéfinissez le numéro de contrôle. Vous pouvez modifier les numéros de contrôle dans les pages de propriétés suivantes :  
  
-   Numéro de contrôle de l'échange X12 : page Définition des segments ISA (dans le nœud Tiers en tant que récepteur d'échanges) pour les propriétés X12  
  
-   Numéro de contrôle du groupe ou du document informatisé X12 : page Définition des segments GS et ST (dans le nœud Tiers en tant que récepteur d'échanges pour les propriétés X12)  
  
-   Numéro de contrôle de l'échange EDIFACT : page Définition du segment UNB (dans le nœud Tiers en tant que récepteur d'échanges) pour les propriétés EDIFACT)  
  
-   Numéro de contrôle du groupe ou du document informatisé EDIFACT : page Définition des segments UNG et UNH (dans le nœud Tiers en tant que récepteur d'échanges pour les propriétés EDIFACT)  
  
## <a name="biztalk-server-validates-with-schemas-that-have-unh-segments-with-seven-data-elements"></a>BizTalk Server valide à l'aide de schémas qui ont des segments UNH avec sept éléments de données  
 Dans les versions antérieures d’EDIFACT, le segment UNH comprend quatre éléments, plutôt que les sept éléments (dont trois sont facultatifs) ayant le segment UNH dans les versions ultérieures. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise la version ultérieure avec sept éléments pour la validation.  
  
## <a name="error-messages-generated-for-multiple-cross-field-validation-rules-will-not-be-specific-to-the-rule"></a>Messages d'erreur générés pour plusieurs règles de validation de champ croisé non spécifiques à la règle  
 Si un schéma contient plusieurs règles de validation de champ croisé pour un élément de données d'un message et qu'une erreur se produise avec cet élément, une erreur distincte est générée pour chaque règle de validation. En revanche, toutes ces erreurs ont un code d'erreur et une description identiques ; les erreurs ne sont pas spécifiques à la règle de validation.  
  
## <a name="if-edi-type-validation-is-disabled-on-receive-and-enabled-on-send-the-send-pipeline-will-not-be-able-to-serialize-the-message"></a>Si la validation de type EDI est désactivée pour la réception et activée pour l'envoi, le pipeline d'envoi ne peut pas sérialiser le message  
 Si vous désactivez la validation de type EDI côté réception, le pipeline de réception EDI génère un message XML à partir d'un message EDI reçu, que ce dernier soit valide ou non. Si la validation EDI est activée côté envoi, le pipeline d'envoi EDI ne peut pas retraiter le XML en fichier EDI valide si le fichier XML contient des erreurs. Il génère donc une erreur.  
  
## <a name="edi-promoted-properties-are-only-available-if-your-application-has-a-reference-to-the-biztalk-edi-application"></a>Propriétés EDI promues disponibles uniquement si votre application contient une référence à l'application EDI BizTalk  
 **Symptôme**  
  
 Les propriétés promues sous l'espace de noms EDI ne figurent pas dans la liste de propriétés promues que vous tentez d'utiliser, par exemple, dans une orchestration ou dans les conditions de filtrage pour un port d'envoi.  
  
 **Cause possible**  
  
 L'application BizTalk que vous utilisez ne comprend pas de référence à l'application EDI BizTalk. Les schémas de propriété pour les propriétés EDI promues figurent dans le fichier Microsoft.BizTalk.Edi.BaseArtifacts.dll inclus dans le dossier Ressources de l'application EDI BizTalk.  
  
 **Résolution**  
  
 Ajoutez à l'application BizTalk que vous utilisez une référence à l'application EDI BizTalk.  
  
## <a name="the-data-element-name-in-a-context-property-name-contains-an-underscore-not-a-period"></a>Trait de soulignement au lieu d'un point dans le nom d'un élément de données dans un nom de propriété de contexte  
 Le nom d'un élément de données dans un segment EDI contient un point (par exemple, UNB2.1, qui correspond au champ d'identification du segment d'expéditeur UNB2). Toutefois, lorsque le nom d'un élément de données est inclus comme propriété de contexte EDI, le point est remplacé par un trait de soulignement. Par exemple, la propriété de contexte de l'élément d'identification de l'expéditeur est « EDI.UNB2_1 » et non « EDI.UNB2.1 ». En effet, le point n'est pas pris en charge dans le nom d'une propriété de contexte.  
  
## <a name="irrelevant-string-is-appended-to-instance-validation-error-message"></a>Ajout de chaîne inappropriée à un message d'erreur de validation d'instance  
 Chaque fois que vous recevez un message d'erreur durant une validation d'instance, la chaîne « BEC 2004 » est ajoutée au message. Vous pouvez ignorer cette chaîne.  
  
## <a name="edifact-schema-names-are-case-sensitive"></a>Noms de schémas EDIFACT sensibles à la casse  
 Le nom d'un schéma EDIFACT, telle qu'indiqué dans l'élément de données root_reference du schéma, est sensible à la casse. Par exemple, EFACT_D98B_ORDERS et EFACT_d98B_Orders désignent deux schémas différents.  
  
## <a name="invalid-edi-messages-can-be-suspended-even-if-edi-type-validation-is-disabled"></a>Possibilité de suspension de messages EDI non valides même si la validation de type EDI est désactivée  
 Validation structurelle EDI est effectuée même si la validation de Type EDI est désactivée. Un échange dont les validations structurelles de base échouent est suspendu, même si la validation de type EDI est désactivée.  
  
## <a name="the-edi-assembler-will-serialize-an-unbatched-interchange-even-if-a-separator-character-is-used-in-an-envelope-header"></a>Sérialisation d'un échange non regroupé par l'assembleur EDI même si un caractère de séparation est utilisé dans l'en-tête de l'enveloppe  
 Les caractères de séparation utilisés pour séparer les champs d'en-tête et de code de fin ne doivent pas être utilisés dans la définition de tout champ d'en-tête ou de code de fin d'échange, de groupe ou de transaction, comme défini pour le tiers en tant que récepteur d'échanges. S'ils sont utilisés, le traitement de l'échange échoue soit dans l'assembleur EDI du BizTalk Server expéditeur, soit dans le désassembleur du tiers récepteur. L'échange échoue dans l'Assembleur EDI s'il s'agit d'un lot sortant parce que l'Assembleur valide l'enveloppe par rapport au schéma (service) de contrôle d'en-tête. Si l'échange n'est pas regroupé, l'assembleur EDI le sérialise, mais le traitement dans le désassembleur du tiers récepteur échoue.  
  
## <a name="mismatched-character-sets-can-result-in-suspended-interchanges"></a>Discordance de jeux de caractères pouvant entraîner une suspension des échanges  
 Le jeu de caractères utilisé pour un échange sortant doit être identique à celui utilisé pour créer les documents informatisés insérés dans l'échange. Si ce n'est pas le cas, il est probable que l'échange soit suspendu et que s'affiche un message d'erreur indiquant la présence de caractères non valides.  
  
 Par exemple, si vous créez un lot EDIFACT à l'aide du jeu de caractères UNOA alors que des documents informatisés ajoutés au lot comprennent des caractères minuscules, l'orchestration du traitement par lot suspend le message parce qu'UNOA ne permet pas d'utiliser des minuscules.  
  
 Autre exemple, si vous configurez le pipeline d'envoi EDI pour des échanges X12 avec le jeu de caractères « De base » alors qu'un échange par lot X12 utilise des caractères minuscules parce que le jeu de caractères X12 sélectionné dans la page Génération de l'enveloppe d'échange X12 pour le tiers en tant que récepteur d'échanges est défini sur « Étendu » ou « UTF8/Unicode », le message traité par lot est suspendu lorsque les paramètres d'enveloppe sont appliqués.  
  
## <a name="using-unh25-for-schema-resolution-requires-an-update-to-the-schema"></a>Nécessité de mettre à jour le schéma pour utiliser UNH2.5 pour la résolution de schéma  
 Si vous utilisez UNH2.5 (Code d'association assigné) pour la résolution de schéma d'un échange EDIFACT entrant, vous devez mettre à jour le schéma de document approprié dans le dossier \Program Files\Microsoft BizTalk Server 20xx\Schema. Vous devez ajouter la valeur d'UNH2.5 aux valeurs existantes pour root_reference, display_reference et xs:element name. Par exemple, si UNH2.5 est « EAN008 » alors que vous utilisez le schéma EFACT_D96A_INVOIC, vous devez définir root_reference, display_reference et xs:element name sur « EFACT_D96A_INVOIC_EAN008 ».  
  
## <a name="the-compressed-file-of-schemas-will-be-replaced-when-an-upgrade-is-performed"></a>Remplacement du fichier compressé de schémas lors d'une mise à niveau  
 Si vous procédez à une mise à niveau de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le fichier MicrosoftEdiXSDTemplates.exe de l'installation existante est remplacé par le fichier MicrosoftEdiXSDTemplates.exe associé à la mise à niveau. Si vous comptez continuer à utiliser les schémas de l'ancien fichier compressé, vous n'aurez plus accès à ce dernier après la mise à niveau, sauf si vous le sauvegardez.  
  
## <a name="if-a-group-contains-multiple-x12-transaction-sets-all-must-be-of-the-same-type"></a>Nécessité que tous les documents informatisés X 12 d'un groupe soient du même type  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge le mélange de documents informatisés différents à l'intérieur d'un même groupe. Si un groupe contient plusieurs documents informatisés, la valeur ST01 doit être identique pour tous.  
  
## <a name="receiving-x12-interchanges-that-contain-non-ascii-delimiters-may-result-in-the-message-becoming-suspended"></a>Possibilité de suspension de message lors de la réception d'échanges X 12 contenant des délimiteurs non ASCII  
 **Symptôme**  
  
 Lors de la réception d'un échange X12 utilisant des valeurs de délimiteur non ASCII, il peut arriver que le message soit suspendu et qu'une erreur soit consignée dans le journal des événements de l'application.  
  
 **Cause possible**  
  
 Ce problème peut se produire si l'échange n'est pas codé en UTF-8.  
  
 **Résolution**  
  
 Veillez à ce que tout échange X 12 entrant contenant des délimiteurs non ASCII soit codé en UTF-8.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec le traitement EDI](../core/known-issues-with-edi-processing.md)   
 [Messagerie EDI](../core/edi-messaging.md)   
 [Validation des messages EDI](../core/edi-message-validation.md)   
 [Schémas EDI](../core/edi-schemas.md)   
 [Développement des schémas EDI](../core/developing-edi-schemas.md)