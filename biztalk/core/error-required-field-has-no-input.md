---
title: Erreur - obligatoire ne comporte aucune entrée champ | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdFieldHasNoInput
ms.assetid: 2454baf8-aa28-4b7b-93cd-aab9afc63823
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 343b565dec1ee3d0bc2487bd32ea3854cbacb3bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---required-field-has-no-input"></a>Erreur : champ obligatoire ne comporte aucune entrée.
**Code d’erreur**  
  
 btm1028  
  
 **Explication**  
  
 Le nœud indiqué dans le schéma de destination est défini comme étant obligatoire. Cependant, il ne comporte ni lien entrant, ni valeur constante ou par défaut, et ne sera donc pas inclus dans les messages d'instance sortants fournis par ce mappage.  
  
 **Action de l’utilisateur**  
  
 Si nécessaire, vous pouvez définir le nœud indiqué dans le schéma de destination comme étant facultatif ou lui affecter un lien entrant, une valeur constante ou une valeur par défaut.