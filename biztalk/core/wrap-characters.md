---
title: "Encapsuler les caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7268f46-9bf6-4c76-9b3a-b4ee0e8db997
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f95ed10811232b15762c31bfc435ac7772a53b3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wrap-characters"></a>Encapsuler des caractères

## <a name="overview"></a>Vue d'ensemble
Un caractère de retour à la ligne est un caractère unique utilisé pour renvoyer les caractères de données à la ligne dans un champ afin de supprimer toute signification spéciale que ces caractères de données auraient sinon. Pour exemple, si vous définissez un enregistrement de fichier plat comme présentant les caractéristiques suivantes :  
  
-   Nom = Record1  
  
-   Délimité  
  
-   Délimiteur enfant = virgule (,)  
  
-   Classement enfant = infix  
  
-   Caractère d’échappement = barre oblique inverse (\\)  
  
-   Balise = RECORD1  
  
-   Trois champs nommés Field1, Field2 et Field3, chacun défini de manière à utiliser le signe dièse (#) comme leur caractère de retour à la ligne.  
  
 Ensuite, les données de fichier plat suivantes s'appliquent à l'enregistrement.  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 Les données sont désassemblées dans le fragment suivant de XML.  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2></Field2>  
    <Field3></Field3>  
</Record1>  
  
```  
  
 Notez que les caractères de retour à la ligne (#) entourant les caractères de données en gras field1, field2 et field3 ont été supprimés.  
  
 Lorsque l’assembleur de fichier plat effectue l’opération inverse, de convertir la version XML de l’enregistrement de son enregistrement de fichier plat équivalent, les caractères de retour à la ligne sont insérés avant et après les caractères de données de chacun des champs, on obtient la séquence d’origine de caractères de fichier plat.  
  
 Le caractère d'échappement défini peut être utilisé conjointement avec le caractère de retour à la ligne défini. Supposez par exemple que la valeur de Field1 soit modifiée comme suit (texte en gras).  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2>field2</Field2>  
    <Field3>field3</Field3>  
</Record1>  
  
```  
  
 Lorsque ce fragment XML sera assemblé, à l'aide des définitions d'enregistrement et de champ fournies, la séquence suivante de caractères de fichier plat sera produite (la séquence de caractères d'échappement et de dièses est en gras).  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 Lorsque vous créez un schéma de fichier plat à l’aide de l’Éditeur BizTalk, vous pouvez définir un caractère de retour à la ligne par défaut pour l’ensemble du schéma à l’aide de la **Default Wrap Character** et **par défaut caractère de retour** propriétés de la **Schéma** nœud. Vous pouvez ensuite configurer chaque champ dans le schéma à utiliser ce caractère de retour à la ligne par défaut ou un caractère personnalisé, spécifiques aux champs de type wrap à l’aide de la **Wrap Character** et **caractère de retour** propriétés de la **Fieldelement** ou **attribut de champ** nœuds dans les schémas de fichier plat.
  
## <a name="see-also"></a>Voir aussi  
- [Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- Encapsuler les propriétés de caractères [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    -  Caractère de retour par défaut (propriété de nœud des schémas de fichier plat
    -  Type de caractère de retour à la ligne par défaut (propriété de nœud des schémas de fichier plat
    -  Encapsuler des caractères (propriété de nœud des schémas de fichier plat  
    -  Encapsuler le Type de caractère (propriété de nœud des schémas de fichier plat