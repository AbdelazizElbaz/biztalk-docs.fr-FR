---
title: "Conception des Architectures système pour BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, security
- security, deploying
ms.assetid: b7ded72a-2487-4bb7-9894-cd13235a52c7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a18656a2d4d3827cd38a3f791af2ac856df8ce36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-the-system-architectures-for-biztalk-server"></a>Conception des architectures système pour BizTalk Server
Les impératifs de votre déploiement Microsoft® BizTalk® Server en matière de sécurité, de performances, de disponibilité et d'opérabilité dépendent fortement de diverses caractéristiques de votre entreprise (besoins, exigences, partenaires, taille, etc.). Il est difficile de considérer une configuration des composants BizTalk Server comme typique et de fournir des directives la concernant. Cette section contient toutefois des instructions et recommandations relatives au paramétrage des différentes fonctionnalités de BizTalk Server dans le cadre d'une configuration sécurisée et distribuée pour l'environnement de production d'une grande entreprise.  
  
 Les architectures présentées dans cette section visent à fournir des informations de référence sur le déploiement de BizTalk Server dans un environnement hautement distribué qui prend en compte la sécurité. Chaque application de BizTalk Server est susceptible d’avoir son propre ensemble unique d’exigences de sécurité basé sur le domaine du problème, les protocoles utilisés, et l’environnement particulier de la solution fonctionne dans. Performances, disponibilité et considérations relatives aux coûts peuvent influencer ces impératifs. Vous devez utiliser ces architectures et les recommandations de ce document comme blocs de construction pour créer votre propre déploiement de BizTalk Server adapté aux besoins et ressources de votre entreprise, ainsi qu'aux menaces auxquelles elle est confrontée.  
  
 Cette section contient des informations sur la conception de l'architecture du système pour BizTalk Server afin de sécuriser les différentes fonctionnalités de BizTalk Server et, par conséquent, les données traitées et stockées par les serveurs. Elle inclut également des informations sur le placement des serveurs dans un environnement distribué afin de réduire le risque de compromission des données et serveurs critiques en cas d'attaque ou de sinistre. Cette section ne fournit pas de recommandations sur la configuration du développement, ou des environnements de test, ou encore des détails sur le déploiement d'un assembly dans un environnement de production. Pour plus d’informations sur le déploiement des assemblys, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md)  
  
-   [Conception d’une Architecture distribuée](../core/designing-a-distributed-architecture.md)  
  
-   [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)