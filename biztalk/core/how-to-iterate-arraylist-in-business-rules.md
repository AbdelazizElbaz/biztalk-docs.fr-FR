---
title: "Comment effectuer une itération d’ArrayList dans les règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, ArrayList
- business rules, arrays
- Business Rules Framework, programming
ms.assetid: 935e8648-72dc-4128-986c-72b0487bc074
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95896b63e5bb982a4778b05970900c989ebc66b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-iterate-arraylist-in-business-rules"></a>Comment effectuer une itération d’ArrayList dans les règles d’entreprise
Cette section fournit un exemple d’itération sur les membres d’un **ArrayList** dans les règles d’entreprise.  
  
 Supposons que vous avez un **ArrayList** avec une collection de **MyClass** objets. Vos règles d'entreprise se présentent alors comme suit :  
  
## <a name="rule-a"></a>Règle A  
 IF 1==1  
  
 THEN Assert (ArrayList.GetEnumerator)  
  
 Un **IEnumerator** type est déclaré dans la mémoire de travail, car la condition de règle (1 == 1) a toujours la valeur true.  
  
## <a name="rule-b"></a>Règle B  
 IF IEnumerator.MoveNext  
  
 THEN    Assert (IEnumerator.get_Current)  
  
 Update (IEnumerator)  
  
 Comme la règle effectue une itération dans les **ArrayList**, chaque **MyClass** objet dans la collection est déclaré dans la mémoire de travail.  
  
## <a name="rule-c"></a>Règle C  
 IF MyClass.MyProperty==2  
  
 PUIS \<faire quelque chose... >  
  
 Cette règle exécute une ou des actions lorsque la valeur de propriété de l'objet a une correspondance dans la condition.