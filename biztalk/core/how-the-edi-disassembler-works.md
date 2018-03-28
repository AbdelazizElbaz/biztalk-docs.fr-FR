---
title: Fonctionne du désassembleur EDI | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8da91ba4-e1c9-4e6b-bbd1-fe71ea880118
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4edf1353a9f06103205e1e6e4296c2aa77e74dc6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-the-edi-disassembler-works"></a>Fonctionnement du Désassembleur EDI
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue la plus grande partie du traitement des échanges EDI reçus dans le pipeline de réception EDI (`Microsoft.BizTalk.DefaultPipelines.EDIReceivePipeline`). Ce pipeline inclut le composant de pipeline Désassembleur EDI, qui effectue le traitement suivant :  
  
-   Fractionne plusieurs échanges d'un seul message en échanges distincts (si la propriété de pipeline « DetectMID » pour l'emplacement de réception est définie sur True). Pour ce faire, le Désassembleur EDI recherche un en-tête de contrôle de l'échange (ISA, UNA ou UNB) même après avoir rencontré un code de fin de contrôle de l'échange (IEA ou UNZ).  
  
-   Valide l'enveloppe.  
  
-   Désassemble l'échange.  
  
-   Traite les champs déclencheurs pour les échanges HIPAA.  
  
-   Valide les propriétés EDI et spécifiques au partenaire, selon le cas. Il effectue notamment une validation du schéma EDI, une validation de champ croisé pour les messages X12 (si configurée), une validation structurelle EDI et une validation étendue de schéma (si le schéma est personnalisé avec un nœud qui a un type de données non EDI). Pour plus d’informations, consultez [Validation des Messages EDI reçus](../core/validation-of-received-edi-messages.md).  
  
-   Vérifie que les numéros de contrôle échange, groupe et transaction ne sont pas des doublons, si les vérifications sont activées dans le **Validation** page (sous **paramètres d’échange**) de la bidirectionnelles onglet d’accord de la **propriétés de l’accord** boîte de dialogue. Vérifie le numéro de contrôle de l'échange par rapport aux échanges reçus précédemment. Vérifie le numéro de contrôle du groupe par rapport à d'autres numéros de contrôle du groupe dans l'échange. Vérifie le numéro de contrôle du document informatisé par rapport à d'autres numéros de contrôle du document informatisé dans ce groupe. Si un doublon est découvert, le rapport d'état indique qu'il existe un enregistrement en double.  
  
-   Génère un document XML pour chaque document informatisé. Sur chaque fichier XML, promeut la propriété de contexte de BTS.MessageType, en la définissant sur le nom de schéma avec l'espace de noms.  
  
-   Convertit l’ensemble de l’échange au format XML si le **entrants option de traitement par lots** est définie sur l’un des deux **préserver l’échange** valeurs. Cette propriété peut être définie à partir de la **paramètres d’hôte Local** page sous **paramètres de l’échange** de l’onglet d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue. Le pipeline de réception promeut la propriété ReuseEnvelope pour identifier l'échange comme conservé.  
  
-   Génère un accusé de réception technique et/ou fonctionnel (si configuré). Cela peut inclure le traitement par lot des accusés de réception (si configuré). Promeut la propriété de contexte de BizTalk Server. MessageType, en lui affectant égale au schéma de contrôle dans le http://schemas.microsoft.com/EDI/ \<X12 ou EDIFACT\> espace de noms (par exemple, X12_997_Root pour un accusé de réception 997). Promeut également la propriété de contexte EDI.DestinationPartyName, ce qui garantit que l'accusé de réception est récupéré pour l'envoi. Pour plus d’informations, consultez [envoyer un accusé de réception EDI](../core/sending-an-edi-acknowledgment.md).  
  
-   Fractionne des documents HIPAA 276/277 (version 5010 uniquement) 834, 835 (version 4010 uniquement) et 837, le cas échéant.  
  
-   Promeut ou écrit des propriétés dans le contexte de message (consultez la section suivante).  
  
