---
title: "Avertissement : incompatibilité de Type de données de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.fieldDataTypeMismatch
ms.assetid: 0c15d926-1d05-404b-bb16-a5fe8bc3575d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af42f5c921333e34c9ee219020cdb0fba97a7b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---field-data-type-mismatch"></a>Avertissement : incompatibilité de Type de données de champ
**Code d’erreur**  
  
 BEC1002  
  
 **Explication**  
  
 Le **Type de données** propriété du nœud indiqué a été trouvée pour être différente de celle la **Type de données** propriété de la **élément de champ** nœud auquel il est promu dans le schéma de propriété correspondant. Le type de données d’un nœud dans un schéma doit correspondre au type de données affecté à la **élément de champ** nœud utilisé pour la promotion du champ de propriété, ou au moins, les types de données affecté doivent correspondre au même type common language runtime (CLR).  
  
 **Action de l’utilisateur**  
  
 Modifier la **Type de données** propriétés du nœud indiqué et **élément de champ** nœud auquel il est en cours de promotion aux mêmes données de type valeur, ou au moins pour les données de type de valeurs qui correspondent au même type de données CLR.