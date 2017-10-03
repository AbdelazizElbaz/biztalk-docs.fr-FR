---
title: "La gestion d’exécution des alertes BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], executing alerts
- Notification Services, configuration files
- BAM Management utility
- alerts, executing
ms.assetid: 44bb738e-fa2c-4b32-9e8d-e756d6c3778e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5607bed785ee4f91a341b546dbe81ec39458c4e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-alert-execution"></a><span data-ttu-id="8b597-102">Gestion de l'exécution des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="8b597-102">Managing BAM Alert Execution</span></span>
<span data-ttu-id="8b597-103">L'exécution des alertes BAM peut être modifiée au moyen de trois outils différents : le portail BAM, l'utilitaire de gestion de l'analyse BAM et le script ProcessBamNSFiles.vbs.</span><span class="sxs-lookup"><span data-stu-id="8b597-103">BAM Alert execution can be modified through three avenues, The BAM Portal, the BAM management utility, and the ProcessBamNSFiles.vbs script.</span></span>  
  
## <a name="bam-portal"></a><span data-ttu-id="8b597-104">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="8b597-104">BAM Portal</span></span>  
 <span data-ttu-id="8b597-105">Les travailleurs du savoir et les administrateurs peuvent modifier la manière dont les alertes sont transmises en utilisant le gestionnaire d'alertes du portail BAM.</span><span class="sxs-lookup"><span data-stu-id="8b597-105">Knowledge workers and administrators can modify the manner in which alerts are delivered by using the Alert Manager in the BAM portal.</span></span> <span data-ttu-id="8b597-106">Dans le portail BAM, une alerte peut être activée ou désactivée et les niveaux limite, les emplacements de réception et d'autres paramètres ayant un impact sur l'exécution de l'alerte peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="8b597-106">From the BAM portal, the Alert can be enabled or disabled, threshold levels can be modified, delivery locations can be modified, as well as other parameters the affect the execution of the alert.</span></span>  
  
 <span data-ttu-id="8b597-107">Pour plus d’informations sur la modification des alertes, consultez [Gestionnaire d’alertes sur la Page du portail BAM](../core/alert-manager-on-the-bam-portal-page.md) et [alertes dans le portail BAM](../core/alerts-in-the-bam-portal.md).</span><span class="sxs-lookup"><span data-stu-id="8b597-107">For more information on modifying alerts, see [Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md) and [Alerts in the BAM Portal](../core/alerts-in-the-bam-portal.md).</span></span>  
  
### <a name="bam-management-utility"></a><span data-ttu-id="8b597-108">Utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="8b597-108">BAM Management Utility</span></span>  
 <span data-ttu-id="8b597-109">Les administrateurs peuvent se servir de l'utilitaire de gestion de l'analyse BAM pour activer, désactiver et supprimer des alertes.</span><span class="sxs-lookup"><span data-stu-id="8b597-109">Administrators can use the BAM Management utility to enable, disable, and remove alerts.</span></span>  
  
 <span data-ttu-id="8b597-110">Pour plus d'informations sur le maniement de cet utilitaire pour les alertes, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b597-110">For information on using the BAM Management Utility to mange alerts, the following topics:</span></span>  
  
-   [<span data-ttu-id="8b597-111">Comment activer les alertes</span><span class="sxs-lookup"><span data-stu-id="8b597-111">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md) 
  
-   [<span data-ttu-id="8b597-112">Comment désactiver les alertes</span><span class="sxs-lookup"><span data-stu-id="8b597-112">How to Disable Alerts</span></span>](../core/how-to-disable-alerts.md)  
  
-   [<span data-ttu-id="8b597-113">Comment supprimer des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="8b597-113">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)  
  
### <a name="modifying-notification-services-configuration-files"></a><span data-ttu-id="8b597-114">Modification des fichiers de configuration des services de notification</span><span class="sxs-lookup"><span data-stu-id="8b597-114">Modifying Notification Services Configuration Files</span></span>  
 <span data-ttu-id="8b597-115">Les administrateurs peuvent utiliser le script ProcessBamNSFiles.vbs pour modifier la manière dont les services de notification envoient des alertes.</span><span class="sxs-lookup"><span data-stu-id="8b597-115">Administrators can use the ProcessBamNSFiles.vbs script to change the manner in which the Notification Services delivers alerts.</span></span> <span data-ttu-id="8b597-116">Pour plus d’informations du fichier de définition d’Application (ADF) pour Notification Services, consultez [http://go.microsoft.com/fwlink/?LinkId=127016](http://go.microsoft.com/fwlink/?LinkId=127016).</span><span class="sxs-lookup"><span data-stu-id="8b597-116">For more information the Application Definition File (ADF) for Notification Services, see [http://go.microsoft.com/fwlink/?LinkId=127016](http://go.microsoft.com/fwlink/?LinkId=127016).</span></span>  
  
 <span data-ttu-id="8b597-117">Pour modifier le fichier ADF associé à l'analyse BAM, vous pouvez suivre les grandes étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b597-117">To modify the ADF associated with BAM you can follow these general steps:</span></span>  
  
1.  <span data-ttu-id="8b597-118">Exécutez le script pour obtenir la configuration actuelle et les fichiers ADF.</span><span class="sxs-lookup"><span data-stu-id="8b597-118">Run the script to obtain the current configuration and ADF files.</span></span>  
  
2.  <span data-ttu-id="8b597-119">Modifiez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="8b597-119">Modify the files.</span></span>  
  
3.  <span data-ttu-id="8b597-120">Exécutez le script pour appliquer les modifications.</span><span class="sxs-lookup"><span data-stu-id="8b597-120">Run the script to apply the changes.</span></span>  
  
 <span data-ttu-id="8b597-121">Pour plus d’informations sur le script ProcessBamNSFiles.vbs, voir [Script de ligne de commande BAM pour les fichiers de Configuration de Services de Notification](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="8b597-121">For more information on the ProcessBamNSFiles.vbs script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b597-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b597-122">See Also</span></span>  
 <span data-ttu-id="8b597-123">[Gestion du portail BAM](../core/managing-the-bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="8b597-123">[Managing the BAM Portal](../core/managing-the-bam-portal.md) </span></span>  
 <span data-ttu-id="8b597-124">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="8b597-124">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="8b597-125">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="8b597-125">BAM Management Utility</span></span>](../core/bam-management-utility.md)