## <a name="promoting-or-writing-properties-to-the-context"></a>Promotion ou écriture de propriétés dans le contexte  
 Lorsque le Désassembleur EDI traite un message reçu, il promeut ou écrit les propriétés suivantes dans le contexte de message :  
  
-   Pour un X12 message non regroupé, promeut les propriétés suivantes à partir de l’enveloppe : ISA06, ISA08, ISA15 ; GS01, GS02, GS03, GS08 ; ST03 et ST01.  
  
    > [!NOTE]
    >  Pour un échange HIPAA 837 entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge trois schémas HIPAA 837 : revendication-Dental_837D, revendication-Institutional_837I et Professional_837P de revendication. La propriété ST01 pour chacun d’eux est « 837 ». Ces trois schémas ont des valeurs différentes pour GS08 dans la version 5010 : « 005010X223A1 » pour 837I, « 005010X224A1 » pour 837d et « 005010 X 222 » pour 837p. Les schémas ont des valeurs différentes pour GS08 dans la version 4010 : « 004010X096A1 » pour 837I, « 004010X097A1 » pour 837d et « 004010X098A1 » pour 837p.  
  
-   Pour un message non regroupés par lots encodé en EDIFACT, promeut les propriétés suivantes à partir de l’enveloppe : UNB2.1, UNB2.3, UNB3.1, UNB11 ; UNG1, UNG2.1, UNG3.1 ; UNH2.1, UNH2.2, UNH2.3.  
  
-   Si un échange par lot est fractionné, écrit ISA_Segment et GS_Segment dans le contexte pour les messages X12 ou écrit UNA_Segment, UNB_Segment et UNG_Segment dans le contexte pour les messages EDIFACT.  
  
    > [!NOTE]
    >  Les segments ci-avant sont écrits dans le contexte. Ils n'y sont pas promus. Vous pouvez, toutefois, ajouter ces segments à un document informatisé à l'aide de l'exemple d'enrichissement de message. Vous pouvez également prendre le code qui ajoute les exemples et l'ajouter à un composant de pipeline personnalisé. Pour plus d’informations, consultez [exemple d’enrichissement de Message (exemple BizTalk Server)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
    > [!NOTE]
    >  La propriété ISA_Segment promue contient des informations de sécurité ou d'autorisation (ISA02, informations d'autorisation, et ISA04, informations de sécurité) qui peuvent entraîner une divulgation d'informations. Vous pouvez utiliser la **masque la propriété des informations de sécurité / d’autorisation/mot de passe dans la propriété de contexte** (dans **paramètres d’hôte Local** page **paramètres de l’échange** pour propriétés de l’accord bidirectionnel) pour remplacer chaque caractère des champs ISA02 et ISA04 par un caractère « # ». Il s’agit d’un processus à sens unique : les caractères « # » ne peut pas être reconvertis en caractères réels.  
  
-   Pour les messages X12 et EDIFACT, promeut ReuseEnvelope qui indique si un échange par lot est fractionné ou conservé.  
  
