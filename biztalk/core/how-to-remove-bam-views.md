---
title: Comment supprimer des vues BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, views
- managing [BAM definitions], deleting views
- Remove-View command [BAM]
ms.assetid: 1a43ec81-20b1-41f7-941f-753132ac9ed2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04d8930fb4e3f2014945b743b15da4dbdfff3451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-views"></a><span data-ttu-id="24ebe-102">Suppression des vues BAM</span><span class="sxs-lookup"><span data-stu-id="24ebe-102">How to Remove BAM Views</span></span>
<span data-ttu-id="24ebe-103">Les administrateurs utilisent la **remove-view** commande pour supprimer une vue à partir de la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="24ebe-103">Administrators use the **remove-view** command to remove a view from the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24ebe-104">La suppression d'une vue entraîne automatiquement la suppression des alertes ayant été définies pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="24ebe-104">When you remove a view, you also automatically remove any alerts defined for that view.</span></span>  
  
### <a name="to-remove-bam-views"></a><span data-ttu-id="24ebe-105">Pour supprimer des vues BAM</span><span class="sxs-lookup"><span data-stu-id="24ebe-105">To remove BAM views</span></span>  
  
1.  <span data-ttu-id="24ebe-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="24ebe-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="24ebe-107">Accédez au dossier des suivis en tapant **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="24ebe-107">Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** at the command prompt.</span></span> <span data-ttu-id="24ebe-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="24ebe-108">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="24ebe-109">Type **bm remove-view-nom :\<nom de la vue >**.</span><span class="sxs-lookup"><span data-stu-id="24ebe-109">Type **bm remove-view -Name:\<view name>**.</span></span>  
  
4.  <span data-ttu-id="24ebe-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="24ebe-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ebe-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24ebe-111">See Also</span></span>  
 <span data-ttu-id="24ebe-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="24ebe-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="24ebe-113">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="24ebe-113">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 <span data-ttu-id="24ebe-114">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="24ebe-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="24ebe-115">Comment supprimer des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="24ebe-115">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)