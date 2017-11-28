---
title: "Sécurité de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows SharePoint Services
- Windows SharePoint Services, security
- security, BAS
- BAS, security
ms.assetid: ada6abd3-b867-49a6-8ee0-1466adc87dc5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184f5a237f796eac69de6c481e69a87a4a5358df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-security"></a><span data-ttu-id="d78b4-102">Sécurité de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="d78b4-102">Windows SharePoint Services Security</span></span>
<span data-ttu-id="d78b4-103">Windows SharePoint Services 3.0 utilise des groupes de sites Windows SharePoint Services pour gérer la sécurité de l’échelle du site.</span><span class="sxs-lookup"><span data-stu-id="d78b4-103">Windows SharePoint Services 3.0 uses Windows SharePoint Services site groups to manage site-wide security.</span></span> <span data-ttu-id="d78b4-104">Chaque groupe de sites possède les droits correspondants.</span><span class="sxs-lookup"><span data-stu-id="d78b4-104">Each site group possesses corresponding rights.</span></span> <span data-ttu-id="d78b4-105">Les droits sont des actions que les utilisateurs peuvent effectuer, comme l’affichage, modifier et supprimer des ressources de site.</span><span class="sxs-lookup"><span data-stu-id="d78b4-105">Rights are actions that users can perform—such as view, edit, and delete site resources.</span></span> <span data-ttu-id="d78b4-106">Les ressources incluent des listes de sites, bibliothèques de documents et administration du site.</span><span class="sxs-lookup"><span data-stu-id="d78b4-106">Resources include site lists, document libraries, and site administration.</span></span> <span data-ttu-id="d78b4-107">Pour chaque rôle créé dans le Client Web de profil vous devez définir un groupe de sites Windows SharePoint Services et attribuer des droits en conséquence chaque ressource à laquelle ce groupe a accès.</span><span class="sxs-lookup"><span data-stu-id="d78b4-107">For each role created in the Profile Web Client you need to define a Windows SharePoint Service site group and assign rights accordingly to each resource to which that group has access.</span></span>  
  
 <span data-ttu-id="d78b4-108">Pour plus d’informations sur la sécurité de WSS 3.0, consultez le guide d’évaluation de WSS 3.0 à [http://go.microsoft.com/fwlink/?LinkID=94370](http://go.microsoft.com/fwlink/?LinkID=94370).</span><span class="sxs-lookup"><span data-stu-id="d78b4-108">For more information about WSS 3.0 security, see the WSS 3.0 evaluation guide at [http://go.microsoft.com/fwlink/?LinkID=94370](http://go.microsoft.com/fwlink/?LinkID=94370).</span></span>  
  
 <span data-ttu-id="d78b4-109">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="d78b4-109">This section contains:</span></span>  
  
-   [<span data-ttu-id="d78b4-110">Configuration d’A4SWIFT utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d78b4-110">Configuring A4SWIFT Users</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-a4swift-users.md)  
  
-   [<span data-ttu-id="d78b4-111">Configuration des groupes de Site A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="d78b4-111">Configuring A4SWIFT Site Groups</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-a4swift-site-groups.md)  
  
-   [<span data-ttu-id="d78b4-112">Attribution des droits</span><span class="sxs-lookup"><span data-stu-id="d78b4-112">Assigning Rights</span></span>](../../adapters-and-accelerators/accelerator-swift/assigning-rights.md)