---
title: "Les Types de données SAP base dans l’adaptateur mySAP dans BizTalk | Documents Microsoft"
description: "Prise en charge ABAP et la base de données les types de données pour l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 296b4813-f175-4a02-8fd3-227ae301bc3d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40e7dc6f98e1de2ff0388a8e7e52fdabafc7681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-sap-data-types"></a>Types de données SAP de base
Les types de paramètre qui le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge est régies par la :  
  
-   Types de données ABAP SAP prend en charge  
  
-   Types de données de base de données qui prend en charge par SAP  
  
 Cette section présente un mappage entre les types de données ABAP et la base de données et leurs types de schémas XML et .NET correspondants.  
  
> [!NOTE]
>  Les informations contenues dans cette section s’applique à la RFC, tRFCs et BAPI. Types de données SAP sont toujours représentés en tant que chaînes IDOC (XSD : String). Il s’agit pour prendre en charge de l’Analyseur de fichier plat BizTalk Server.  
  
## <a name="supported-abap-data-types"></a>Types de données ABAP pris en charge  
 Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge la saisie sécurisée pour certains types de données ABAP. Lors de la saisie sécurisée est activé, ces types de données sont représentées sous forme de chaînes. Vous configurez la saisie sécurisée en définissant le **EnableSafeTyping** propriété de liaison. Tapant sécurisé est désactivée par défaut. Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 Le tableau suivant montre comment les types de données ABAP sont signalées lors de la saisie sécurisée n’est pas activé. (**EnableSafeTyping** a la valeur false). Types de données qui sont signalées différemment lors de la saisie sécurisée est activé sont marqués d’un astérisque (*).  
  
|Type de données ABAP|Type RFC|Type XSD|Type .NET|Chaîne de format|  
|--------------------|--------------|--------------|---------------|-------------------|  
|I (entier)|RFC_INT|xsd:int|Int32|-|  
|Interne (RFC_INT1)|RFC_INT1|xsd:unsignedByte|Byte|-|  
|Interne (RFC_INT2)|RFC_INT2|xsd:short|Int16|-|  
|F (Float)|RFC_FLOAT|xsd:double|Double|-|  
|P (nombre BCD)|RFC_BCD|XSD : decimal si longueur < = 28<br />XSD : String si longueur > 28|Décimal<br />Chaîne|Nombre décimal. 0 décimales.<br />Nombre décimal. avec > 0 décimales|  
|C (caractère)|RFC_CHAR|xsd:string|Chaîne|-|  
|D (Date : YYYYMMDD) *|RFC_DATE|xsd:dateTime|DateTime|En interne, l’adaptateur désérialise la valeur dans un **DateTime** objet. Il appelle ensuite la **DateTime.ToUniversalTime** méthode pour convertir la valeur de cet objet au format UTC. Enfin le composant de date (**DateTime.Date**) est utilisé pour créer la valeur qui est envoyée au système SAP. Le système SAP traite cette valeur de date en heure locale.<br /><br /> Vous devez spécifier des valeurs de date comme UTC pour éviter la conversion.<br /><br /> -Pour XSD : DateTime, le modèle suivant est recommandé : » (\d\d\d\d-\d\d-\d\d)T(00:00:00) (.\*) Z ».<br />-Pour **DateTime** objets ensemble **DateTime.Kind** à **DateTimeKind.Utc**.|  
|T (heure : HHMMSS) *|RFC_TIME|xsd:dateTime|DateTime|En interne, l’adaptateur désérialise la valeur dans un **DateTime** objet. Il appelle ensuite la **DateTime.ToUniversalTime** méthode pour convertir la valeur de cet objet au format UTC. Enfin le composant d’heure (**DateTime.Time**) est utilisé pour créer la valeur qui est envoyée au système SAP. Le système SAP traite cette valeur d’heure en heure locale.<br /><br /> Vous devez spécifier des valeurs d’heure en heure UTC pour éviter la conversion.<br /><br /> -Pour XSD : DateTime, le modèle suivant est recommandé : » (0001-01-01)T(\d\d:\d\d:\d\d) (.\*) ».<br />-Pour **DateTime** objets ensemble **DateTime.Kind** à **DateTimeKind.Utc**.<br /><br /> Par exemple, si votre heure locale est 9 h 15, la formulation en tant que « (001-01-01) T (09 : 15:00) Z »|  
|N (chaîne numérique) *|RFC_NUM|XSD : int si lenrth < = 9<br />XSD : long si longueur > 9 et < = 19<br />XSD : String si longueur > 19|Int32<br />long<br />Chaîne|-|  
|X (octets)|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
|CHAÎNE|RFC_STRING|xsd:string|Chaîne|-|  
|XSTRING|RFC_BYTE|xsd:base64Binary|Byte[]|-|  
  
 * Indique que le type de données apparaissent différemment lors de la saisie sécurisée est activé.  
  
