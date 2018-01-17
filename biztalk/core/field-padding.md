---
title: Remplissage de champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47017036-7d64-4222-b574-d2913bf69358
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56aa8490bd9e72677c9c8eefa73e7f6bd8438dfd
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="field-padding"></a>Remplissage des champs

## <a name="overview"></a>Vue d'ensemble

Les caractères de remplissage sont utilisés dans les champs d'enregistrements délimités et positionnels lorsque les données contenues dans le champ sont inférieures au nombre de caractères ou octets réservés au champ. Ces caractères occupent la partie du champ non utilisée par les données, le cas échéant. Caractères de remplissage sont spécifiés dans un champ par champ à l’aide de la **caractère de remplissage** et **caractère de remplissage** propriétés correspondantes **élément de champ** et  **Attribut de champ** nœuds. Si aucun caractère de remplissage n'est spécifié pour un champ particulier, le caractère de remplissage par défaut, à savoir l'espace («   »), est utilisé pour le champ.  
  
## <a name="inbound-instances"></a>Instances entrantes
 Pour les messages d'instance entrants, qu’il s’agisse d’un enregistrement positionnel ou délimité, le désassembleur de fichier plat élimine les caractères de remplissage spécifiés ou par défaut de début ou de fin d’un champ particulier lorsque le message d’instance est converti en sa forme XML équivalente. Si elle est de début ou de fin des instances du caractère de remplissage correspondant éliminé varie selon que le **Justification** propriété correspondant **Fieldelement** et **champ Attribut** nœud a la valeur **droite** ou **gauche**, respectivement.  

## <a name="outbound-instances"></a>Instances sortants  
 Pour les messages d'instance sortants, l'assembleur de fichier plat insère le nombre approprié de caractères de remplissage spécifiés ou par défaut dans les champs pour que leur longueur soit correcte. Les caractères de remplissage seront insérés avant ou après les caractères de données basée sur le fait que le **Justification** propriété correspondantes **Fieldelement** et **attribut de champ** nœud a la valeur **droite** ou **gauche**, respectivement.  
  
 Lorsque le champ être complétées dans un message d’instance sortant se trouve dans un enregistrement positionnel, la **décalage de position** et **longueur positionnelle** propriétés correspondantes **champ Élément** ou **attribut de champ** nœud, combinée avec le nombre de caractères de données que le champ doit contenir, déterminer si des caractères de remplissage sont requis et si tel est le cas, combien. Lorsque le champ être complétées dans un message d’instance sortant se trouve dans un enregistrement délimité, caractères de remplissage ne sont insérés que lorsque la valeur de la **longueur minimale avec caractère de remplissage** propriété correspondantes  **Élément de champ** ou **attribut de champ** nœud dépasse le nombre de caractères de données.  

## 
Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## <a name="see-also"></a>Voir aussi  
 [Considérations relatives aux champs](../core/field-considerations.md)   
 [Justification des champs](../core/field-justification.md)   
 [Spécification de positions de champ dans les enregistrements positionnels](../core/specification-of-field-positions-within-positional-records.md)  