---
title: "Haute disponibilité de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, MQSeries adapters
- MQSeries adapters, availability
- MQSeries adapters, performance
- high availability, MQSeries adapters
ms.assetid: 4339b10b-b35d-47c0-b78a-c60207e06c8e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c0b6486e49cb2ccddfab37271a94a4ba7a6948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-high-availability"></a>Haute disponibilité de l’adaptateur MQSeries
Lors de l'utilisation de l'adaptateur, vous pouvez améliorer la disponibilité par l'intermédiaire des méthodes suivantes :  
  
-   Configuration d'un environnement d'hébergement à tolérance de pannes pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Utilisation du clustering Windows avec IBM WebSphere MQ.  
  
 Pour plus d’informations sur la tolérance de panne et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md) et [plateforme de votre planification pour la tolérance de panne](../core/planning-your-platform-for-fault-tolerance.md) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Pour garantir le fonctionnement des communications entre l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une installation distante du composant MQSAgent, assurez-vous que l'accès COM+ réseau a été activé sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et sur le serveur hébergeant IBM WebSphere MQ. Pour plus d’informations sur l’activation de l’accès COM + réseau, consultez la Base de connaissances Microsoft l’article 817065, « Comment activer l’accès COM + réseau dans Windows Server 2003 » disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=196580](http://go.microsoft.com/fwlink/?LinkId=196580).  
  
 Aucune condition requise n'est exigée pour mettre en cluster l'application MQSAgent (MQSAgent2) COM+ utilisée avec l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour que ce composant bénéficie de la haute disponibilité, installez-le sur chaque nœud du cluster. Si l'application COM+ s'arrête, le prochain appel en provenance du client la démarrera.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)