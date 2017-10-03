---
title: "Optimisation de l’utilisation des ressources via la limitation des hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host throttling
- performance, host throttling
ms.assetid: 823b431d-707d-4201-9a6e-4a879e767b66
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa30cb66371ef519741658dec47e08f6f92e871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-resource-usage-through-host-throttling"></a>Optimisation de l'utilisation des ressources par l'intermédiaire de la limitation des hôtes
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise plusieurs technologies Microsoft, chacun d’eux peut consommer une partie significative de la mémoire, disque et les ressources processeur disponibles sur le serveur BizTalk server et le serveur SQL qui contient les bases de données BizTalk Server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise un mécanisme de limitation pour aider à gérer l’utilisation des ressources disponibles pour limiter la contention d’utilisation de ressources. Cette rubrique explique comment ce mécanisme est conçu. Pour plus d’informations sur la façon d’ajuster les valeurs de limitation, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Ce qui est la limitation des hôtes ?](../core/what-is-host-throttling.md)  
  
-   [Comment BizTalk Server implémente la limitation de l’hôte](../core/how-biztalk-server-implements-host-throttling.md)  
  
-   [Limitation des compteurs de performances de l’hôte](../core/host-throttling-performance-counters.md)  
  
-   [Limitation des recommandations sur la conception](../core/throttling-design-recommendations.md)