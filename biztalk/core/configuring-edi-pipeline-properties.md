---
title: Configuration des propriétés de Pipeline EDI | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edir2.edi.pipeline.properties
ms.assetid: 1b6229b6-a8b0-4824-86bd-39021844c5a8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c810b8507a98b91c0b906131e127f189f0a4fd0f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-edi-pipeline-properties"></a>Configuration des propriétés du pipeline EDI
Les propriétés de pipeline permettent de traiter les échanges EDI entrants et sortants lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne parvient pas à déterminer l'accord correspondant aux échanges. Dans certains cas, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise la propriété de pipeline pour traiter les échanges. Dans d'autres cas, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l'accord de secours. Pour plus d’informations, consultez [la Validation d’un EDI de l’échange est configuré](../core/how-validation-of-an-edi-interchange-is-configured.md).  
  
 Il y a quelques exceptions à cette règle :  
  
-   Pour X12, le jeu de caractères utilisé lors de l'exécution est déterminé par la propriété de pipeline, même si l'accord est déjà identifié. Le jeu de caractères décrit dans l'accord est utilisé aux seules fins de validation des paramètres de la propriété d'accord.  
  
-   Pour EDIFACT, si un échange entrant n’a pas de segment UNA, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les délimiteurs spécifiés dans la propriété de pipeline EfactDelimiters, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n’utilise pas les propriétés définies dans l’accord correspondant au message ou le secours accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="edi-pipeline-properties"></a>Propriétés de pipeline EDI  
 Les propriétés suivantes peuvent être définies dans les pipelines EDI :  
  
|Propriété|Utiliser|Valeurs|Pipeline - Étape|  
|--------------|---------|------------|-----------------------|  
|AllowTrailingDelimiters|Génère des séparateurs de fin sur l'échange reçu.|False (valeur par défaut)<br /><br /> True|EdiReceive - Désassembler<br /><br /> AS2EdiReceive - Désassembler<br /><br /> EdiSend - Assembler<br /><br /> AS2EdiSend - Assembler|  
|CharacterSet|Spécifie le jeu de caractères à utiliser lors de la validation des échanges EDI sortants au moment de l'exécution.<br /><br /> Cette propriété est utilisée pour le traitement des échanges X12 uniquement, pas pour les échanges EDIFACT.|UTF8 (valeur par défaut)<br /><br /> Basic<br /><br /> Étendue|EdiReceive - désassembler<br /><br /> AS2EdiReceive - Désassembler<br /><br /> EdiSend - Assembler<br /><br /> AS2EdiSend - Assembler|  
|ConvertToImpliedDecimal|Dans le cas d'un échange entrant, convertit un nombre EDI spécifié au format Nn en une valeur numérique de base 10 dans le fichier XML intermédiaire dans BizTalk Server.<br /><br /> Cette propriété est utilisée pour le traitement des échanges X12 uniquement, pas pour les échanges EDIFACT.|False (valeur par défaut)<br /><br /> True|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|CreateXMLTagForTrailingSeparators|Crée des balises XML vides pour chacun des séparateurs de fin (si vous avez défini **AllowTrailingDelimiters** sur true).|False (valeur par défaut)<br /><br /> True|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|DetectMID|Permet au Désassembleur EDI d'analyser plusieurs échanges dans un seul message.|True (valeur par défaut)<br /><br /> False|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|EdiDataValidation|Active la validation de type EDI (éléments de données) pour les échanges EDI sortants, mais aussi la validation de la longueur de champ, le caractère facultatif et le nombre de répétitions.|True (valeur par défaut)<br /><br /> False|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler<br /><br /> EdiSend - Assembler<br /><br /> AS2EdiSend - Assembler|  
|EfactDelimiters|Indique les délimiteurs à utiliser dans le cadre du traitement d'un échange entrant. Cette propriété est utilisée si un échange entrant n'a pas de segment UNA.<br /><br /> Les délimiteurs sont les suivants :<br /><br /> -UNA1 (séparateur d’éléments de données composant)<br />-UNA2 (séparateur d’éléments de données)<br />-UNA3 (notation décimale)<br />-UNA4 (indicateur de version)<br />-UNA5 (séparateur de répétition)<br />-UNA6 (terminateur de Segment) **Remarque :** cette propriété est utilisée pour EDIFACT, le traitement uniquement, pas pour X12.|0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27 (valeurs par défaut)|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
IgnoreMessageEncoding|Spécifie que le composant BatchMarker ne définira pas EDI. Propriété de contexte Type_codage \<X12\> ou \<EDIFACT\>. Cette propriété s'applique aux pipelines personnalisés utilisés dans le cadre du traitement des messages non-EDI.|False (valeur par défaut)<br /><br /> True|EdiReceive - RésoudreTiers<br /><br /> AS2EdiReceive - RésoudreTiers|  
|MaskSecurityInformation|Masque les informations de sécurité d'autorisation/de mot de passe dans la propriété de contexte d'un échange EDI entrant afin d'empêcher toute divulgation d'informations. Cette propriété s'applique aux champs ISA1, ISA2, ISA3 et ISA4 pour les échanges X12, et aux champs UNB6 pour les échanges EDIFACT.|True (valeur par défaut)<br /><br /> False|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|PreserveInterchange|Spécifie qu'un lot reçu sera traité sous forme d'unité globale.|False (valeur par défaut)<br /><br /> True|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|RouteAckOn2WayPort|Renvoie un accusé de réception EDI via la connexion ouverte d'un port de réception bidirectionnel de requête-réponse.|True (valeur par défaut)<br /><br /> False|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|UseDotAsDecimalSeperator|Lorsque cette propriété a la valeur True, l’EDI pipeline de réception utilise une notation décimale de «. » au lieu de la notation décimale du document entrant.|False (valeur par défaut)<br /><br /> True|EdiReceive-désassembler<br /><br /> AS2EdiReceive - désassembler|  
|UseIsa11AsRepetitionSeparator|Spécifie l'utilisation d'ISA11 comme séparateur de répétition au lieu d'un identificateur standard. **Remarque :** cette propriété est utilisée pour X12 traitement uniquement, pas pour EDIFACT.|False (valeur par défaut)<br /><br /> True|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler|  
|XmlSchemaValidation|Permet la validation étendue (BTS-XSD) des échanges EDI sortants. Cette propriété s'applique uniquement si le schéma a été personnalisé à l'aide d'éléments d'un type de données autre qu'EDI. Ces éléments ajoutés ne sont pas destinés à être validés via la validation EDI. Ils sont donc soumis à la validation étendue.|False (valeur par défaut)<br /><br /> True|EdiReceive - désassembler<br /><br /> AS2EdiReceive - désassembler<br /><br /> EdiSend - Assembler<br /><br /> AS2EdiSend - Assembler|  
  
### <a name="to-set-a-pipeline-property"></a>Pour définir une propriété de pipeline  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur l’emplacement de réception port d’envoi ou à l’aide du pipeline que vous souhaitez définir les propriétés de, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur le bouton représentant des points de suspension (…) en regard du pipeline pour lequel définir les propriétés.  
  
3.  Dans le **configurer le Pipeline** boîte de dialogue, entrez la valeur de la propriété, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la validation d’un échange EDI](../core/how-validation-of-an-edi-interchange-is-configured.md)