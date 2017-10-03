---
title: "Liste de vérification : Archivage et la purge de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], checklist
- checklists, purging [Tracking database]
- purging, checklist
- checklists, archiving [Tracking database]
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22e97ac12e6b6b304318f57f309767ec7c63815f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-archiving-and-purging-the-biztalk-tracking-database"></a><span data-ttu-id="c93ce-102">Liste de vérification : Archivage et la purge de la base de données de suivi de BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-102">Checklist: Archiving and Purging the BizTalk Tracking Database</span></span>
|<span data-ttu-id="c93ce-103">Étape</span><span class="sxs-lookup"><span data-stu-id="c93ce-103">Step</span></span>|<span data-ttu-id="c93ce-104">Référence</span><span class="sxs-lookup"><span data-stu-id="c93ce-104">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="c93ce-105">Lisez la présentation relative à l'archivage et à la purge afin de vous familiariser avec l'archivage et la purge des données de suivi.</span><span class="sxs-lookup"><span data-stu-id="c93ce-105">Read the Archiving and Purging overview to become more familiar with the process of archiving and purging tracking data.</span></span>|[<span data-ttu-id="c93ce-106">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-106">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="c93ce-107">Bien qu'il vous soit possible d'exécuter le travail de purge et d'archivage DTA en recourant aux informations d'identification que vous avez utilisées pour vous connecter, il est préférable, pour une meilleure sécurité, que vous configuriez le rôle BTS_BACKUP_USERS à l'aide des informations d'identification SQL Server nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c93ce-107">Although you can run the DTA Purge and Archive job using your logon credentials, for added security, you should configure the BTS_BACKUP_USERS role with the necessary SQL Server credentials to run the DTA Purge and Archive job.</span></span> <span data-ttu-id="c93ce-108">Ainsi, il est inutile d'étendre les privilèges.</span><span class="sxs-lookup"><span data-stu-id="c93ce-108">This helps to prevent elevation of privileges.</span></span>|[<span data-ttu-id="c93ce-109">Comment configurer le rôle BTS_BACKUP_USERS pour l’archivage et la purge des données de la base de données de suivi de BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-109">How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|<span data-ttu-id="c93ce-110">Configurez le travail de purge et d'archivage DTA.</span><span class="sxs-lookup"><span data-stu-id="c93ce-110">Configure the DTA Purge and Archive job.</span></span>|[<span data-ttu-id="c93ce-111">Configuration du travail de purge et d’archivage DTA</span><span class="sxs-lookup"><span data-stu-id="c93ce-111">How to Configure the DTA Purge and Archive Job</span></span>](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|<span data-ttu-id="c93ce-112">Exécutez le travail de purge et d'archivage DTA en vue d'archiver les données dans la base de données des suivis BizTalk (BizTalkDTADb) et de purger les données anciennes.</span><span class="sxs-lookup"><span data-stu-id="c93ce-112">Run the DTA Purge and Archive job, which archives the data in your BizTalk Tracking (BizTalkDTADb) database and purges old data.</span></span>|[<span data-ttu-id="c93ce-113">Purge des données de la base de données de suivi de BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-113">How to Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="c93ce-114">Si vous le souhaitez, purgez manuellement les données de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="c93ce-114">Optionally, you can manually purge data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>|[<span data-ttu-id="c93ce-115">Purge manuelle des données à partir de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-115">How to Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="c93ce-116">Activez la validation automatique des données archivées de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="c93ce-116">Enable automatic validation of the archived data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>|[<span data-ttu-id="c93ce-117">Comment activer la Validation de l’archivage automatique</span><span class="sxs-lookup"><span data-stu-id="c93ce-117">How to Enable Automatic Archive Validation</span></span>](../core/how-to-enable-automatic-archive-validation.md)|  
|<span data-ttu-id="c93ce-118">Copiez les messages de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="c93ce-118">Copy tracked messages into the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="c93ce-119">Cette opération est obligatoire pour pouvoir purger les données avec le travail DTA Purge and Archive.</span><span class="sxs-lookup"><span data-stu-id="c93ce-119">This is required in order to purge data using the DTA Purge and Archive job.</span></span>|[<span data-ttu-id="c93ce-120">Comment copier des Messages suivis dans la base de données de suivi de BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-120">How to Copy Tracked Messages into the BizTalk Tracking Database</span></span>](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c93ce-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c93ce-121">See Also</span></span>  
 [<span data-ttu-id="c93ce-122">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="c93ce-122">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)