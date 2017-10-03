---
title: "À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2 | Documents Microsoft"
ms.custom: 
ms.date: 2016-01-04
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Passive configuration [Master Secret server]
- Active configuration [Master Secret server]
- clustering, about clustering
- high availability
- Windows Server cluster, warnings
- installation, high availibility planning
- Master Secret server
- installation, configuring
- Master Secret server, configuring
- installation, Windows Server cluster
- clustering
ms.assetid: 4d7f0842-561e-49e0-ab08-504256b9294f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 338f9fd39208f85ce5748f5ebe5548fa9487c9df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-windows-server-cluster-to-provide-high-availability-for-biztalk-server-hosts2"></a>À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit des fonctionnalités qui vous permet de configurer un hôte BizTalk en tant que ressource en cluster dans un groupe de clusters de basculement Windows Server. La prise en charge de la mise en cluster d'hôtes permet de doter en haute disponibilité des adaptateurs BizTalk intégrés qu'il est impossible d'exécuter simultanément sur plusieurs instances de l'hôte. Il s'agit d'adaptateurs, tels que le gestionnaire de réception FTP ou, dans certaines conditions, le gestionnaire de réception POP3. Cette prise en charge garantit également la cohérence transactionnelle des messages envoyés ou reçus via l'adaptateur MSMQ dans des scénarios exigeant une mise en cluster du service MSMQ.  
  
> [!NOTE]
>  La mise en cluster d'hôtes n'est disponible qu'avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Entreprise.  
  
> [!NOTE]
>  Avant de mettre en cluster un hôte BizTalk, vous devez configurer au moins deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe en tant que membres d’un cluster de basculement Windows Server. Pour plus d’informations sur la configuration d’un cluster de basculement Windows Server, consultez l’aide en ligne de Windows Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations sur l’installation de BizTalk Server sur un Cluster Windows Server](../core/considerations-for-installing-biztalk-server-on-a-windows-server-cluster2.md)  
  
-   [Comment configurer un hôte BizTalk en tant que ressource de Cluster](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md)  
  
-   [Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)