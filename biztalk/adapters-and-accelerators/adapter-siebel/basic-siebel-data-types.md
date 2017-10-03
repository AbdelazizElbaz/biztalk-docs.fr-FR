---
title: "Types de données de base Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Siebel data types, supported
ms.assetid: bf86f639-6c45-49db-9e58-79c3ad2c9978
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0266f445c2fd8a7cba9a0e2089b9542813230580
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-siebel-data-types"></a>Types de données de base Siebel
Cette section décrit comment les types de données Siebel sont prises en charge sur le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## <a name="supported-siebel-data-types"></a>Types de données Siebel pris en charge  
 Le tableau suivant présente les types de données Siebel qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge et comment ils sont représentés par l’adaptateur BizTalk (type XSD) et dans le modèle de service WCF (type .NET). Pour les types marqués avec un astérisque, voir la remarque sous le tableau.  
  
|Type de données|Type XSD|Type .NET| Description|  
|---------------|--------------|---------------|-----------------|  
|DTYPE_BOOL|xsd:boolean|Booléen|-|  
|DTYPE_CURRENCY|xsd:decimal|Décimal|-|  
|DTYPE_DATE|XSD:DateTime*|DateTime|La valeur ne doit pas être temps universel coordonné (UTC).<br /><br /> -Pour XSD : DateTime, les valeurs sont attendues pour suivre ce modèle : « (\d\d\d\d-\d\d-\d\d)T(00:00:00) (.\*) ».<br />-Pour **DateTime** objets,**DateTime.Kind** doit être **DateTimeKind.Unspecified**.<br /><br /> Le composant heure sera ignoré par l’adaptateur.<br /><br /> Pour les messages sortants, l’adaptateur effectue une validation d’exécution pour vous assurer que la valeur spécifiée n’est pas UTC (z ou au décalage UTC). Si cette validation échoue, l’adaptateur lève une exception.<br /><br /> Lorsque ce type est exposé en tant que XSD : String (selon les règles expliqués ci-dessous) :<br /><br /> -Le format est déterminé par la base de données sous-jacente.<br />-Aucune exécution de validation de la valeur.|  
|DTYPE_DATETIME|XSD:DateTime*|DateTime|La valeur peut contenir des composants de date et heure et ne doit pas être UTC.<br /><br /> -Pour **DateTime** objets, **DateTime.Kind** doit être **DateTimeKind.Unspecified**.<br /><br /> Pour les messages sortants, l’adaptateur effectue une validation de l’exécution pour vous assurer que ces conditions sont remplies ; Si la validation échoue, l’adaptateur lève une exception.<br /><br /> Lorsque ce type est exposé en tant que XSD : String (selon les règles expliqués ci-dessous) :<br /><br /> -Le format est déterminé par la base de données sous-jacente.<br />-Aucune exécution de validation de la valeur.|  
|DTYPE_ID|xsd:string|Chaîne|-|  
|DTYPE_INTEGER|xsd:int|Int32|-|  
|DTYPE_NOTE|xsd:string|Chaîne|-|  
|DTYPE_NUMBER|xsd:decimal|Décimal|-|  
|DTYPE_PHONE|xsd:string|Chaîne|-|  
|DTYPE_TEXT|xsd:string|Chaîne|-|  
|DTYPE_TIME|XSD:DateTime*|DateTime|La valeur ne doit pas être UTC.<br /><br /> -Pour XSD : DateTime, les valeurs sont attendues pour suivre ce modèle : (1753-01-01)T(\d\d:\d\d:\d\d) (.\*) ».<br />-Pour **DateTime** objets**, DateTime.Kind** doit être **DateTimeKind.Unspecified**.<br /><br /> Pour les messages sortants, l’adaptateur effectue une validation d’exécution pour vous assurer que la valeur spécifiée n’est pas UTC (z ou au décalage UTC). Si cette validation échoue, l’adaptateur lève une exception.<br /><br /> Lorsque ce type est exposé en tant que XSD : String (basé sur les règles expliqués ci-dessous) :<br /><br /> -Le format est déterminé par la base de données sous-jacente.<br />-Aucune exécution de validation de la valeur.|  
|DTYPE_UTCDATETIME|XSD:DateTime*|DateTime|La valeur peut contenir des composants de date et heure et doit être l’heure UTC.<br /><br /> -Pour XSD : DateTime, la valeur doit être exprimée en heure UTC (la notation 'Z' ou au décalage UTC).<br />-Pour **DateTime** objets **DateTime.Kind** doit être **DateTimeKind.Utc**.<br /><br /> Pour les messages sortants, l’adaptateur effectue une validation de l’exécution pour vous assurer que ces conditions sont remplies ; Si la validation échoue, l’adaptateur lève une exception.<br /><br /> Lorsque ce type est exposé en tant que XSD : String (selon les règles expliqués ci-dessous) :<br /><br /> -Le format est déterminé par la base de données sous-jacente.<br />-Aucune exécution de validation de la valeur.|  
  
 Voici les types d’arguments de méthode Service métier :  
  
 Date  
 Identique à DTYPE_DATE.  
  
 Number  
 Identique à DTYPE_NUMBER.  
  
 Chaîne  
 Identique à DTYPE_TEXT.  
  
 Hiérarchie  
 Correspond à XSD de type xsd : String et pour le type .net String.  Dans les messages XML, il doit être placé dans un nœud CDATA.  
  
 Objet d’intégration  
 La même que la hiérarchie.  
  
 * L’adaptateur détermine s’il faut utiliser xsd : DateTime ou XSD : String pour représenter des champs DTYPE_DATE, DTYPE_DATETIME, DTYPE_TIME et DTYPE_UTCDATETIME dans des composants d’entreprise de la manière suivante.  
  
