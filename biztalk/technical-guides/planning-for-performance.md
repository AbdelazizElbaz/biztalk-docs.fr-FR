---
title: Planification des performances | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 267a8bc6-a0ab-4335-bc04-c22d5a56792f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fac21f0b483ac3cbaec64c48b524a17422cb146
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-performance"></a>Planification des performances
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est une plate-forme d’application. Il n’est pas simplement un produit serveur ou simplement un produit de développeur. Il s’agit d’une plate-forme d’application qui est utilisée pour créer des systèmes de gestion des processus métier, pour intégrer des applications d’entreprise, pour automatiser les flux de travail, et pour activer le service des architectures orientées.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]dépend de nombreux autres composants logiciels. La plate-forme d’application BizTalk comprend généralement plusieurs composants logiciels suivants : le système d’exploitation Windows Server, SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], externe (facultatif), d’IIS systèmes qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interagit avec, ainsi que les adaptateurs non Microsoft et des composants.  
  
 En raison de la complexité d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, il existe plusieurs considérations à observer lors de la planification des performances. Il existe plusieurs paramètres par défaut qui s’appliquent à tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements et il existe des considérations et des méthodes d’optimisation spécifiques [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architectures.  
  
 Cette rubrique fournit une vue d’ensemble des paramètres par défaut que vous devez appliquer lors de l’optimisation des performances pour tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements. Il fournit également des recommandations pour le test et d’optimisation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements qui sont conçues pour des scénarios spécifiques.  
  
## <a name="settings-that-you-should-apply-to-all-biztalk-server-environments"></a>Paramètres que vous devez appliquer à tous les environnements de BizTalk Server  
 Le [opérationnel préparation des listes de contrôle](../technical-guides/operational-readiness-checklists.md) section de ce guide contient une liste d’éléments que vous devez examiner avant d’utiliser une solution BizTalk. Cette liste de vérification contient des éléments d’action qui peuvent avoir un impact significatif sur les performances de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, quelle que soit la nature spécifique de la solution BizTalk qui est utilisée.  
  
## <a name="considerations-for-testing-and-optimizing-a-biztalk-solution"></a>Considérations relatives à des fins de test et d’optimisation d’une Solution BizTalk  
 Différentes solutions BizTalk peuvent avoir des critères de performances considérablement différent. Par exemple, une solution BizTalk qui est construite autour d’orchestrations en cours d’exécution aura un profil de performance qu’une solution BizTalk se concentre sur la réception, de conversion et de mappage des documents de fichier plat. Une solution axée sur l’orchestration peut être beaucoup le processeur ou peut appeler des composants personnalisés qui bénéficient de l’optimisation, lors d’une solution d’axée sur le mappage et de conversion de fichier plat peuvent être beaucoup plus de mémoire.  
  
 Les adaptateurs et les pipelines utilisés pour recevoir et envoyer des documents et se déconnecte de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut avoir également un impact important sur les performances de la solution BizTalk. Le niveau de suivi de document nécessaire à la solution affecte considérablement les performances. En raison de profils de performances divergentes sont possibles dans les différentes solutions BizTalk, il est absolument essentiel que la solution BizTalk pour mesurer les performances maximales admissibles et les performances de suivi maximal acceptable à tester.  
  
 Après avoir déterminé les performances maximales admissibles et les performances de suivi maximal acceptable de la solution BizTalk, il existe des étapes spécifiques que vous pouvez employer pour supprimer les goulots d’étranglement dans la solution BizTalk. Pour plus d’informations, consultez la [Guide des performances BizTalk Server 2009](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).  
  
## <a name="see-also"></a>Voir aussi  
 [Planification du niveau BizTalk Server](../technical-guides/planning-the-biztalk-server-tier.md)