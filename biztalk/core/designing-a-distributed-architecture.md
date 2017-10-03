---
title: "Conception d’une Architecture distribuée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- SQL Server, clustering
ms.assetid: 8a8f1710-4d53-42bf-b5e5-2be3b43813b4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 156c7107abfd0fd140a5e7b07f06d00eabf7c961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-a-distributed-architecture"></a>Conception d'une architecture distribuée
Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 L’architecture présentée dans la rubrique [grand Distributed Architecture](../core/large-distributed-architecture.md) résout de nombreux des menaces de sécurité à laquelle un environnement BizTalk est vulnérable. Si la sécurité doit être l'une de vos priorités lors de la conception de votre architecture, d'autres considérations doivent être prises en compte dans un environnement distribué (haute disponibilité, évolutivité et performances). Cette section décrit les autres options envisageables lors de la conception de votre architecture [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="domains"></a>Domaines  
 Si votre entreprise utilise principalement des communications Internet, vous pouvez supprimer les services intranet du domaine d'entreprise. Inversement, si vous utilisez BizTalk Server pour vous connecter aux autres applications ou partenaires commerciaux connectés via l'intranet, vous pouvez supprimer le réseau de périmètre. Si votre entreprise utilise Internet et intranet orientées communication avec un petit nombre de partenaires, vous pouvez envisager de combiner les services intranet et le réseau de périmètre.  
  
 Si vous souhaitez minimiser la latence de la communication entre les serveurs de traitement et les serveurs SQL Server dans le domaine de données (les problèmes de sécurité tels que le reniflage de réseau, la falsification de paquets et l'usurpation d'hôte dans le réseau interne ne se posant pas par ailleurs), vous pouvez supprimer le pare-feu entre les domaines de traitement et de données, puis fusionner ces domaines. Il est recommandé d'utiliser par la suite le protocole IPSec (Internet Protocol security) ou SSL (Secure Sockets Layer) pour protéger les données transférées d'un serveur à un autre.  
  
## <a name="sql-server-clustering"></a>Clustering SQL Server  
 Bien que cette section n'aborde pas cet aspect de façon détaillée, il est fortement recommandé de mettre en cluster vos bases de données pour bénéficier de la protection par basculement. Pour plus d’informations sur le clustering de basculement SQL Server 2008, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016).  
  
## <a name="messagebox-database"></a>Base de données MessageBox  
 Selon les besoins de votre entreprise en termes de débit des messages, vous pouvez ajouter ou supprimer des bases de données MessageBox. Pour plus d’informations sur la messagebox multiples, consultez [Scaled-Out de bases de données](../core/scaled-out-databases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md)   
 [Planification de la haute disponibilité](../core/planning-for-high-availability3.md)   
 [Planification des performances soutenues](../core/planning-for-sustained-performance.md)   
 [Conception des Architectures système pour BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)