-   Si un échange par lot est conservé, promeut les propriétés suivantes :  
  
    -   InboundTransportatLocation  
  
    -   InboundTransportType  
  
    -   ISA05  
  
    -   ISA07  
  
    -   ISA06  
  
    -   ISA08  
  
    -   ISA15  
  
    -   LastInterchangeMessage = {True&#124;False}  
  
    -   MessageType  
  
    -   ReceivePortID  
  
    -   ReceivePortName  
  
    -   ReuseEnvelope  
  
## <a name="parsing-the-envelope"></a>Analyse de l'enveloppe  
 Le pipeline de réception EDI utilise le schéma de contrôle d'en-tête pour analyser l'enveloppe d'un message EDI reçu et le schéma de document EDI pour analyser les documents informatisés / messages dans l'échange.  
  
 Si un message EDIINT/AS2 est reçu via le transport HTTP/HTTPS, le Désassembleur EDI inspecte la propriété de contexte BTS.MessageDestination. Si cette propriété est définie sur SuspendQueue, indiquant qu'une erreur s'est produite dans le traitement AS2 et que le message doit être interrompu, le Désassembleur EDI agit comme un composant de pipeline PassThrough et interrompt le message dans la MessageBox.  
  
 Lors de l'analyse des échanges EDIFACT, le pipeline de réception EDI supprime l'indicateur de version utilisé pour échapper des caractères. L’indicateur de version n’est pas inclus dans la validation EDI. Le pipeline de réception EDI n'inclut pas l'indicateur de version lorsqu'il calcule des restrictions de longueur.  
  
 **Jeu de caractères**  
  
 Pour les échanges X12, les propriétés de composant de pipeline déterminent le jeu de caractères que le Désassembleur EDI utilise pour traiter l'échange. Il peut être Basic, Extended ou UTF8/Unicode. La valeur par défaut est UTF8. Pour les échanges EDIFACT, le champ UNB1.1 détermine le jeu de caractères.  
  
 **Détection de séparateur dynamique**  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange EDI, aucune propriété de l'accord n'indique quels doivent être les séparateurs dans l'échange. Au lieu de cela, le Désassembleur EDI détecte les délimiteurs (pour X12 ou EDIFACT) au moment de l'exécution.  
  
 Pour les messages X12, le Désassembleur EDI utilise les caractères suivants à partir de l'échange :  
  
|Séparateur|Caractère|  
|---------------|---------------|  
|Séparateur d'éléments de données|4e caractère de l'ISA|  
|Séparateur d'éléments de composant|ISA16|  
|Séparateur de segments|106e caractère de l'ISA|  
|Suffixe du terminateur de segment|Caractère situé entre le segment ISA et le segment GS<br /><br /> **Valeurs :** aucun, CR, LF ou CRLF **Remarque :** le séparateur peut prendre uniquement les valeurs ci-dessus.|  
|Séparateur de répétition ou identificateur standard<br /><br /> (en fonction de la propriété d’accord « Utilisation d’ISA11 » sur le **enveloppes** page de l’onglet d’accord bidirectionnel)|ISA11|  
  
 Pour les échanges EDIFACT, le Désassembleur EDI vérifie le segment UNA qui définit les séparateurs dans l'échange. Si l'échange n'a pas de segment UNA, qui est facultatif, le Désassembleur utilise les valeurs par défaut définies dans les propriétés de composant de pipeline.  
  
|Séparateur|Caractère de l'UNA|  
|---------------|----------------------|  
|Séparateur d'éléments de composant|4e|  
|Séparateur d'éléments de données|5e|  
|Notation décimale|6e|  
|Caractère d’échappement|7e|  
|Caractère de répétition|8e|  
|Séparateur de segments|9e|  
|Suffixe séparateur de segments|Caractère situé entre le segment UNA et le segment UNB<br /><br /> **Valeurs :** aucun, CR, LF ou CRLF **Remarque :** le séparateur peut prendre uniquement les valeurs ci-dessus.|  
  
 La chaîne UNA est facultative. Si elle est présente, elle définit tous les délimiteurs pour le fichier. En son absence, le Désassembleur EDI utilise la propriété de composant de pipeline EfactDelimiters pour déterminer les délimiteurs. Pour plus d’informations, consultez [configuration des propriétés de Pipeline EDI](../core/configuring-edi-pipeline-properties.md).  
  
 **Erreurs de validation**  
  
 Si le Désassembleur EDI rencontre une erreur de traitement EDI, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publie les deux erreurs suivantes dans l'Observateur d'événements (si une telle publication est activée) :  
  
-   Une erreur consignée par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] source lorsqu'il interrompt le message. Il s'agit d'une erreur requise relative au traitement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Une erreur signalant des problèmes dans le document informatisé, comme consigné par l'EDI [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] source. Cette erreur est spécifique à EDI.  
  
