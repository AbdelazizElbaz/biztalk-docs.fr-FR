---
title: "Service de créer des comptes pour les nouveaux ordinateurs hôtes et les Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager, service accounts
- Windows groups, service accounts
- Configuration Manager
- service accounts, Windows groups
- hosts, service accounts
- service accounts, hosts
- service accounts, Configuration Manager
- service accounts, creating
- creating, service accounts
ms.assetid: cef97f4a-8db1-41b6-9614-608c2fbf59a9
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d4887d78466340b12b95ed43d27523955ab0689
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-service-accounts-for-new-hosts-and-host-instances"></a>Création des comptes de service pour les nouveaux hôtes et instances d'hôte
Le Gestionnaire de configuration configure les groupes Windows et les comptes d'utilisateur nécessaires lors de l'installation et de la configuration de BizTalk Server sur un seul ordinateur.  
  
 Vous devez créer manuellement les groupes Windows et les comptes d'utilisateur, puis ajouter ces derniers aux groupes Windows dans un environnement de domaine avant d'exécuter le Gestionnaire de configuration. Pour plus d’informations, consultez [groupes de domaine](../core/domain-groups.md).  
  
 Vous devez effectuer la procédure suivante avant de créer un hôte ou une instance d'hôte.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs ou Administrateurs de domaine.  
  
### <a name="to-create-service-accounts-for-new-hosts-or-host-instances"></a>Pour créer des comptes de service pour les nouveaux hôtes ou instances d'hôte  
  
1.  Créez un groupe d'hôtes Windows pour l'hôte que vous allez créer. Pour plus d’informations sur la création d’un nouvel hôte, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md).  
  
2.  Créez des comptes de service pour chaque instance d'hôte qui sera ajoutée au nouvel hôte. Pour plus d’informations sur la création d’une instance d’hôte, consultez [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).  
  
3.  Ajoutez les comptes de service au groupe Windows de l'hôte. Pour plus d’informations sur les groupes Windows auxquels vous devez ajouter le compte de service, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
4.  Utilisez le groupe Windows et le compte de service lors de la création de l'hôte et des instances d'hôte.  
  
    > [!NOTE]
    >  Ne spécifiez pas \< *nom de l’ordinateur*\>\ en tant que le préfixe dans une configuration d’ordinateur unique avec des groupes locaux.  
  
    > [!NOTE]
    >  Si vous utilisez un groupe de domaine, vous devez spécifier \< *nom de domaine NetBIOS*\>\ en tant que le préfixe du nom d’hôte groupe Windows. Par exemple, CONTOSO\btssvc.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des hôtes et des comptes de Service](../core/managing-hosts-and-service-accounts.md)   
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)   
 [Comment gérer le groupe d’administrateurs BizTalk Server](../core/how-to-manage-the-biztalk-server-administrators-group.md)   
 [Bonnes pratiques pour la gestion des groupes et comptes d’utilisateurs Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)