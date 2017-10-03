---
title: Justification du champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04380208-9bfd-43cf-a279-104daea2b978
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da9209040e64380b3a7a167dd013a15232543a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-justification"></a>Justification des champs

## <a name="overview"></a>Vue d'ensemble
La justification des champs détermine si les caractères des données d’un champ sont placés avant (alignement à gauche) ou après (alignement à droite) les caractères de remplissage d’accompagnement.  
  
 Il arrive que les caractères de données contenus dans un champ ne nécessitent pas tout l’espace consacré au champ. Cela est vrai plus fréquemment dans les enregistrements positionnels, où le nombre d’octets ou de caractères consacrés à un champ est fixe, comme déterminé par le **longueur positionnelle** et **décalage de position** propriétés. Dans de tels cas, il est courant que les éléments de données soient plus petits que la longueur du champ, laissant une partie du champ inutilisée occupée par des caractères de remplissage.  
  
 Tel remplissage peut également se produire dans les enregistrements délimités lorsque la valeur de la **longueur minimale avec caractère de remplissage** propriété dépasse l’espace nécessaire au stockage de l’élément de données correspondant.  
  
 Dans ces deux cas, la valeur de la **Justification** propriété (**gauche** ou **droite**) de la **élément de champ** ou **Attribut de champ** nœud détermine si les caractères de remplissage suivront les caractères de données (alignement à gauche) ou si les caractères de remplissage doit précéder les caractères de données (alignement à droite).  
  
 Lorsque le désassembleur de fichier plat convertit un message d’instance de fichier plat en un message d’instance XML équivalent, la **Justification** propriété est utilisée lors de l’analyse du champ correspondant. Lorsque l’assembleur de fichier plat convertit un message d’instance XML en un message d’instance de fichier plat équivalent, la **Justification** propriété est utilisée pour déterminer quand les caractères de remplissage associé à un champ particulier, le cas échéant, doit être ajouté au flux de données : avant ou après les caractères de données correspondante.  
  
## <a name="see-also"></a>Voir aussi  
- [Considérations relatives aux champs](../core/field-considerations.md)   
- Plus d’informations sur les propriétés suivantes [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - Justification (propriété de nœud des schémas de fichier plat)  
    - Décalage de position (propriété de nœud des schémas de fichier plat)  
    - Longueur positionnelle (propriété de nœud des schémas de fichier plat)