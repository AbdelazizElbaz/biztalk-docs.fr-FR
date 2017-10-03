---
title: "Exemple de scénario basé sur le concentrateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- hub-and-spoke systems
- supply chains, hub-and-spoke systems
- examples, supply chains
- trading partners, supply chains
ms.assetid: ee92c24d-a281-4950-a61e-9cb3bd08d291
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b417398786e602379d16d6734a5ed366b9d6f2ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-hub-based-scenario"></a>Exemple de scénario basé sur un hub
Dans de nombreux scénarios de chaînes logistiques, les sociétés travaillent avec leurs partenaires commerciaux pour instaurer une connexion RNIF (RosettaNet Implementation Framework). Il s'agit d'un moyen efficace pour normaliser les communications tout au long de la chaîne logistique. Ce scénario est décrit dans [exemple fournir un scénario de chaîne](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md).  
  
 Il existe une autre façon d'automatiser les transactions dans la chaîne logistique : la société demande à une autre société de configurer et gérer le système intégré. Il s'agit d'un scénario basé sur un hub.  
  
## <a name="how-a-hub-based-system-works"></a>Fonctionnement d'un système basé sur un hub  
 Dans un système basé sur un hub, la société commanditaire qui sous-traite un système intégré se connecte à la société hub à l'aide d'une connexion RNIF. Le hub se connecte ensuite à tous les partenaires commerciaux de la société via n'importe quel type de connexion électronique demandé. La société hub fournit à tous les partenaires commerciaux les options de connexion suivantes : connexions RNIF, EDI, fichiers plats, applications web ou connexions propriétaires non compatibles. La gestion du système de communications est l'affaire de la société hub. La figure suivante illustre le fonctionnement de ce système.  
  
 ![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")  
  
 Un système basé sur un hub présente de nombreux avantages :  
  
-   La société commanditaire n'a pas à gérer la complexité de la chaîne logistique, car la société hub s'en charge.  
  
-   La société commanditaire n'a pas à gérer ou mettre à niveau le système. Elle n'est pas responsable des temps d'arrêt. La société hub est responsable de la maintenance du système et des temps d'arrêt.  
  
-   La société commanditaire tire parti des avantages d'un système compatible avec RosettaNet, notamment en matière de normalisation, d'automatisation, de réductions des coûts et de visibilité.  
  
-   La société commanditaire a entièrement automatisé sa chaîne logistique avec une variété de connexions électroniques qui permettent à l'ensemble des partenaires commerciaux de disposer de plusieurs choix de connexions. La société commanditaire n'a pas à gérer l'expertise technologique liée à la diversité des options de connexion.  
  
-   Un partenaire commercial peut continuer à utiliser une connexion propriétaire, du moment que la société hub la prend en charge.  
  
-   Le système est flexible. Les partenaires commerciaux n'ont pas à adopter un système compatible avec RosettaNet. Toutefois, s'ils le font, ils pourront tirer parti des avantages d'un tel système.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server résout les besoins de l’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [La nécessité d’intégration de partenaires commerciaux](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md)   
 [Le défi de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md)   
 [La Solution de chaîne d’approvisionnement](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md)   
 [Exemple de scénario de chaîne logistique](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)