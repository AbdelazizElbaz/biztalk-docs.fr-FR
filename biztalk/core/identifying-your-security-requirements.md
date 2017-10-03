---
title: "Identifier vos exigences de sécurité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, configuring
- planning, security
- security, planning
ms.assetid: 5a12c959-59b5-4d44-b2f4-e1ed7053ffd5
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea9b21cfdfe722d80779dcf9098355b9a5ae3727
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-your-security-requirements"></a>Identifier vos exigences de sécurité
Les réponses aux questions suivantes vous permettent de planifier la meilleure façon de déployer BizTalk Server dans votre environnement.  
  
|Question|Recommandation|  
|--------------|--------------------|  
|Quelle est la méthode conseillée pour déployer BizTalk Server au sein d'un environnement sécurisé ?|La réponse à cette question dépend en grande partie des besoins spécifiques à votre environnement, des ressources de votre entreprise, du niveau de vulnérabilité de ces ressources aux menaces potentielles et la manière dont vous souhaitez protéger celles-ci. Il est important de réaliser une analyse du modèle des menaces pour identifier les principales ressources à protéger.<br /><br /> [Architecture distribuée de grand](../core/large-distributed-architecture.md) fournit des recommandations pour sécuriser votre environnement BizTalk Server. Après avoir mis au point le modèle des menaces, exploitez les informations de cette section pour concevoir votre propre déploiement sécurisé de BizTalk Server.|  
|Envisagez-vous d'utiliser l'analyse BAM (Business Activity Monitoring) ?|L'analyse BAM nécessite que les utilisateurs présents dans le réseau d'entreprise accèdent aux ressources BizTalk Server. Si vous utilisez cette fonctionnalité, vous devez prendre en compte certaines recommandations ayant trait à la sécurité lorsque vous créez votre déploiement BizTalk Server. Pour plus d’informations, consultez [grande Architecture distribuée avec les Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md).|  
|Quelle est la meilleure façon de sécuriser les fonctionnalités BizTalk Server que vous envisager d'utiliser ?|Pour obtenir des recommandations générales sur la sécurisation d’un environnement BizTalk Server, consultez [recommandations de sécurité pour un déploiement de BizTalk Server](../core/security-recommendations-for-a-biztalk-server-deployment.md).<br /><br /> Pour des recommandations sur la sécurisation des différentes fonctionnalités BizTalk Server, consultez la rubrique ayant trait à la sécurité pour cette fonctionnalité.|  
|Quelles sont les menaces potentielles auxquelles est exposé un environnement BizTalk ?|Pour plus d’informations, consultez [identifier les menaces potentielles](../core/identifying-potential-threats.md).|  
|Quelles sont les menaces potentielles à une implémentation de BizTalk Server et comment les atténuer ?|Pour identifier les menaces potentielles planant sur votre environnement et la manière d'atténuer les risques, il est recommandé de mener à bien une analyse du modèle des menaces. Pour plus d’informations sur la modélisation des menaces, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=25224](http://go.microsoft.com/fwlink/?LinkId=25224).|  
|Comment protéger un environnement des attaques par déni de service ?|Une attaque par déni de service constitue l'une des menaces les plus dangereuses que vous devez empêcher. Bien que vous ne puissiez pas protéger entièrement votre environnement de manière à éviter ces menaces, les éléments suivants vous permettront d'atténuer leur impact sur celui-ci. Pour plus d’informations, consultez [atténuation des attaques par déni de Service](../core/mitigating-denial-of-service-attacks.md).|  
|Quels sont les ports à ouvrir sur les pare-feu pour les services BizTalk ?|Pour plus d’informations, consultez [les Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md).|  
|Quels comptes utiliser avec un déploiement BizTalk Server distribué ?|Les comptes spécifiques que vous utilisez dans votre environnement dépendent des services auxquels vous faites appel. Toutefois, il est recommandé d'utiliser différents groupes et comptes pour différents services. Pour plus d’informations, consultez [des comptes Windows pour un Secure Distributed déploiement de BizTalk Server](../core/windows-accounts-for-a-secure-distributed-biztalk-server-deployment.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la sécurité](../core/planning-for-security.md)   
 [Recommandations de sécurité pour un déploiement BizTalk Server](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [Identifier les menaces potentielles](../core/identifying-potential-threats.md)   
 [Limitation des attaques de déni de Service des attaques par](../core/mitigating-denial-of-service-attacks.md)