---
title: "Vs de faits à court terme. Faits à long terme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- facts, short-term
- facts, long-term
- short-term facts
- business rules, facts
- long-term facts
ms.assetid: de020b20-1012-498a-969e-4adc4549918c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d5c37926fb1da5499f34e22c35f8a8f32d238bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="short-term-facts-vs-long-term-facts"></a>Vs de faits à court terme. Faits à long terme
Deux types de faits sont déclarés dans la mémoire de travail du moteur de règles, des faits à court terme et des faits à long terme.  
  
## <a name="short-term-facts"></a>Faits à court terme  
 Un fait à court terme est propre à un cycle d'exécution unique du moteur de règles. Les faits à court terme sont automatiquement retirés de la mémoire de travail du moteur de règles après l'exécution de la stratégie. Si les données d'une stratégie changent entre les cycles d'exécution du moteur de règles, vous soumettez ces données au moteur de règles sous la forme d'un fait à court terme.  
  
 Exemples de faits à court terme :  
  
-   Faits soumis en tant que paramètres à la **Policy.Execute** (méthode).  
  
-   Faits soumis en tant que paramètres à la **appeler règles** forme.  
  
-   Faits soumis à partir d’une action d’une règle utilisant le **Assert** (fonction).  
  
## <a name="long-term-facts"></a>Faits à long terme  
 Les faits à long terme sont chargés dans la mémoire de travail du moteur de règles pour une utilisation sur un nombre arbitraire de cycles d'exécution. En règle générale, ces faits varient peu et ne changent pas entre les différentes exécutions d'une stratégie. Par exemple, vous pouvez décider de créer une connexion de base de données une seule fois et d'exécuter la stratégie plusieurs fois par le biais de la même connexion. La seule véritable distinction entre les faits à court et long terme réside dans leur implémentation.  
  
 Pour soumettre un fait à long terme, procédez de la façon suivante :  
  
1.  Créez un extracteur de faits qui implémente le **IFactRetriever** interface. Créez et déclarez le fait dans la mémoire de travail de la règle de moteur quand le **UpdateFacts** méthode est appelée pour la première fois et le fait que lorsque cela est nécessaire pour les appels suivants de mise à jour de la **UpdateFacts**(méthode).  
  
2.  Configurer la stratégie pour utiliser l’extracteur de faits à l’aide de l’éditeur des règles d’entreprise.  
  
 Pour plus d’informations sur la création d’un extracteur de faits et de l’utiliser dans une stratégie, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Faits](../core/facts.md)