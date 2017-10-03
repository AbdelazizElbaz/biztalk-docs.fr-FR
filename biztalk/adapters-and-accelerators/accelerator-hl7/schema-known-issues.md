---
title: "Problèmes connus de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, schemas
- schemas, known issues
ms.assetid: 17651462-baa9-448a-954c-c09e70640f17
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0568a892559ea119b9a198368b4521cbe49ddf45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-known-issues"></a>Problèmes connus de schéma
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de schéma.  
  
## <a name="mcf21glodefxsd-schema"></a>Schéma de MCF_21_GLO_DEF.xsd  
 Dans le dossier templates\schemas\2.1, schéma MCF_21_GLO_DEF.xsd n’est pas une partie du projet Common231.  
  
## <a name="miscellaneous-errors-can-result-from-undeployed-schemas"></a>Erreurs diverses peuvent être dû à des schémas annulés  
 Si vous ne parvenez pas à identifier une erreur lors de l’analyse ou la sérialisation, vérifiez que vous avez déployé des schémas de propriété et des schémas courants (MSH/ACK). Schémas de propriété annulé et les schémas courants peuvent provoquer des erreurs diverses.  
  
## <a name="if-the-starter-project-is-installed-but-the-hl7-2x-schemas-are-not-installed-running-the-schema-wizard-generates-an-error"></a>Si le projet de démarrage est installé, mais le HL7 2.X schémas ne sont pas installés, l’exécution de l’Assistant schéma génère une erreur  
 Si vous exécutez une installation personnalisée de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) dans lequel vous installez le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] projet de démarrage, mais ne pas installer le HL7 les schémas 2.X, puis essayez d’exécuter l’Assistant schéma, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère une erreur. La solution est de réexécuter le processus d’installation personnalisé pour installer le HL7 2.X schémas.  
  
## <a name="msh91-enumeration-list-needs-to-be-updated"></a>Liste d’énumération MSH9.1 doit être mis à jour  
 Le schéma MSH_25_GLO_DEF installé par [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation ne contient pas les listes d’énumération complète pour MSH9.1 (le MessageType) et MSH9.2 (EventTrigger), dans le HL72. X standard. Le tableau suivant répertorie le type et le déclencheur événement valeurs du message d’avoir à ajouter à la table associée, si vous souhaitez utiliser un schéma dont le type de message contient la valeur. Par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne traitera pas un QBP ^ Z99 message jusqu'à ce que vous ajoutez « QBP » à l’énumération pour Table76 dans MSH_25_GLO_DEF, et il ne traitera pas un QBP ^ Z99 message jusqu'à ce que vous ajoutez « Z99 » à l’énumération pour Table3 dans MSH_25_GLO_DEF.  
  
 Pour ajouter une valeur à une énumération MSH9.2 ou MSH9.1, consultez la procédure « pour ajouter une valeur d’énumération à un schéma d’en-tête de message » dans [énumérations d’extension](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
|Champ ou de la Table|Valeur à ajouter à une énumération|  
|------------------|--------------------------------------|  
|MessageType/Table76|ARD, RDO, RRO|  
|TriggerEvent/Table3|K11, K13, K15, L’AUTHENTIFICATION MULTIFACTEUR, O22, Q 11, Q 13, Q15, Q26, Q27, Q28, Q29, R0R, Z73, Z74, Z75, Z76, Z77, Z78, Z79, Z80, Z81, Z82, Z83, Z84, Z85, Z86, Z87, Z88, Z89, Z90, Z91, Z92, Z93, Z94, Z95, Z96, Z97, Z98, Z99|  
|MessageStructure/Table354|ARD_A19, ORL_O22|  
  
## <a name="btahl7-does-not-support-schemas-with-an-ambiguous-structure"></a>BTAHL7 ne prend pas en charge les schémas avec une structure ambiguë  
 Le moteur de BTAHL7 ne peut pas traiter les instances de message conforme aux schémas HL7 qui ont une structure ambigüe. Une structure de schéma ambigu est celle qui n’est pas complètement défini par la norme HL7. Ces schémas incluent ceux pour les types de messages CSU, OMD, ORD et SUR.  
  
## <a name="btahl7-will-return-a-segment-sequence-error-for-some-messages"></a>BTAHL7 retourne une erreur de séquence de segment pour certains messages  
 BTAHL7 ne peut pas traiter les messages conformes aux schémas répertoriés ci-dessous. L’analyse du corps de ces messages échouera, ce qui entraîne l’erreur suivante : « Erreur de séquence (segment non valide trouvé après ce segment) du Segment ». Les ID de Segment affectés dans les messages sont répertoriés ci-dessous. Les numéros de séquence affectés pour toutes ces erreurs est « 2 ».  
  
|Version|Type de message|Événement déclencheur|ID de segment|  
|-------------|------------------|-------------------|----------------|  
|VERSION 2.3|CSU|C09|ORC_CommonOrderSegment|  
|VERSION 2.3|CSU|C10|ORC_CommonOrderSegment|  
|VERSION 2.3|CSU|C11|ORC_CommonOrderSegment|  
|VERSION 2.3|CSU|C12|ORC_CommonOrderSegment|  
|VERSION 2.3|SUR|P09|PSH_ProductSummaryHeader|  
|V2.3.1|CSU|C09|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C10|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C11|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C12|ORC_CommonOrderSegment|  
|V2.3.1|SUR|P09|PSH_ProductSummaryHeader<br />Segment|  
|V2.4|CSU|C09|ORC_CommonOrder|  
|V2.4|CSU|C10|ORC_CommonOrder|  
|V2.4|CSU|C11|ORC_CommonOrder|  
|V2.4|CSU|C12|ORC_CommonOrder|  
|V2.4|OMD|O03|ORC_CommonOrder|  
|V2.4|ORD|O04|ORC_CommonOrder|  
|V2.4|SUR|P09|PSH_ProductSummaryHeader|  
|2.5|CSU|C09|ORC_CommonOrder|  
|2.5|CSU|C10|ORC_CommonOrder|  
|2.5|CSU|C11|ORC_CommonOrder|  
|2.5|CSU|C12|ORC_CommonOrder|  
|2.5|OMD|O03|ORC_CommonOrder|  
|2.5|ORD|O04|ORC_CommonOrder|  
|2.5|SUR|P09|PSH_ProductSummaryHeader »|  
|2.5|RDE|025|PSH_ProductSummaryHeader »|  
|2.5|OUL|R24|PSH_ProductSummaryHeader »|  
|2.5|OML|035|PSH_ProductSummaryHeader »|  
|2.5|ORL|034|PSH_ProductSummaryHeader »|  
  
> [!NOTE]
>  La liste ci-dessus pour la version 2.5 n’est pas exhaustive et peut inclure des types de messages supplémentaires qui provoque le « erreur de séquence Segment ».  
  
## <a name="btahl7-does-not-support-some-v231-schemas"></a>BTAHL7 ne prend pas en charge certains schémas v2.3.1  
 Le programme d’installation BTAHL7 n’installe pas les schémas v2.3.1 suivants :  
  
-   OMD_O01_231_GLO_DEF  
  
-   OMN_O01_231_GLO_DEF  
  
-   OMS_O01_231_GLO_DEF  
  
-   ORD_O02_231_GLO_DEF  
  
-   ORN_O02_231_GLO_DEF  
  
-   ORS_O02_231_GLO_DEF  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)