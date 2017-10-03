---
title: "Considérations de sécurité pour le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, administrator accounts
- user accounts, BAM
- administrator accounts, BAM portal
- BAM portal, user accounts
- security, BAM portal
ms.assetid: 5c8e6034-dfb8-4dba-b040-0c19504abdb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b0f5220eba5b66daf41dffc7ab74f93df8bb509
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-the-bam-portal"></a>Considérations de sécurité relatives au portail BAM
Selon le principe des privilèges les plus faibles, les comptes utilisateurs doivent disposer d'autorisations limitées leur permettant uniquement d'effectuer des tâches routinières dans le portail BAM. Gardez à l'esprit les points suivants lorsque vous configurez les comptes utilisateurs pour permettre au composant BAM de trouver un compromis entre le niveau de sécurité nécessaire et les autorisations d'accès aux utilisateurs.  
  
## <a name="user-accounts"></a>Comptes d'utilisateur  
 Comptes d’utilisateur avec les autorisations minimales ne sont pas en mesure d’utiliser le navigationfeature distribuée de portail BAM. Pour pouvoir l'utiliser, ces comptes doivent disposer des autorisations leur permettant d'accéder aux services Web, depuis un ordinateur distant ou local.  
  
 Les comptes utilisateur ayant accès aux services Web BAM doivent disposer des autorisations d'accès à toutes les bases de données référencées et doivent y être membres du rôle BAM_ManagementWS.  
  
 Selon le type d'utilisateur mentionné, tenez compte des éléments suivants :  
  
-   Utilisateurs de domaine : ils doivent disposer d'autorisations d'accès sur des ordinateurs distants hébergeant des bases de données d'importation principales accessibles.  
  
-   Utilisateurs auxquels un rôle d'utilisateur local a été attribué : ils ne peuvent pas utiliser la fonctionnalité de navigation distribuée.  
  
## <a name="administrator-accounts"></a>Comptes d'administrateur  
 Les administrateurs doivent être membres des groupes securityadmin ou sysadmin pour accorder des autorisations d'accès aux utilisateurs de domaine.  
  
 Pour pouvoir exécuter l'utilitaire de gestion de l'analyse BAM, vous devez être défini en tant qu'opérateur de base de données au moins pour les bases de données BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Portail BAM](../core/bam-portal.md)