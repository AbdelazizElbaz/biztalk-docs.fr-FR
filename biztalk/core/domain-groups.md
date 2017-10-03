---
title: Groupes de domaine | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: domain groups
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fc5cc05718aa6d9e0ca89bc48467052fb916a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="domain-groups"></a>Groupes de domaine
BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs. Pour les configurations multiserveurs, vous devez respecter les prérequis répertoriés dans cette section et dans la rubrique « Considérations relatives aux environnements multiserveurs » (Considerations for Multiserver Environments) du guide d'installation. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
-   Si vous utilisez des groupes de domaine pour configurer BizTalk Server, vous devez créer manuellement les groupes avant de configurer BizTalk Server. Le Gestionnaire de configuration ne peut pas créer de groupes de domaine.  
  
-   Après avoir créé des groupes de domaine ou des comptes d’utilisateur, ajoutez les comptes d’utilisateur aux groupes appropriés en fonction des affiliations de groupe dans [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Utilisez  **\<nom_domaine >\\< nom d’utilisateur\>**  lors de la spécification des informations de compte de domaine dans le Gestionnaire de Configuration.  
  
-   BizTalk Server nécessite des comptes de domaine pour tous les scénarios de mise en cluster. Vous ne pouvez pas utiliser de comptes locaux avec un serveur SQL ou SSO (serveur de secret principal) mis en cluster.  
  
-   L’administrateur de l’installation et la configuration de BizTalk Server doit être membre des groupes suivants : administrateurs de SSO (uniquement lors de la configuration du serveur de secret principal) ; Administrateurs locaux ; rôle sysadmin SQL Server ; Administrateurs OLAP.  
  
> [!NOTE]
>  Vous pouvez créer le groupe de domaine automatiquement si vous en spécifiez un lors de la configuration pour les administrateurs SSO et les administrateurs d'applications associées à authentification unique, et si vous possédez les autorisations nécessaires. Si vous ne disposez pas d'autorisations suffisantes, assurez-vous que ces groupes existent déjà.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes locaux](../core/local-groups.md)   
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Groupes et comptes d’utilisateur Windows dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)