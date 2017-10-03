---
title: Recommandations sur la Phase de conception | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3d183e-a6f3-47d0-90ac-99b12c064607
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0f361734aa7539f12940212a339b582bb4f2641
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="design-phase-recommendations"></a>Recommandations de Phase de conception
Les premiers éléments livrables associés à la phase de conception sont des spécifications de conception à la fois pour le système et les tests de validation des fonctionnalités et performances du système. Le processus de conception comprend en général la vérification de la faisabilité des fonctionnalités et tests. Il implique le développement initial et, dans le cas d'une conception de validation, les premiers tests d'implémentation de validation technique abordés dans cette section.  
  
## <a name="acquire-detailed-throughput-and-latency-profiles"></a>Acquérir les profils détaillés de latence et débit  
 En vous basant sur les profils de charge initiaux sur lesquels les critères de déclenchement des performances de la phase précédente du projet ont été établis, définissez des profils de débit et de latence détaillés pendant la phase de conception. Si possible, procurez-vous des données de performances à partir des systèmes de production. L'utilisation de données de production permet de disposer de profils de performances réalistes à partir desquels vous pouvez concevoir des tests pendant cette phase. Si vous ne possédez pas de données de production, un profil réaliste doit être extrapolé à partir de la charge attendue.  
  
 Il est essentiel que les tests de performances créés au cours de la phase de conception incluent des profils de performances simulant de façon très fidèle ce qui sera attendu du système en cours de production. Pour plus d’informations sur la création de profils de performances réalistes et durables, consultez [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md)  
  
## <a name="investigate-performance-risk-mitigations"></a>Rechercher des solutions aux risques liés aux performances  
 Au cours de la phase de configuration, les risques associés aux objectifs de performances définis ont été identifiés, ainsi que des solutions possibles.  Ces risques et solutions doivent être étudiés aussi tôt que possible lors de la phase de conception afin de disposer de temps pour apporter des changements, le cas échéant. Chaque risque identifié doit tout d'abord être prouvé par le biais d'un test de validation technique. Les solutions proposées doivent ensuite également être testées de façon à en évaluer l'efficacité.  
  
 Prenons l'exemple d'un système hérité qui utilise le protocole FTP pour communiquer avec d'autres systèmes. Cependant, si l'on étudie le débit que le serveur FTP hérité peut atteindre en combinaison avec l'adaptateur FTP BizTalk Server, il est clair qu'il n'est pas possible d'atteindre le débit souhaité (établi en tant que critère de déclenchement au cours de la configuration). Afin de limiter les risques pour le projet, les solutions suivantes sont identifiées au cours de la phase de configuration :  
  
-   Faire évoluer le serveur FTP de façon horizontale ou verticale et créer plusieurs adresses FTP logiques dédiées aux types de messages spécifiques de façon à répartir la charge.  
  
-   Modifier le système hérité de façon à transmettre de nombreux messages dans un seul fichier sous la forme d'un lot, afin de réduire la charge de transfert par message.  
  
-   Modifier le système hérité de façon à utiliser un autre protocole, plus rapide que FTP, tel que MSMQ.  
  
 La première chose à faire dans cet exemple est de prouver que le risque existe. Pour cela, vous devez tester les performances du système FTP existant. Une solution de validation technique simple recevant simplement les messages à partir du serveur FTP doit être définie et déployée. Le profil de charge de production attendu pour le parcours FTP doit ensuite lui être appliqué. Si le serveur parvient à gérer la charge souhaitée, le risque n'est pas prouvé et les recherches peuvent s'arrêter là. S'il n'est pas capable de traiter la charge, la solution la plus susceptible de régler le problème avec un coût et des risques limités doit être recherchée par le biais du processus de validation technique.  
  
## <a name="refine-system-size-estimate"></a>Affiner les estimations liées à la taille du système  
 Les recherches menées lors de la phase de conception fournissent des informations empiriques précieuses sur les performances du système.  
  
 Ainsi, si nous poursuivons avec l'exemple ci-dessus pour lequel les performances du serveur FTP étaient trop faibles. Étant donné que certains systèmes de l'environnement utilisent déjà le transport de messagerie MSMQ, il a été décidé de modifier le système hérité pour qu'il l'utilise également. Cependant, pendant le test de performances d'une nouvelle validation technique utilisant MSMQ, vous remarquez que l'utilisation de l'UC du serveur SQL sur lequel la base de données MessageBox est installée est pratiquement tout le temps de 100 % et que vous n'arrivez pas à atteindre le débit attendu sur le parcours MSMQ.  
  
 En supposant que la configuration de SQL Server est optimale pour l'application, il apparaît que le matériel SQL Server n'est pas suffisant pour le débit souhaité et que la taille du système doit être affinée. Dans ce cas, le matériel SQL Server a besoin d'UC supplémentaires, d'UC plus rapides ou des deux.  
  
## <a name="see-also"></a>Voir aussi  
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Recommandations sur la configuration requise Phase](../core/requirements-phase-recommendations.md)   
 [Recommandations de Phase d’implémentation](../core/implementation-phase-recommendations.md)   
 [Recommandations de Phase de vérification](../core/verification-phase-recommendations.md)   
 [Recommandations de Phase de mise en production](../core/release-phase-recommendations.md)