---
title: "Les Types de données Oracle base dans l’adaptateur Oracle eBusiness Suite dans BizTalk | Documents Microsoft"
description: "Données et XSD types, la saisie sécurisée et la validation dans Oracle e-Business Suite dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 008bf621-8b4e-450d-b354-ee26b91592f2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9012e2ef6adaf94f55b87bbccfc24b7fb889fbf3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="basic-oracle-data-types"></a>Types de données Oracle de base
Cette rubrique décrit comment les [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] met en évidence des types de données de base Oracle.  
  
## <a name="supported-oracle-data-types"></a>Types de données Oracle prises en charge  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la saisie sécurisée pour certains types de données Oracle. Lors de la saisie sécurisée est activé, ces types de données sont représentées sous forme de chaînes. Vous configurez en tapant sécurisé en activant la **EnableSafeTyping** (désactivée par défaut) de propriété de liaison. Pour plus d’informations sur la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
> [!NOTE]
>  Tapant sécurisé n’est pas prise en charge si les types de données sont à l’intérieur des Types de définis par l’utilisateur (UDT).  
  
 Le tableau suivant montre comment les types de données Oracle sont signalées à saisir sécurisé désactivé (**EnableSafeTyping** est **false**). Les types de données Oracle qui sont affectés par la **EnableSafeTyping** propriété de liaison sont marqués d’un astérisque (*).  
  
|Type de données Oracle|Type XSD|Type .NET|Commentaires|  
|----------------------|--------------|---------------|--------------|  
|BFile|d’entrée : xsd : String<br /><br /> sortie : xsd : base64Binary|Chaîne<br /><br /> Byte[]|Type de données BFile n’est pas pris en charge dans les types complexes (par exemple, RecordType TableType, UDT et VArray).|  
|Objet BLOB|xsd:base64Binary|Byte[]|-|  
|Char|xsd:string|Chaîne|-|  
|CLOB|xsd:string|Chaîne|-|  
|Date *<br /><br /> (Non-safe si en tapant à l’intérieur d’un UDT)|xsd:dateTime|DateTime|Les valeurs de date ne peut pas contenir les informations de fuseau horaire (décalages UTC ou l’heure UTC) :<br /><br /> -les valeurs de xsd : DateTime ne doivent pas contenir UTC ou l’heure UTC offsets<br />-   **DateTime.Kind** doit être **DateTimeKind.Unspecified**<br /><br /> Si les informations de fuseau horaire sont spécifiées, l’adaptateur génère un **XmlReaderParsingException** exception avec un message qui indique le champ. **Remarque :** le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose le type de données Oracle Date comme xsd : DateTime au lieu de xsd : date, car : <ul><li>Type de données Date Oracle peut également contenir la valeur d’heure.</li><li>Il n’existe aucun .NET équivalent pour XSD : date.</li></ul>|  
|Float **|type xsd : float si prec < = 7<br /><br /> XSD : double si prec > 7 et < = 15<br /><br /> XSD : String si prec > 15|Float<br /><br /> Double<br /><br /> Chaîne|Vous devez spécifier la valeur cohérente avec le format spécifié pour le caractère décimal et le séparateur de groupes dans le **NumericCharacters** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **NumericCharacters** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
|IntervalDS|xsd:string<br /><br /> XSD:Duration si à l’intérieur d’un UDT|Chaîne<br /><br /> Intervalle de temps si à l’intérieur d’un UDT|L’adaptateur retourne les données IntervalDS sous forme de chaîne à l’aide de la méthode OracleIntervalDS.ToString.<br /><br /> La valeur doit être exprimée dans le format natif Oracle : jour HH:MI:SSxFF (par exemple, « 5 15:30:12.99 »).|  
|IntervalYM|xsd:string<br /><br /> XSD : long si à l’intérieur d’un UDT|Chaîne<br /><br /> If long à l’intérieur d’un UDT|L’adaptateur retourne les données IntervalYM sous forme de chaîne à l’aide de la méthode OracleIntervalYM.ToString.<br /><br /> La valeur doit être exprimée dans le format natif Oracle : année-mois ; par exemple, « 1-2 » (1 année et 2 mois).|  
|Long|xsd:string|Chaîne|À compter de la version 9i de base de données Oracle, le type de données de type LONG est déconseillé. Oracle recommande d’utiliser les types de données objet volumineux (LOB) à la place. Par conséquent, lorsque l’exécution d’opérations sur Oracle base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], nous recommandons d’utiliser des artefacts de base de données Oracle qui fonctionnent sur les types de données LOB et pas les données de type LONG type.|  
|LongRaw|xsd:base64Binary|Byte[]|-|  
|NChar|xsd:string|Chaîne|-|  
|NClob|xsd:string|Chaîne||  
|Nombre **|XSD : decimal si prec < = 28<br /><br /> XSD : String si prec > 28|Décimal<br />Chaîne|-|  
|NVarchar2|xsd:string|Chaîne|-|  
|Brut|xsd:base64Binary|Byte[]||  
|ID de ligne|xsd:string|Chaîne|-|  
|Horodatage *<br /><br /> (Non-safe si en tapant à l’intérieur d’un UDT)|XSD : DateTime si prec < = 7<br /><br /> XSD : String si prec > 7|DateTime<br /><br /> Chaîne|Lorsqu’elle est exposée en tant que chaîne (prec > 7), la valeur doit être exprimée dans Oracle NLS_TIMESTAMP_FORMAT. Vous pouvez spécifier le format de chaîne pour les types de données TimeStamp dans la **TimeStampFormat** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **TimeStampFormat** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.<br /><br /> Les valeurs d’horodatage ne peut pas contenir les informations de fuseau horaire (décalages UTC ou l’heure UTC) :<br /><br /> -les valeurs de xsd : DateTime ne doivent pas contenir UTC ou l’heure UTC offsets<br />-   **DateTime.Kind** doit être **DateTimeKind.Unspecified**<br /><br /> Si les informations de fuseau horaire sont spécifiées, l’adaptateur génère un **XmlReaderParsingException** exception avec un message qui indique le champ.|  
|TimeStampLTZ|xsd:string|Chaîne|TimeStampLTZ n’est pas pris en charge dans les types UDT.<br /><br /> **En dehors d’un UDT**: la valeur doit être exprimée dans Oracle NLS_TIMESTAMP_TZ_FORMAT. Vous pouvez spécifier le format de chaîne pour les types de données TimeStampLTZ dans les **TimeStampTZFormat** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **TimeStampTZFormat** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
|TimeStampTZ|xsd:string<br /><br /> XSD : DateTime si à l’intérieur d’un UDT|Chaîne<br /><br /> DateTime si à l’intérieur d’un UDT|**En dehors d’un UDT**: la valeur doit être exprimée dans Oracle NLS_TIMESTAMP_TZ_FORMAT. Vous pouvez spécifier le format de chaîne pour les types de données TimeStampTZ dans les **TimeStampTZFormat** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **TimeStampTZFormat** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
|Decimal **|XSD : decimal si prec < = 28<br /><br /> XSD : String si prec > 28|Décimal<br /><br /> Chaîne|-|  
|VARCHAR2|xsd:string|Chaîne|-|  
|Binaire Float **|type xsd : float si prec < = 7<br /><br /> XSD : String si prec > 7|Float<br /><br /> Chaîne|Vous devez spécifier la valeur cohérente avec le format spécifié pour le caractère décimal et le séparateur de groupes dans le **NumericCharacters** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **NumericCharacters** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
|Binaire Double **|XSD : double si prec < = 15<br /><br /> XSD : String si prec > 15|Double<br /><br /> Chaîne|-|  
|Entier binaire **|xsd:integer|Int32||  
|Booléen|xsd:boolean|Valeur booléenne Nullable||  
|XMLTYPE|xsd:string|Chaîne|Prise en charge pour les paramètres de la procédure de niveau supérieur.<br /><br /> Réservés de caractères XML tels que «**\<**','**\>**' doivent être remplacées par leur représentation entité **(&lt;, &gt;)**lors du développement d’applications dans BizTalk Server, et lors de l’utilisation de WCF de modèle de canal. Cela n’est pas nécessaire dans le cas du modèle de Service WCF.|  
  
 \*La méthode dans laquelle ces types de données Oracle sont signalées est affectée par la **EnableSafeTyping** propriété de liaison.  
  
 \*\*La façon dans lequel ces Oracle des types de données numériques à l’intérieur des jeux de données et faiblement typée REF CURSOR sont signalées est affectée par la **EnableSafeTyping** propriété de liaison.  
  
