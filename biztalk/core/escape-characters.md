---
title: "Caractères d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af800b9-d31b-487a-9a06-6eda47d1574e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e961a205b77a9944a497d6e6cbed0df71f63e03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="escape-characters"></a>Caractères d’échappement

## <a name="overview"></a>Vue d'ensemble
Un caractère d'échappement est un caractère unique qui supprime toute signification du caractère qui le suit. Pour exemple, si vous définissez un enregistrement de fichier plat comme présentant les caractéristiques suivantes :  
  
-   Nom = Record1  
  
-   Délimité  
  
-   Délimiteur enfant = virgule (,)  
  
-   Classement enfant = préfixe  
  
-   Caractère d’échappement = barre oblique inverse (\\)  
  
-   Balise = RECORD1  
  
-   Deux champs nommés Field1 et Field2  
  
 Ensuite, les données de fichier plat suivantes s'appliquent à l'enregistrement.  
  
```  
RECORD1,testfield1\,testfield1,testfield2  
                  ^^  
  
```  
  
 Les données seront désassemblées dans le fragment suivant de XML.  
  
```  
<Record1>  
    <Field1>testfield1,testfield1</Field1>  
    <Field2>testfield2</Field2>  
</Record1>  
  
```  
  
 Notez que la séquence de caractère d’échappement `\,` figurant sur la ligne suivant l'enregistrement de fichier plat a été convertie en une virgule seule sans caractère d'échappement dans les données du champ Field1 dans l'enregistrement XML équivalent. De plus, cette virgule n'a pas été interprétée comme un séparateur de champs comme l’étaient les deux autres virgules.  
  
 Lorsque l'assembleur de fichier plat effectue l'opération inverse, convertissant la version XML de l'enregistrement en son équivalent en fichier plat, le caractère d'échappement est inséré avant la virgule, au milieu de Field1, indiquant ainsi qu’il doit être interprété comme une donnée et non comme un délimiteur de champ.  
  
 Lorsque vous créez un schéma de fichier plat à l’aide de l’Éditeur BizTalk, vous pouvez définir un caractère d’échappement par défaut pour l’ensemble du schéma à l’aide de la **de caractères d’échappement par défaut** et **Type de caractère d’échappement par défaut** propriétés de la **schéma** nœud. Vous pouvez ensuite configurer chaque enregistrement individuel dans le schéma à utiliser ce caractère d’échappement par défaut ou un caractère d’échappement personnalisée, spécifiques à l’enregistrement à l’aide de la **caractère d’échappement]** et **le Type de caractère d’échappement**propriétés de la **enregistrement** nœud.  
  
## <a name="see-also"></a>Voir aussi  
- [Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- Séquence d’échappement de caractères, propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - Caractère d’échappement par défaut (propriété de nœud des schémas de fichier plat)
    - Type de caractère d’échappement par défaut (propriété de nœud des schémas de fichier plat)
    - Caractère d’échappement (propriété de nœud des schémas de fichier plat)  
    - Type de caractère (propriété de nœud des schémas de fichier plat) d’échappement