---
title: "Propriétés de contexte de remplacement EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78cd56f-1e34-4503-8ee1-93b52137097f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182ddc6a243a578a890a47dc70faa427b4f6df88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-override-context-properties"></a>Propriétés de contexte de remplacement EDI
Les propriétés de contexte de message du schéma de propriété global EdiOverride permettent de remplacer les valeurs de l'enveloppe EDI au moment de l'exécution. Elles sont définies dans le fichier edi-properties.xsd dans l'assembly Microsoft.BizTalk.Edi.BaseArtifacts. L'espace de noms de ces propriétés est `http://schemas.microsoft.com/BizTalk/2006/edi-properties`.  
  
 Les propriétés de contexte EdiOverride sont également disponibles dans une orchestration, tant qu'une référence vers l'assembly Microsoft.BizTalk.Edi.BaseArtifacts est ajoutée au projet d'orchestration.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|OverrideEDIHeader|boolean|Si la valeur est True, le pipeline d'envoi EDI tente de créer l'enveloppe EDI à l'aide des valeurs de la collection de propriétés EdiOverride.|  
|ISA01|chaîne|Qualificateur d'informations d'autorisation (X12)|  
|ISA02|chaîne|Informations d'autorisation (X12)|  
|ISA03|chaîne|Qualificateur d'informations de sécurité (X12)|  
|ISA04|chaîne|Informations de sécurité (X12)|  
|ISA05|chaîne|Qualificateur d'expéditeur des échanges (X12)|  
|ISA06|chaîne|ID de l'expéditeur des échanges (X12)|  
|ISA07|chaîne|Qualificateur de récepteur des échanges (X12)|  
|ISA08|chaîne|ID du récepteur des échanges (X12)|  
|ISA09|chaîne|Date de l'échange (X12)<br /><br /> Ce champ doit contenir la valeur réelle de la date, et non le format de date.|  
|ISA10|chaîne|Heure de l'échange (X12)<br /><br /> Ce champ doit contenir la valeur réelle de l'heure, et non la valeur de la date.|  
|ISA11|chaîne|Identificateur de normes de contrôle d'échange (X12)|  
|ISA12|chaîne|Numéro de version de contrôle d'échange (X12)|  
|ISA13|chaîne|Numéro de contrôle de l'échange (X12)<br /><br /> Si le numéro de contrôle de l'échange est remplacé, le segment de code de fin de l'échange (IEA) correspondant est redéfini pour correspondre à la valeur spécifiée.|  
|ISA14|chaîne|Accusé de réception obligatoire (X12)|  
|ISA15|chaîne|Indicateur de test (X12)|  
|ISA16|chaîne|Séparateur d'éléments composites (X12)|  
|GS01|chaîne|Code d'identificateur fonctionnel (X12)|  
|GS02|chaîne|Code de l’expéditeur de l’Application (X12)|  
|GS03|chaîne|Code de l'application réceptrice (X12)|  
|GS04|chaîne|Date (X12)<br /><br /> Ce champ doit contenir la valeur réelle de la date, et non le format de date.<br /><br /> Cette valeur doit être au format SSAAMMJJ ou AAMMJJ. La date fournie est utilisée même si son format diffère de celui sélectionné dans les propriétés du tiers.|  
|GS05|chaîne|Heure (X12)<br /><br /> Ce champ doit contenir la valeur réelle de l'heure, et non le format d'heure.<br /><br /> Cette valeur doit être au format HHMM, HHMMSS ou HHMMSSjj. L'heure fournie est utilisée même si son format diffère de celui sélectionné dans les propriétés du tiers.|  
|GS06|chaîne|Numéro de contrôle du groupe (X12)<br /><br /> Si le numéro de contrôle du groupe est remplacé, le champ correspondant dans le segment GE est redéfini pour correspondre à la valeur spécifiée.|  
|GS07|chaîne|Code de l'entité responsable (X12)|  
|GS08|chaîne|Code identificateur de la version, de la version finale, de l'activité (X12)|  
|ST02|chaîne|Le numéro de contrôle Transaction (X12)<br /><br /> Si le numéro de contrôle du document informatisé est remplacé, le champ correspondant du segment de code de fin du document informatisé (SE) est redéfini pour correspondre à cette valeur.|  
|GenerateUNA|boolean|Détermine si le pipeline d'envoi EDI va créer un segment UNA pour le document EDIFACT sortant.<br /><br /> Si les valeurs de OverrideEdiHeader et GenerateUNA sont définies sur True, un segment UNA est généré. Si OverrideEdiHeader est défini sur True, et GenerateUNA sur False, aucun segment UNA n'est généré.<br /><br /> Les valeurs du segment UNA sont déterminées dans l'ordre suivant :<br /><br /> -Les propriétés de contexte EdiOverride, si toutes les propriétés UNA sont présentes.<br />-Si ce n’est pas toutes les propriétés de contexte sont présentes et segment Generateuna est activé dans les propriétés de tiers, une combinaison de propriétés de contexte et des propriétés de tiers.<br />-Si toutes les propriétés de contexte sont présentes, et pas segment Generateuna est activé dans les propriétés du tiers, une combinaison de propriétés de contexte et des valeurs UNA standard **Remarque :** ce champ n’a aucun effet si OverrideEdiHeader est défini sur false.|  
|UNA1|chaîne|Séparateur d'éléments de données composites (EDIFACT)|  
|UNA2|chaîne|Séparateur d'éléments de données (EDIFACT)|  
|UNA3|chaîne|Marqueur décimal (EDIFACT)|  
|UNA4|chaîne|Caractère d'échappement (EDIFACT)|  
|UNA5|chaîne|Séparateur de répétition (EDIFACT)|  
|UNA6|chaîne|Terminateur de segment (EDIFACT)|  
|UNA6Suffix|chaîne|Suffixe du terminateur de segment (EDIFACT)|  
|UNB1_1|chaîne|Identificateur de syntaxe (EDIFACT)|  
|UNB1_2|chaîne|Numéro de version de syntaxe (EDIFACT)|  
|UNB10|chaîne|ID de l'accord de communications (EDIFACT)|  
|UNB11|chaîne|Indicateur de test (EDIFACT)|  
|UNB2_1|chaîne|Identification de l'expéditeur (EDIFACT)|  
|UNB2_2|chaîne|Qualificateur de code de l'identification du partenaire (EDIFACT)|  
|UNB2_3|chaîne|Adresse de routage inverse (EDIFACT)|  
|UNB3_1|chaîne|Identification du destinataire (EDIFACT)|  
|UNB3_2|chaîne|Qualificateur de code de l'identification du partenaire (EDIFACT)|  
|UNB3_3|chaîne|Adresse de routage (EDIFACT)|  
|UNB4_1|chaîne|Date (EDIFACT)<br /><br /> Ce champ doit contenir la valeur réelle de la date, et non le format de date.|  
|UNB4_2|chaîne|Heure (EDIFACT)<br /><br /> Ce champ doit contenir la valeur réelle de l'heure, et non le format d'heure.|  
|UNB5|chaîne|Référence de contrôle de l'échange (EDIFACT)<br /><br /> Si la référence de contrôle de l'échange est remplacée, le numéro de contrôle du segment de code de fin de l'échange (UNZ) est redéfini pour correspondre à la valeur spécifiée.|  
|UNB6_1|chaîne|Mot de passe ou référence du destinataire (EDIFACT)|  
|UNB7|chaîne|Référence d'application (EDIFACT)|  
|UNB8|chaîne|Code de priorité de traitement (EDIFACT)|  
|UNB9|chaîne|Accusé de réception obligatoire (EDIFACT)|  
|GenerateUNG|boolean|Détermine si le pipeline d'envoi EDI va créer un segment UNG pour le document EDIFACT sortant.<br /><br /> Si OverrideEdiHeader et GenerateUNG sont définis sur True, un segment UNA est généré. Si OverrideEdiHeader est défini sur True, et GenerateUNG sur False, aucun segment UNG n'est généré.<br /><br /> Les valeurs du segment UNG sont déterminées dans l'ordre suivant :<br /><br /> -Les propriétés de contexte EdiOverride, si toutes les propriétés UNG sont présentes.<br />-Si ce n’est pas toutes les propriétés de contexte sont présentes et segment Generateung est activé dans les propriétés de tiers, une combinaison de propriétés de contexte et des propriétés de tiers.<br />-Si toutes les propriétés de contexte sont présentes, et pas segment Generateung est activé dans les propriétés du tiers, une combinaison de propriétés de contexte et des valeurs UNA standard **Remarque :** ce champ n’a aucun effet si OverrideEdiHeader est défini sur false.|  
|UNG1|chaîne|Identification du groupe de message (EDIFACT)|  
|UNG2_1|chaîne|Identification de l'expéditeur de l'application (EDIFACT)|  
|UNG2_2|chaîne|Qualificateur de code d'identification (EDIFACT)|  
|UNG3_1|chaîne|L’Identification destinataire (EDIFACT)|  
|UNG3_2|chaîne|Qualificateur de code d'identification (EDIFACT)|  
|UNG4_1|chaîne|Date de préparation (EDIFACT)<br /><br /> Ce champ doit contenir la valeur réelle de la date, et non le format de date.|  
|UNG4_2|chaîne|Heure de préparation (EDIFACT)<br /><br /> Ce champ doit contenir la valeur réelle de l'heure, et non le format d'heure.|  
|UNG5|chaîne|Numéro de référence du groupe (EDIFACT)<br /><br /> Si le numéro de référence du groupe est remplacé, le champ correspondant du segment de code de fin du groupe (UNE) est redéfini pour correspondre à la valeur spécifiée.|  
|UNG6|chaîne|Agence de contrôle codée (EDIFACT)|  
|UNG7_1|chaîne|Numéro de version du message (EDIFACT)|  
|UNG7_2|chaîne|Numéro de version finale du message (EDIFACT)|  
|UNG7_3|chaîne|Code d'association assigné (EDIFACT)|  
|UNG8|chaîne|Mot de passe de l'application (EDIFACT)|  
|UNH1|chaîne|Numéro de référence du message (EDIFACT)<br /><br /> Si le numéro de référence du message est remplacé, le champ correspondant du segment de code de fin du message (UNT) est redéfini pour correspondre à la valeur spécifiée.|  
  
