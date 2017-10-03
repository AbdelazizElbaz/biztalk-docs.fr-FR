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
# <a name="configuring-a4swift-site-groups"></a><span data-ttu-id="c703f-102">Configuration des groupes de Site A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="c703f-102">Configuring A4SWIFT Site Groups</span></span>
<span data-ttu-id="c703f-103">Vous devez créer les groupes de sites correspondante pour verrouiller les autorisations sur les bibliothèques de documents créés lors de la configuration de Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="c703f-103">You need to create the corresponding site groups to lock down the permissions on the document libraries created during Message Repair and New Submission configuration.</span></span> <span data-ttu-id="c703f-104">Pour ce faire, dans l’exemple dans la section précédente, un administrateur A4SWIFT serait accédez au site MRSR et configurer les groupes de site suivants :</span><span class="sxs-lookup"><span data-stu-id="c703f-104">To do so with the example in the preceding section, an A4SWIFT Administrator would go to the MRSR site and set up the following site groups:</span></span>  
  
-   <span data-ttu-id="c703f-105">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="c703f-105">Payments_Creators</span></span>  
  
-   <span data-ttu-id="c703f-106">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="c703f-106">Payments_Repairers</span></span>  
  
-   <span data-ttu-id="c703f-107">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="c703f-107">Payments_Approvers</span></span>  
  
 <span data-ttu-id="c703f-108">Pour chacun de ces groupes de site, les autorisations suivantes doivent s’appliquer :</span><span class="sxs-lookup"><span data-stu-id="c703f-108">For each of these site groups the following permissions should be applied:</span></span>  
  
-   <span data-ttu-id="c703f-109">**Afficher les éléments.**</span><span class="sxs-lookup"><span data-stu-id="c703f-109">**View Items.**</span></span> <span data-ttu-id="c703f-110">Afficher les éléments dans les listes, bibliothèques de documents, afficher les commentaires de discussion Web et configurer des alertes par courrier électronique pour les listes.</span><span class="sxs-lookup"><span data-stu-id="c703f-110">View items in lists, documents in document libraries, view Web discussion comments, and set up e-mail alerts for lists.</span></span>  
  
-   <span data-ttu-id="c703f-111">**Afficher les Pages.**</span><span class="sxs-lookup"><span data-stu-id="c703f-111">**View Pages.**</span></span> <span data-ttu-id="c703f-112">Afficher les pages d’un site Web.</span><span class="sxs-lookup"><span data-stu-id="c703f-112">View pages in a Web site.</span></span>  
  
 <span data-ttu-id="c703f-113">Pour chaque utilisateur qui participe dans les rôles pour le service des paiements, vous devez créer un nouvel utilisateur de site et affectez cet utilisateur au groupe de sites qui correspond à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] rôles créés lors de la configuration de la console MMC.</span><span class="sxs-lookup"><span data-stu-id="c703f-113">For each user who participates in the roles for the Payments department, you need to create a new site user and assign that user to the site group that corresponds to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] roles created during MMC configuration.</span></span>