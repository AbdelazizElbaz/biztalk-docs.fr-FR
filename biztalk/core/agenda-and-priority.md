---
title: "Agenda et priorité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, executing
- Business Rules Engine, agendas
- Business Rules Engine, priorities
- business rules, priorities
- business rules, examples
- Business Rules Engine, examples
- examples, Business Rules Engine
- Business Rules Engine, rules
ms.assetid: ca54f750-4f2d-4734-8e6e-7af1b4967e6a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4529753251c2bf7934616b91662bde836c8339e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agenda-and-priority"></a>Agenda et priorité
Pour comprendre comment le moteur de règles d’entreprise évalue les règles et exécute les actions, vous devez comprendre les concepts de *agenda* et *priorité*.  
  
## <a name="agenda"></a>Agenda  
 L'agenda est une planification dont se sert le moteur pour mettre en file d'attente les règles à exécuter. L'agenda est lié à une instance de moteur et agit sur une stratégie, pas sur plusieurs. Lorsque les conditions d'une règle donnée sont satisfaites et qu'un fait est déclaré en mémoire de travail, la règle est placée sur l'agenda et exécutée selon sa priorité. Les actions d'une règle sont exécutées dans l'ordre, du haut vers le bas. Les actions de la règle suivante sur l'agenda sont ensuite exécutées.  
  
 Les actions appartenant à une règle sont traitées comme un bloc afin que toutes soient exécutées avant le début de la règle suivante. Toutes les actions d'un bloc de règle s'exécutent indépendamment les unes des autres. Pour plus d’informations sur les déclarations, consultez [les fonctions de contrôle du moteur](../core/engine-control-functions.md).  
  
 L'exemple suivant illustre le fonctionnement de l'agenda.  
  
 **Règle1**  
  
```  
IF  
Fact1 == 1  
THEN  
Action1  
Action2  
```  
  
 **Rule2**  
  
```  
IF  
Fact1 > 0  
THEN  
Action3  
Action4  
```  
  
 Nous déclarons le fait Fait1 qui possède la valeur 1 dans le moteur. Étant donné que les conditions de Règle 1 et Règle  2 sont satisfaites, ces deux règles sont déplacées dans l'agenda pour que leurs actions puissent être exécutées.  
  
|Mémoire de travail|Agenda|  
|--------------------|------------|  
|Fait1 ( valeur = 1 )|**Règle1**<br /><br /> -Action1<br />-Action2<br /><br /> **Rule2**<br /><br /> -Action3<br />-Action4|  
  
## <a name="priority"></a>Priorité  
 Une priorité d'exécution est définie pour chaque règle, avec une priorité par défaut de 0 pour toutes. La priorité peut être positive ou négative ; les nombres les plus élevés correspondent aux priorités les plus importantes. Les actions sont exécutées de la priorité la plus élevée à la priorité la plus faible.  
  
 L'exemple suivant montre l'incidence de la priorité sur l'ordre d'exécution des règles.  
  
 **Règle1 (priorité = 0)**  
  
```  
IF  
Fact1 == 1  
THEN  
Discount = 10%  
```  
  
 **Règle2 (priorité = 10)**  
  
```  
IF  
Fact1 > 0  
THEN  
Discount = 15%  
```  
  
 Les conditions des deux règles sont satisfaites, mais Règle2 est exécutée en premier car elle a la priorité la plus importante. La remise finale est de 10 % car il s'agit du résultat de l'action exécutée pour Règle1, comme l'illustre le tableau suivant.  
  
|Mémoire de travail|Agenda|  
|--------------------|------------|  
|Fait1 ( valeur = 1 )|**Rule2**<br /><br /> Remise = 15 %<br /><br /> **Règle1**<br /><br /> Remise  = 10 %|  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de règles](../core/rule-engine.md)