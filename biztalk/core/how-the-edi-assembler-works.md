---
title: "Fonctionne de l’assembleur EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3785870-08ab-4fc2-8f7e-7c5a37639a7a
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f11fa41cabb6d5199953c2df005aa79965216f9
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-the-edi-assembler-works"></a>Fonctionnement de l'Assembleur EDI
Le plus souvent, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite les échanges EDI à envoyer dans le pipeline d'envoi EDI (`Microsoft.BizTalk.DefaultPipelines.EDISendPipeline`). Ce pipeline inclut le composant de pipeline Assembleur EDI, qui effectue le traitement suivant :  
  
-   Sérialise l'échange EDI, en convertissant des messages XML en documents informatisés EDI dans l'échange.  
  
-   Effectue une validation du schéma EDI, une validation de champ croisé pour les messages X12 (si configurée), une validation structurelle EDI et une validation étendue de schéma (si le schéma est personnalisé avec un nœud qui a un type de données non EDI).  
  
-   Applique une enveloppe au message EDI.  
  
-   Traite les accusés de réception technique et fonctionnel reçus en réponse aux messages EDI, en décomposant les lots d'accusés de réception, si configuré.  
  
## <a name="applying-an-envelope-to-an-outgoing-edi-message"></a>Application d'une enveloppe à un message EDI sortant  
 Lorsque le pipeline d'envoi EDI crée un message EDI sortant à partir d'un fichier XML intermédiaire, il applique une enveloppe contenant des en-têtes d'échange et de groupe au message en fonction des propriétés EDI établies dans le cadre de l'accord côté réception. Si le pipeline d'envoi ne peut pas déterminer l'accord récepteur à partir du port d'envoi, il utilise l'accord de secours pour appliquer l'enveloppe.  
  
 Si la propriété de contexte `EdiOverride.OverrideEdiHeader` est définie sur true, le pipeline d'envoi EDI utilise les valeurs spécifiées dans la collection de propriétés EdiOverride pour créer l'enveloppe. Si aucune valeur n'est présente dans la collection, la valeur EDI correspondante dans les propriétés de l'accord est utilisée. Si aucune valeur n'existe dans la collection EdiOverride ou les propriétés de l'accord, les propriétés de l'accord EDI de secours sont utilisées.  
  
 Si le fichier XML intermédiaire a une balise réservée ou la propriété de contexte ReuseEnvelope, le message est un lot conservé et la logique d'application de l'enveloppe ne convient pas.  
  
### <a name="sources-for-x12-envelope-values"></a>Sources des valeurs de l'enveloppe X12  
 Le tableau suivant indique l'endroit où le pipeline d'envoi EDI va chercher les informations dont il a besoin pour chaque partie d'une enveloppe X12 :  
  
|En-tête|Source|  
|------------|------------|  
|En-tête de contrôle de l'échange (ISA)|-Propriétés de contexte EdiOverride (si `EdiOverride.OverrideEdiHeader` a la valeur true).<br />-Si un accord est défini, définitions du segment ISA à partir de différentes pages, dans le **paramètres de l’échange** section dans les propriétés d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.<br />-Si aucun accord n’est défini, définitions du segment ISA à partir de différentes pages, dans le **paramètres de l’échange** section dans le **paramètres de secours EDIFACT** boîte de dialogue.|  
|En-têtes de groupe fonctionnel (GS)|-Propriétés de contexte EdiOverride (si `EdiOverride.OverrideEdiHeader` a la valeur true)<br />-Si un accord est défini, définitions du segment GS à partir de la **enveloppes** page (sous **paramètres des documents informatisés** section) dans les propriétés d’accord unidirectionnel dans la **propriétés de l’accord**  boîte de dialogue<br />-Si aucun accord n’est défini, définitions du segment GS à partir de la **enveloppes** page (sous **paramètres des documents informatisés** section) dans le **X12 paramètres de secours** boîte de dialogue<br /><br /> Si un accord est défini, les valeurs des éléments de données GS sont déterminées en fonction de la combinaison de l'identificateur de document informatisé (ST1), de la version et de l'espace de noms cible. Ces valeurs sont comparées à la grille dans le **enveloppes** page (sous **paramètres des documents informatisés** section) des propriétés de l’accord (si un accord est défini) ou les propriétés de l’accord de secours (le cas aucun accord n’est définie) :<br /><br /> -S’il existe une ligne correspondante, les valeurs contenues dans la ligne correspondante sont utilisés pour l’en-tête GS.<br />-Si aucune correspondance, mais une ligne par défaut est définie, tous les éléments de données GS, à l’exception de GS01 sont remplis à partir de la ligne par défaut. GS01 est déterminé de manière dynamique, en fonction de la valeur de ST1.<br />-Si aucune ligne correspondante et aucune ligne par défaut, le message est suspendu. **Remarque :** pour un groupe se différencie des autres groupes, toutes ces valeurs peuvent être les mêmes que ceux d’un autre groupe. <br /><br /> Si aucun accord n'est défini, les éléments de données GS sont renseignés à partir des propriétés de l'accord de secours.|  
  