1.  Si le champ de composant d’entreprise possède l’un des types de données précédent, l’adaptateur sera l’exposer en tant que le XSD : DateTime type (dans .net correspond au type DateTime).  
  
2.  Si le champ du composant a aucun type de données, l’adaptateur de l’exposer en tant que XSD : String (dans .net que correspond au type de chaîne).  
  
## <a name="supported-facets-for-the-xml-schema-types"></a>Facettes prises en charge pour les Types de schémas XML  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge des facettes suivantes pour les types de schémas XML.  
  
|Type de Siebel|Facette|  
|-----------------|-----------|  
|DTYPE_BOOL|Aucune|  
|DTYPE_CURRENCY|Précision (22), mise à l’échelle|  
|DTYPE_DATE|(\d\d\d\d-\d\d-\d\d) T(00:00:00)(.*)|  
|DTYPE_DATETIME|Aucune|  
|DTYPE_ID|MaxLength (15)|  
|DTYPE_INTEGER|Précision (22)|  
|DTYPE_NOTE|MaxLength (16384)|  
|DTYPE_NUMBER|Précision (22), mise à l’échelle|  
|DTYPE_PHONE|MaxLength (40)|  
|DTYPE_TEXT|MaxLength (2048)|  
|DTYPE_TIME|(1753-01-01) T(\d\d:\d\d:\d\d)(.*)|  
|DTYPE_UTCDATETIME|Aucune|  
  
 Les éléments suivants sont des règles qui déterminent quand et comment les facettes et leurs valeurs, sont publiés :  
  
 Si l’attribut de longueur du champ est défini sur une valeur supérieure à zéro et inférieur ou égal à la valeur maximale (spécifiée entre parenthèses dans le tableau précédent) :  
  
-   La facette de précision est publiée comme suit :  
  
    -   Si l’attribut de précision est définie pour le champ, la même valeur est publiée en tant que facettes de précision.  
  
    -   Si l’attribut de précision n’est pas définie pour le champ, la valeur de longueur est publiée en tant que la facette de précision.  
  
