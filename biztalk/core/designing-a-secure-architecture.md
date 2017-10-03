---
title: "Conception d’une Architecture sécurisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls
- architecture, security
- installation, firewalls
- installation, security
ms.assetid: 93df6a3f-396c-4767-99c8-2145bddf8fdf
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 157c11477efb9dec455e9ac2de81736cd4ea72ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-a-secure-architecture"></a>Conception d'une architecture sécurisée
Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 L’architecture présentée dans la rubrique [grand Distributed Architecture](../core/large-distributed-architecture.md) résout de nombreux des menaces de sécurité à laquelle un environnement BizTalk est vulnérable. Pour déterminer l'architecture adaptée à votre situation, vous devez évaluer les actifs de votre entreprise, les menaces auxquelles elle est confrontée et les ressources disponibles pour protéger vos actifs et réduire les menaces potentielles. Cette section décrit les autres options de sécurité envisageables lors de la conception de votre architecture [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="firewalls"></a>Pare-feux  
 Vous pouvez utiliser des pare-feu physiques (matériels) ou logiciels pour restreindre l'accès aux ressources de votre environnement. Lors de la rubrique [grand Distributed Architecture](../core/large-distributed-architecture.md) utilise Forefront Threat Management Gateway (TMG) 2010 server, vous pouvez créer une architecture similaire à l’aide de matériel ou des pare-feu logiciel tiers, tant que vous ouvrez et configurer les ports requis pour la communication entre les différents composants de BizTalk Server. Pour plus d’informations sur les ports utilisés par BizTalk Server, consultez [les Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md).  
  
## <a name="active-directory"></a>Active Directory  
 Dans l'exemple de déploiement, le service d'annuaire Active Directory® permet de créer une limite de sécurité en dur autour de chaque groupe de serveurs. Les approbations unidirectionnelles permettent de renforcer la protection de l'environnement BizTalk Server face aux attaques liées aux défauts d'autres applications non-BizTalk Server exécutées sur les serveurs de traitement, tandis que les applications BizTalk Server sont exécutées sous des comptes créés dans le domaine de données. Comme le domaine de données n'approuve pas les comptes dans les autres domaines, la compromission d'un compte dans un autre domaine n'affecte pas l'environnement BizTalk Server.  
  
## <a name="ipsec-and-ssl"></a>IPSec et SSL  
 Si votre environnement n'est pas affecté par les menaces critiques nécessitant le niveau de sécurité fourni par les pare-feu, mais que les segments de réseau qui connectent les domaines de données, de traitement et de services ne sont pas sécurisés physiquement contre les attaques réseau (par exemple, détection ou falsification des paquets), vous devez protéger les données tandis que celles-ci sont transmises entre des serveurs. Dans ce cas, vous pouvez utiliser le protocole IPSec (Internet Protocol security) ou SSL (Secure Sockets Layer) pour chiffrer le trafic entre les serveurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’une Architecture distribuée](../core/designing-a-distributed-architecture.md)   
 [Planification de la sécurité](../core/planning-for-security.md)   
 [Conception des Architectures système pour BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)