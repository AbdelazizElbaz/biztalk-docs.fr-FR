---
title: "Nombre d’étapes de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 74bd9f8c-99b4-4931-a096-6c54221ab2e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f61c5c348e54ea096c921cb6fc63f0db339dbf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-processing-stages"></a>Nombre d’étapes de traitement
La solution décompose le processus de commande en étapes, de sorte qu'il est possible de modifier le processus (par remplacement d'étapes) sans interrompre les commandes à long terme. Pour plus d’informations sur la façon dont le processus a été divisé en étapes, consultez « Division des processus d’entreprise » dans [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
 La version actuelle de la solution contient uniquement deux étapes de traitement. Elle peut toutefois en contenir plus. Un nombre d'étapes plus important implique davantage de points auxquels il est possible de créer des versions du processus et de continuer à travailler sur la dernière version d'une étape de traitement. Toutefois, chaque étape implique une coordination supplémentaire des messages transitant via la base de données MessageBox, ce qui accroît le délai de traitement. Vous devez analyser les performances de la solution pour déterminer si le nombre d'étapes est excessif.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)