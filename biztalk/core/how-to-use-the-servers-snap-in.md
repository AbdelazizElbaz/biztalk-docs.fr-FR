---
title: Comment utiliser le composant logiciel enfichable serveurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f520692-9606-41f5-98ed-5a4962bd1f09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12eb72323a6dcd1132f03febc9b4d9bd75316c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-servers-snap-in"></a>Utilisation du composant logiciel enfichable de serveurs
Cette version de l'authentification unique de l'entreprise inclut le composant logiciel enfichable de serveurs ENTSSO, lequel vous permet d'afficher, d'analyser et d'effectuer certaines actions sur votre serveur ENTSSO via l'interface Windows.  
  
> [!NOTE]
>  Si votre système est protégé par un pare-feu et si le nom de votre serveur utilise le format FQDN, vous risquez de ne pas pouvoir contacter le serveur. Vous devez alors spécifier le nom NetBIOS ou l'adresse IP qui lui sont associés.  
  
### <a name="to-use-the-entsso-servers-snap-in"></a>Pour utiliser le composant logiciel enfichable de serveurs ENTSSO  
  
1.  Ouvrez l'authentification unique de l'entreprise.  
  
2.  Dans le volet d’étendue, cliquez sur le **serveurs** nœud.  
  
     Les informations suivantes sont affichées dans le volet Résultats.  
  
    -   **Nom**: nom spécifié.  
  
    -   **État**: état du service ENTSSO (en ligne, hors connexion, en attente, démarré, arrêté, attente de démarrage, arrêt en attente).  
  
    -   **Date**: obtention des informations de Date.  
  
    -   **Heure**: obtention des informations de temps.  
  
    -   **Serveur d’authentification unique**: nom complet du serveur.  
  
    -   **Compte de service**: compte de service ENTSSO.  
  
    -   **Base de données SSO**: base de données ENTSSO avec lequel communique ce serveur.  
  
    -   **Serveur de secret principal**: indique si le module du serveur de secret principal est en cours d’exécution.  
  
    -   **Synchronisation de mot de passe**: indique si la synchronisation de mot de passe est installée.  
  
    -   **Ordinateur**: nom NETBIOS de l’ordinateur.  
  
    -   **Événement compte**: nombre d’événements informations/avertissement/erreurs. Si vous réinitialisez cette valeur, le compteur redémarrera à 0.  
  
    -   **Version SSO installée**: numéro de Version d’ENTSSO.exe. Indique également s'il s'agit d'une version 32 bits (x86) ou 64 bits (x64).  
  
### <a name="to-start-or-stop-the-server-service"></a>Pour démarrer ou arrêter le service du serveur  
  
-   Dans le serveurs enfichable ENTSSO, cliquez sur le serveur, sur **Démarrer** ou **arrêter**.  
  
### <a name="to-display-information-for-one-server"></a>Pour afficher les informations d'un serveur  
  
-   Dans l'arborescence des serveurs, cliquez sur le serveur.  
  
     Les informations sont affichées dans le volet Résultats.  
  
### <a name="to-add-a-server"></a>Pour ajouter un serveur  
  
-   Avec le bouton droit dans le volet d’étendue, puis cliquez sur **ajouter un serveur**.  
  
     Le **ajouter un serveur** boîte de dialogue s’affiche. Tapez ou recherchez le serveur que vous souhaitez ajouter.  
  
> [!NOTE]
>  Dans certains environnements de groupe de travail, en cliquant sur le **Parcourir** bouton entraînera fermer cette boîte de dialogue. Au lieu d’utiliser le **Parcourir** bouton, tapez le nom du serveur dans la zone.  
  
### <a name="to-view-or-change-server-properties"></a>Pour afficher ou modifier des propriétés de serveur  
  
-   Dans l’arborescence du serveur, cliquez sur le serveur, puis cliquez sur **propriétés**.  
  
     Le **propriétés du serveur** boîte de dialogue s’affiche. Vous pouvez afficher ou modifier les informations sous les onglets suivants :  
  
    -   **Niveaux d’audit**  
  
    -   **Base de données SSO**  
  
    -   **Service d’authentification unique**  
  
    -   **Synchronisation de mot de passe**  
  
    -   **Avancé**