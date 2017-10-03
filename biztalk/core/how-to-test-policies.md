---
title: "Comment tester les stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- Business Rule Composer, testing
- Business Rule Composer, policies
- testing, Business Rule Composer
- policies, testing
ms.assetid: 122dee26-d1f1-49a6-a6d5-a9d3d861a66b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7a0f8c0d63d14d5a529039a6e1c8af5b363cc9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-policies"></a>Comment les stratégies de Test
Pour tester une stratégie, vous avez besoin de faits sur lesquels les règles peuvent être exécutées. Vous pouvez ajouter des faits en spécifiant des valeurs dans les documents XML ou dans les tables de bases de données vers lesquels vous pointerez dans le testeur de stratégie, ou vous pouvez utiliser un créateur de faits qui fournira au moteur un ensemble d'objets .NET en guise de faits. Pour plus d’informations, consultez [création d’un créateur de faits](../core/how-to-create-a-fact-creator.md).  
  
### <a name="to-test-a-policy-in-the-business-rule-composer"></a>Pour tester une stratégie dans l’Éditeur des règles d’entreprise  
  
1.  Dans la fenêtre Explorateur de stratégies, cliquez sur la version de stratégie que vous voulez tester.  
  
2.  Cliquez sur le **tester la stratégie** bouton (flèche verte) dans la barre de menus.  
  
     Le volet du haut affiche les types de faits référencés par les règles de stratégie.  
  
3.  Pour ajouter une instance de fait, cliquez sur une **Document XML** ou **Table de base de données** type de fait, puis cliquez sur **ajouter une Instance**.  
  
4.  Si vous souhaitez supprimer une instance de fait, cliquez sur le type de fait correspondant, puis cliquez sur **supprimer une Instance**.  
  
5.  Si vous souhaitez ajouter un créateur de faits que vous avez écrit, cliquez sur **ajouter** dans le volet du créateur de faits.  
  
6.  Cliquez sur **Test**.  
  
     Le résultat du suivi du test de la stratégie s’affiche dans la fenêtre de sortie de test.  
  
7.  Cliquez avec le bouton droit dans la fenêtre de sortie pour enregistrer, effacer, sélectionner ou copier le texte de sortie.  
  
     ![](../core/media/ebiz-testpolicy.gif "ebiz_testpolicy")  
Sélection de faits pour le test d’une stratégie