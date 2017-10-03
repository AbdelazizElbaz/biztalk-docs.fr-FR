---
title: "Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, Windows groups
- authenticating, best practices
- Windows groups, security
- best practices, user accounts
- best practices, security
- security, best practices
- user accounts, security
- authenticating, security
- Windows groups, best practices
- best practices, authenticating
- user accounts, best practices
- hosts, security
- hosts, best practices
- best practices, hosts
ms.assetid: 0c4a141e-97ce-434a-8e45-a56c634bbd6c
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f7560e3867bf290f20e0f2f49a740d7298131b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-managing-windows-groups-and-user-accounts"></a>Méthodes conseillées pour la gestion des groupes et comptes d'utilisateur Windows
Cette section présente les meilleures pratiques relatives à la gestion de la sécurité dans les groupes et les comptes d'utilisateur Windows.  
  
-   **Utiliser des comptes de service avec des privilèges minimaux requis pour les instances d’hôte**  
  
     Pour garantir la sécurité de votre environnement BizTalk Server, il est recommandé d'utiliser les comptes de service avec les privilèges minimaux requis pour l'exécution des instances d'hôte. Pour plus d’informations sur les privilèges minimaux qui requièrent des comptes de service, consultez [contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md).  
  
-   **Utilisez différents groupes d’utilisateurs pour l’authentification de la confiance et les hôtes non approuvés**  
  
     Pour vérifier que les hôtes non approuvés par authentification bénéficient de moins de privilèges que les hôtes approuvés par authentification, vous devez utiliser des comptes de service différents pour chaque hôte.  
  
-   **Utiliser un groupe d’utilisateurs différents pour chaque hôte BizTalk**  
  
     Pour maximiser la limite de sécurité entre les hôtes, il est recommandé d'utiliser différents groupes d'utilisateurs Windows pour chaque hôte BizTalk de votre groupe BizTalk.  
  
-   **Supprimer l’utilisateur de l’installation à partir du groupe Administrateurs de BizTalk Server**  
  
     Lorsque vous installez BizTalk Server sur un seul serveur avec des groupes locaux, l'utilisateur effectuant une installation interactive de BizTalk Server est automatiquement ajouté au groupe Administrateurs BizTalk Server. De cette manière, l'utilisateur peut configurer BizTalk Server avec le Gestionnaire de configuration.  
  
     Si l'utilisateur qui installe le serveur BizTalk Server n'est pas l'administrateur de ce dernier, il est recommandé de le supprimer du groupe Administrateurs BizTalk Server une fois le serveur BizTalk Server configuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)