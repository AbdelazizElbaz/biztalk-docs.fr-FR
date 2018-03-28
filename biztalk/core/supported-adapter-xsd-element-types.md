---
title: Prise en charge des Types d’éléments XSD adaptateur | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00691a9e-434f-4baa-9a01-b6f452758ab3
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3992ecface8fafacb5e1e616c930178ad0ce33a7
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="supported-adapter-xsd-element-types"></a>Types d’éléments XSD adaptateur pris en charge
Le tableau suivant répertorie les éléments pris en charge par l'infrastructure d'adaptateurs. Lorsque vous définissez un nouvel élément dans votre schéma de configuration, utilisez l'un des types suivants pour remplacer `string` dans l'exemple suivant :  
  
```  
<xs:element name="uri" type="xs:string">  
```  
  
|Type|Type XML|Comportement de l'interface utilisateur|Autres spécificités|  
|----------|--------------|-----------------|---------------------|  
|chaîne|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|normalizedString|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|entier|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|positiveInteger|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|negativeInteger|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|nonNegativeInteger|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|nonPositiveInteger|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|int|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|UnsignedInt|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|long|Aucun|Zone d'édition acceptant uniquement un type et une valeur décimale.|Attribut pour contraindre max/min|  
|unsignedLong|Aucun|Zone d'édition acceptant uniquement un type et une valeur décimale.|Attribut de définition du maximum ou du minimum contraint|  
|short|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|unsignedShort|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|Décimal|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|float|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|double|Aucun|Zone d'édition acceptant uniquement un type.|Attribut pour contraindre max/min|  
|boolean|Aucun|Liste déroulante contenant des valeurs booléennes.|Aucun|  
|time|Aucun|Zone d'édition acceptant uniquement un type.|Aucun|  
|dateTime|Aucun|Zone d'édition acceptant uniquement un type. Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur les points de suspension pour afficher le calendrier.|Aucun|  
|date|Aucun|Zone d'édition acceptant uniquement un type. Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur les points de suspension pour afficher le calendrier.|Aucun|  
|gMonth|Aucun|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de mois à la place.|  
|gYear|Aucun|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur d'année à la place.|  
|gYearMonth|Aucun|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur d'année et de mois à la place.|  
|gDay|Aucun|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de jour à la place.|  
|gMonthDay|Aucun|Zone d'édition acceptant uniquement un type.|Cette valeur est une chaîne et risque donc de ne pas se comporter comme prévu. Envisagez d'utiliser des types xsd:int avec des restrictions pour stocker la valeur de mois et de jour à la place.|  
|Nom|Aucun|Zone d'édition acceptant uniquement un type.|Aucun|  
|NCName|Aucun|Zone d'édition acceptant uniquement un type.|Aucun|  
|anyURI|Aucun|Zone d'édition acceptant uniquement un type.|Aucun|  
|Séquence|Élément de schéma « Sequence »|Aucun|Aucun|  
|Groupes|Aucun|Signe « + » ou « - » qui développe ou réduit tous les champs d'un groupe.<br /><br /> Aucune fonctionnalité d'édition sur le côté droit de la page des propriétés.|Aucun|  
|Nom de fichier|FileName|Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur le bouton de sélection et la **Windows FileOpen** boîte de dialogue s’affiche, et vous permet de sélectionner un fichier.|Aucun|  
|Folder Name|FolderName|Des points de suspension apparaissent à la fin de la zone de champs. Cliquez sur le bouton de sélection et la **ouverture de dossier Windows** boîte de dialogue s’affiche ce qui permet la sélection d’un dossier.|Aucun|  
|SSO App ID|SSOAppID|Liste déroulante contenant la liste des applications à authentification unique|Aucun|  
|Mot de passe|Mot de passe|Zone d'édition affichant des « * » au lieu de texte en clair.|Aucun|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de conception de l’adaptateur](../core/adapter-design-issues.md)