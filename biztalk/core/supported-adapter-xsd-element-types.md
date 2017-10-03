---
title: "Prise en charge des Types d’éléments XSD adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00691a9e-434f-4baa-9a01-b6f452758ab3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3992ecface8fafacb5e1e616c930178ad0ce33a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="supported-adapter-xsd-element-types"></a>Types d’éléments XSD adaptateur pris en charge
Le tableau suivant répertorie les éléments pris en charge par l'infrastructure d'adaptateurs. Lorsque vous définissez un nouvel élément dans votre schéma de configuration, utilisez l'un des types suivants pour remplacer `string` dans l'exemple suivant :  
  
```  
<xs:element name="uri" type="xs:string">  
```  
  
|Type|Type XML|Comportement de l'interface utilisateur|Autres spécificités|  
|----------|--------------|-----------------|---------------------|  
|chaîne|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|normalizedString|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|entier|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|positiveInteger|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|negativeInteger|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|nonNegativeInteger|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|nonPositiveInteger|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|int|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|UnsignedInt|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|long|Aucune|Zone d'édition acceptant uniquement un type et une valeur décimale.|Attribut pour contraindre max/min|  
|unsignedLong|Aucune|Zone d'édition acceptant uniquement un type et une valeur décimale.|Attribut de définition du maximum ou du minimum contraint|  
|short|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|unsignedShort|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|decimal|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|float|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|double|Aucune|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|boolean|Aucune|Liste déroulante contenant des valeurs booléennes.|Aucune|  
|time|Aucune|Zone d'édition acceptant uniquement un type.|Aucune|  
|dateTime|Aucune|Zone d'édition acceptant uniquement un type. Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur les points de suspension pour afficher le calendrier.|Aucune|  
|date|Aucune|Zone d'édition acceptant uniquement un type. Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur les points de suspension pour afficher le calendrier.|Aucune|  
|gMonth|Aucune|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de mois à la place.|  
|gYear|Aucune|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur d'année à la place.|  
|gYearMonth|Aucune|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur d'année et de mois à la place.|  
|gDay|Aucune|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de jour à la place.|  
|gMonthDay|Aucune|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de mois et de jour à la place.|  
|Nom|Aucune|Zone d'édition acceptant uniquement un type.|Aucune|  
|NCName|Aucune|Zone d'édition acceptant uniquement un type.|Aucune|  
|anyURI|Aucune|Zone d'édition acceptant uniquement un type.|Aucune|  
|Séquence|Élément de schéma « Sequence »|Aucune|Aucune|  
|Groupes|Aucune|Signe « + » ou « - » qui développe ou réduit tous les champs d'un groupe.<br /><br /> Aucune fonctionnalité d'édition sur le côté droit de la page des propriétés.|Aucune|  
|Nom de fichier|FileName|Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur le bouton de sélection et la **Windows FileOpen** boîte de dialogue s’affiche, et vous permet de sélectionner un fichier.|Aucune|  
|Folder Name|FolderName|Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur le bouton de sélection et la **ouverture de dossier Windows** boîte de dialogue s’affiche ce qui permet la sélection d’un dossier.|Aucune|  
|SSO App ID|SSOAppID|Liste déroulante contenant la liste des applications à authentification unique|Aucune|  
|Mot de passe|Mot de passe|Zone d'édition affichant des « * » au lieu de texte en clair.|Aucune|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de conception de l’adaptateur](../core/adapter-design-issues.md)