### <a name="sources-for-edifact-envelope-values"></a>Sources des valeurs de l'enveloppe EDIFACT  
 Le tableau suivant indique l'endroit où le pipeline d'envoi EDI va chercher les informations dont il a besoin pour chaque partie d'une enveloppe EDIFACT :  
  
|En-tête|Source|  
|------------|------------|  
|Options de l'échange (UNA)|-Propriétés de contexte EdiOverride (si `EdiOverride.OverrideEdiHeader` a la valeur true).<br />-Si un accord est défini, définitions du segment UNA à partir de **jeu de caractères et séparateurs** page dans les propriétés d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.<br />-Si aucun accord n’est défini, définitions du segment UNA à partir de **jeu de caractères et séparateurs** page dans le **paramètres de secours EDIFACT** boîte de dialogue.|  
|En-tête de contrôle de l'échange (UNB)|-Propriétés de contexte EdiOverride (si `EdiOverride.OverrideEdiHeader` a la valeur true).<br />-Si un accord est défini, définitions du segment UNB à partir de différentes pages, dans le **paramètres de l’échange** section dans les propriétés d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.<br />-Si aucun accord n’est défini, définitions du segment UNB à partir de différentes pages, dans le **paramètres de l’échange** section dans le **paramètres de secours EDIFACT** boîte de dialogue.|  
|En-têtes de groupe fonctionnel (UNG)|-Propriétés de contexte EdiOverride (si `EdiOverride.OverrideEdiHeader` a la valeur true).<br />-Si un accord est défini, UNG et UNH définitions à partir du segment du **enveloppes** page (sous **paramètres des documents informatisés** section) dans les propriétés d’accord unidirectionnel dans la **accord Propriétés** boîte de dialogue<br />-Si aucun accord n’est défini, UNG et UNH définitions à partir du segment du **enveloppes** page (sous **paramètres des documents informatisés** section) dans les propriétés d’accord unidirectionnel dans la **accord Propriétés** boîte de dialogue de la **paramètres de secours EDIFACT** boîte de dialogue<br /><br /> Si un accord est défini, les valeurs des éléments de données UNG sont déterminées en fonction de la combinaison du type de message (UNH2.1), du numéro de version finale du message (UNH2.3), du code assigné (UNH2.5), de la version et de l'espace de noms cible. **Remarque :** pour un groupe se différencie des autres groupes, toutes ces valeurs peuvent être les mêmes que ceux d’un autre groupe.|  
  
### <a name="applying-transaction-set-header-and-trailer-segments"></a>Application de segments d'en-tête et de code de fin de document informatisé  
 Un document informatisé XML en cours de sérialisation dans un échange EDI sortant doit avoir un en-tête et un code de fin de document informatisé. L'Assembleur EDI traite toutefois le message même s'il n'inclut pas d'en-tête et de code de fin de document informatisé. Les segments d'en-tête et de code de fin de document informatisé dans les schémas X12 et EDIFACT sont facultatifs pour les documents informatisés XML. Si un document informatisé n'inclut pas d'en-tête ou de code de fin, l'Assembleur EDI dans le pipeline d'envoi EDISend ou AS2EDISend lui ajoute les valeurs d'en-tête et de code de fin de document informatisé. Ces valeurs sont basées sur les mappages ou calculs. L'Assembleur EDI procède ainsi pour le fichier XML d'échange (un lot conservé), le fichier XML de document informatisé par lot et le fichier XML de document informatisé.  
  
 Si le mappage génère une erreur de validation, le document informatisé XML ou le fichier XML d'échange est interrompu et une erreur appropriée s'affiche dans l'observateur d'événements, telle qu'une longueur, un type de données ou un code d'agence de contrôle invalide.  
  