### <a name="safe-typing-enabled"></a>Tapant sécurisé activé  
 Le tableau suivant présente les types de données ABAP exposés différemment lors de la saisie sécurisée est activé (la **EnableSafeTyping** liaison de la propriété a la valeur true).  
  
|Type de données ABAP|Type RFC|Type XSD|Type .NET|Chaîne de format|  
|--------------------|--------------|--------------|---------------|-------------------|  
|D (Date : YYYYMMDD)|RFC_DATE|xsd:string|Chaîne|Format de date SAP : AAAAMMJJ.<br /><br /> Caractères sont autorisées pour les chiffres de la date, la valeur est essentiellement une chaîne de huit caractères|  
|T (heure : HHMMSS)|RFC_TIME|xsd:string|Chaîne|Format d’heure SAP : format HHMMSS.<br /><br /> Caractères sont autorisées pour les chiffres de temps, la valeur est essentiellement une chaîne de six caractères|  
|N (chaîne numérique)|RFC_NUM|xsd:string|Chaîne|Une chaîne de caractères n ; où n = longueur du champ numc.|  
  
 Les types de données ABAP qui ne sont pas dans ce tableau sont signalées dans la même façon que lors de la saisie sécurisée n’est pas activé.  
  
### <a name="support-for-date-and-time-fields"></a>Prise en charge pour les champs Date et heure  
 Lors de la saisie sécurisée n’est pas activée, les types de Date ABAP (D) et d’heure (T) sont exposés en tant que XSD : DateTime ; Toutefois, la facette de modèle visible pour les types de Date et d’heure est différente.  
  
-   La facette de modèle pour la Date est la suivante :`(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)`  
  
     Par exemple, 7 juillet 2007 (2007-07-07) est représenté en tant que :  
  
     `(2007-07-07)T(00:00:00)`.  
  
-   La facette de modèle pour le moment est la suivante :`(0001-01-01)T(\d\d:\d\d:\d\d)(.*)`  
  
     Par exemple, 18:30:30 (6 h 30 et 30 secondes) est représenté en tant que :  
  
     `(0001-01-01)T(18:30:30)`.  
  
#### <a name="how-does-the-adapter-represent-minimum-and-maximum-time-values-on-inbound-messages-from-sap"></a>En quoi la carte représentent les valeurs minimale et maximale temps sur les Messages entrants (à partir de SAP) ?  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise les instructions suivantes lorsqu’il reçoit des valeurs d’heure à partir du système SAP :  
  
-   L’adaptateur traite 000000 (hhmmss) et 240000 (hhmmss) en tant que les heures, 0, 0 minutes et 0 secondes.  
  
## <a name="supported-database-data-types"></a>Types de données pris en charge de la base de données  
 La façon dont le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] types de données de base de données de surfaces dépend également si la saisie sécurisée est activé. Le tableau suivant montre comment les surfaces de carte de base de données des types de données lors de la saisie sécurisée n’est pas activée (la **EnableSafeTyping** liaison de la propriété a la valeur false). Types de données qui sont signalées différemment lors de la saisie sécurisée est activé sont marqués d’un astérisque (*).  
  
