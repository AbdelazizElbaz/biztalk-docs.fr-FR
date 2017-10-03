---
title: "Comment créer un groupe de Cluster avec un disque, adresse IP et nommez Resource1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b361f721-60db-485e-9ce3-48a6871ebd79
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63310706742ffcc10de5266dda7053da79fc04fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource"></a>Création d'un groupe de clusters avec un disque, une adresse IP et une ressource de nom
Pour cluster [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] composants et dépendances doit être accessible sur le réseau via NetBIOS, un cluster **nom réseau** ressource doit être créée dans le même groupe de clusters. Pour une ressource de nom de réseau en cluster doit être accessible via le protocole TCP/IP, une **adresse IP** ressource doit être créée dans le même groupe cluster. Certains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dépendances requièrent également l’utilisation d’un cluster **disque physique** ressource pour fonctionner correctement. Pour créer un groupe de clusters avec un **disque physique**, **adresse IP** et **nom réseau** ressource procédez comme suit :  
  
### <a name="to-create-a-service-or-application-with-a-physical-disk-ip-address-and-network-name-resource"></a>Pour créer un service ou une application avec des ressources Disque physique, Adresse IP et Nom de réseau  
  
1.  Dans Windows, cliquez sur **Démarrer**, **programmes**, **outils d’administration**, puis **gestion du Cluster de basculement** pour démarrer le basculement Programme de gestion de cluster.  
  
2.  Basculez l'ensemble des services et applications sur le nœud de cluster sur lequel vous exécutez l'application Gestion du cluster de basculement. Pour basculer d’un service ou une application, avec le bouton droit sur le service ou l’application dans le volet gauche de la gestion du Cluster de basculement, pointez sur **déplacer ce service ou cette application vers un autre nœud** et sélectionnez le nœud de destination.  
  
    > [!NOTE]
    >  Le nœud de cluster qui héberge les ressources de cluster en cours d’exécution est également connu sous le **active** nœud. Le nœud de cluster qui héberge les ressources de cluster de non-en cours d’exécution est également connu sous le **passif** nœud.  
  
3.  Dans le volet gauche, cliquez sur **Services et Applications**, cliquez sur **configurer un Service ou une Application** pour lancer l’Assistant haute disponibilité, puis cliquez sur **suivant**.  
  
4.  Cliquez pour sélectionner **serveur de fichiers** et cliquez sur **suivant**.  
  
    > [!NOTE]
    >  En sélectionnant **serveur de fichiers** à ce stade s’agit d’un moyen simple de créer un groupe de cluster avec une ressource de disque.  
  
5.  Sur le **Point d’accès Client** page de l’Assistant haute disponibilité permet d’entrer un nom de réseau unique dans le **nom** zone, par exemple *Clusterbiztalk*, entrez une adresse IP disponible adresse sous **adresse**, puis cliquez sur **suivant**.  
  
6.  Sur le **sélectionner le stockage** page, cliquez pour sélectionner une ressource de disque disponible, puis cliquez sur **suivant**.  
  
7.  Sur le **Confirmation** page, cliquez sur **suivant** pour créer le groupe de clusters.  
  
8.  Sur le **Résumé** page, cliquez sur **Terminer**.