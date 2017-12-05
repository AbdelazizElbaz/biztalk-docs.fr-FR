---
title: Comment supprimer des comptes dans un affichage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- managing [BAM], deleting accounts from views
- Remove-Account command [BAM]
ms.assetid: b74a64a0-ddb3-45d2-add7-6261c31be0f0
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e598dc13abb40a4b15d0624d68280c8f5279630a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-accounts-from-a-view"></a><span data-ttu-id="0dbfd-102">Suppression de comptes d'une vue</span><span class="sxs-lookup"><span data-stu-id="0dbfd-102">How to Remove Accounts from a View</span></span>
<span data-ttu-id="0dbfd-103">Les administrateurs utilisent la **remove-account** commande pour supprimer des utilisateurs à partir de vues BAM et protéger les vues de la feuille de calcul Excel BAM à partir de tout accès non autorisé.</span><span class="sxs-lookup"><span data-stu-id="0dbfd-103">Administrators use the **remove-account** command to remove users from BAM views and protect BAM Excel Spreadsheet views from unauthorized access.</span></span>  
  
 <span data-ttu-id="0dbfd-104">Pour plus d’informations sur l’affichage des vues BAM, consultez [comment répertorier les vues BAM](../core/how-to-list-bam-views.md).</span><span class="sxs-lookup"><span data-stu-id="0dbfd-104">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-remove-an-account-from-a-view"></a><span data-ttu-id="0dbfd-105">Pour supprimer un compte d'une vue</span><span class="sxs-lookup"><span data-stu-id="0dbfd-105">To remove an account from a view</span></span>  
  
1.  <span data-ttu-id="0dbfd-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0dbfd-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="0dbfd-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]de suivi</span><span class="sxs-lookup"><span data-stu-id="0dbfd-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking</span></span>  
  
3.  <span data-ttu-id="0dbfd-108">Type **bm remove-account - AccountName :\<nom de compte\> -View :\<nom de la vue\>**.</span><span class="sxs-lookup"><span data-stu-id="0dbfd-108">Type **bm remove-account -AccountName:\<account name\> -View:\<view name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0dbfd-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0dbfd-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="0dbfd-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="0dbfd-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbfd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dbfd-111">See Also</span></span>  
 <span data-ttu-id="0dbfd-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="0dbfd-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="0dbfd-113">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="0dbfd-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)