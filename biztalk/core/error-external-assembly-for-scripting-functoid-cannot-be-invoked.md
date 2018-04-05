---
title: 'Erreur : l’Assembly externe du fonctoid script ne peut pas être appelé | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.cannotInvokeExternalAssembly
ms.assetid: 30d97b05-2cbf-44a5-b219-3a5ae17fc597
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f6df36a955f2f40da35368fd72fd2d1fcbb7b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---external-assembly-for-scripting-functoid-cannot-be-invoked"></a>Erreur - Assembly externe du fonctoid script ne peut pas être appelée.
**Code d’erreur**  
  
 btm1067  
  
 **Explication**  
  
 La méthode d’assembly externe qui est associée à la **script** fonctoid ne peut pas être appelé. Bien que cette méthode ne soit pas obligatoire pour la compilation des mappages, l'opération Test Map requiert la présence de ces assemblys externes dans le Global Assembly Cache (GAC). Toute opération d'exécution normale nécessite également que les assemblys externes se trouvent dans le GAC.  
  
 **Action de l’utilisateur**  
  
 Vérifiez que l’assembly externe correspondant au **script** fonctoid figure dans le GAC.