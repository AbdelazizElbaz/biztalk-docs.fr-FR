---
title: "Spécification des Positions de champ dans les enregistrements positionnels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33c2eee3-ec30-46c5-a143-a3d2e2f265a6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91a253c76e8f3394897514716978e1902cf2e3d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="specification-of-field-positions-within-positional-records"></a>Spécification des Positions de champ dans les enregistrements positionnels
Pour définir un enregistrement positionnel, vous devez fournir des informations concernant les positions et les longueurs des champs au sein de l’enregistrement. Si l'enregistrement contient des sous-enregistrements, les positions et longueurs des champs du sous-enregistrement sont cumulées pour alimenter les informations sur l'enregistrement qui les contient.  
  
 La somme des valeurs que vous spécifiez pour le **décalage de position** et **longueur positionnelle** propriétés pour un particulier **élément de champ** ou **attribut de champ**  nœud détermine le nombre de caractères consacrés au champ correspondant. L’ensemble des sommes pour tous les champs de l’enregistrement et de tous ses sous-enregistrements détermine les limites des champs dans les enregistrements.  
  
> [!NOTE]
>  Lorsque le **compter les Positions par octet** propriété de la **schéma** nœud a la valeur **Oui**, le **longueur positionnelle** et  **Décalage de position** propriétés spécifient les octets plutôt que des caractères.  

Afficher plus de détails sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="positional-offset-property"></a>Propriété Décalage de position  
 Lorsque le désassembleur de fichier plat convertit un message d’instance de fichier plat en un message d’instance XML équivalent, la valeur que vous spécifiez pour le **décalage de position** propriété définit un nombre de caractères (ou d’octets) qui sont ignorés et a été ignorée sur à cette position dans le message d’instance. En d’autres termes, toutes les informations figurant à la position de départ et de la longueur (celle-ci étant spécifiée par la **décalage de position** propriété) dans l’instance de fichier plat message ne sera copié dans la version XML du message.  
  
 Lorsque l’assembleur de fichier plat convertit un message d’instance XML en un message d’instance de fichier plat équivalent, la valeur que vous spécifiez pour le **décalage de position** propriété définit un nombre de caractères (ou d’octets) qui sont remplis avec caractères d’espace à cette position de départ dans le message d’instance de fichier plat en cours de création. Les positions de décalage sont toujours remplies par des espaces ; le caractère utilisé n'est pas configurable.  
  
 Le **décalage de position** propriété fournit une flexibilité permettant d’interpréter le contenu des enregistrements positionnels. Cette propriété vous permet essentiellement d'ignorer toutes les données de longueur fixe précédant le champ pour lequel elle a une valeur différente de zéro. Ces données de longueur fixe peuvent correspondre à un ou plusieurs champs de données entiers ou à certains types de données constantes, tels qu'une balise associée à un champ, qui ne doivent pas nécessairement être inclus dans l'équivalent XML de ce message d'instance de fichier plat. Pour plus d'informations, reportez-vous à l'exemple suivant.  
  
## <a name="positional-length-property"></a>Propriété Longueur positionnelle  
 Lorsque le désassembleur de fichier plat convertit un message d’instance de fichier plat en un message d’instance XML équivalent, la valeur que vous spécifiez pour le **longueur positionnelle** propriété définit le nombre de caractères (ou d’octets) qui sont associé au champ à cette position dans le message d’instance. Les informations qui se produisent au niveau que la position de début et la longueur dans le message d’instance de fichier plat constitue les données dans le champ, soumises à des informations supplémentaires fournies par associé **Justification** et  **Caractère de remplissage** propriétés. Pour plus d’informations sur la justification et le remplissage des champs, consultez [Justification des champs](../core/field-justification.md) et [remplissage des champs](../core/field-padding.md).  
  
 Lorsque l’assembleur de fichier plat convertit un message d’instance XML en un message d’instance de fichier plat équivalent, la valeur que vous spécifiez pour le **longueur positionnelle** propriété définit un nombre de caractères (ou d’octets) disponible pour l’écriture des données associées à ce champ. Si le nombre de caractères de données est inférieur à la longueur spécifiée pour le champ, le caractère de remplissage correspondant est utilisé pour combler la différence. S’il y a plus de caractères de données que la longueur spécifiée du champ, le début ou la fin des données est tronqué en fonction du paramètre de la **Justification** propriété et pas inclus dans le message d’instance fichier plat en cours construit.  
  
