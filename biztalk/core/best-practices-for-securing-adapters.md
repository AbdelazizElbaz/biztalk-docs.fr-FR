---
title: "Meilleures pratiques pour sécuriser les adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, security
- best practices, adapters
- adapters, permissions
- security, adapters
- permissions, adapters
- best practices, security
- adapters, best practices
ms.assetid: 004e1a01-b316-4eee-967f-5a806431de2b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86abbba06e851b9b289b29cd7fbbf01b3af292a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-securing-adapters"></a>Méthodes conseillées pour sécuriser les adaptateurs
Cette rubrique fournit une liste des meilleures pratiques pour la sécurité des adaptateurs.  
  
 **N’installez pas les adaptateurs non approuvés sur votre ordinateur ; utiliser uniquement certifiés partenaires.**  
  
 **Ne stockez pas les données sensibles dans le schéma de l’adaptateur par défaut.**  
  
 Vous devez configurer le nom d'utilisateur et le mot de passe uniquement après avoir déployé un adaptateur. Cela garantit que les informations sont bien stockées dans la base de données SSO. Pour plus d’informations sur la base de données SSO, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
 **Accordez les autorisations suivantes sur les dossiers partagés qui sont utilisées pour récupérer et supprimer des fichiers à l’aide des adaptateurs File et EDI (le dossier de réception et le dossier d’envoi) :**  
  
-   **Dossier de réception**  
  
     Le dossier de réception de l'adaptateur FILE peut être configuré sur l'emplacement de réception. Le dossier de réception de l'adaptateur EDI peut être configuré sur le gestionnaire de réception. Le compte de service de l'hôte BizTalk qui récupère le fichier doit disposer des autorisations suivantes au niveau du système de fichiers :  
  
    -   Lister le dossier/Lire les données  
  
    -   Supprimer le sous-dossier et les fichiers  
  
     Si le dossier de réception se trouve sur un partage réseau, les autorisations suivantes doivent être octroyées au niveau du partage de fichiers :  
  
    -   Le compte de service de l'hôte BizTalk qui récupère le fichier doit disposer des autorisations de contrôle total.  
  
    -   Les administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent disposer des autorisations de contrôle total pour la résolution des problèmes.  
  
    -   L'utilisateur ou les programmes externes qui déposent des fichiers à cet emplacement doivent disposer des autorisations en écriture.  
  
-   **Dossier d’envoi**  
  
     Le dossier d'envoi des adaptateurs FILE et EDI peut être configuré sur le port d'envoi.  
  
    -   Le compte de service du ou des hôtes BizTalk qui déposent des fichiers à cet emplacement doivent disposer des autorisations en écriture.  
  
    -   Les administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent disposer des autorisations de contrôle total.  
  
    -   L'utilisateur ou le programme externe qui récupère les fichiers doit disposer des autorisations en lecture.  
  
 **Ajoutez le compte d’utilisateur sous lequel le service EDI est exécuté au rôle SQL BTS_HOST_USERS.**  
  
 Cette opération permet d'obtenir l'accès au modèle objet de l'Explorateur BizTalk sans autorisations administratives. Pour ce faire, ajoutez les utilisateurs du sous-système EDI au rôle BTS_HOST_USERS dans la base de données de gestion BizTalk (BizTalkMgmtDb).  
  
 Pour ajouter les utilisateurs du sous-système EDI au rôle BTS_HOST_USERS sous SQL Server 2005, procédez comme suit :  
  
1.  Lancez SQL Server Management Studio à partir de **Démarrer, programmes, Microsoft SQL Server 2008**.  
  
2.  Connectez-vous au serveur SQL qui héberge votre base de données de gestion BizTalk.  
  
3.  Développez ce serveur dans l'Explorateur d'objets.  
  
4.  Développez **bases de données**, puis développez la base de données de gestion BizTalk.  
  
5.  Développez **sécurité**, développez **rôles**, puis cliquez sur pour sélectionner **des rôles de base de données**  
  
6.  Dans le volet de détails, cliquez sur le rôle BTS_HOST_USERS, puis cliquez sur **propriétés**.  
  
7.  Dans la boîte de dialogue BTS_HOST_USERS, cliquez sur **ajouter**, cliquez sur **Parcourir**et puis activez la case en regard du groupe utilisateurs du sous-système EDI pour l’ajouter.  
  
     Si le groupe Utilisateurs du sous-système EDI ne figure pas dans la liste des utilisateurs à ajouter, vous devez l'ajouter en tant que nouvel utilisateur à la base de données de gestion BizTalk. Pour ce faire, procédez comme suit dans SQL Server Management Studio :  
  
    1.  Développez la base de données de gestion BizTalk.  
  
    2.  Développez **sécurité**.  
  
    3.  Avec le bouton droit **utilisateurs** et cliquez sur **nouvel utilisateur**.  
  
    4.  Cliquez sur le bouton de sélection (...) en regard de la zone de texte **nom de connexion** pour afficher les **sélectionner la connexion** boîte de dialogue.  
  
    5.  Cliquez sur le bouton Parcourir, entrez le **utilisateurs du sous-système EDI** de groupe, puis cliquez sur **OK.** Si vous êtes invité au **plusieurs objets trouvés** boîte de dialogue, sélectionnez le **utilisateurs du sous-système EDI** connexion et cliquez sur **OK**.  
  
    6.  Sur le **nouvel utilisateur de base de données** boîte de dialogue Entrez **utilisateurs du sous-système EDI** pour le **nom d’utilisateur** zone de texte et cliquez sur **OK**.  
  
 **Ajoutez le compte d’utilisateur sous lequel le service BizTalk est en cours d’exécution au groupe utilisateurs du sous-système EDI.**  
  
 Pour ce faire, procédez comme suit.  
  
-   **Si BizTalk Server est configuré pour utiliser des groupes de domaine :**  
  
    1.  Ouvrez une session sur un ordinateur Windows Server dans le domaine.  
  
    2.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers**.  
  
        > [!NOTE]
        >  Vous devez disposer des autorisations de niveau domaine approprié pour modifier les objets dans le **Active Directory Users and Computers** interface.  
  
    3.  Cliquez pour développer le conteneur de domaine, puis cliquez pour développer le **utilisateurs** conteneur.  
  
    4.  Double-cliquez sur le **utilisateurs du sous-système EDI** groupe pour afficher les propriétés pour ce groupe.  
  
    5.  Cliquez sur le **membres** onglet de la **utilisateurs du sous-système EDI** boîte de dialogue groupe.  
  
    6.  Cliquez sur le **ajouter** pour ajouter le compte d’utilisateur pour le BizTalk Service à ce groupe.  
  
    7.  Cliquez sur **OK**.  
  
-   **Si BizTalk Server est configuré pour utiliser des groupes locaux :**  
  
    1.  Ouvrez une session sur le serveur BizTalk.  
  
    2.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
    3.  Cliquez pour développer **Outils système**, cliquez pour développer **utilisateurs et groupes locaux**et développez **groupes**.  
  
    4.  Double-cliquez sur le **utilisateurs du sous-système EDI** groupe pour afficher les propriétés pour ce groupe.  
  
    5.  Cliquez sur le **ajouter** pour ajouter le compte d’utilisateur pour le service BizTalk à ce groupe.  
  
    6.  Cliquez sur **OK**.