---
title: "Surveillance des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fee5015-e818-459b-aeeb-a084ef355600
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fed740f0c2689c8c531a2f92ad4be356d82205db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-biztalk-server-databases"></a>Surveillance des bases de données BizTalk Server
Vous pouvez exécuter la tâche d’analyse BizTalk Server, SQL Agent pour identifier les problèmes connus dans les bases de données de gestion, MessageBox ou DTA. La fonction est créée lorsque vous configurez un groupe BizTalk dans la console Administration de BizTalk Server ou procédez à une mise à niveau de BizTalk à partir d'une version antérieure.  
  
## <a name="the-monitor-biztalk-server-job"></a>Le travail de surveillance de BizTalk Server  
 La fonction Analyser BizTalk Server recherche les problèmes suivants dans les bases de données Gestion, MessageBox ou DTA :  
  
> [!NOTE]  
>  La fonction Analyser BizTalk Server recherche uniquement d'éventuels problèmes. Elle ne corrige pas les problèmes trouvés.  
  
-   Messages sans références  
  
-   Messages sans nombres de références  
  
-   Messages avec un nombre de références inférieur à 0  
  
-   Références de messages sans lignes de mise en file d'attente  
  
-   Références de messages sans instances  
  
-   État d'instance sans instances  
  
-   Abonnements d'instance sans instances correspondantes  
  
-   Instances de service DTA orphelines  
  
-   Exceptions d'instances de service DTA orphelines  
  
-   Le service TDDS n’est pas exécuté sur n’importe quelle instance d’hôte lorsque l’option de suivi global est activée.  
  
 La fonction Analyser BizTalk Server est configurée et automatisée pour s'exécuter une fois par semaine. Étant donné que le travail est nécessitant, il est recommandé que vous planifiez son exécution pendant les périodes de temps d’arrêt ou de faible trafic.  
La tâche échoue si elle rencontre des problèmes ; la chaîne d’erreur contient le nombre de problèmes rencontrés. Sinon, elle réussit. Vous pouvez voir les détails dans l'historique de la fonction. Si vous exécutez la tâche avec des privilèges d’administrateur, la chaîne d’erreur est consignée dans l’historique des travaux et le journal d’Application SQL Server.  
  
> [!IMPORTANT]  
>  Échec de ce travail ne constitue pas nécessairement un problème critique, mais plutôt d’un problème qui doit être examiné et traité en tant que partie de la maintenance régulière des bases de données BizTalk Server. Cette tâche échoue à la conception dans l’événement qu’il détecte un des problèmes répertoriés ci-dessus.