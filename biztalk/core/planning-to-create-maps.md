---
title: Planification de la création de mappages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, planning
ms.assetid: e86af976-b989-4e24-80d5-3a9a3ac4e443
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72dde6b09b7777204547d00d26af571c9998d73f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-to-create-maps"></a>Planification de la création des mappages
Vous utilisez des mappages pour convertir des messages entrants conformes à un schéma en messages de sortie conformes à un schéma différent. Ces conversions peuvent être simples ou relativement complexes, impliquant des calculs et la consolidation des informations.  
  
 Le tableau suivant répertorie certaines questions auxquelles vous devez répondre lorsque vous envisagez de créer des mappages.  
  
|Question relative à la planification|Recommandation|  
|-----------------------|--------------------|  
|Quels mappages dois-je créer ?|Dressez la liste des documents commerciaux que vous allez traiter avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Votre liste peut contenir des documents tels qu'un bon de commande, une facture, une confirmation d'expédition, etc. Elle pourra également inclure plusieurs exemplaires de chaque document commercial, par exemple, si la structure d'un bon de commande reçu d'un partenaire commercial est différente de celle d'un bon de commande reçu d'un autre partenaire commercial.<br /><br /> Parcourez la liste et décidez quels documents doivent être dans un format différent ou quels documents sont mieux traités par conversion dans un format commun.|  
|Où ai-je besoin de mappages ?|Vous pouvez utiliser des mappages dans des ports d’envoi, des ports de réception et des orchestrations représentant des processus d'entreprise. Réfléchissez aux endroits où vous voulez ou devez convertir des documents.|  
|Ai-je d’anciens mappages à convertir ?|Les mappages créés dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 devraient migrer sans modification. Consacrez suffisamment de temps au test des mappages migrés. Toutefois, les mappages créés dans les versions antérieures de BizTalk ouvriront ne peut-être pas dans BizTalk Server. **Remarque :** les mappages créés dans les versions antérieures à [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] fonctionneront peut-être correctement dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009. Toutefois, les mappages peuvent ne pas s’ouvrir dans BizTalk Server. <br /><br /> Mappages contenant **script** fonctoids ou des fonctoids personnalisés peuvent requérir des tâches supplémentaires. Pour plus d’informations, consultez [migration des fonctoids](../core/migrating-functoids.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des mappages](../core/about-maps.md)   
 [Migration des fonctoids](../core/migrating-functoids.md)