####  <a name="BKMK_X12"></a>X12 en-tête du document informatisé et les Segments de code de fin  
 Pour les documents informatisés X12 sans segments d'en-tête et de code de fin, l'Assembleur EDI définit les segments ST et SE comme suit :  
  
|Segment d'en-tête / de code de fin|Valeur|  
|----------------------------|-----------|  
|ST01 (code identificateur du document informatisé)|Mappé aux trois derniers caractères du nom RootNode issu du document informatisé XML entrant. Par exemple, « 855 » à partir de « X12_00401_855 ». Pour les demandes HIPAA avec un code identificateur du document informatisé 837P, 837D ou 837I, « 837 » est utilisé.|  
|ST02 (numéro de contrôle du document informatisé)|La valeur de `EdiOverride.ST02` (si `EdiOveride.OverrideEdiHeader` a la valeur true,) ou mappé à la valeur de la **numéro de contrôle (ST02) du document informatisé** dans le **paramètres d’hôte Local** page (sous **de l’échange Paramètres**) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.<br /><br /> Un numéro de contrôle nouveau ou incrémenté est appliqué indépendamment du paramètre de la **appliquer le nouvel ID** propriété.|  
|ST03 (identificateur de version)|Mappé à la valeur de ST03 dans le document informatisé XML entrant. Par exemple, « 005010X218 » pour un document 5010 HIPAA 820 (déduction de salaire). ST03 est validé par rapport au schéma qui est utilisé pour valider le document informatisé. **Remarque :** ST03 est obligatoire pour toutes les transactions de la version 5010 HIPAA, à l’exception de 835.|  
|SE01 (nombre de segments inclus)|Défini sur le nombre total de segments dans le document informatisé, segments ST et SE inclus.|  
|SE02 (numéro de contrôle du document informatisé)|Mappé à la valeur de ST02 dans le document informatisé.|  
  
 Les autres éléments de données dans l'en-tête du document informatisé, tels que ST03, sont facultatifs et n'ont donc pas de valeur dans les segments générés.  
  
####  <a name="BKMK_EDIFACT"></a>En-tête du document informatisé EDIFACT et Segments de code de fin  
 Pour les documents informatisés EDIFACT sans segments d'en-tête et de code de fin, l'Assembleur EDI définit les segments UNH et UNT comme suit :  
  