|Type de données de base de données|Type RFC|XSD|Type .NET|  
|------------------------|--------------|---------|---------------|  
|ACCP (période de validation) *|RFC_NUM|xsd:int|Int32|  
|CHAR|RFC_CHAR|xsd:string|Chaîne|  
|CLNT (Client)|RFC_CHAR|xsd:string|Chaîne|  
|TYP (champ devise)|RFC_BCD|XSD : decimal **Remarque :** le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] arrondit les valeurs décimales basés sur la définition du paramètre décimal. Par exemple, si un paramètre décimal peut accepter jusqu'à cinq chiffres après la virgule décimale, une valeur telle que 4,000028 est arrondie à 4.00003.|Décimal|  
|CUKY (clé de devise)|RFC_CHAR|xsd:string|Chaîne|  
|Fichiers DAT (champ Date) *|RFC_DATE|xsd:dateTime<br /><br /> En interne, l’adaptateur désérialise la valeur dans un **DateTime** objet. Il appelle ensuite la **DateTime.ToUniversalTime** méthode pour convertir la valeur de cet objet au format UTC. Enfin le composant de date (**DateTime.Date**) est utilisé pour créer la valeur qui est envoyée au système SAP. Le système SAP traite cette valeur de date en heure locale.<br /><br /> Vous devez spécifier des valeurs de date comme UTC pour éviter la conversion. Le modèle suivant est recommandé de : » (\d\d\d\d-\d\d-\d\d) T (00 : 00:00)(.*) Z ».|DateTime<br /><br /> Vous devez spécifier des valeurs de date comme UTC (DateTime.Kind = DateTimeKind.Utc) pour éviter la conversion.|  
|DEC (quantité)|RFC_BCD|XSD : decimal **Remarque :** le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] arrondit les valeurs décimales basés sur la définition du paramètre décimal. Par exemple, si un paramètre décimal peut accepter jusqu'à cinq chiffres après la virgule décimale, une valeur telle que 4,000028 est arrondie à 4.00003.|Décimal|  
|FLTP (virgule flottante)|RFC_FLOAT|xsd:double|Double|  
|INT1|RFC_INT1|XSD:unsignedByte|Byte|  
|INT2|RFC_INT2|xsd:short|Int16|  
|INT4|RFC_INT|xsd:int|Int32|  
|LANG (clé de langue)|RFC_CHAR|xsd:string|Chaîne|  
|LCHR|RFC_STRING|xsd:string|Chaîne|  
|LRAW (seq octets de long)|RFC_BYTE|XSD : base64Binary|Byte[]|  
|NUMC *|RFC_NUM|xsd:int<br />xsd:long<br />xsd:string|Int32 si longueur < = 9<br />Int64 Si longueur > 9 et < = 19<br />Chaîne si longueur > 19|  
|PREC (précision)|RFC_INT2|xsd:short|Int16|  
|QUAN (quantité)|RFC_BCD|XSD : decimal **Remarque :** le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] arrondit les valeurs décimales basés sur la définition du paramètre décimal. Par exemple, si un paramètre décimal peut accepter jusqu'à cinq chiffres après la virgule décimale, une valeur telle que 4,000028 est arrondie à 4.00003.|Décimal|  
|RAW (séquence d’octets)|RFC_BYTE|XSD : base64Binary|Byte[]|  
|RAWSTRING (de longueur variable)|RFC_BYTE|XSD : base64Binary|Byte[]|  
|STRING (longueur variable)|RFC_STRING|xsd:string|Chaîne|  
|TIM (champ d’heure) *|RFC_TIME|xsd:datetime<br /><br /> En interne, l’adaptateur désérialise la valeur dans un **DateTime** objet. Il appelle ensuite la **DateTime.ToUniversalTime** méthode pour convertir la valeur de cet objet au format UTC. Enfin le composant d’heure (**DateTime.Time**) est utilisé pour créer la valeur qui est envoyée au système SAP. Le système SAP traite cette valeur d’heure en heure locale.<br /><br /> Vous devez spécifier des valeurs d’heure en heure UTC pour éviter la conversion. Le modèle suivant est recommandé de : » (0001-01-01) T (\d\d:\d\d:\d\d)(.*) Z ».<br /><br /> Par exemple, si votre heure locale est 9 h 15, la formulation en tant que « (001-01-01) T (09 : 15:00) Z »|DateTime<br /><br /> Vous devez spécifier des valeurs d’heure en heure UTC (DateTime.Kind = DateTimeKind.Utc) pour éviter la conversion.|  
|(Unité pour Qty)|RFC_CHAR|xsd:string|Chaîne|  
|[Non pris en charge]|--|--|Chaîne|  
  
 * Indique que l’adaptateur met en évidence le type de données différemment lorsque tapant sécurisé est activé.  
  
