---
title: "Surveiller les bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f137fc5-0e95-4952-8465-008771a1a377
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d0ad2f450a859bc7c56a4829ba5315745fbf80a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitor-the-biztalk-server-databases"></a><span data-ttu-id="715a4-102">Surveiller les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="715a4-102">Monitor the BizTalk Server Databases</span></span>
<span data-ttu-id="715a4-103">Vous pouvez exécuter la tâche d’analyse BizTalk Server, SQL Agent pour identifier les problèmes connus dans les bases de données de gestion, MessageBox ou DTA.</span><span class="sxs-lookup"><span data-stu-id="715a4-103">You can run the Monitor BizTalk Server SQL Agent job to identify any known issues in Management, Message Box, or DTA databases.</span></span> <span data-ttu-id="715a4-104">La fonction est créée lorsque vous configurez un groupe BizTalk dans la console Administration de BizTalk Server ou procédez à une mise à niveau de BizTalk à partir d'une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="715a4-104">The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.</span></span>  
  
## <a name="the-monitor-biztalk-server-job"></a><span data-ttu-id="715a4-105">Le travail de surveillance de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="715a4-105">The Monitor BizTalk Server Job</span></span>  
 <span data-ttu-id="715a4-106">La fonction Analyser BizTalk Server recherche les problèmes suivants dans les bases de données Gestion, MessageBox ou DTA :</span><span class="sxs-lookup"><span data-stu-id="715a4-106">The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="715a4-107">La fonction Analyser BizTalk Server recherche uniquement d'éventuels problèmes.</span><span class="sxs-lookup"><span data-stu-id="715a4-107">The Monitor BizTalk Server job only scans for issues.</span></span> <span data-ttu-id="715a4-108">Elle ne corrige pas les problèmes trouvés.</span><span class="sxs-lookup"><span data-stu-id="715a4-108">It does not fix the issues found.</span></span>  
  
-   <span data-ttu-id="715a4-109">Messages sans références</span><span class="sxs-lookup"><span data-stu-id="715a4-109">Messages without any references</span></span>  
  
-   <span data-ttu-id="715a4-110">Messages sans nombres de références</span><span class="sxs-lookup"><span data-stu-id="715a4-110">Messages without reference counts</span></span>  
  
-   <span data-ttu-id="715a4-111">Messages avec un nombre de références inférieur à 0</span><span class="sxs-lookup"><span data-stu-id="715a4-111">Messages with reference count less than 0</span></span>  
  
-   <span data-ttu-id="715a4-112">Références de messages sans lignes de mise en file d'attente</span><span class="sxs-lookup"><span data-stu-id="715a4-112">Message references without spool rows</span></span>  
  
-   <span data-ttu-id="715a4-113">Références de messages sans instances</span><span class="sxs-lookup"><span data-stu-id="715a4-113">Message references without instances</span></span>  
  
-   <span data-ttu-id="715a4-114">État d'instance sans instances</span><span class="sxs-lookup"><span data-stu-id="715a4-114">Instance state without instances</span></span>  
  
-   <span data-ttu-id="715a4-115">Abonnements d'instance sans instances correspondantes</span><span class="sxs-lookup"><span data-stu-id="715a4-115">Instance subscriptions without corresponding instances</span></span>  
  
-   <span data-ttu-id="715a4-116">Instances de service DTA orphelines</span><span class="sxs-lookup"><span data-stu-id="715a4-116">Orphaned DTA service instances</span></span>  
  
-   <span data-ttu-id="715a4-117">Exceptions d'instances de service DTA orphelines</span><span class="sxs-lookup"><span data-stu-id="715a4-117">Orphaned DTA service instance exceptions</span></span>  
  
-   <span data-ttu-id="715a4-118">Le service TDDS n’est pas exécuté sur n’importe quelle instance d’hôte lorsque l’option de suivi global est activée.</span><span class="sxs-lookup"><span data-stu-id="715a4-118">TDDS is not running on any host instance when global tracking option is enabled</span></span>  
  
 <span data-ttu-id="715a4-119">La fonction Analyser BizTalk Server est configurée et automatisée pour s'exécuter une fois par semaine.</span><span class="sxs-lookup"><span data-stu-id="715a4-119">The Monitor BizTalk Server job is configured and automated to run once in a week.</span></span> <span data-ttu-id="715a4-120">Étant donné que le travail est nécessitant, il est recommandé que vous planifiez son exécution pendant les périodes de temps d’arrêt ou de faible trafic.</span><span class="sxs-lookup"><span data-stu-id="715a4-120">Since the job is computationally intensive, we recommended that you schedule it to run during periods of downtime or low traffic.</span></span>  
<span data-ttu-id="715a4-121">La tâche échoue si elle rencontre des problèmes ; la chaîne d’erreur contient le nombre de problèmes rencontrés.</span><span class="sxs-lookup"><span data-stu-id="715a4-121">The job fails if it encounters any issues; the error string returned contains the number of issues found.</span></span> <span data-ttu-id="715a4-122">Sinon, elle réussit.</span><span class="sxs-lookup"><span data-stu-id="715a4-122">Else, it runs successfully.</span></span> <span data-ttu-id="715a4-123">Vous pouvez voir les détails dans l'historique de la fonction.</span><span class="sxs-lookup"><span data-stu-id="715a4-123">You can see the details in the job history.</span></span> <span data-ttu-id="715a4-124">Si vous exécutez la tâche avec des privilèges d’administrateur, la chaîne d’erreur est consignée dans l’historique des travaux et le journal d’Application SQL Server.</span><span class="sxs-lookup"><span data-stu-id="715a4-124">If you run the job with Administrator privileges, the error string will be logged to both the job history and the SQL Server Application log.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="715a4-125">Échec de ce travail ne constitue pas nécessairement un problème critique, mais plutôt d’un problème qui doit être examiné et traité en tant que partie de la maintenance régulière des bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="715a4-125">Failure of this job does not necessarily constitute a critical issue, but rather an issue that should be investigated and addressed as part of regular maintenance of the BizTalk Server databases.</span></span> <span data-ttu-id="715a4-126">Cette tâche échoue à la conception dans l’événement qu’il détecte un des problèmes répertoriés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="715a4-126">This job fails by design in the event it discovers one of the issues listed above.</span></span> <span data-ttu-id="715a4-127">Pour plus d’informations sur les problèmes répertoriés ci-dessus et pour accéder aux utilitaires qui sont couramment utilisées par les Services de Support technique Microsoft pour résoudre ces problèmes, voir [à l’aide de BizTalk Terminator pour résoudre les problèmes identifiés par BizTalk Server MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=210367) (http://go.microsoft.com/fwlink/?LinkId=210367).</span><span class="sxs-lookup"><span data-stu-id="715a4-127">For more information about the issues listed above and to access utilities that are commonly used by Microsoft Product Support Services to troubleshoot these issues please see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=210367) (http://go.microsoft.com/fwlink/?LinkId=210367).</span></span>