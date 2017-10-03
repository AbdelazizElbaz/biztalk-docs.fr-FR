---
title: "Contrôle d’accès pour les groupes et comptes de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access control, service accounts
- user accounts, default accounts
- service accounts, security
- user accounts, unsupported
- access control, groups
- service accounts, access control
- groups, access control
- groups, security
ms.assetid: 411a7bfa-6675-4d09-9e37-83e2941df3c6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67bc5799d88c0dca876df463eb37d4af65ec84d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-for-groups-and-service-accounts"></a>Contrôle d’accès pour les groupes et comptes de Service
Chaque instance de l'hôte BizTalk est exécutée sous un compte de service créé par un utilisateur. Vous devez indiquer les comptes de service et leur mot de passe au moment de la création de l'instance de l'hôte sur un ordinateur. BizTalk Server vérifie ensuite que les comptes disposent des droits d'utilisateur minimaux requis dont ils ont besoin pour effectuer leurs tâches en ajoutant chacun de ces comptes de service à un groupe Windows de domaine ou local qui, à son tour, l'ajoute au rôle de base de données SQL Server spécifique à l'hôte.  
  
 Cette approche offre les avantages suivants :  
  
-   Vous pouvez attribuer un compte de service distinct à chaque instance de l'hôte, ce qui permet de modifier les mots de passe de ces instances d'hôte sans avoir à mettre les serveurs hors ligne. Vous pouvez ainsi effectuer des mises à jour propagées de mots de passe sans interrompre le service.  
  
    > [!NOTE]
    >  Il est impossible d'utiliser le même compte de service pour les hôtes approuvés par authentification et pour les hôtes qui ne le sont pas.  
  
-   Si vous octroyez à une ressource des droits d'utilisateur au groupe de domaine ou au groupe local au niveau de Microsoft SQL Server™, vous pouvez ajouter et retirer des comptes de service sans avoir à modifier les droits d'utilisateurs octroyés dans SQL Server, ce qui permet ainsi de réduire la charge de gestion et le coût total de possession.  
  
 Pour garantir que les comptes de service disposent des droits d'utilisateur minimaux dont ils ont besoin pour effectuer leurs tâches, les rôles de base de données SQL Server que BizTalk crée pour les comptes de service ne sont pas identiques dans toutes les bases de données BizTalk Server. Pour les bases de données de gestion et des suivis, tous les comptes de service ont besoin d'accéder aux mêmes objets SQL Server : BizTalk Server a donc créé un rôle de base de données SQL Server unique intitulé BTS_Host_User. BizTalk ajoute tous les groupes Windows créés pour les hôtes BizTalk à ce rôle de base de données SQL Server.  
  
 Pour la base de données MessageBox, chaque hôte dispose de ressources dédiées à l'hôte. BizTalk Server crée un rôle de base de données SQL Server par hôte, appelé BTS_\<*nom d’hôte*> _User, et ajoute le groupe Windows pour chaque hôte à son rôle respectif de la base de données SQL Server afin de bloquer l’accès d’un ordinateur hôte ressources par un autre hôte.  
  
## <a name="accounts-not-supported-by-biztalk-server"></a>Comptes non pris en charge par BizTalk Server  
 BizTalk Server ne prend pas en charge l'utilisation des comptes Windows suivants :  
  
-   NT_AUTHORITY\NetworkService  
  
-   LocalSystem  
  
-   NT_AUTHORITY\LocalService  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle d’accès pour les rôles d’administration](../core/access-control-for-administrative-roles.md)   
 [Autorisations de sécurité minimales](../core/minimum-security-user-rights.md)   
 [Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md)