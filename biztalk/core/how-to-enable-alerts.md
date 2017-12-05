---
title: Comment activer les alertes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enable-Alerts command [BAM]
- managing [BAM definitions], enabling alerts
- alerts, enabling
ms.assetid: 18f494b7-54fb-4aaf-89d1-7e3fe91f35c6
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9986bea177471a236cab888f20d915292d540e5b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-alerts"></a><span data-ttu-id="740c8-102">Activation des alertes</span><span class="sxs-lookup"><span data-stu-id="740c8-102">How to Enable Alerts</span></span>
<span data-ttu-id="740c8-103">Les administrateurs utilisent la **enable-alerts** commande pour activer toutes les alertes dans la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="740c8-103">Administrators use the **enable-alerts** command to enable all of the alerts on the specified view.</span></span>  
  
### <a name="to-enable-an-alert"></a><span data-ttu-id="740c8-104">Pour activer une alerte</span><span class="sxs-lookup"><span data-stu-id="740c8-104">To enable an alert</span></span>  
  
1.  <span data-ttu-id="740c8-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="740c8-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="740c8-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="740c8-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="740c8-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="740c8-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="740c8-108">Type **bm enable-alerts-View :\<nom de la vue\>**.</span><span class="sxs-lookup"><span data-stu-id="740c8-108">Type **bm enable-alerts -View:\<view name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="740c8-109">Si vous avez exporté une configuration BAM en tant que fichier XML, ne modifiez pas le fichier XML liés aux alertes.</span><span class="sxs-lookup"><span data-stu-id="740c8-109">If you have exported a BAM configuration as XML, do not modify the XML related to alerts.</span></span> <span data-ttu-id="740c8-110">Si vous modifiez le fichier XML liés aux alertes et déployez les modifications, bm.exe détectera les modifications et activera les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="740c8-110">If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.</span></span>  
  
4.  <span data-ttu-id="740c8-111">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="740c8-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740c8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="740c8-112">See Also</span></span>  
 <span data-ttu-id="740c8-113">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="740c8-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="740c8-114">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="740c8-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="740c8-115">entrer la description de l’image ici</span><span class="sxs-lookup"><span data-stu-id="740c8-115">enter link description here</span></span>](../core/how-to-disable-alerts.md)