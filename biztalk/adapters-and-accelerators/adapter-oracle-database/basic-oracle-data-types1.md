---
title: "Oracle base données Types1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, supported
- data types, unsupported
ms.assetid: 491230b9-b946-4681-a048-5da46102c370
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86349adae1a3ae061cb07c6c770532cf92c74dc8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="basic-oracle-data-types"></a>Types de données Oracle de base
Cette rubrique décrit comment les [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types de données de base Oracle.  
  
## <a name="supported-oracle-data-types"></a>Types de données Oracle prises en charge  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge la saisie sécurisée pour certains types de données Oracle. Lors de la saisie sécurisée est activé, ces types de données sont représentées sous forme de chaînes. Vous configurez la saisie sécurisée en définissant le **EnableSafeTyping** propriété de liaison. Tapant sécurisé est désactivée par défaut. Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
> [!NOTE]
>  Tapant sécurisé n’est pas prise en charge si les types de données sont à l’intérieur des Types de définis par l’utilisateur (UDT).  
  
 Le tableau suivant montre comment les types de données Oracle sont signalées à saisir sécurisé désactivé (**EnableSafeTyping** a la valeur false). Les types de données Oracle qui sont affectés par la **EnableSafeTyping** propriété de liaison sont marqués d’un astérisque (*).  
  
|Type de données Oracle|Type XSD|Type .NET|Commentaires|  
|----------------------|--------------|---------------|--------------|  
|BFile|d’entrée : xsd : String<br />sortie : xsd : base64Binary|Chaîne<br />Byte[]|Type de données BFile n’est pas pris en charge dans les types complexes (par exemple, RecordType TableType, UDT et VArray).|  
|Objet BLOB|xsd:base64Binary|Byte[]|Prise en charge des procédures et des opérations de table.|  
|Char|xsd:string|Chaîne|Prise en charge des procédures et des opérations de table.|  
|CLOB|xsd:string|Chaîne|Prise en charge des procédures et des opérations de table.|  
|Date *<br /><br /> (Non-safe si en tapant à l’intérieur d’un UDT)|xsd:dateTime|DateTime|Les valeurs de date ne peut pas contenir les informations de fuseau horaire (décalages UTC ou l’heure UTC) :<br /><br /> -les valeurs de xsd : DateTime ne doivent pas contenir UTC ou l’heure UTC offsets<br />-   **DateTime.Kind** doit être **DateTimeKind.Unspecified**<br /><br /> Si les informations de fuseau horaire sont spécifiées, l’adaptateur génère un **XmlReaderParsingException** exception avec un message qui indique le champ.|  
|Float **|type xsd : float si prec < = 7<br />XSD : double si prec > 7 et < = 15<br />XSD : String si prec > 15|Float<br />Double<br />Chaîne|-|  
|IntervalYM|xsd:string<br /><br /> XSD : long si à l’intérieur d’un UDT|Chaîne<br /><br /> If long à l’intérieur d’un UDT|La valeur doit être exprimée dans le format natif Oracle : année-mois ; Par exemple, « 1-2 » (1 année et 2 mois).|  
|IntervalDS|xsd:string<br /><br /> XSD:Duration si à l’intérieur d’un UDT|Chaîne<br /><br /> Intervalle de temps si à l’intérieur d’un UDT|La valeur doit être exprimée dans le format natif Oracle : jour HH:MI:SSxFF ; par exemple, « 5 15:30:12.99 »|  
|Long|xsd:string|Chaîne|Prise en charge pour toutes les opérations de table, procédures stockées et fonctions. **Remarque :** depuis la version 9i de base de données Oracle, le type de données de type LONG est déconseillé. Oracle recommande d’utiliser les types de données LOB à la place. Par conséquent, lorsque l’exécution d’opérations sur Oracle base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], nous recommandons d’utiliser des artefacts de base de données Oracle qui fonctionnent sur les types de données LOB et pas les données de type LONG type.|  
|LongRaw|xsd:base64Binary|Byte[]|-|  
|NChar|xsd:string|Chaîne|-|  
|NClob|xsd:string|Chaîne|Prise en charge des procédures et des opérations de table.|  
|Nombre **|XSD : decimal si prec < = 28<br />XSD : String si prec > 28|Décimal<br />Chaîne|-|  
|NVarchar2|xsd:string|Chaîne|-|  
|Brut|xsd:base64Binary|Byte[]|Prise en charge des procédures et des opérations de table.|  
|ID de ligne|xsd:string|Chaîne|-|  
|Horodatage *<br /><br /> (Non-safe si en tapant à l’intérieur d’un UDT)|XSD : DateTime si prec < = 7<br />XSD : String si prec > 7|DateTime<br />Chaîne|Les valeurs d’horodatage ne peut pas contenir les informations de fuseau horaire (décalages UTC ou l’heure UTC) :<br /><br /> -les valeurs de xsd : DateTime ne doivent pas contenir UTC ou l’heure UTC offsets<br />-   **DateTime.Kind** doit être **DateTimeKind.Unspecified**<br /><br /> Si les informations de fuseau horaire sont spécifiées, l’adaptateur génère un **XmlReaderParsingException** exception avec un message qui indique le champ.|  
|TimeStampLTZ|xsd:string|Chaîne|TimeStampLTZ n’est pas pris en charge dans les types UDT.<br /><br /> **En dehors d’un UDT**: la valeur doit être exprimée en NLS_TIMESTAMP_TZ_FORMAT.|  
|TimeStampTZ|xsd:string<br /><br /> XSD : DateTime si à l’intérieur d’un UDT|Chaîne<br /><br /> DateTime si à l’intérieur d’un UDT|**En dehors d’un UDT**: la valeur doit être exprimée en NLS_TIMESTAMP_TZ_FORMAT.|  
|Decimal **|XSD : decimal si prec < = 28<br />XSD : String si prec > 28|Décimal<br />Chaîne|-|  
|VARCHAR2|xsd:string|Chaîne|-|  
|Binaire Float **|type xsd : float si prec < = 7<br />XSD : String si prec > 7|Float<br />Chaîne|Vous devez spécifier la valeur dans un formulaire cohérent avec vos paramètres régionaux (**System.Globalization.CultureInfo.CurrentCulture**). Par exemple, utilisez une virgule pour les paramètres régionaux anglais ('. ') pour spécifier la virgule décimale ; pour des paramètres régionaux Français, utilisez une virgule («, »).|  
|Binaire Double **|XSD : double si prec < = 15<br />XSD : String si prec > 15|Double<br />Chaîne|-|  
|Entier binaire **|xsd:integer|Int32|Prise en charge pour les procédures, fonctions et des packages.|  
|Booléen|xsd:boolean|Valeur booléenne Nullable||  
|XMLTYPE|xsd:string|Chaîne|Prise en charge pour les paramètres de la procédure de niveau supérieur.<br /><br /> Réservés de caractères XML tels que «**\<**','**\>**' doivent être remplacées par leur représentation entité **(&lt;, &gt;)**lors du développement d’applications dans BizTalk Server, et lors de l’utilisation de WCF de modèle de canal. Cela n’est pas nécessaire dans le cas du modèle de Service WCF.|  
  
 \*La méthode dans laquelle ces types de données Oracle sont signalées est affectée par la **EnableSafeTyping** propriété de liaison.  
  
 \*\*La façon dans lequel ces Oracle des types de données numériques à l’intérieur des jeux de données et faiblement typée REF CURSOR sont signalées est affectée par la **EnableSafeTyping** propriété de liaison.  
  
