---
title: Didacticiel de bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loopbacks, tutorial
- loopback tutorial, about the loopback tutorial
- loopback tutorial
- tutorials, loopback tutorial
ms.assetid: 0f69c1f1-4039-4949-8eed-127ceabbc3cc
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b013eb65320dc36dd1319d7332e45ed54b2444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loopback-tutorial"></a>Didacticiel de bouclage
Ce didacticiel contient des procédures détaillées qui décrivent comment vous pouvez utiliser [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pour simuler une implémentation de processus entre l’organisation d’accueil et partenaire sur un seul ordinateur.  
  
 Dans un environnement de production réel, l’implémentation de votre organisation partenaire réside sur un ordinateur distant. Ce didacticiel utilise l’utilitaire de bouclage pour créer un miroir commerciaux d’accord pour simuler le partenaire commercial sur le même ordinateur. À l’aide d’un scénario de bouclage seul ordinateur fonctionne pour à des fins de développement et de test. Il est recommandé que vous n’utilisez ne pas l’utilitaire de bouclage dans un environnement de production.  
  
 Ce scénario de bouclage ne prend pas en charge la signature des messages et donc ne prend pas en charge non répudiation.  
  
 Ce scénario prend en charge le chiffrement des messages si vous avez configurée une autorité de certification, et que vous avez une clé privée pour le chiffrement disponible à des fins de test.  
  
 Dans ce didacticiel, vous créez une organisation d’origine, une organisation partenaire, un accord commercial, utilisez l’utilitaire de bouclage pour créer un accord de mise en miroir, puis exécutez un exemple de processus pour vérifier que le scénario de bouclage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Préparation pour le didacticiel](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-tutorial.md)  
  
-   [Étape 1 : Créer l’organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)  
  
-   [Étape 2 : Créer l’organisation du partenaire](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-the-partner-organization.md)  
  
-   [Étape 3 : Modifier le Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)  
  
-   [Étape 4 : Créer un accord commercial](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)  
  
-   [Étape 5 : Créer un accord de mise en miroir](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)  
  
-   [Étape 6 : Démarrer des Orchestrations](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)  
  
-   [Étape 7 : Créer un exemple de Message LOB](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)  
  
-   [Étape 8 : Afficher les Messages dans les bases de données BTARN](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)