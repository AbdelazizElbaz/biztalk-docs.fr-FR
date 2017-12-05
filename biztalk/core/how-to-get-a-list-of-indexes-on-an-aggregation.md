---
title: "Comment obtenir la liste des index sur une agrégation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes [BAM], listing indexes
- aggregations [BAM], listing indexes
- Get-Index command [BAM]
ms.assetid: 46a4a2fc-10f8-499c-bf2a-d0a19bb84151
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad7eabf54dc410ebed143641602599438f376a30
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-get-a-list-of-indexes-on-an-aggregation"></a><span data-ttu-id="cb9d3-102">Affichage des index d'une agrégation</span><span class="sxs-lookup"><span data-stu-id="cb9d3-102">How to Get a List of Indexes on an Aggregation</span></span>
<span data-ttu-id="cb9d3-103">Les administrateurs utilisent la **get-index** commande pour obtenir une liste de tous les index sur l’activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-103">Administrators use the **get-index** command to get a list of all the indexes on the specified activity.</span></span>  
  
### <a name="to-get-a-list-of-indexes-on-an-aggregation"></a><span data-ttu-id="cb9d3-104">Obtenir une liste des index sur une agrégation</span><span class="sxs-lookup"><span data-stu-id="cb9d3-104">To get a list of indexes on an aggregation</span></span>  
  
1.  <span data-ttu-id="cb9d3-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="cb9d3-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="cb9d3-107">Type **bm get-index-activité :\<nom de l’activité\>**.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-107">Type **bm get-index -Activity:\<activity name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb9d3-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="cb9d3-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="cb9d3-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9d3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb9d3-110">See Also</span></span>  
 <span data-ttu-id="cb9d3-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="cb9d3-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="cb9d3-112">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="cb9d3-112">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="cb9d3-113">[Comment supprimer un Index](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="cb9d3-113">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="cb9d3-114">Comment créer un Index</span><span class="sxs-lookup"><span data-stu-id="cb9d3-114">How to Create an Index</span></span>](../core/how-to-create-an-index.md)