> [!IMPORTANT]
>  -   La longueur maximale de la valeur dans un type de données Oracle dans la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est liée à la longueur maximale de la valeur de prise en charge par ODP.NET pour le type de données Oracle.  
> -   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] traite en interne des types de données numériques Oracle à l’intérieur des UDT comme .NET Decimal. Toutefois, en général (qui est extérieur UDT), le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] traite en interne des types de données numériques Oracle comme OracleDecimal.  
  
## <a name="safe-typing-enabled"></a>Tapant sécurisé activé  
 Le tableau suivant montre comment les types de données Oracle qui sont affectées en tapant sécurisés sont modifiées lorsque le **EnableSafeTyping** la liaison de propriété est **true**.  
  
> [!NOTE]
>  Les types de données Oracle qui ne sont pas dans ce tableau sont signalées de la même façon tapant sécurisé est activé ou désactivé.  
  
|Type de données Oracle|Type XSD|Type .NET|Commentaire|  
|----------------------|--------------|---------------|-------------|  
|Date|xsd:string|Chaîne|La valeur doit être exprimée en NLS_DATE_FORMAT d’Oracle. Vous pouvez spécifier le format pour les types de données de Date dans le **DateFormat** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **DateFormat** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
|TimeStamp|xsd:string|Chaîne|La valeur doit être exprimée en NLS_TIMESTAMP_FORMAT d’Oracle. Vous pouvez spécifier le format de chaîne pour les types de données TimeStamp dans la **TimeStampFormat** liaison de la propriété sous la **MlsSettings** propriété de liaison. Si aucune valeur n’est spécifiée pour le **TimeStampFormat** propriété de liaison, l’adaptateur utilise les paramètres MLS pour le client ODP.NET sur le même ordinateur où est installé l’adaptateur.|  
  
> [!IMPORTANT]
>  Si la saisie sécurisée est activé, les types de données numériques à l’intérieur des jeux de données et faiblement typée REF CURSOR Oracle sont toujours affichés sous forme de chaînes.  
  
## <a name="validation"></a>Validation  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] n’exécute aucune validation explicite sur les valeurs que vous spécifiez pour les types de données Oracle. Toutefois, selon le type de données Oracle et indique si la saisie sécurisée est activé ou désactivé, la validation implicite peut être exécutée :  
  
-   Lors de la désérialisation entre les données XML sont transmises dans un message et les types .NET qui sont utilisées en interne par l’adaptateur.  
  
-   Par ODP.NET pour certains types de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et schémas de message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)