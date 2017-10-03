---
title: Diagramme physique | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deploying, network configuration
ms.assetid: 4291727b-8687-496a-8f03-0da4b3201967
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fcd0558d8fe3d45063a53800b1f3c082a2ba056
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="physical-diagram"></a>Diagramme physique
Un déploiement classique a mis en cluster des ordinateurs BizTalk Server pour la messagerie (envoi et réception), les ordinateurs pour exécuter le processus d’entreprise (orchestration), les ordinateurs BizTalk Server pour les modèles InfoPath (site MRSR), de l’accès à BizTalk Server et ordinateurs SQL Server en cluster. Le déploiement suivant permet de garantir un environnement sécurisé à partir de l’intranet et les utilisateurs sur Internet.  
  
> [!NOTE]
>  Ce déploiement typique est la configuration recommandée. Vous devez vérifier vos propres besoins et les configurations de serveur pour vous assurer que votre déploiement fonctionne correctement.  
  
 Vous pouvez faire évoluer ce déploiement vers le haut ou vers le bas, out ou, selon le profil d’utilisation et des besoins commerciaux croissants. Les scénarios d’évolutivité classiques comprennent l’ajout d’un ou plusieurs serveurs dans chaque cluster afin de garantir une disponibilité élevée ou un meilleur débit. Petites entreprises préférerez peut-être opter pour réduire la puissance leur déploiement pour que les mêmes serveurs exécuter plusieurs fonctions, telles qu’avoir une [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ordinateur gérer l’orchestration et messagerie. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]prend en charge le déploiement sur un seul serveur. L’illustration suivante montre un exemple de l’environnement de déploiement distribué recommandée pour un déploiement complet de A4SWIFT.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-deploy-full.gif "FSA_Deploy_Full")  
Exemple de déploiement complet A4SWIFT