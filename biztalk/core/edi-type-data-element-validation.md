---
title: "Validation de Type (élément de données) EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd53685f-a49c-41c8-813e-29700fc0b62b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88a71a44c305e1eabbcdb9aede32b44439f6b03c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-type-data-element-validation"></a>Validation de type EDI (élément de données)
Le pipeline de réception EDI et le pipeline d'envoi EDI exécutent la validation EDI sur les éléments de données de document informatisé. Cette validation est configurée pour tous les messages depuis ou vers un tiers spécifiques via les propriétés de l’accord de ce tiers sur la **Validation** page (sous la **paramètres des documents informatisés** section soit X12 ou accords EDIFACT). Si le **Validation de Type EDI** propriété n’est pas sélectionnée dans le **Validation** page, les données validations décrites dans cette rubrique ne seront pas effectuées.  
  
 Validation de type EDI est activée pour les messages entrants, ainsi que sortants en sélectionnant le **Validation de type EDI** propriété dans le **Validation** page des onglets d’accord bidirectionnel dans le **Propriétés de l’accord** boîte de dialogue. Pour les messages entrants et sortants, cette propriété est sélectionnée par défaut de sorte que la validation EDI soit activée par défaut.  
  
## <a name="validation-checks"></a>Contrôles de validation  
 Lorsque le pipeline de réception EDI ou le pipeline d'envoi EDI exécute la validation EDI, il valide les éléments suivants :  
  
-   Les types de données, comme définis par les propriétés EDI du schéma  
  
-   Les restrictions de longueur  
  
-   Les éléments de données vides et les séparateurs de fin  
  
    > [!NOTE]
    >  Cette validation ne vérifie pas les jeux de codes (énumérations), ni les occurrences minimum ou maximum.  
  
 **Jeux de caractères**  
  
 Pour effectuer la validation d'éléments de données EDI, les pipelines de réception EDI et d'envoi EDI exigent que le jeu de caractères soit défini comme suit :  
  
-   Pour EDIFACT, le jeu de caractères est établi dans l’élément de données **UNB1** de la **jeu de caractères et séparateurs** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue ou le **paramètres de secours EDIFACT** boîte de dialogue (si aucun accord n’a été établie).  
  
-   Pour KEDIFACT, le caractère est établi dans l’élément de données **UNB1** de la **jeu de caractères et séparateurs** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue zone, comme pour EDIFACT. La valeur de la **UNB1.1** élément doit être défini sur `KECA`.  
  
-   Pou X12, le jeu de caractères du message est défini dans les propriétés de pipeline.  
  
    > [!NOTE]
    >  Lorsque le composant d'exécution BizTalk effectue la validation EDI d'un message, il utilise le jeu de caractères X12 sélectionné dans les propriétés de pipeline. Toutefois, la validation des propriétés spécifiées dans les pages de la **propriétés de l’accord** boîte de dialogue est effectuée à l’aide du jeu de caractères sélectionné dans le **jeu de caractères et séparateurs** page de cette boîte de dialogue. Pendant l’exécution, le pipeline ignore la valeur de la X12 propriété du jeu de caractères **jeu de caractères et séparateurs** page de la **propriétés de l’accord** boîte de dialogue. Si ces deux paramètres ne sont pas identiques (par exemple, le X12 propriété de jeu de caractères dans le **propriétés de l’accord** boîte de dialogue est définie sur **étendue** alors que le X12 dans les propriétés de pipeline est définie sur **Base**), peuvent entraîner des erreurs de validation de message.  
  
 **Validation de Type de données**  
  
 Pour X12, les types de données EDI suivants sont annotés dans le schéma pour validation par les composants Désassembleur/Assembleur des pipelines de réception ou d'envoi : numérique, décimal, identificateur, chaîne, date, heure, binaire et composite.  
  
 Pour XEDIFACT, les types de données EDI suivants sont annotés dans le schéma pour validation par les composants Désassembleur/Assembleur des pipelines de réception ou d'envoi : alphabétique, numérique, identificateur, chaîne et composite.  
  
 **Restrictions de longueur**  
  
 Pour X12 et EDIFACT, les éléments ou sous-éléments doivent être validés conformément aux exigences de longueur (minimum et maximum). On entend par longueur le nombre de positions de caractère utilisées. Les symboles et les notations décimales ne sont pas pris en compte dans la définition de la longueur.  
  
> [!NOTE]
>  Pour les types de données Chaîne X12_AN, les espaces de début sont conservés et les espaces de fin autorisés dans n'importe quel segment pour satisfaire les exigences de longueur minimale.  
  
 Pour KECA, la longueur est interprétée comme étant le nombre d'octets. Par exemple, si la longueur est définie sur 3, l'élément ou le sous-élément peut inclure trois caractères d'un octet ou une combinaison d'un caractère de deux octets et d'un caractère d'un octet.  
  
 **Vide les éléments de données et la Validation de séparateur à droite**  
  
 Pour X12, les éléments de données marqués comme obligatoires ne peuvent pas être vides dans une instance si le segment est présent. Si l'élément de données est de type composite, au moins un élément de données composites doit être évalué.  
  
 Pour EDIFACT, les éléments de données (et sous-composants) non évalués et conditionnels peuvent être exclus. Cependant, le séparateur est conservé.  
  
 Les séparateurs de fin ne sont pas obligatoires pour X12 ou EDIFACT, mais recommandés.  
  