## <a name="edioverride-context-property-usage"></a>Utilisation de la propriété de contexte EDIOverride  
 Si le **OverrideEdiHeader** propriété de contexte a la valeur true, les valeurs spécifiées dans les propriétés de contexte EDIOverride seront utilisés pour créer l’enveloppe EDI pour le message sortant. Si aucune valeur n'est spécifiée pour une propriété de contexte EDIOverride, le tiers ou la propriété globale correspondante est utilisé.  
  
 Les valeurs spécifiées pour les propriétés de contexte EDIOverride doivent être conformes aux normes X12 ou EDIFACT ainsi qu'aux extensions de schéma de service.  
  
-   Les champs doivent contenir des valeurs valides pour ce type de champ, y compris les extensions de schéma de service.  
  
-   Les numéros de contrôle doivent être valides, mais ne doivent pas nécessairement suivre l'ordre des paramètres de tiers existants.  
  
-   Les champs Date et Heure doivent contenir des valeurs de date et d'heure, et doivent correspondre à la norme EDI appropriée, même si le format de la valeur ne correspond pas au format défini dans les paramètres du tiers.  
  
 Certaines propriétés de contexte EDIOverride sont uniquement prises en charge lorsque le message envoyé par le pipeline d'envoi EDI est une transaction unique ou un lot. Le tableau suivant répertorie les propriétés de contexte prises en charge pour chaque type de message :  
  
|Transaction EDI en cours d'envoi|Propriétés de contexte EDIOverride prises en charge|  
|--------------------------------|----------------------------------------------|  
|Document informatisé unique|-Tous les segments ISA<br />-Tous les segments GS<br />-ST02<br />-GenerateUNA<br />-Tous les segments UNA<br />-Tous les segments UNB<br />-GenerateUNG<br />-Tous les segments UNG<br />-UNH1|  
|Lot de documents informatisés publiés par l'orchestration de traitement par lot ou document informatisé entrant ou sortant du lot publié par le pipeline de réception EDI|-Tous les segments ISA<br />-GS04<br />-GS05<br />-GenerateUNA<br />-Tous les segments UNA<br />-Tous les segments UNB<br />-GenerateUNG<br />-UNG4.1<br />-UNG4.2|  
  
 Bien que les propriétés de contexte EDIOverride puissent également être appliquées aux messages traités par lot, l'orchestration de traitement par lot prend uniquement en charge les propriétés de contexte EDIOverride ST01 et UNH1.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)