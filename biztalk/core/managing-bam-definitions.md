---
title: "Gestion des définitions BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions]
- definitions [BAM], managing
- definition files [BAM], managing
- managing [BAM], definitions
- managing [BAM definitions], about managing BAM definitions
ms.assetid: 7aba0e40-b8d3-4afc-9e4c-92392f1f6269
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93cf3d280d0e615442a4141b7fa41f6ee3566490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-definitions"></a><span data-ttu-id="85a5b-102">Gestion  des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-102">Managing BAM Definitions</span></span>
<span data-ttu-id="85a5b-103">Les définitions BAM font partie de l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="85a5b-103">A BAM definition is part of the BAM infrastructure.</span></span> <span data-ttu-id="85a5b-104">Elles définissent les données à suivre et à agréger, ainsi que la vue de l'utilisateur final du processus d'entreprise dans les données de suivi.</span><span class="sxs-lookup"><span data-stu-id="85a5b-104">It defines the data to track and aggregate, as well as the business end user's view on the tracking data.</span></span> <span data-ttu-id="85a5b-105">Les rubriques de cette section indiquent des procédures de gestion des éléments de définitions BAM que sont les activités, les vues, les artefacts et les alertes.</span><span class="sxs-lookup"><span data-stu-id="85a5b-105">The topics in this section give procedures for managing the elements of BAM definitions, which include activities, views, artifacts, and alerts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85a5b-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="85a5b-106">In This Section</span></span>  
  
-   [<span data-ttu-id="85a5b-107">Droits d’utilisateur requis pour la gestion des fichiers de définition BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-107">Required User Rights for Managing BAM Definition Files</span></span>](../core/required-user-rights-for-managing-bam-definition-files.md)  
  
-   [<span data-ttu-id="85a5b-108">Comment déployer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-108">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)  
  
-   [<span data-ttu-id="85a5b-109">Comment supprimer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-109">How to Remove BAM Definitions</span></span>](../core/how-to-remove-bam-activities.md)  
  
-   [<span data-ttu-id="85a5b-110">Comment répertorier les modifications apportées à l’Infrastructure BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-110">How to List Changes to the BAM Infrastructure</span></span>](../core/how-to-list-changes-to-the-bam-infrastructure.md)  
  
-   [<span data-ttu-id="85a5b-111">Affichage des activités BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-111">How to List BAM Activities</span></span>](../core/how-to-list-bam-activities.md)  
  
-   [<span data-ttu-id="85a5b-112">Comment supprimer des activités BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-112">How to Remove BAM Activities</span></span>](../core/how-to-remove-bam-activities.md)  
  
-   [<span data-ttu-id="85a5b-113">Comment répertorier les vues BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-113">How to List BAM Views</span></span>](../core/how-to-list-bam-views.md)  
  
-   [<span data-ttu-id="85a5b-114">Comment supprimer des vues BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-114">How to Remove BAM Views</span></span>](../core/how-to-remove-bam-views.md)  
  
-   [<span data-ttu-id="85a5b-115">Comment activer les alertes</span><span class="sxs-lookup"><span data-stu-id="85a5b-115">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md)  
  
-   [<span data-ttu-id="85a5b-116">Comment désactiver les alertes</span><span class="sxs-lookup"><span data-stu-id="85a5b-116">How to Disable Alerts</span></span>](../core/how-to-disable-alerts.md)  
  
-   [<span data-ttu-id="85a5b-117">Comment supprimer des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-117">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)  
  
-   [<span data-ttu-id="85a5b-118">Comment mettre à jour des artefacts BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-118">How to Update BAM Artifacts</span></span>](../core/how-to-update-bam-artifacts.md)  
  
-   [<span data-ttu-id="85a5b-119">Comment supprimer des artefacts déployés</span><span class="sxs-lookup"><span data-stu-id="85a5b-119">How to Remove Deployed Artifacts</span></span>](../core/how-to-remove-deployed-artifacts.md)  
  
-   [<span data-ttu-id="85a5b-120">Configuration des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-120">Configuring BAM Alerts</span></span>](../core/configuring-bam-alerts.md)  
  
-   [<span data-ttu-id="85a5b-121">La gestion d’exécution des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="85a5b-121">Managing BAM Alert Execution</span></span>](../core/managing-bam-alert-execution.md)  
  
-   [<span data-ttu-id="85a5b-122">Comment modifier la fréquence à laquelle les alertes sont évaluées.</span><span class="sxs-lookup"><span data-stu-id="85a5b-122">How to Change the Frequency With Which Alerts Are Evaluated</span></span>](../core/how-to-change-the-frequency-with-which-alerts-are-evaluated.md)