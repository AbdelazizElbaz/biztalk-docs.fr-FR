---
title: "Gestion de la sécurité de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- security, user accounts
- security, passwords
- certificates, security
- security, certificates
- security, BizTalk Server
- passwords, security
- user accounts, security
ms.assetid: adc89b0a-9846-4c99-b0fc-a32fc56ed769
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f31ef3483661b20ff62cadb0ec601282a05af9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-server-security"></a>Gestion de la sécurité de BizTalk Server
Pour bénéficier d'un environnement Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sécurisé, vous devez gérer des comptes, des certificats et des mots de passe. Pour garantir la sécurité des documents commerciaux traités par BizTalk Server, les administrateurs BizTalk Server gèrent les comptes et certificats suivants :  
  
-   **Groupe Administrateurs BizTalk Server**. Les utilisateurs qui exécutent des tâches d'administration via la console Administration de BizTalk ou le fournisseur Microsoft Windows Management Instrumentation (WMI) doivent bénéficier des autorisations appropriées dans Microsoft SQL Server et Microsoft Windows. Pour plus d’informations sur les privilèges pour les tâches administratives, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).  
  
     Pour plus d’informations sur l’ajout d’utilisateurs au groupe Administrateurs de BizTalk Server ou la suppression des utilisateurs du groupe Administrateurs de BizTalk Server, consultez [comment gérer le groupe d’administrateurs BizTalk Server](../core/how-to-manage-the-biztalk-server-administrators-group.md).  
  
     Pour plus d’informations sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
-   **Groupe opérateurs BizTalk Server**. Le rôle Opérateurs BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.  
  
     Les membres du groupe Opérateurs BizTalk Server peuvent effectuer les tâches suivantes :  
  
    -   Afficher l'état et le flux de messages du service.  
  
    -   Démarrer ou arrêter des applications.  
  
    -   Démarrer ou arrêter des orchestrations.  
  
    -   Arrêter ou démarrer des ports d'envoi et des groupes de ports d'envoi.  
  
    -   Activer ou désactiver des emplacements de réception. Les modifications ne sont pas prises en compte avant la fin de l'intervalle d'actualisation du cache de 60 secondes (intervalle par défaut). Cet intervalle est défini au niveau du groupe BizTalk Server.  
  
    -   Terminer et reprendre les instances de service.  
  
     Les membres du groupe Opérateurs BizTalk Server ne peuvent pas effectuer les tâches suivantes :  
  
    -   Modifier la configuration de BizTalk Server.  
  
    -   Afficher les propriétés de contexte de message marquées comme informations d'identification personnelle ou les corps de message.  
  
    -   Modifier le routage des messages, par exemple supprimer ou ajouter des abonnements au système en cours d'exécution, ou publier des messages dans un composant d'exécution BizTalk Server.  
  
    > [!NOTE]
    >  Un utilisateur membre du groupe Opérateurs BizTalk Server et administrateur local sur les ordinateurs exécutant BizTalk Server peut accéder aux données présentes sur ceux-ci et non disponibles aux membres du groupe Opérateurs. Pour plus d’informations, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).  
  
    > [!NOTE]
    >  Si vous souhaitez autoriser un utilisateur membre du groupe Opérateurs BizTalk Server à surveiller des serveurs BizTalk distants, cet utilisateur doit également être membre du groupe Administrateurs local sur les ordinateurs distants.  
  
-   **Les comptes de service et les hôtes**. Lors de la création d'un hôte et des instances d'hôte associées, vous devez fournir au groupe Windows les informations d'identification des comptes hôtes et de service pour chaque instance d'hôte. Vous devez vous assurer que les comptes de service d'instance d'hôte sont membres du groupe Windows pour l'hôte.  
  
-   **Certificats de signature**. Les certificats de signature (certificats de clé privée) sont spécifiés pour le groupe BizTalk. Ils sont facultatifs et un administrateur BizTalk Server peut les modifier à tout moment.  
  
 Pour plus d’informations relatives aux comptes Windows qui utilise de BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)  
  
-   [Meilleures pratiques pour la gestion des certificats](../core/best-practices-for-managing-certificates1.md)  
  
-   [La gestion des comptes d’utilisateurs et groupes Windows](../core/managing-windows-groups-and-user-accounts.md)