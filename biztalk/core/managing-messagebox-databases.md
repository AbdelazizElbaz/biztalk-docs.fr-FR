---
title: "Gestion des bases de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [MessageBox database], about managing MessageBox database
- managing [MessageBox database]
- MessageBox database, managing
ms.assetid: 9675b5d5-7a69-468d-be42-34a72cd6e5c2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e854ad0f7014de8241f8a7b6af6addd49cb4da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-messagebox-databases"></a>Gestion des bases de données MessageBox
La base de données MessageBox permet d'effectuer trois fonctions essentielles. Elle stocke les abonnements et les informations de suivi et envoie les messages aux services correspondant aux abonnements. C'est une plateforme hôte qui stocke les files d'attente et les tables d'état de chaque hôte BizTalk. Elle stocke également les messages et leurs propriétés.  
  
 Si les bases de données MessageBox sont très exposées aux risques dans votre environnement, nous vous recommandons d'utiliser la sécurité du protocole Internet (IPSec) ou SSL (Secure Sockets Layer) pour limiter et sécuriser la communication avec les bases de données MessageBox.  
  
 Si vous utilisez Windows Server 2003, vous devez activer le coordinateur de transactions distribuées (DTC) sur la base de données MessageBox. Vous devez également activer les clients réseau dans le cas de déploiements sur plusieurs ordinateurs. Pour plus d’informations, consultez [Ports pour le serveur d’Administration](../core/ports-for-the-administration-server.md).  
  
 Cette section contient des procédures de gestion des bases de données MessageBox dans votre environnement. Pour plus d’informations conceptuelles sur les bases de données MessageBox et l’abonnement modèle Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour traiter les messages, consultez [la base de données MessageBox](../core/the-messagebox-database.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment ajouter une nouvelle base de données MessageBox](../core/how-to-add-a-new-messagebox-database.md)  
  
-   [Comment désactiver la Publication des nouveaux messages](../core/how-to-disable-new-message-publication.md)  
  
-   [Comment supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md)