> [!NOTE]
>  La fin des données alignées à gauche est tronquée et supprimée. Le début des données alignées à droite est tronqué et supprimé.  
  
## <a name="example"></a>Exemple  
 Considérez les définitions de champ suivantes pour un enregistrement.  
  
|Nom de nœud de champ|Offset|Longueur|Caractère de remplissage|Justification|  
|---------------------|------------|------------|-------------------|-------------------|  
|Field1|0|6|Par défault (espace)|Gauche|  
|Field2|0|4|*|Droit|  
|Field3|2|6|*|Gauche|  
|Field4|4|6|Par défault (espace)|Droit|  
  
 Le flux suivant de caractères figure au point de début d'un enregistrement associé à ces définitions de champ (la première ligne sert à compter les positions des caractères).  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12345678**skip  here  
```  
  
 Lorsque ces définitions de champ sont appliquées à cet exemple de données d’enregistrement, le désassembleur de fichier plat produit le code XML équivalent suivant (les données étant affichées en gras).  
  
```  
<Field1>abc</Field1>  
<Field2>12</Field2>  
<Field3>5678</Field3>  
<Field4>here</Field4>  
```  
  
 Les observations suivantes concernent la façon dont les données sont analysées :  
  
-   Les caractères associés à Field1 (longueur 6 sans décalage) sont «`abc` », mais les espaces ne figurent pas dans le code XML, car le caractère espace est le caractère de remplissage (par défaut) pour Field1 et Field1 est défini comme aligné à gauche.  
  
-   Les caractères associés à Field2 (longueur 4 sans décalage) sont « `**12` », mais les astérisques ne sont pas inclus dans la version XML parce que l’astérisque correspond au caractère de remplissage défini pour Field2 et que Field2 est défini avec un alignement à droite.  
  
-   Les caractères associés à Field3 (longueur 6 avec un décalage de 2) sont « `345678**` », mais les caractères 3 et 4 ne sont pas inclus dans la version XML du fait du décalage. Les astérisques ne sont pas non plus inclus dans XML parce que le caractère astérisque correspond au caractère de remplissage défini pour Field2 et que Field2 est défini avec un alignement à gauche.  
  
-   Les caractères associés à Field4 (longueur 6 avec un décalage de 4) sont « `skip  here` », mais la séquence de caractères « `skip` » n'est pas incluse dans XML à cause du décalage. Les deux caractères d’espacement ne sont pas non plus inclus dans XML parce que le caractère d'espacement est le caractère de remplissage (par défaut) pour Field4 et que Field4 est défini avec un alignement à droite.  
  
 Si le XML généré par le désassembleur de fichier plat dans cet exemple est passé à l’assembleur de fichier plat en utilisant les définitions de champ de même, les mêmes données de fichier plat sont générées, à deux exceptions près : le décalage éliminées séquences 34 et skip sont remplacés par des tabulations (indiquée par le `^` caractère de la ligne qui suit les données).  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12  5678**      here  
          ^^      ^^^^  
  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations relatives aux champs](../core/field-considerations.md)    
-  [Justification des champs](../core/field-justification.md)   
-  [Remplissage des champs](../core/field-padding.md)   
- Plus d’informations sur les propriétés suivantes [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - Compter les Positions en octets (propriété de nœud des schémas de fichier plat)  
    - Justification (propriété de nœud des schémas de fichier plat)  
    - Caractère de remplissage (propriété de nœud des schémas de fichier plat) 
    - Décalage de position (propriété de nœud des schémas de fichier plat)
    - Longueur positionnelle (propriété de nœud des schémas de fichier plat)