### <a name="safe-typing-enabled"></a>Tapant sécurisé activé  
 Le tableau suivant présente la base de données des types de données qui sont signalées différemment lors de la saisie sécurisée est activé (la **EnableSafeTyping** liaison de la propriété a la valeur true).  
  
|Type de données de base de données|Type RFC|XSD|Type .NET|Format de valeur de chaîne|  
|------------------------|--------------|---------|---------------|-------------------------|  
|ACCP (période de validation)|RFC_NUM|xsd:string|Chaîne|Chaîne de caractères|  
|NUMC|RFC_NUM|xsd:string|Chaîne|Chaîne de caractères|  
|Fichiers DAT (champ de Date)|RFC_DATE|xsd:string|Chaîne|AAAAMMJJ|  
|TIM (champ d’heure)|RFC_TIME|xsd:string|Chaîne|HHMMSS|  
  
 Types de données qui ne sont pas dans ce tableau sont signalées dans la même façon que lors de la saisie sécurisée n’est pas activé.  
  
## <a name="supported-xsd-facets"></a>Facettes XSD prises en charge  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les facettes XSD suivants.  
  
|Type RFC|Facette XSD (**EnableSafeTyping** = false)|Facette XSD (**EnableSafeTyping** = true)|  
|--------------|-------------------------------------------------|------------------------------------------------|  
|RFC_BCD|**Facette de modèle XSD**<br /><br /> **Nombre de décimales de zéro :**`"([\\-]{0,1})(([0-9]{1,"`  `+ digitsBeforeDecimal +`  `"}))"`<br /><br /> **Nombre de décimales :**`"([\\-]{0,1})(([0-9]{0,"` + `digitsBeforeDecimal +``"}\\.[0-9]{0,"``+ digitsAfterDecimal +``"})&#124;([0-9]{1,"``+ digitsBeforeDecimal +``"}))"`|Même|  
|RFC_NUM|**Facette de totalDigits XSD** Si longueur < = 19<br /><br /> **Facette de modèle XSD** Si longueur > 19|**Facette maxLength XSD (dépend de la longueur de la valeur sur SAP)**|  
|RFC_DATE|**Facette de modèle XSD**<br /><br /> `"(\d\d\d\d-\d\d-\d\d)T(00:00:00)(.*)"`<br /><br /> Modèle contient l’heure 00:00:00 pour être compatible avec`xsd:datetime`|**Facette maxLength XSD = 8**|  
|RFC_TIME|**Facette de modèle XSD**<br /><br /> `"(0001-01-01)T(\d\d:\d\d:\d\d)(.*)"`<br /><br /> Modèle contient date à 0001-01-01 pour être compatible avec`xsd:datetime`|**Facette maxLength XSD = 6**|  
|RFC_CHAR|**Facette maxLength XSD**|Même|  
  
## <a name="unsupported-data-types"></a>Types de données non pris en charge  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge le type de données suivantes :  
  
-   Types de table (hiérarchiques) ITAB II  
  
