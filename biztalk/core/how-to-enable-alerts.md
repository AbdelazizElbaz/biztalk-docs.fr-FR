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
ms.openlocfilehash: 22bb3610d489f02aa535b562057b4bb09e208983
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-alerts"></a><span data-ttu-id="b1a38-102">Activation des alertes</span><span class="sxs-lookup"><span data-stu-id="b1a38-102">How to Enable Alerts</span></span>
<span data-ttu-id="b1a38-103">Les administrateurs utilisent la **enable-alerts** commande pour activer toutes les alertes dans la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b1a38-103">Administrators use the **enable-alerts** command to enable all of the alerts on the specified view.</span></span>  
  
### <a name="to-enable-an-alert"></a><span data-ttu-id="b1a38-104">Pour activer une alerte</span><span class="sxs-lookup"><span data-stu-id="b1a38-104">To enable an alert</span></span>  
  
1.  <span data-ttu-id="b1a38-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1a38-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b1a38-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="b1a38-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="b1a38-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b1a38-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="b1a38-108">Type **bm enable-alerts-View :\<nom de la vue >**.</span><span class="sxs-lookup"><span data-stu-id="b1a38-108">Type **bm enable-alerts -View:\<view name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1a38-109">Si vous avez exporté une configuration BAM en tant que fichier XML, ne modifiez pas le fichier XML liés aux alertes.</span><span class="sxs-lookup"><span data-stu-id="b1a38-109">If you have exported a BAM configuration as XML, do not modify the XML related to alerts.</span></span> <span data-ttu-id="b1a38-110">Si vous modifiez le fichier XML liés aux alertes et déployez les modifications, bm.exe détectera les modifications et activera les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b1a38-110">If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.</span></span>  
  
4.  <span data-ttu-id="b1a38-111">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b1a38-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a38-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1a38-112">See Also</span></span>  
 <span data-ttu-id="b1a38-113">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b1a38-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="b1a38-114">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b1a38-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="b1a38-115">entrer la description de l’image ici</span><span class="sxs-lookup"><span data-stu-id="b1a38-115">enter link description here</span></span>](../core/how-to-disable-alerts.md)