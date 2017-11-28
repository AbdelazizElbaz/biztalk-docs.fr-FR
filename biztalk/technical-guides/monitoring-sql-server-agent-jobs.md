---
title: "Analyse des travaux de l’Agent SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 489e9e8e8b5bf5b00125036d71ff5fa0f37f3545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs"></a><span data-ttu-id="a1ff3-102">Analyse des travaux de l’Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="a1ff3-102">Monitoring SQL Server Agent Jobs</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a1ff3-103"> inclut des travaux SQL Server Agent multiples qui remplissent des fonctions importantes pour le bon fonctionnement de vos serveurs.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-103"> includes multiple SQL Server Agent jobs that perform important functions to keep your servers operational and healthy.</span></span> <span data-ttu-id="a1ff3-104">Vérifiez le bon fonctionnement de ces travaux et assurez-vous qu'aucune erreur ne se produit.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-104">You should monitor the health of these jobs and ensure that they are running without errors.</span></span>  
  
## <a name="guidelines-for-monitoring-the-sql-server-agent-jobs"></a><span data-ttu-id="a1ff3-105">Instructions pour analyser les travaux de l’Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="a1ff3-105">Guidelines for Monitoring the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="a1ff3-106">Voici des recommandations pour les travaux d’analyse :</span><span class="sxs-lookup"><span data-stu-id="a1ff3-106">Following are guidelines for monitoring the jobs:</span></span>  
  
-   <span data-ttu-id="a1ff3-107">**Vérifiez que le service SQL Server Agent s’exécute.**</span><span class="sxs-lookup"><span data-stu-id="a1ff3-107">**Verify that the SQL Server Agent service is running**</span></span>  
  
-   <span data-ttu-id="a1ff3-108">**Vérifiez que les travaux de l’Agent SQL Server installés par BizTalk Server sont activées et en cours d’exécution avec succès**</span><span class="sxs-lookup"><span data-stu-id="a1ff3-108">**Verify that the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully**</span></span>  
  
     <span data-ttu-id="a1ff3-109">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des travaux de l’Agent SQL Server sont cruciaux : s’ils n’exécutent pas, les performances du système se dégradent au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent jobs are crucial: if they are not running, system performance will degrade over time.</span></span>  
  
-   <span data-ttu-id="a1ff3-110">**Vérifiez que les travaux de SQL Server Agent BizTalk Server sont achèvent en temps voulu**</span><span class="sxs-lookup"><span data-stu-id="a1ff3-110">**Verify that the BizTalk Server SQL Server Agent jobs are completing in a timely manner**</span></span>  
  
     <span data-ttu-id="a1ff3-111">Configurer Microsoft System Center Operations Manager pour surveiller les travaux.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-111">Set up Microsoft System Center Operations Manager to monitor the jobs.</span></span>  
  
     <span data-ttu-id="a1ff3-112">Vous devez être conscient des planifications qui sont spécifiques à certaines tâches :</span><span class="sxs-lookup"><span data-stu-id="a1ff3-112">You should be aware of schedules that are particular to certain jobs:</span></span>  
  
    -   <span data-ttu-id="a1ff3-113">Le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb s’exécute en continu par défaut.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-113">The MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job runs continuously by default.</span></span> <span data-ttu-id="a1ff3-114">Logiciel de surveillance doit tenir compte de cette planification et pas génèrent des avertissements.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-114">Monitoring software should take this schedule into account and not produce warnings.</span></span>  
  
    -   <span data-ttu-id="a1ff3-115">Le travail MessageBox_Message_Cleanup_BizTalkMsgBoxDb n’est pas activé ou planifié, mais elle est démarrée par le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb toutes les 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-115">The MessageBox_Message_Cleanup_BizTalkMsgBoxDb job is not enabled or scheduled, but it is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job every 10 seconds.</span></span> <span data-ttu-id="a1ff3-116">Par conséquent, cette tâche de ne doit pas être activée, planifiée ou démarrée manuellement.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-116">Therefore, this job should not be enabled, scheduled, or manually started.</span></span>  
  
-   <span data-ttu-id="a1ff3-117">**Vérifiez que le type de démarrage du service de l’Agent SQL Server est correctement configuré.**</span><span class="sxs-lookup"><span data-stu-id="a1ff3-117">**Verify that the Startup type of the SQL Server Agent service is configured correctly**</span></span>  
  
     <span data-ttu-id="a1ff3-118">Vérifiez que le service SQL Server Agent est configuré avec un **Startuptype** de **automatique** , sauf si le service de l’Agent SQL Server est configuré en tant que ressource de cluster sur un cluster Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-118">Verify that the SQL Server Agent service is configured with a **Startuptype** of **Automatic** unless the SQL Server Agent service is configured as a cluster resource on a Windows Server cluster.</span></span> <span data-ttu-id="a1ff3-119">Si le service de l’Agent SQL Server est configuré en tant que ressource de cluster, vous devez configurer le **Startuptype** en tant que **manuel** étant donné que le service est géré par le service de Cluster.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-119">If the SQL Server Agent service is configured as a cluster resource, then you should configure the **Startuptype** as **Manual** since the service will be managed by the Cluster service.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="a1ff3-120">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a1ff3-120">Additional Resources</span></span>  
  
-   <span data-ttu-id="a1ff3-121">Pour plus d’informations sur la surveillance de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travaux SQL Agent, consultez [analyse les travaux de l’Agent SQL Server et les bases de données](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a1ff3-121">For more information about monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent jobs, see [Monitoring SQL Server Agent Jobs and Databases](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md).</span></span>  
  
-   <span data-ttu-id="a1ff3-122">Pour plus d’informations sur les travaux de l’Agent SQL Server qui sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] consultez [« Base de données de Structure et travaux »](http://go.microsoft.com/fwlink/?LinkID=153451) (http://go.microsoft.com/fwlink/?LinkID=153451).</span><span class="sxs-lookup"><span data-stu-id="a1ff3-122">For more information about the SQL Server Agent jobs that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] see ["Database Structure and Jobs"](http://go.microsoft.com/fwlink/?LinkID=153451) (http://go.microsoft.com/fwlink/?LinkID=153451).</span></span>