---
title: Messages de fichier plat avec des enregistrements délimités | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ad7119b-4e39-43df-9dba-a04382eb6db2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5dc9eb0253e2bfe8824f6395e1c619c23f0e551
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="flat-file-messages-with-delimited-records"></a>Messages de fichier plat avec des enregistrements délimités
Les enregistrements délimités d'un message d'instance de fichier plat contiennent des enregistrements imbriqués et/ou des champs individuels (éléments de données) séparés par un caractère ou un ensemble de caractères prédéfinis. Les champs sont analysés selon ces délimiteurs de séparation. Prenons l'exemple des enregistrements délimités suivants issus d'un message d'instance de fichier plat et contenant deux lignes d'un bon de commande hypothétique :  
  
```  
  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Electric-120vac,ITEM926-AA|Baby Monitor|1|39.98|Electric-4AA|2004-01-21  
  
```  
  
 Une définition raisonnable de cet enregistrement dans un schéma de fichier flat peut être celle-ci :  
  
-   Des éléments nommés d'un enregistrement délimité avec un délimiteur enfant (,), un préfixe de classement enfant et la balise ITEMS (en gras)  
  
    -   Élément avec un délimiteur enfant nommé d’enregistrement répété A délimités, &#124;, valeur infix de classement enfant et la balise d’élément.  
  
    -   Un élément « partNum ».  
  
    -   Un élément « productName ».  
  
    -   Un élément « quantity ».  
  
    -   Un élément « USPrice ».  
  
    -   Un élément « powerSource ».  
  
-   Un élément facultatif « shipDate ».  
  
 Sur la base de ces définitions d'enregistrement et de champ, le désassembleur de fichier plat produit l'équivalent XML de ces enregistrements.  
  
```  
  
<items>  
    <item partNum="872-AA">  
        <productName>Lawnmower</productName>  
        <quantity>1</quantity>  
        <USPrice>148.95</USPrice>  
        <powerSource>Electric-120vac</powerSource>  
    </item>  
    <item partNum="926-AA">  
        <productName>Baby Monitor</productName>  
        <quantity>1</quantity>  
        <USPrice>39.98</USPrice>  
        <powerSource>Electric-4AA</powerSource>  
        <shipDate>2004-01-21</shipDate>  
    </item>  
</items>  
  
```  
  
 Il y a un certain nombre d'aspects relatifs aux enregistrements délimités qui ont une incidence sur la manière dont l'enregistrement est analysé lors de sa réception et construit lors de son envoi. Parmi eux, citons :  
  
-   Le ou les caractères utilisés pour substituer l'interprétation des délimiteurs de manière à ce qu'ils soient traités comme faisant partie des données. Pour plus d’informations, consultez [comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).  
  
-   Une balise optionnelle au début de l'enregistrement, utilisée pour le distinguer d'autres enregistrements similaires. Pour plus d’informations, consultez [gestion des balises dans les enregistrements délimités](../core/tag-handling-in-delimited-records.md).  
  
-   Comment les données sont justifiées dans les champs à longueur minimum, relativement aux caractères de remplissage les accompagnant. Pour plus d’informations, consultez [remplissage des champs](../core/field-padding.md), [Justification des champs](../core/field-justification.md), et [Minimum champ longueurs dans les enregistrements délimités](../core/minimum-field-lengths-within-delimited-records.md).  
  
-   Les enregistrements positionnels imbriqués dans d'autres enregistrements délimités. Pour plus d’informations, consultez [enregistrements imbriqués positionnels et délimités](../core/nested-positional-and-delimited-records.md).  
  
-   Comment les données sont justifiées dans un champ de longueur fixe, relativement aux caractères de remplissage les accompagnant. Pour plus d’informations, consultez [Justification des champs](../core/field-justification.md).  
  
-   Les considérations ayant trait au positionnement des délimiteurs relativement aux données qu'ils délimitent. Pour plus d’informations, consultez [considérations d’ordre enfant](../core/child-order-considerations.md).  
  
-   La préservation et la suppression de délimiteurs lors de la réception ou de l'envoi des messages de fichier plat. Pour plus d’informations, consultez [délimiteur préservation et Suppression de](../core/delimiter-preservation-and-suppression.md).  
  
 Pour vous aider à mieux comprendre comment fonctionnent les fichiers plats délimités, consultez les exemples dans les dossiers FlatFileReceive et FlatFileSend dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\.  
  
> [!NOTE]
>  Si votre fichier plat contient des enregistrements délimités et positionnels, vous devez définir le **Structure** propriété du nœud racine à **délimité** et **Structure** propriété de secondaire des nœuds d’enregistrement soit **délimité** ou **positionnel** selon le cas.  
  
> [!NOTE]
>  Les champs délimités des fichiers plats sont limités à 50 000 000 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)   
 [Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md)   
 [Migration des enregistrements de fichier plat](../core/migrating-flat-file-records.md)