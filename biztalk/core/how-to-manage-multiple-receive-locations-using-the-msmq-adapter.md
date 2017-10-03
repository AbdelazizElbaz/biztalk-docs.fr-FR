---
title: "Pour gérer plusieurs emplacements à l’aide de l’adaptateur MSMQ de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, threads
- receive locations, multiple
- threads
- receive locations, MSMQ adapters
- receive locations, threads
- configuring [MSMQ adapters], receive locations
ms.assetid: 5b2ee043-bcc9-443b-84b0-df7f487159eb
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72438551d2ecab09b918808d43e7d7de6d600677
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-multiple-receive-locations-using-the-msmq-adapter"></a>Gestion de plusieurs emplacements de réception à l'aide de l'adaptateur MSMQ
Afin améliorer les performances, l'adaptateur MSMQ est du type multithread. Si vous disposez de plusieurs emplacements de réception, il risque de ne pas y avoir suffisamment de threads disponibles pour chacun d'entre eux. Cette restriction empêche ainsi certains emplacements de réception de récupérer des messages. Il existe trois méthodes permettant de résoudre ce problème :  
  
-   ajouter des hôtes BizTalk à vos ordinateurs et répartir les emplacements de réception parmi les hôtes. L'ajout d'hôtes augmente le nombre de threads disponibles pour les emplacements de réception ;  
  
-   Définir le **traitement en série** propriété `True` sur chaque emplacement de réception. La propriété `True` attribue un seul thread à chaque emplacement de réception. Ainsi, davantage de threads sont disponibles dans le pool. Toutefois, cela risque d'entraîner la réduction des performances ;  
  
-   modifier le Registre de manière à augmenter le nombre de threads accessibles à l'hôte pour le gestionnaire de réception de l'adaptateur MSMQ. Pour plus d’informations, consultez la **modifier les valeurs de thread CLR Hosting de l’hôte** section de [les paramètres de Configuration qui affectent les performances carte](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)