|Segment d'en-tête / de code de fin|Valeur|  
|----------------------------|-----------|  
|UNH01 (numéro de contrôle de référence du message)|La valeur de `EdiOverride.UNH1` (si `EdiOverride.OverrideEdiHeader` a la valeur true,) ou mappé à la valeur de **numéro de référence (UNH1)** dans les **paramètres d’hôte Local** page (sous **paramètres de l’échange**) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Un numéro de contrôle nouveau ou incrémenté est appliqué indépendamment du paramètre de la **appliquer le nouvel ID** propriété.|  
|UNH2.1 (type de message)|Mappé aux six derniers caractères du nom RootNode à partir du document informatisé XML entrant. Par exemple, « INVOIC » à partir de « EFACT_D96A_INVOIC ».|  
|UNH2.2 (numéro de version du message)|Mappé au septième caractère du nom RootNode à partir du document informatisé XML entrant. Par exemple, « D » à partir de « EFACT_D96A_INVOIC ».|  
|UNH2.3 (numéro de version finale du message)|Mappé aux huitième, neuvième et dixième caractères du nom RootNode à partir du document informatisé XML entrant. Par exemple, « 96A » à partir de « EFACT_D96A_INVOIC ».|  
|UNH2.4 (code d'agence de contrôle)|Toujours mappé à la chaîne « UN ».|  
|UNT01 (nombre de segments inclus)|Défini sur le nombre total de segments dans le document informatisé, segments UNH et UNT inclus.|  
|UNH02 (numéro de contrôle de référence du message)|Mappé à la valeur de **numéro de référence (UNH1)** dans les **paramètres d’hôte Local** page (sous **paramètres de l’échange**) de l’onglet d’accord unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue|  
  
 Les autres éléments de données dans l'en-tête du document informatisé UNH, tels que les éléments UNH3 à UNH6, sont facultatifs et n'ont donc pas de valeur dans les segments générés. Si l'un de ces champs est requis, vous devez les définir sur une valeur dans le document informatisé XML entrant.  
  
### <a name="additional-processing-on-envelope-of-an-outgoing-message"></a>Traitement supplémentaire sur l'enveloppe d'un message sortant  
 Le pipeline d'envoi EDI effectue le traitement suivant sur l'enveloppe d'un message sortant.  
  
#### <a name="control-numbers"></a>Numéros de contrôle  
 Le pipeline d'envoi EDI entre un numéro de contrôle de l'échange, un numéro de contrôle du groupe et un numéro de contrôle (ou référence) du document informatisé dans les segments d'enveloppe de chaque échange sortant. Ces numéros sont disponibles dans le tableau suivant :  
  
|Numéro de contrôle|Champ X12|Champ EDIFACT|  
|--------------------|---------------|-------------------|  
|Numéro de contrôle de l'échange|ISA13|UNB5|  
|Numéro de contrôle du groupe|GS6|UNG5|  
|Numéro de contrôle du document informatisé (X12)<br /><br /> Numéro de référence du document informatisé (EDIFACT)|ST2|UNH1|  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]définit le numéro de contrôle pour le prochain échange envoyé en fonction de la plage de valeurs que vous avez entré dans le **numéro de contrôle d’échange (ISA13)** propriété sur le **paramètres d’hôte Local** page () sous **paramètres de l’échange**) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Il incrémente ce numéro pour chaque échange suivant, jusqu'à atteindre la valeur maximale.  
  
 Si le numéro de contrôle de l'échange est spécifié à l'aide des propriétés de contexte EdiOverride, les valeurs spécifiées sont utilisées pour cet échange et n'affectent pas le numéro de contrôle de l'échange spécifié dans l'accord.  
  
> [!NOTE]
>  Le numéro de contrôle de groupe dans EDIFACT est incrémenté uniquement si le **appliquer les segments UNG** propriété dans le **enveloppes** page de propriétés de l’accord EDIFACT est sélectionnée. Le deuxième champ (numéro de référence) est incrémenté ; les champs de préfixe et suffixe ne sont pas incrémentés. Numéros de contrôle de transaction sont incrémentés uniquement si le **appliquer le nouvel ID** propriété est sélectionnée.  
  
