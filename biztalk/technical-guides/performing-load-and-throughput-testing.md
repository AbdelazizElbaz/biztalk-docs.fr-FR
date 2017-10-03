---
title: "Exécution de charge et tests de débit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ff86ebd-a77f-4e29-bfea-0306e88bbf67
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3da46b2dc3208208305e60e9efbfadd0c60d7d32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performing-load-and-throughput-testing"></a>Exécution de charge et tests de débit
Vous devez vous disponible un environnement correspondant à votre environnement de production pour des performances et de test de stress. Cet environnement doit avoir tous les services standards installé et en cours d’exécution, comme la surveillance des agents et le logiciel antivirus.  
  
## <a name="how-adding-applications-affects-load"></a>Comment ajouter des Applications affecte la charge  
 Vous devez également tester les nouvelles applications BizTalk en même temps que les autres applications BizTalk qui s’exécutent sur le même matériel de production. C’est parce que les nouvelles applications BizTalk placer une charge supplémentaire sur les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server. Cela est particulièrement important de point de vue de l’hôte de la limitation des algorithmes qui sont utilisés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L’algorithme de limitation contrôle total des ressources disponibles et par conséquent, la charge supplémentaire induite par une application BizTalk peut induire une condition de limitation qui affecte toutes les applications en cours d’exécution de BizTalk. Pour plus d’informations, consultez [comment BizTalk Server implémente la limitation des hôtes](http://go.microsoft.com/fwlink/?LinkId=154389) (http://go.microsoft.com/fwlink/?LinkId=154389).  
  
## <a name="testing-load-and-determining-recovery-time"></a>Test de charge et la détermination des temps de récupération  
 Vous devez tester toutes les applications BizTalk pour les performances et de contrainte avant de les placer en production. Vous devez effectuer vos tests sur la charge attendue et pics de charge. Vous devez déterminer le débit maximal acceptable (MST) de l’application BizTalk. En outre, vous devez déterminer le temps pris par le système pour récupérer des pics de charge. Si le système ne récupère pas entièrement à partir d’une charge de pointe avant le pic suivant charge se produit, puis le système recevront progressivement situés et ne sera pas en mesure de récupérer entièrement. Pour plus d'informations, consultez :  
  
-   [Mesurer le débit de moteur maximal acceptable](http://go.microsoft.com/fwlink/?LinkId=154388) (http://go.microsoft.com/fwlink/?LinkId=154388)  
  
-   [Mesurer le débit de suivi maximal acceptable](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815)  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Test opérationnelle](../technical-guides/checklist-testing-operational-readiness.md)