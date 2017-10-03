---
title: Messages de fichier plat avec des enregistrements positionnels | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c17c25-3847-458e-a43e-0dbdc42db749
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c9e4551abcbd0fba32b21fb8e4205bece6e82f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-messages-with-positional-records"></a>Messages de fichier plat avec des enregistrements positionnels
Les enregistrements positionnels d'un message d'instance de fichier plat contiennent des champs individuels (éléments de données) qui ont chacun une longueur prédéfinie. Les champs sont analysés selon ces longueurs. Prenons l'exemple de l'enregistrement positionnel suivant, issu d'un message d'instance de fichier plat et qui contient une adresse de livraison (la première ligne indique le nombre de caractères réservés à chaque champ).  
  
```  
123456789012345678901234567890123456789012345678901234567890123456789012345  
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952  
```  
  
 Une définition raisonnable d'un tel enregistrement dans un schéma de fichier plat peut être celle d'un enregistrement positionnel appelé shipTo contenant les champs suivants :  
  
-   Un attribut appelé pays/région aligné à gauche, long de 10 caractères, avec un décalage de zéro caractère.  
  
-   Un élément appelé nom aligné à gauche, long de 20 caractères, avec un décalage de zéro caractère.  
  
-   Un élément appelé rue aligné à gauche, long de 20 caractères, avec un décalage de zéro caractère.  
  
-   Un élément appelé ville aligné à gauche, long de 15 caractères, avec un décalage de zéro caractère.  
  
-   Un élément appelé département aligné à gauche, long de 2 caractères, avec un décalage de zéro caractère.  
  
-   Un élément appelé code postal aligné à gauche, long de 5 caractères, avec un décalage d'un caractère.  
  
 Sur la base de ces définitions d'enregistrement et de champ, le désassembleur de fichier plat génèrera l'équivalent XML suivant de cet enregistrement.  
  
```  
<shipTo country/region="US">  
    <name>Alice Smith</name>  
    <street>123 Maple Street</street>  
    <city>Mill Valley</city>  
    <state>CA</state>  
    <zip>90952</zip>  
</shipTo>  
  
```  
  
 Il y a un certain nombre d'aspects relatifs aux enregistrements positionnels qui ont une incidence sur la manière dont l'enregistrement est analysé lors de sa réception et construit lors de son envoi. Parmi eux, citons :  
  
-   Le caractère utilisé pour remplir la portion inutilisée de chaque champ et connu sous le nom de caractère de remplissage. Pour plus d’informations, consultez [remplissage des champs](../core/field-padding.md).  
  
-   Une balise optionnelle se trouvant dans l'enregistrement et utilisée pour le distinguer d'autres enregistrements similaires. Les balises sont généralement placées au début des enregistrements mais peuvent très bien trouver place à n'importe quel autre endroit des enregistrements. Pour plus d’informations, consultez [gestion des balises dans les enregistrements positionnels](../core/tag-handling-in-positional-records.md). Il est possible de définir si les enregistrements positionnels doivent comporter ou non une balise, mais une fois la décision prise, elle doit être respectée.  
  
-   Comment les données sont justifiées dans un champ de longueur fixe, par rapport aux caractères de remplissage accompagnant. Pour plus d’informations, consultez [Justification des champs](../core/field-justification.md).  
  
-   Enregistrements positionnels imbriqués dans d'autres enregistrements positionnels ou délimités. Pour plus d’informations, consultez [enregistrements positionnels imbriqués](../core/nested-positional-records.md).  
  
-   Enregistrements positionnels dotés de longueurs de champ spécifiées sous la forme d'un nombre spécifique d'octets et non d'un nombre spécifique de caractères. Pour plus d’informations, consultez [comptage des positions en octets](../core/position-counting-in-bytes.md).  
  
 Pour vous aider à mieux comprendre comment fonctionnent les fichiers plats positionnels, consultez les exemples dans les dossiers FlatFileReceive et FlatFileSend dans \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\SDK\Samples\Pipelines\AssemblerDisassembler\\.  
  
> [!NOTE]
>  Si votre fichier plat contient des enregistrements délimités et positionnels, vous devez définir le **Structure** propriété du nœud racine à **délimité** et **Structure** propriété de secondaire des nœuds d’enregistrement soit **délimité** ou **positionnel** selon le cas.  
  
> [!NOTE]
>  Les champs des enregistrements positionnels sont limités à 50 000 000 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)   
 [Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md)