## <a name="when-edi-type-validation-is-disabled"></a>Lorsque la validation de type EDI est désactivée  
 Si vous désactivez la validation de type EDI, le pipeline de réception ou d'envoi EDI traite les éléments de données présentant des erreurs vérifiées par la validation de type EDI sans suspendre le message en cours de traitement.  
  
> [!NOTE]
>  La validation structurelle EDI est effectuée même si la validation de type EDI est désactivée. Un échange dont les validations structurelles de base échouent est suspendu, même si la validation de type EDI est désactivée.  
  
 Voici certaines des erreurs dont le traitement ne suspend pas le message :  
  
-   Un document informatisé inattendu/non défini  
  
-   Données inattendues/non définies au niveau du segment/de la boucle et de l'élément de données  
  
-   Caractère facultatif (occurrences minimum et maximum) au niveau du segment/de la boucle et de l'élément de données  
  
-   Violation des exigences de longueur (min./max.) au niveau de l'élément de données (données dont la longueur dépasse le niveau maximal ou est inférieure au niveau minimal)  
  
-   Incompatibilité de types de données au niveau de l'élément de données (excepté pour le type de données d'ID qui dispose de son propre contrôle)  
  
-   Liste d'énumération non valide au niveau de l'élément de données.  
  
 Si la validation de type EDI est désactivée côté réception, mais activée côté envoi, le pipeline d'envoi EDI ne peut pas retraiter le XML généré par le pipeline de réception en un fichier EDI valide si le fichier XML contient des erreurs. Le pipeline d'envoi génère donc une erreur.  
  
 Si la validation de type EDI est désactivée, le pipeline de réception ou d'envoi EDI gère les erreurs comme suit :  
  
|||  
|-|-|  
|Données inattendues|Action|  
|Document informatisé inattendu/non défini|Le pipeline de réception ou d'envoi EDI accepte un document informatisé même si le schéma correspondant n'a pas été déployé.|  
|Segment/enregistrement inattendu|Le pipeline de réception génère une balise avec le préfixe approprié : \<UnexpectedSegment_ % SegmentID % >.<br /><br /> Le pipeline d'envoi utilise le premier des trois caractères du nom de balise XML comme nom de segment.|  
|Élément de données simples inattendu|Le pipeline de réception génère une balise XML avec un préfixe, un identificateur de segment et un index indiquant la position de l'élément de données dans le segment : <UnexpectedDataElement_%FieldName%.|  
|Élément de données composites inattendu|Le pipeline de réception génère une balise XML avec un préfixe, un identificateur de segment et un index indiquant la position de l'élément de données dans le segment : <UnexpectedCompositeDataElement_%FieldName%.|  
|Données requises manquantes|Le pipeline traite les données comme étant facultatives.|  
|Violation de la longueur de l'élément de données|Le pipeline traite la longueur non valide de l'élément de données comme valide (min. = 0 et max. = unbounded).|  
|Valeur d'énumération non valide dans l'instance (application au type de données d'ID)|Le pipeline ignore l'erreur et poursuit le traitement.|  
|Violation du nombre maximum de répétitions dans l'instance|Le pipeline traite les données répétées comme valides (occurrences min. = 0 et occurrences max. = unbounded).|  
  
 **Rapport d'erreurs**  
  
 Lorsque la validation de type EDI est désactivée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne consigne pas d'erreurs dans l'Observateur d'événements, mais un génère un avertissement. De plus, l'accusé de réception renvoie un message d'acceptation au tiers source, définissant AK501 et AK901 comme « E » dans les accusés de réception X12 997 ou UCI.4, UCM.3 et UCF.4 comme « 7 » dans les accusés de réception EDIFACT CONTRL, supprimant ainsi toute possibilité de rectification dans les futures transmissions. Cependant, les récepteurs du message ont la possibilité de récupérer manuellement le document, évitant ainsi au message d'être rejeté ou suspendu. De plus, la propriété de contexte `Edi.ErrorsInTransactionSet` est promue si le pipeline de réception EDI ne rencontre aucune de ces erreurs. Cette propriété est promue comme « True » si des erreurs de validation EDI ou étendue sont détectées. En l'absence d'erreurs, cette propriété est promue comme « False ».  
  
 Si le pipeline de réception ou d'envoi rencontre des données inattendues, il signale l'erreur au niveau parent et ignore les erreurs au niveau enfant, comme indiqué ci-dessous :  
  
|||  
|-|-|  
|Données inattendues|Action|  
|Document informatisé inattendu|L'accusé de réception signale cette erreur et ignore les erreurs suivantes au niveau du segment/de la boucle et de l'élément de données.|  
|Segment/boucle inattendu(e)|L'accusé de réception signale cette erreur et ignore les erreurs au niveau de l'élément de données.|  
|Élément de données inattendu|L'accusé de réception signale cette erreur et ignore les erreurs composites relatives aux propriétés telles que l'ID, la longueur et les occurrences et celles inhérentes aux champs d'élément de données composites (le cas échéant).|  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)   
 [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md)