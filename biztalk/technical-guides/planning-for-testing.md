---
title: Planification du test | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bdf5f35d5d612ec077ebdac83339c5a6838109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-testing"></a>Planification du test
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]test peut être divisé en plusieurs catégories, notamment les tests unitaires, test fonctionnel, le test de charge et tests de disponibilité. Cette rubrique décrit l’unité et le test de charge et la planification de chacun.  
  
## <a name="planning-for-unit-testing"></a>Planification pour les tests unitaires  
 Le test unitaire est une procédure qui permet de valider que des unités de code fonctionnent comme prévu. Test unitaire peut être considéré comme « réparation « test : le logiciel effectue la fonctionnalité souhaitée sous différentes conditions et peut les gérer les erreurs logicielles qui se produisent dans ces conditions ?  
  
 Étant donné que le test unitaire est généralement effectuée sur des composants individuels, le banc d’essai associé ne doit pas les fonctions de traitement d’un environnement de production réel. Pour cette raison, vous devez envisager d’effectuer des tests unitaires dans un environnement de serveur virtuel, ce qui nécessite beaucoup moins de ressources matérielles.  
  
 Un autre aspect des tests unitaires qui peut-être être effectué dans un environnement virtualisé est mis en œuvre. Mise en lots est le processus de l’unité de tester le déploiement réel d’une solution BizTalk. Pour optimiser les ressources matérielles disponibles, envisagez d’utiliser le serveur virtuel pour votre environnement intermédiaire.  
  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtuel, consultez [à l’aide de Virtual Server pendant le processus](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ). Pour plus d’informations sur les outils qui peuvent être utiles pour une solution BizTalk de tests unitaires, consultez [outils de test](~/technical-guides/tools-for-testing.md). Pour obtenir la liste des considérations pour l’exécution de tests unitaires, consultez [effectuant des tests unitaires](../technical-guides/performing-unit-testing.md).  
  
## <a name="planning-for-load-testing"></a>Planification du test de charge  
 Le test de charge est le processus de mesure des performances maximales admissibles et maximum acceptable de suivi des performances d’une solution BizTalk, puis en supprimant les goulots d’étranglement INHIBANT le débit de la solution. Pour plus d’informations sur la charge de test et suppression des goulots d’étranglement d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, consultez le [Guide des performances BizTalk Server 2009](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).  
  
 Pour plus d’informations sur les outils qui peuvent être utiles pour une solution BizTalk de test de charge, consultez [outils de test](~/technical-guides/tools-for-testing.md). Pour obtenir la liste des considérations en matière de tests de charge, consultez [effectuer le chargement et le test de débit](../technical-guides/performing-load-and-throughput-testing.md).  
  
## <a name="plan-to-test-for-the-lifetime-of-the-solution"></a>Plan de Test pour la durée de vie de la Solution  
 Alors que les tests unitaires et tests de charge sont particulièrement importantes pendant les premières phases de la solution, planifier des tests réguliers tout au long de la durée de vie de la solution pour découvrir les problèmes potentiels qui peuvent se produire lorsque la charge augmente ou en tant que de nouvelles fonctionnalités ou composants sont ajoutés à la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification du niveau BizTalk Server](../technical-guides/planning-the-biztalk-server-tier.md)   
 [Liste de vérification : Test opérationnelle](../technical-guides/checklist-testing-operational-readiness.md)