> [!IMPORTANT]
>  -   La longueur maximale de la valeur dans un type de données Oracle dans la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est liée à la longueur maximale de la valeur de prise en charge par ODP.NET pour le type de données Oracle.  
> -   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] traite en interne des types de données numériques Oracle à l’intérieur des UDT comme .NET Decimal. Toutefois, en général (qui est extérieur UDT), le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] traite en interne des types de données numériques Oracle comme OracleDecimal.  
  
### <a name="safe-typing-enabled"></a>Tapant sécurisé activé  
 Le tableau suivant montre comment les types de données Oracle qui sont affectées en tapant sécurisés sont modifiées lorsque le **EnableSafeTyping** liaison de la propriété a la valeur true.  
  
|Type de données Oracle|Type XSD|Type .NET|Commentaire|  
|----------------------|--------------|---------------|-------------|  
|Date|xsd:string|Chaîne|La valeur doit être exprimée en NLS_DATE_FORMAT d’Oracle.|  
|TimeStamp|xsd:string|Chaîne|La valeur doit être exprimée en NLS_TIMESTAMP_FORMAT d’Oracle.|  
  
> [!IMPORTANT]
>  Si la saisie sécurisée est activé, les types de données numériques à l’intérieur des jeux de données et faiblement typée REF CURSOR Oracle sont toujours affichés sous forme de chaînes.  
  
 Les types de données Oracle qui ne sont pas dans ce tableau sont signalées de la même façon tapant sécurisé est activé ou désactivé.  
  
### <a name="validation"></a>Validation  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] n’exécute aucune validation explicite sur les valeurs que vous spécifiez pour les types de données Oracle. Toutefois, selon le type de données Oracle et indique si la saisie sécurisée est activé ou désactivé, la validation implicite peut être exécutée :  
  
-   Lors de la désérialisation entre les données XML sont transmises dans un message et les types .NET qui sont utilisées en interne par l’adaptateur.  
  
-   Par ODP.NET pour certains types de données.  
  
