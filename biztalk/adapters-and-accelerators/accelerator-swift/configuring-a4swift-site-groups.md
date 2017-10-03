---
title: Configuration des groupes de Site A4SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- site groups, creating
- creating, site groups
- security, user accounts
- user accounts, site groups
- site groups, user accounts
ms.assetid: ec2f3efe-439a-4018-ad94-5ab0fb2808ee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0070f10819ebbde18cdeab9c3bd534ca74bfbcd9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a4swift-site-groups"></a>Configuration des groupes de Site A4SWIFT
Vous devez créer les groupes de sites correspondante pour verrouiller les autorisations sur les bibliothèques de documents créés lors de la configuration de Message Repair et New Submission. Pour ce faire, dans l’exemple dans la section précédente, un administrateur A4SWIFT serait accédez au site MRSR et configurer les groupes de site suivants :  
  
-   Payments_Creators  
  
-   Payments_Repairers  
  
-   Payments_Approvers  
  
 Pour chacun de ces groupes de site, les autorisations suivantes doivent s’appliquer :  
  
-   **Afficher les éléments.** Afficher les éléments dans les listes, bibliothèques de documents, afficher les commentaires de discussion Web et configurer des alertes par courrier électronique pour les listes.  
  
-   **Afficher les Pages.** Afficher les pages d’un site Web.  
  
 Pour chaque utilisateur qui participe dans les rôles pour le service des paiements, vous devez créer un nouvel utilisateur de site et affectez cet utilisateur au groupe de sites qui correspond à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] rôles créés lors de la configuration de la console MMC.