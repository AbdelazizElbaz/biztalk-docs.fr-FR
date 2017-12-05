---
title: Groupes de domaine | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ae4f855b01a7cfcd789e8d8a37e375f9e72c1a7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="domain-groups-in-biztalk"></a>Groupes de domaine dans BizTalk Server
BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs. Pour les configurations multiserveurs, vous devez respecter les prérequis répertoriés dans cette section et dans la rubrique « Considérations relatives aux environnements multiserveurs » (Considerations for Multiserver Environments) du guide d'installation. Pour plus d’informations, consultez la [vue d’ensemble de l’installation](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).  
  
## <a name="before-you-begin"></a>Avant de commencer
-   Si vous utilisez des groupes de domaine pour configurer BizTalk Server, vous devez créer manuellement les groupes avant de configurer BizTalk Server. Le Gestionnaire de configuration ne peut pas créer de groupes de domaine.  
  
-   Après avoir créé des groupes de domaine ou des comptes d’utilisateur, ajoutez les comptes d’utilisateur aux groupes appropriés en fonction des affiliations de groupe dans [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Utilisez  **\<DomainName\>\\< nom d’utilisateur\>**  lors de la spécification des informations de compte de domaine dans le Gestionnaire de Configuration.  
  
-   BizTalk Server nécessite des comptes de domaine pour tous les scénarios de mise en cluster. Vous ne pouvez pas utiliser de comptes locaux avec un serveur SQL ou SSO (serveur de secret principal) mis en cluster.  
  
-   L’administrateur de l’installation et la configuration de BizTalk Server doit être membre des groupes suivants : administrateurs de SSO (uniquement lors de la configuration du serveur de secret principal) ; Administrateurs locaux ; rôle sysadmin SQL Server ; Administrateurs OLAP.  
  
> [!NOTE]
>  Vous pouvez créer le groupe de domaine automatiquement si vous en spécifiez un lors de la configuration pour les administrateurs SSO et les administrateurs d'applications associées à authentification unique, et si vous possédez les autorisations nécessaires. Si vous ne disposez pas d'autorisations suffisantes, assurez-vous que ces groupes existent déjà.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes locaux](../core/local-groups.md)   
 [Vue d’ensemble de l’installation](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)   
 [Groupes et comptes d’utilisateur Windows dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)