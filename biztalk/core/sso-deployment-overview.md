---
title: "Vue d’ensemble du déploiement de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, deploying example
- SSO, deploying
- deploying, SSO
- SSO, multiple computers
- examples, deploying
ms.assetid: 6eccee26-c392-41fe-97fb-3afe1685540f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f88afb52f1db1263112732e70befb2ab95e6b135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-deployment-overview"></a>Vue d’ensemble du déploiement de l’authentification unique
Dans cet exemple, le système est déployé sur trois domaines, lesquels contiennent les ordinateurs suivants :  
  
 **Domaine ORCH.com**  
  
-   Contrôleur de domaine ORCH  
  
-   HIS1, le serveur HISSO  
  
-   HIS2, le serveur de secret principal  
  
-   HIS3, la base de données d'administration  
  
 **Domaine SQL.com**  
  
-   Contrôleur de domaine SQL  
  
-   SQL2, la base de données SSO  
  
 **Domaine HIS.com**  
  
-   Contrôleur de domaine HIS  
  
-   Base de données HIS4  
  
 Les points clés qui définissent ce déploiement sont les suivants :  
  
-   Les domaines ORCH.com et SQL.com entretiennent une relation d'approbation sélective bidirectionnelle.  
  
-   Le domaine ORCH.com est configuré en tant que niveau fonctionnel [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] natif.  
  
-   Tous les services SSO sont exécutés sous un compte d'utilisateur du domaine ORCH.com (Orch\SSOSvcUser). L'utilisateur dispose des autorisations d'accès à l'ordinateur SQL2 du domaine SQL.com. La transition de protocole et la délégation contrainte sont également configurées pour l'utilisateur au sein du domaine ORCH.com.  
  
-   Un autre utilisateur du domaine ORCH.com (Orch\TestAppUser) est configuré pour exécuter des programmes de test. La transition de protocole et la délégation contrainte sont également configurées pour cet utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus de déploiement](../core/deployment-process.md)