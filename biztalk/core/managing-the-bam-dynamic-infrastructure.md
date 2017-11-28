---
title: "Gestion de l’Infrastructure dynamique BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- infrastructure, managing [BAM]
- managing [BAM], infrastructure
ms.assetid: af8a76b5-407a-484d-aff4-0d911f88313e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 631a6bb3bab613004e11410a382687147e4adad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bam-dynamic-infrastructure"></a><span data-ttu-id="33556-102">Gestion de l'infrastructure dynamique de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="33556-102">Managing the BAM Dynamic Infrastructure</span></span>
<span data-ttu-id="33556-103">Les fonctions BAM (Business Activity Monitoring) utilisent une infrastructure de traitement analytique en ligne (OLAP) et SQL générée dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="33556-103">Business Activity Monitoring (BAM) features use a dynamically generated SQL and online analytical processing (OLAP) infrastructure.</span></span> <span data-ttu-id="33556-104">Les administrateurs ont recours à l'utilitaire de gestion de l'analyse BAM pour déployer le classeur ou le fichier XML de définition BAM qu'un analyste d'entreprise se charge ensuite de développer.</span><span class="sxs-lookup"><span data-stu-id="33556-104">Administrators use the BAM Management utility to deploy the BAM definition workbook or XML file, which the business analyst develops.</span></span>  
  
 <span data-ttu-id="33556-105">L'infrastructure dynamique de l'analyse BAM est composée des vues du classeur BAM, des déploiements de l'analyse BAM, des lots DTS (Data Transformation Services) BAM et des bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="33556-105">The BAM dynamic infrastructure consists of the BAM workbook views, BAM deployments, the BAM Data Transformation Services (DTS) packages, and the BAM databases.</span></span> <span data-ttu-id="33556-106">Pour plus d’informations sur l’infrastructure dynamique BAM, consultez [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md).</span><span class="sxs-lookup"><span data-stu-id="33556-106">For more information about the BAM dynamic infrastructure, see [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md).</span></span>  
  
 <span data-ttu-id="33556-107">BizTalk Server crée les bases de données BAM suivantes lorsque vous configurez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="33556-107">BizTalk Server creates the following BAM databases when you configure [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:</span></span>  
  
-   <span data-ttu-id="33556-108">Base de données d'importation principale BAM (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="33556-108">BAM Primary Import (BAMPrimaryImport) database</span></span>  
  
-   <span data-ttu-id="33556-109">Base de données de schémas en étoile BAM (BAMStarSchema) (facultative)</span><span class="sxs-lookup"><span data-stu-id="33556-109">BAM Star Schema (BAMStarSchema) database (optional)</span></span>  
  
-   <span data-ttu-id="33556-110">Base de données d'analyse BAM (BAMAnalysis) (facultative)</span><span class="sxs-lookup"><span data-stu-id="33556-110">BAM Analysis (BAMAnalysis) database (optional)</span></span>  
  
-   <span data-ttu-id="33556-111">Base de données des archives BAM (BAMArchive)</span><span class="sxs-lookup"><span data-stu-id="33556-111">BAM Archive (BAMArchive) database</span></span>  
  
 <span data-ttu-id="33556-112">Pour plus d’informations sur les bases de données BAM, consultez [la gestion des bases de données BAM](../core/managing-bam-databases.md).</span><span class="sxs-lookup"><span data-stu-id="33556-112">For information about the BAM databases, see [Managing BAM Databases](../core/managing-bam-databases.md).</span></span>  
  
 <span data-ttu-id="33556-113">Les administrateurs accomplissent les tâches de gestion décrites dans cette section pour l'infrastructure de l'analyse BAM :</span><span class="sxs-lookup"><span data-stu-id="33556-113">Administrators perform the following management tasks for the BAM infrastructure, which are described in this section:</span></span>  
  
-   <span data-ttu-id="33556-114">Déployer et annuler le déploiement de définitions et de vues BAM</span><span class="sxs-lookup"><span data-stu-id="33556-114">Deploy and undeploy BAM definitions and views</span></span>  
  
-   <span data-ttu-id="33556-115">Gérer l'accès utilisateur aux vues BAM</span><span class="sxs-lookup"><span data-stu-id="33556-115">Manage user access to BAM views</span></span>  
  
-   <span data-ttu-id="33556-116">Exécuter les lots DTS BAM</span><span class="sxs-lookup"><span data-stu-id="33556-116">Run the BAM DTS packages</span></span>  
  
-   <span data-ttu-id="33556-117">Sauvegarder les bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="33556-117">Back up the BAM databases</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33556-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33556-118">In This Section</span></span>  
  
-   [<span data-ttu-id="33556-119">Gestion des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="33556-119">Managing BAM Definitions</span></span>](../core/managing-bam-definitions.md)
  
-   [<span data-ttu-id="33556-120">Gestion de la sécurité de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="33556-120">Managing BAM Security</span></span>](../core/managing-bam-security.md)  
  
-   [<span data-ttu-id="33556-121">Gestion des agrégations</span><span class="sxs-lookup"><span data-stu-id="33556-121">Managing Aggregations</span></span>](../core/managing-aggregations.md) 
  
-   [<span data-ttu-id="33556-122">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="33556-122">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)
  
## <a name="see-also"></a><span data-ttu-id="33556-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33556-123">See Also</span></span>  
 [<span data-ttu-id="33556-124">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="33556-124">Managing BAM</span></span>](../core/managing-bam.md)