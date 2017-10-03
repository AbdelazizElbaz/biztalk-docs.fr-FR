---
title: "Les environnements à faible privilège | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abdc45d0-b63a-4b6c-80c4-1f8e87644cd9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d43f363bd96dd8e3109a8ce21b9565fb43e5f9bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="low-privilege-environments"></a>Environnements avec privilèges faibles
Plusieurs flux de travail qui sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration nécessitent des autorisations élevées pour exécuter certaines actions. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Pack d’administration vous permet de vous permet d’effectuer des fonctionnalités de surveillance de base dans un environnement à faible privilège. Il existe deux rôles d’administration : l’administrateur du serveur BizTalk et l’opérateur de BizTalk Server. Le rôle administrateur de BizTalk Server dispose de privilèges élevés lui donnant accès à des données de configuration et de suivi. L’administrateur du serveur BizTalk peuvent effectuer toutes les tâches administratives clés telle l’inscription et le démarrage des artefacts. Le rôle opérateur de BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage. Pour plus d’informations, consultez [autorisations de sécurité minimales](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx).  
  
 À l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration :  
  
-   Les membres du groupe Opérateurs BizTalk Server peuvent effectuer les tâches suivantes :  
  
    -   Analyser BizTalk Server pour les erreurs, recherchez des messages ou instances suspendus, afficher la configuration.  
  
    -   Surveiller les installations de BizTalk Server et les artefacts.  
  
    -   Afficher l'état et le flux de messages du service.  
  
    -   Démarrer ou arrêter des applications et des artefacts tels que les orchestrations, ports d’envoi ou envoyer des groupes de ports qui sont dans un état inscrit.  
  
    -   Activer ou désactiver des emplacements de réception. Les modifications ne sont pas prises en compte avant la fin de l'intervalle d'actualisation du cache de 60 secondes (intervalle par défaut). Cet intervalle est défini au niveau du groupe BizTalk Server.  
  
-   Les membres du groupe Opérateurs BizTalk Server ne peuvent pas effectuer les tâches suivantes :  
  
    -   Modifier la configuration de BizTalk Server.  
  
    -   Afficher les propriétés de contexte de message marquées comme informations d'identification personnelle ou les corps de message.  
  
    -   Modifier le routage des messages, par exemple supprimer ou ajouter des abonnements au système en cours d'exécution, ou publier des messages dans un composant d'exécution BizTalk Server.  
  
> [!NOTE]  
>  Pour effectuer toutes les tâches de surveillance fournies par le Pack d’administration telles que le redémarrage du service BTSNTSvc.exe, vous devez être membre du groupe Administrateurs local sur les serveurs BizTalk Server.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Surveillance](../technical-guides/monitoring.md)  
  
-   [Découvertes](../technical-guides/discoveries.md)