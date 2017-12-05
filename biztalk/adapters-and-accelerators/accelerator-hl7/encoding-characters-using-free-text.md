---
title: "Encodage de caractères à l’aide de texte libre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a69dffe1-3fb2-4902-a9a2-093f3ea7b11f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02294e089eef6fa541f7e5bbcd2864c6f1bf023d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="encoding-characters-using-free-text"></a>Encodage de caractères à l’aide de texte libre
En commençant par [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], « FreeText » peut être utilisé dans un champ ou d’un segment. Données du champ de « FreeText » / segment ne sont pas analysées.  
  
## <a name="what-you-need-to-know"></a>Ce que vous devez savoir  
  
||Comportement|Exemple|  
|-|--------------|-------------|  
|~ : Séparateur de répétition|Dans un champ, répétition (~) est traitée comme un délimiteur répété. Dans un segment non libre, répétition (~) est traitée comme un délimiteur répété. Dans un segment libre, répétition (~) est traitée en tant que partie du texte libre, pas une répétition de nouveau.|Dans l’exemple suivant, FRE est Segment libre. Il peut avoir n’importe quel caractère sous forme de texte, y compris ~. Les répétitions supplémentaires (~) ne sont pas considérés comme un délimiteur de répétition et sont traitées en tant que le contenu de texte libre. La validation réussit même si l’enfant du Segment libre est non reproductible et contient de répétition (~). Exemple FRE :<br /><br /> **FRE &#124; Foo & ^ &#124; Foo & ^ &#124; Foo & ^ &#124; Foo & ^ ~ Foo & ^ &#124; Foo & ^ &#124; Foo & ^ &#124; Foo & ^**<br /><br /> Dans l’exemple suivant, EVN4 est défini en tant que texte libre, car elle contient  *&^* . Lorsque le « &#124; « séparateur est rencontré, il est traité comme la fin du texte libre actuel. Exemple EVN :<br /><br /> **EVN &#124; &#124; &#124; &#124; Foo & ^ Foo & ^ Foo & ^ Foo & ^ Foo & ^ &#124; &#124;**<br /><br /> Dans l’exemple suivant, le premier enfant de EVN5 est défini en tant que texte libre, car elle contient  *&* . Lorsque le « ^ » séparateur est rencontré, il est traité comme la fin du texte libre actuel. EVN5 exemple :<br /><br /> **EVN &#124; &#124; &#124; &#124; &#124; Foo & Foo & Foo & Foo & Foo & ^ 5.2 &#124;**<br /><br /> Dans l’exemple suivant, 5.2.1 et 5.2.2 ne peut pas avoir de délimiteurs sous forme de texte, même si elle est définie comme FreeText dans le schéma. exemple 5.2.1 et 5.2.2 :<br /><br /> **EVN &#124; &#124; &#124; &#124; &#124; Foo1 ^ 5.2.1 & 5.2.2 &#124;**<br /><br /> Dans l’exemple suivant, supposons que EVN4 peut être répété est de type texte libre. *Foo1 & ^* est traité comme la première répétition et *Foo2 & ^* est traité comme la répétition de seconde. Si EVN4 n’est pas répétée (MaxOccurs = 1), la validation échoue si elle contient ~, même s’il s’agit du type de texte libre (comme dans les cas des champs de texte non disponible). EVN4 exemple :<br /><br /> **EVN &#124; &#124; &#124; &#124; Foo1 & ^ ~ Foo2 & ^ &#124; &#124;**|  
|&#124; : séparateur de champs|Si un séparateur de champs est manquant après la balise de segment d’un segment libre, la Validation réussit.|Dans les exemples suivants, FRE est un type de texte libre. Contenu de texte libre peut être démarré immédiatement après le FRE segment balise, avec ou sans « &#124; « séparateur de champs. Les deux exemples réussissent :<br /><br /> **FREabc** <br /> **FRE &#124; abc**<br /><br /> Dans les exemples suivants, la validation réussit :<br /><br /> Message d’entrée DASM : **FRE &#124; abcd**<br />Sortie de DASM :  **\<SegmentData\>&#124; abcd\</SegmentData\>**<br />Sortie asm : **FRE &#124; abcd**<br /><br /> Message d’entrée DASM : **FREabcd**<br />Sortie de DASM :  **\<SegmentData\>abcd\</SegmentData\>**<br />Sortie asm : **FREabcd**|  
|Facultatif parent-enfant|Toujours appliqueront des règles de validation facultatif parent-enfant.|Supposons que le parent est facultatif et un de ses enfants est obligatoire, puis :<br /><br /> -Si aucun des autres enfants et les enfants obligatoires ne sont pas remplies, la validation de message réussit.<br />-Si au moins un enfant est rempli, l’enfant obligatoire doit aussi être rempli. Sinon, la validation du message échoue.<br /><br /> Dans l’exemple suivant, champ 1 comme facultatifs. Son *1.a* enfant est facultatif et est le type de texte libre. Son *1.b* enfant est obligatoire :<br /><br /> **XYZ &#124;1.a^1.b &#124; 2**<br /><br /> Dans l’exemple de message, *dfssdf**&**sdf* est considéré comme un seul élément - 1.a. L’analyseur vérifie s’il existe des 1.b. Lorsque le *&#124;* est atteint, il suppose que 1.b n’est pas remplie et validation du message échoue :<br /><br /> **XYZ &#124; dfssdf & sdf &#124; 2**|  
|Segments MSH FSH et BSH|Texte libre est ignoré pour tous les champs. Ces segments correspondent à la section d’en-tête. La validation se produit comme d’habitude, même s’ils sont définis en tant que texte libre.||  
|\\: Caractère d’échappement|S’il existe le nombre pair de « \ » dans l’élément, la validation réussit (même si elles ne sont pas contiguës). S’il existe un nombre impair, la validation échoue. Le même comportement se poursuit pour les champs de texte non libre. Avec des champs de texte libre, il n’existe aucune validation du nombre ; Il est traité en tant que contenu de texte libre.||  
  
 [Délimiteurs de message](../../adapters-and-accelerators/accelerator-hl7/message-delimiters.md) fournit des informations sur les séparateurs dans ces exemples.  
  
## <a name="using-free-text"></a>À l’aide de texte libre  
  
1.  Dans le projet dans Visual Studio, ouvrez le schéma.  
  
2.  Cliquez sur un enregistrement, sélectionnez **insérer un nœud de schéma**, sélectionnez **élément de champ enfant**.  
  
3.  Dans Propriétés, sélectionnez **Type de données**, puis sélectionnez **texte libre (SimpleType)**.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)