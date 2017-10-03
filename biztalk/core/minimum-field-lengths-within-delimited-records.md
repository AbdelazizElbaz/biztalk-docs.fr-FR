---
title: "Longueur minimale des champs dans les enregistrements délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d803eb311bda7c27db5a05830f7a84f9b9857e8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="minimum-field-lengths-within-delimited-records"></a>Longueur minimale des champs dans les enregistrements délimités
Par définition, les champs des enregistrements positionnels sont tous définis avec des longueurs spécifiques exactes. Les champs des enregistrements délimités peuvent également être définis avec une longueur minimale. Cette caractéristique est définie par le **[longueur minimale avec caractère de remplissage** propriété du **élément de champ** et **attribut de champ** nœuds.  
  
 Lorsque vous fournissez une valeur différente de zéro pour le **longueur minimale avec caractère de remplissage** propriété, l’assembleur de fichier plat détermine si le nombre de caractères de données associées au champ est inférieur à celle du paramètre de la **Longueur minimale avec caractère de remplissage** propriété, le caractère de remplissage correspondant permet de faire la différence.  
  
 Les caractères de remplissage sont ajoutés avant ou après les caractères de données en fonction du paramètre de la **Justification** propriété pour le champ. Lorsque le **Justification** est définie sur **gauche**, tous les caractères de remplissage nécessaires pour obtenir la longueur minimale seront ajoutées après les caractères de données. Lorsque le **Justification** est définie sur **droite**, tous les caractères de remplissage nécessaires pour obtenir la longueur minimale sont ajoutés avant les caractères de données.  
  
 Lorsque vous fournissez une valeur différente de zéro pour le **longueur minimale avec caractère de remplissage** propriété, le désassembleur de fichier plat examine le début ou la fin (en fonction du paramètre de la **Justification** propriété) de la valeur du champ de la présence du caractère de remplissage correspondant, et le cas échéant, les caractères de remplissage seront ignorés et n’apparaissent pas dans le message XML équivalent en cours de construction.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations relatives aux champs](../core/field-considerations.md)   
-  **Justification (propriété de nœud des schémas de fichier plat)** et **longueur minimale avec caractère de remplissage (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]