> [!NOTE]
>  Dans un échange par lot conservé, vous pouvez créer un numéro de contrôle de l'échange personnalisé à l'aide de l'exemple d'enrichissement de message. Pour plus d’informations, consultez [exemple d’enrichissement de Message (exemple BizTalk Server)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
 Si aucun accord n'est défini, les numéros proviennent des mêmes pages dans l'accord de secours. Le pipeline d'envoi stocke le dernier numéro de contrôle utilisé, puis entre un numéro incrémenté pour les prochains échange, groupe et document informatisé.  
  
> [!NOTE]
>  Si un numéro de contrôle atteint la valeur maximale de la plage spécifiée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lève une erreur et interrompt l'échange. Vous pouvez réinitialiser le numéro de contrôle, ou configurer manuellement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour rétablir automatiquement à la limite inférieure, dans le **paramètres d’hôte Local** page dans le **propriétés de l’accord** boîte de dialogue pour les deux X12 et Messages EDIFACT.  
  
> [!NOTE]
>  Les numéros de contrôle sont enregistrés dans la table dbo.EdiSequenceNumbers de la base de données MessageBox de BizTalk. Vous devez gérer cette table de base de données en purgeant les numéros de contrôle de la table ou en archivant les numéros de contrôle, selon vos besoins.  
  
 Dans EDIFACT, les numéros de contrôle se composent de valeurs alphanumériques. Les formats suivants sont pris en charge :  
  
-   Nombres (par exemple, « 1 »)  
  
-   PrefixNumbersSuffix (par exemple, « WA1A »)  
  
-   PrefixNumbers (par exemple, « AA1 »)  
  
-   NumbersSuffix (par exemple, « 1AA »)  
  
 Dans ces formats, les caractères numériques peuvent aller de « 0 » à « 9 » et les caractères de préfixe et de suffixe peuvent être n'importe quels caractères, à l'exception des caractères numériques. Seul le nombre est incrémenté pour atteindre la valeur maximale.  
  
#### <a name="count-of-segments"></a>Nombre de segments  
 Pour chaque document informatisé dans un échange, le pipeline d'envoi EDI vérifie le nombre de segments dans le document informatisé, comme indiqué dans l'élément de données SE01 pour X12 et UNT01 pour EDIFACT. Si la valeur de l'élément de données approprié ne correspond pas au nombre réel, le pipeline d'envoi met à jour le nombre pour refléter le nombre réel de segments. Le document informatisé n'est pas rejeté en raison d'un nombre erroné. La mise à jour du nombre est consignée dans un avertissement dans l'observateur d'événements. Cela ne s'applique pas au traitement des lots conservés.  
  
## <a name="additional-steps-in-serializing-an-edi-interchange"></a>Étapes supplémentaires de la sérialisation d'un échange EDI  
 Le pipeline d'envoi EDI effectue également les étapes suivantes au cours de la sérialisation.  
  
### <a name="serializing-the-release-indicator"></a>Sérialisation de l'indicateur de version  
 Lors de la sérialisation d'un message EDIFACT, le pipeline d'envoi EDI insère tout indicateur de version requis dans l'échange EDI. Cela sous-entend que le fichier XML intermédiaire routé vers le pipeline d'envoi n'inclut pas de données échappées. Par exemple, si un indicateur de version est présent dans le données XML routées vers le pipeline d'envoi, le pipeline d'envoi ajoute un autre indicateur de version avant l'indicateur de version existant afin de l'échapper.  
  
 L'indicateur de version n'est pas inclus dans la validation EDI. Le pipeline d'envoi EDI n'inclut pas l'indicateur de version lorsqu'il calcule des restrictions de longueur.  
  
### <a name="adding-trailing-zeroes-to-meet-implied-decimal-requirements"></a>Ajout de zéros de fin pour répondre aux exigences décimales implicites  
 Si l'Assembleur EDI rencontre un nombre qui n'a pas suffisamment de chiffres après le point décimal, il ajoute des zéros de fin après le point décimal pour répondre aux exigences décimales implicites. Par exemple, si l'Assembleur EDI rencontre le nombre « 4.5 » lorsque le nombre devrait avoir le format N2, l'Assembleur change le nombre en « 4.50 ».  
  
### <a name="replacing-separators-in-payload-data"></a>Remplacement des séparateurs dans les données de charge  
 Si les données du message sortant contient des caractères également configurés comme des séparateurs de données, de segment ou de composant, le pipeline d'envoi EDI peut remplacer ces caractères. Par exemple, si le message contient une valeur de « test * données » et le séparateur d’éléments de données est configuré comme\*', cela peut entraîner des problèmes d’analyse sur le système récepteur.  
  
 Le pipeline d’envoi EDI peut être configuré pour remplacer ce caractère en activant le **remplacer les séparateurs dans la charge utile avec** propriété et en spécifiant un caractère de remplacement. Cette propriété se trouve dans le **jeu de caractères et séparateurs** page sous l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
### <a name="transform-hipaa-records-based-on-trigger-fields"></a>Transformation des enregistrements HIPAA en fonction des champs déclencheurs  
 Si le document sortant est un document informatisé HIPAA, l’assembleur EDI transforme tout enregistrement XML unique qui contient un champ déclencheur dans le segment EDI générique correspondant (consultez [Annotations des champs déclencheurs HIPAA schéma](../core/hipaa-schema-trigger-field-annotations.md)). Pour cela, déposez le suffixe du nom d'enregistrement XML après le caractère « _ ».  
  
 Par exemple, les éléments <N1_PayerIdentification_TS835W1_1000A> et <N1_PayeeIdentification_TS835W1_1000B> deviennent des segments N1.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des messages EDI par BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)