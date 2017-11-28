---
title: "Comment désactiver les alertes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, disabling
- managing [BAM definitions], disabling alerts
- Disable-Alerts command [BAM]
ms.assetid: c5938bc2-1043-4633-8cad-02caf442f2e8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0252fc98cdf792626094ffee75fae95c1cab3b00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-alerts"></a><span data-ttu-id="d5d6f-102">Désactivation des alertes</span><span class="sxs-lookup"><span data-stu-id="d5d6f-102">How to Disable Alerts</span></span>
<span data-ttu-id="d5d6f-103">Les administrateurs utilisent la **disable-alerts** commande pour désactiver toutes les alertes dans la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-103">Administrators use the **disable-alerts** command to disable all of the alerts on the specified view.</span></span>  
  
### <a name="to-disable-an-alert"></a><span data-ttu-id="d5d6f-104">Pour désactiver une alerte</span><span class="sxs-lookup"><span data-stu-id="d5d6f-104">To disable an alert</span></span>  
  
1.  <span data-ttu-id="d5d6f-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="d5d6f-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="d5d6f-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="d5d6f-108">Type **bm disable-alerts-View :\<nom de la vue >**.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-108">Type **bm disable-alerts -View:\<view name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5d6f-109">Si vous avez exporté une configuration BAM en tant que fichier XML, ne modifiez pas le fichier XML liés aux alertes.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-109">If you have exported a BAM configuration as XML, do not modify the XML related to alerts.</span></span> <span data-ttu-id="d5d6f-110">Si vous modifiez le fichier XML liés aux alertes et déployez les modifications, bm.exe détectera les modifications et activera les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-110">If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.</span></span>  
  
4.  <span data-ttu-id="d5d6f-111">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="d5d6f-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d6f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5d6f-112">See Also</span></span>  
 <span data-ttu-id="d5d6f-113">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="d5d6f-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="d5d6f-114">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="d5d6f-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="d5d6f-115">Comment activer les alertes</span><span class="sxs-lookup"><span data-stu-id="d5d6f-115">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md)