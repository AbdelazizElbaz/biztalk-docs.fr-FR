---
title: "Récupération d’un ordinateur exécutant BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55af6d6-f11a-46e4-9b8e-0a1ca35998c4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74d9234fa1d3a572afadcc8e8ba90dd4735eb5c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="recovering-a-computer-running-biztalk-server"></a><span data-ttu-id="d7ef3-102">Récupération d'un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d7ef3-102">Recovering a Computer Running BizTalk Server</span></span>
<span data-ttu-id="d7ef3-103">Pour récupérer un ordinateur exécutant BizTalk Server, vous devez pouvoir accéder aux bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-103">In order to recover a computer running BizTalk Server, you must be able to access the BizTalk Server databases.</span></span> <span data-ttu-id="d7ef3-104">Si nécessaire, restaurez les bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-104">If necessary, restore the BizTalk Server databases.</span></span> <span data-ttu-id="d7ef3-105">En outre, avant de récupérer l'ordinateur exécutant BizTalk Server, vous devez réinstaller BizTalk Server et tous les composants requis.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-105">In addition, before you can recover the computer running BizTalk Server, you must reinstall BizTalk Server and all of the prerequisites.</span></span>  
  
 <span data-ttu-id="d7ef3-106">Une fois ces étapes accomplies, vous devez suivre les procédures décrites dans cette section pour récupérer votre serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-106">When these steps are complete, you can use the procedures in this section to recover your BizTalk server.</span></span> <span data-ttu-id="d7ef3-107">Les procédures à suivre pour récupérer BizTalk Server dépendent de l'édition que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-107">The procedures you must follow to recover BizTalk Server depend on the edition you are using.</span></span> <span data-ttu-id="d7ef3-108">Le tableau suivant répertorie les procédures requises pour chaque édition.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-108">The following table lists the required procedures for each edition.</span></span>  
  
|<span data-ttu-id="d7ef3-109">Tâche</span><span class="sxs-lookup"><span data-stu-id="d7ef3-109">Task</span></span>|<span data-ttu-id="d7ef3-110">Standard</span><span class="sxs-lookup"><span data-stu-id="d7ef3-110">Standard</span></span>|<span data-ttu-id="d7ef3-111">Développeur</span><span class="sxs-lookup"><span data-stu-id="d7ef3-111">Developer</span></span>|<span data-ttu-id="d7ef3-112">Enterprise</span><span class="sxs-lookup"><span data-stu-id="d7ef3-112">Enterprise</span></span>|  
|----------|--------------|---------------|----------------|  
|<span data-ttu-id="d7ef3-113">**Comment restaurer le magasin de certificats**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-113">**How to Restore the Certificate Store**</span></span>|<span data-ttu-id="d7ef3-114">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-114">**X**</span></span>|||  
|<span data-ttu-id="d7ef3-115">**Comment récupérer Enterprise Single Sign-On (SSO)**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-115">**How to Recover Enterprise Single Sign-On (SSO)**</span></span>|<span data-ttu-id="d7ef3-116">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-116">**X**</span></span>|<span data-ttu-id="d7ef3-117">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-117">**X**</span></span>|<span data-ttu-id="d7ef3-118">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-118">**X**</span></span>|  
|<span data-ttu-id="d7ef3-119">**Comment récupérer le groupe BizTalk**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-119">**How to Recover the BizTalk Group**</span></span>|<span data-ttu-id="d7ef3-120">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-120">**X**</span></span>|<span data-ttu-id="d7ef3-121">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-121">**X**</span></span>|<span data-ttu-id="d7ef3-122">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-122">**X**</span></span>|  
|<span data-ttu-id="d7ef3-123">**Comment récupérer la Configuration de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-123">**How to Recover the BizTalk Server Configuration**</span></span>|<span data-ttu-id="d7ef3-124">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-124">**X**</span></span>|<span data-ttu-id="d7ef3-125">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-125">**X**</span></span>|<span data-ttu-id="d7ef3-126">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-126">**X**</span></span>|  
|<span data-ttu-id="d7ef3-127">**Comment récupérer les alertes BAM**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-127">**How to Recover BAM Alerts**</span></span><br /><br /> <span data-ttu-id="d7ef3-128">Facultatif, sauf si vous utilisez BAM.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-128">Not required unless you're using BAM.</span></span>|<span data-ttu-id="d7ef3-129">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-129">**X**</span></span>|<span data-ttu-id="d7ef3-130">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-130">**X**</span></span>|<span data-ttu-id="d7ef3-131">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-131">**X**</span></span>|  
|<span data-ttu-id="d7ef3-132">**Comment récupérer le portail BAM**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-132">**How to Recover the BAM Portal**</span></span><br /><br /> <span data-ttu-id="d7ef3-133">Facultatif, sauf si vous utilisez BAM.</span><span class="sxs-lookup"><span data-stu-id="d7ef3-133">Not required unless you're using BAM.</span></span>|<span data-ttu-id="d7ef3-134">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-134">**X**</span></span>|<span data-ttu-id="d7ef3-135">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-135">**X**</span></span>|<span data-ttu-id="d7ef3-136">**X**</span><span class="sxs-lookup"><span data-stu-id="d7ef3-136">**X**</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="d7ef3-137">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d7ef3-137">In This Section</span></span>  
  
-   [<span data-ttu-id="d7ef3-138">Comment restaurer le magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="d7ef3-138">How to Restore the Certificate Store</span></span>](../core/how-to-restore-the-certificate-store.md)  
  
-   [<span data-ttu-id="d7ef3-139">Comment récupérer Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d7ef3-139">How to Recover Enterprise Single Sign-On</span></span>](../core/how-to-recover-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="d7ef3-140">Comment récupérer le groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="d7ef3-140">How to Recover the BizTalk Group</span></span>](../core/how-to-recover-the-biztalk-group.md)  
  
-   [<span data-ttu-id="d7ef3-141">Comment récupérer la Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d7ef3-141">How to Recover the BizTalk Server Configuration</span></span>](../core/how-to-recover-the-biztalk-server-configuration.md)  
  
-   [<span data-ttu-id="d7ef3-142">Comment récupérer les alertes BAM</span><span class="sxs-lookup"><span data-stu-id="d7ef3-142">How to Recover BAM Alerts</span></span>](../core/how-to-recover-bam-alerts.md)  
  
-   [<span data-ttu-id="d7ef3-143">Comment récupérer le portail BAM</span><span class="sxs-lookup"><span data-stu-id="d7ef3-143">How to Recover the BAM Portal</span></span>](../core/how-to-recover-the-bam-portal.md)