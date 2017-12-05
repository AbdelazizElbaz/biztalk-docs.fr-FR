---
title: "Utilisateur de la liste des comptes ayant accès à une vue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, BAM
- managing [BAM], user accounts
- Get-Accounts utility [BAM]
ms.assetid: 690fb45a-6de0-489e-9ddd-e88e29413c16
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80a01aa9b4bd19581cb97f7fee127fc244322d4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-user-accounts-with-access-to-a-view"></a><span data-ttu-id="70c2e-102">Affichage des comptes d'utilisateur ayant accès à une vue</span><span class="sxs-lookup"><span data-stu-id="70c2e-102">How to List User Accounts With Access to a View</span></span>
<span data-ttu-id="70c2e-103">Les administrateurs utilisent la **get-accounts** commande d’utilitaire de gestion BAM pour obtenir une liste de tous les comptes d’utilisateur pour un rôle de la vue, ce qui signifie que tous les comptes d’utilisateurs ayant accès à la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="70c2e-103">Administrators use the **get-accounts** BAM Management utility command to get a list all user accounts for a view role, meaning all user accounts with access to the specified view.</span></span>  
  
 <span data-ttu-id="70c2e-104">Pour plus d’informations sur l’affichage des vues BAM, consultez [comment répertorier les vues BAM](../core/how-to-list-bam-views.md).</span><span class="sxs-lookup"><span data-stu-id="70c2e-104">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-list-user-accounts-with-access-to-a-view"></a><span data-ttu-id="70c2e-105">Pour afficher les comptes d'utilisateur ayant accès à une vue</span><span class="sxs-lookup"><span data-stu-id="70c2e-105">To list user accounts with access to a view</span></span>  
  
1.  <span data-ttu-id="70c2e-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70c2e-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="70c2e-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]de suivi</span><span class="sxs-lookup"><span data-stu-id="70c2e-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking</span></span>  
  
3.  <span data-ttu-id="70c2e-108">Type **bm get-accounts-View :\<nom de la vue\>**.</span><span class="sxs-lookup"><span data-stu-id="70c2e-108">Type **bm get-accounts -View:\<view name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70c2e-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="70c2e-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="70c2e-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="70c2e-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c2e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70c2e-111">See Also</span></span>  
 <span data-ttu-id="70c2e-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="70c2e-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="70c2e-113">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="70c2e-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)