-   La facette de la mise à l’échelle est publiée uniquement si les deux :  
  
    -   L’attribut de la précision a été publié.  
  
    -   L’attribut de l’échelle est définie pour le champ à une valeur supérieure à zéro et inférieure à la valeur publiée dans le cadre de la facette de précision  
  
-   La facette MaxLength est la valeur spécifiée pour l’attribut de longueur. Cela est récupéré à partir du référentiel de définition de champ. Au cas où la longueur n’est pas spécifiée dans le référentiel de définition de champ, la valeur spécifiée dans les parenthèses dans le tableau précédent est publiée.  
  
### <a name="special-cases-related-to-siebel-data-types"></a>Cas particuliers liés aux Types de données Siebel  
 Les règles suivantes affectent les facettes de champ de composant business en fonction du contexte de l’opération dans lequel ils sont utilisés. Ces règles sont appliquent aux opérations INSERT et UPDATE. Pour les opérations de requête, tous les champs de composant d’entreprise sont exposées à l’utilisateur.  
  
 **Champ de composant d’entreprise est marquée comme requise dans Siebel**  
  
 Même si un champ de composant d’entreprise est marqué comme requis dans le système Siebel mais les valeurs par défaut avant ou après par défaut sont définies pour le champ, [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] marque le champ comme facultatif. Par conséquent, si un utilisateur fournit une valeur à insérer ou mettre à jour, l’adaptateur traite cette valeur. Si aucune valeur n’est fournie, Siebel utilise les valeurs de pre-default/post-default.  
  
 **Champ de composant d’entreprise ne pas marqué comme étant en lecture seule dans Siebel**  
  
 Si un champ de composant d’entreprise n’est pas marqué comme READ ONLY, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] il expose sous la forme d’un champ accessible en écriture. Toutefois, il existe deux exceptions à cette règle. Il s'agit des paramètres suivants :  
  
-   Si le champ de composant d’entreprise est un **calculé** champ Siebel, elle n’apparaît pas dans les opérations d’insertion ou de mise à jour car Siebel se charge automatiquement de **calculé** champs.  
  
-   Si le champ du composant est obtenu via une jointure explicite (table de jointure sur une autre table), il est généralement en lecture seule. Toutefois Siebel permet aux données à écrire dans ce champ s’il s’agit d’un champ de liste de choix. Par conséquent, si le champ du composant provient d’une jointure explicite et le champ n’est pas un champ de liste de choix, puis il apparaîtra pas dans les opérations Insert ou Update, car les clients de l’adaptateur ne peut pas écrire de données dans ces champs.  
  
 **Type de données d’un champ non spécifié dans le composant de gestion**  
  
 Si le type de données d’un champ n’est pas spécifié dans le composant d’entreprise, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose les métadonnées de champ à l’aide de l’heuristique suivante.  
  
-   Si le champ est un champ spécial (liste de choix ou jointure), la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] recherche le champ mappé dans le composant d’entreprise de destination. Si ce champ a un type lui est associé le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] va exposer comme le type du champ. Toutefois, si ce type est DTYPE_DATE, DTYPE_TIME, DTYPE_DATETIME ou DTYPE_UTCDATETIME, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose le champ en tant que le type xsd : String. Si le champ mappé n’a pas un type associé, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose le champ d’origine en tant que le type xsd : String.  
  
-   Si le champ n’est pas une liste de choix ou d’un champ de jointure, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposera comme type xsd : String.  
  
 **Type de données, longueur de champ ou la précision d’un composant d’entreprise parent n’est pas disponible**  
  
 Si les type de données, longueur, ou champ précision d’un composant d’entreprise parent (un composant métier qui a un composant d’entreprise enfant basé sur les listes de choix ou MVLs), le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] Obtient les informations sur le type de données, longueur, précision et l’échelle à partir de la composant de liste de choix d’entreprise ou le composant de gestion MVL.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)