## <a name="using-agreement-properties"></a>Utilisation des propriétés de l'accord  
 Le désassembleur EDI utilise les propriétés de l’accord s’il peut identifier l’accord (consultez [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)). Si un accord correspondant est introuvable et que les valeurs correspondantes ne sont pas disponibles dans l’accord de secours, les propriétés de désassembleur EDI définies dans le **propriétés** fenêtre de Visual Studio est utilisé. Toutefois, ce secours se produira pas si l’authentification est nécessaire dans les propriétés de port de réception (si le paramètre **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** sont sélectionnés ). Dans ce cas, un accord doit être configuré sinon l'échange est interrompu.  
  
 Lorsque le Désassembleur EDI utilise des propriétés de l'accord, il requiert la définition des propriétés de l'accord suivantes :  
  
|Propriété|Page Propriétés de l'accord|  
|--------------|-------------------------------|  
|Séparateur de répétition|**Enveloppes** page (sous **paramètres de l’échange**) dans l’onglet d’accord bidirectionnel|  
|Effectuer une validation de type de données EDI|**Validation** page sous **paramètres des documents informatisés** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Validation étendue|**Validation** page sous **paramètres des documents informatisés** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Autoriser les zéros et les espaces de début et de fin|**Validation** page sous **paramètres des documents informatisés** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Créer des balises XML vides si les séparateurs de fin sont autorisés|**Paramètres d’hôte local** page sous **paramètres des documents informatisés** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Option de traitement par lot entrant|**Paramètres d’hôte local** page (sous **paramètres de l’échange**) dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Séparateurs EDIFACT par défaut|-|  
|Masquer les informations de sécurité/d'autorisation/de mot de passe|**Paramètres d’hôte local** page (sous **paramètres de l’échange**) dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Convertir la valeur numérique de format décimal implicite en une valeur numérique de base 10|**Paramètres d’hôte local** page sous **paramètres des documents informatisés** dans l’onglet d’accord bidirectionnel (pour X12 accords)|  
|Acheminer les accusés de réception vers le pipeline d'envoi sur le port de réception de requête-réponse|**Paramètres d’hôte local** page (**paramètres du récepteur** section) sous **paramètres de l’échange** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT)|  
|Jeu de caractères X12|X12 génération de l’enveloppe d’échange **Remarque :** ce paramètre est uniquement utilisé pour valider les valeurs entrées pour les propriétés de l’accord. Le jeu de caractères X12 utilisé pour le traitement au moment de l'exécution est sélectionné dans les propriétés de pipeline. Pour plus d’informations, consultez [jeux de caractères EDI](../core/edi-character-sets.md).|  
  
## <a name="using-hipaa-trigger-fields"></a>Utilisation des champs déclencheurs HIPAA  
 Les segments EDI contiennent souvent des valeurs du qualificateur qui modifient la signification d'un segment. Par exemple, un segment N1 peut contenir un élément de qualification « BT » signifiant « Nom de facturation (bill-to) » ou « ST » pour « Nom de livraison (ship-to) ». Normalement, il reste à la logique métier pour déterminer comment interpréter ces champs et le désassembleur fait correspondre toutes les instances du segment N1 avec le même nom de l’enregistrement XML ; Toutefois, les schémas HIPAA inclus dans BizTalk Server contient des annotations permettant au désassembleur EDI créer des enregistrements XML uniques en fonction de la présence d’une valeur de qualification (consultez [Annotations des champs déclencheurs HIPAA schéma](../core/hipaa-schema-trigger-field-annotations.md)).  
  
 Lors de la réception d'un document informatisé HIPAA, si le Désassembleur EDI rencontre un segment contenant un champ déclencheur, il utilise les informations du déclencheur pour générer un enregistrement XML spécifique à la combinaison segment/déclencheur.  
  
 Le tableau suivant montre comment un segment N1 est converti en un enregistrement XML en fonction de la valeur de N101 :  
  
|Segment N1|Données XML résultantes|  
|----------------|------------------------|  
|N1*PR\*Contoso\*XV\*0000000~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|N1*PE\*Fabrikam\*FI\*9999999~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des messages EDI par BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)