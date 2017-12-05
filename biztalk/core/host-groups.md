---
title: "Groupes hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host groups, privileges
- Windows groups, host groups
- host groups, Windows groups
- host groups, about host groups
- host groups
ms.assetid: 0d92478b-b3a2-4c5a-925e-5495ee481e82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98e3798e42442e1a6533e4f286d194c8e2474be6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="host-groups"></a>Groupes d'hôtes
Le groupe d'hôtes est le groupe Windows (appelé groupe Utilisateurs d'applications BizTalk par défaut) que vous utilisez pour vos comptes avec accès aux hôtes BizTalk In-process (processus hôtes dans BizTalk Server). Il est conseillé d'utiliser un groupe d'hôtes pour chaque hôte In-process de votre environnement.  
  
 Vous ne pouvez associer un ordinateur hôte à un groupe Windows (appelé un *groupe hôte*). Ce groupe d'hôtes doit avoir une connexion et des privilèges SQL Server dans toutes les bases de données BizTalk Server appropriées. Lorsque vous associez un hôte au groupe d'hôtes, vous accordez à cet hôte les privilèges du groupe.  
  
 Si vous faites appel à l'Assistant Configuration pour créer des hôtes et que vous spécifiez un groupe Windows local qui sera utilisé pour ces hôtes, l'Assistant crée automatiquement deux groupes Windows. Par défaut, ces groupes sont appelés Utilisateurs d'applications BizTalk et Utilisateurs d'hôtes BizTalk isolés.  
  
 Lorsque vous créez une instance d'un hôte associé au groupe d'hôtes, cette instance hérite des privilèges de base de données du groupe.  
  
 Le groupe d'hôte est une propriété de l'objet Windows Management Instrumentation (WMI) hôte. Vous pouvez changer le groupe Windows auquel un hôte appartient s'il n'existe pas d'instances de cet hôte.  
  
 Vous spécifiez le groupe d'hôtes auquel un hôte appartient lorsque vous créez cet hôte. Le fournisseur BizTalk WMI accorde à l'hôte les privilèges que le groupe d'hôtes détient (par exemple, les privilèges BizTalk Server requis pour la fonctionnalité d'exécution, y compris les connexions SQL Server et l'accès utilisateur à la base de données). Vous devez spécifier le compte de service (hôte) correct lorsque vous créez une instance d'hôte afin que le fournisseur BizTalk Server WMI octroie les privilèges du groupe d'hôtes à cette instance.  
  
> [!NOTE]
>  Si vous voulez créer un groupe d'hôtes local, vous pouvez définir un groupe Windows local et assigner un utilisateur du domaine comme membre du groupe. Si vous voulez spécifier un groupe Windows local pour l'hôte, vous pouvez utiliser le membre du groupe Windows, qu'il s'agisse d'un utilisateur du domaine ou d'un utilisateur local, comme utilisateur de connexion de l'instance d'hôte.  
  
 Le groupe d'hôtes requiert les privilèges suivants :  
  
-   Il doit être membre du rôle SQL Server BTS_HOST_USERS dans les bases de données suivantes :  
  
    -   Base de données de gestion BizTalk (également appelée Base de données de configuration dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)])  
  
    -   MessageBox  
  
    -   Moteur de règles  
  
    -   Suivi  
  
    -   Importation principale BAM  
  
-   Il doit être un membre de la BTS_\<nom de l’hôte in-process\>rôle SQL Server _USERS pour la base de données MessageBox  
  
-   Il doit être membre du rôle SQL Server BAM_EVENT_WRITER dans la base de données d'importation principale BAM.  
  
> [!NOTE]
>  Si vous désignez un hôte comme hôte de suivi, l'Administration de BizTalk Server supprime automatiquement le groupe d'hôtes BizTalk des rôles SQL Server pour la base de données des suivis BizTalk. Vous devez supprimer manuellement le groupe d'hôtes BizTalk dans les rôles SQL Server pour la base de données de gestion BizTalk et la base de données MessageBox. Pour plus d’informations sur la désignation d’un ordinateur hôte comme hôte de suivi, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Entités](../core/entities.md)