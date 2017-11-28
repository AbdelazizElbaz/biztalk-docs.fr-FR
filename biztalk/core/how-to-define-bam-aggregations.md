---
title: "Comment définir des agrégations BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- aggregations [BAM], creating
- Excel add-in [BAM], security
- Excel add-in [BAM], creating aggregations
- managing [BAM], creating aggregations
ms.assetid: a5ef3a15-b1de-4099-8e94-64af4b5ec746
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1b5b377611eb8e28088cb2d0c2f2ed6f829de8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-bam-aggregations"></a><span data-ttu-id="10959-102">Définition d'agrégations BAM</span><span class="sxs-lookup"><span data-stu-id="10959-102">How to Define BAM Aggregations</span></span>
<span data-ttu-id="10959-103">L'analyse BAM prend en charge deux types d'agrégation de données :</span><span class="sxs-lookup"><span data-stu-id="10959-103">BAM supports two types of data aggregation:</span></span>  
  
-   <span data-ttu-id="10959-104">Les agrégations de traitement analytique en ligne (OLAP)</span><span class="sxs-lookup"><span data-stu-id="10959-104">Online analytical processing (OLAP) aggregations</span></span>  
  
-   <span data-ttu-id="10959-105">Les agrégations RTA</span><span class="sxs-lookup"><span data-stu-id="10959-105">Real-time aggregations (RTA)</span></span>  
  
 <span data-ttu-id="10959-106">L'analyse BAM utilise Microsoft SQL Analysis Service pour implémenter les agrégations OLAP.</span><span class="sxs-lookup"><span data-stu-id="10959-106">BAM uses Microsoft SQL Server Analysis Services to implement OLAP aggregations.</span></span>  
  
 <span data-ttu-id="10959-107">Vous devez configurer les déclencheurs sur la base de données d'importation principale BAM qui définit les agrégations RTA.</span><span class="sxs-lookup"><span data-stu-id="10959-107">You must configure the triggers on the BAM Primary Import database that define RTA.</span></span>  
  
### <a name="to-define-olap-aggregations"></a><span data-ttu-id="10959-108">Pour définir des agrégations OLAP</span><span class="sxs-lookup"><span data-stu-id="10959-108">To define OLAP aggregations</span></span>  
  
1.  <span data-ttu-id="10959-109">Dans le classeur Excel BAM, créez une vue, ajoutez au moins une dimension et une mesure au rapport de tableau croisé dynamique, désactivez le bouton RTA dans la barre d'outils, et enregistrez le classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-109">In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, clear the RTA toolbar button, and then save the workbook.</span></span>  
  
    -   <span data-ttu-id="10959-110">Pour plus d’informations sur l’ouverture du classeur BAM, la création d’une vue et ajout de dimensions et mesures, consultez [définition d’une vue BAM](../core/defining-a-bam-view.md).</span><span class="sxs-lookup"><span data-stu-id="10959-110">For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see [Defining a BAM View](../core/defining-a-bam-view.md).</span></span>  
  
2.  <span data-ttu-id="10959-111">Déployez le classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-111">Deploy the workbook.</span></span>  
  
    -   <span data-ttu-id="10959-112">Pour déployer le classeur, suivez les instructions de [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="10959-112">To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
3.  <span data-ttu-id="10959-113">Un développeur de solutions utilise la **DirectEventStream** classe pour importer des événements dans la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="10959-113">A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.</span></span>  
  
    -   <span data-ttu-id="10959-114">Pour plus d’informations sur la **DirectEventStream** de classe, consultez [classe DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span><span class="sxs-lookup"><span data-stu-id="10959-114">For information about the **DirectEventStream** class, see [DirectEventStream Class](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span></span>  
  
4.  <span data-ttu-id="10959-115">Exécutez le lot DTS (Data Transformation Services) de cube de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="10959-115">Run the update cube Data Transformation Services (DTS) package.</span></span>  
  
    -   <span data-ttu-id="10959-116">Pour plus d’informations sur l’exécution du lot DTS de mise à jour de cube, consultez [lots DTS BAM](../core/bam-dts-packages.md).</span><span class="sxs-lookup"><span data-stu-id="10959-116">For information about running the update cube DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).</span></span>  
  
5.  <span data-ttu-id="10959-117">Ouvrez la copie de données actives la plus récente du classeur pour afficher les agrégations OLAP.</span><span class="sxs-lookup"><span data-stu-id="10959-117">Open the most recent live data copy of the workbook to see the OLAP aggregations.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="10959-118">Pour des raisons de sécurité, l'analyse BAM ne supprime pas les copies de données actives existantes du classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-118">For security reasons, BAM does not delete existing live data copies of the workbook.</span></span> <span data-ttu-id="10959-119">Au lieu de cela, elle incrémente le nom de fichier de la copie de données actives.</span><span class="sxs-lookup"><span data-stu-id="10959-119">Instead, BAM increments the file name of the live data copy.</span></span>  
  
### <a name="to-define-the-rta"></a><span data-ttu-id="10959-120">Pour définir l'agrégation RTA</span><span class="sxs-lookup"><span data-stu-id="10959-120">To define the RTA</span></span>  
  
1.  <span data-ttu-id="10959-121">Dans le classeur Excel BAM, créez une vue, ajoutez au moins une dimension et une mesure au rapport de tableau croisé dynamique, sélectionnez le bouton RTA dans la barre d'outils, et enregistrez le classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-121">In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, select the RTA toolbar button, and then save the workbook.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="10959-122">Ne définissez pas plusieurs RTA utilisant une même activité BAM.</span><span class="sxs-lookup"><span data-stu-id="10959-122">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="10959-123">Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.</span><span class="sxs-lookup"><span data-stu-id="10959-123">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
    -   <span data-ttu-id="10959-124">Pour plus d’informations sur l’ouverture du classeur BAM, création d’une vue et ajout de dimensions et mesures, consultez « Définition d’une vue activité d’entreprise » et « Définition d’agrégations » dans le *Guide de l’utilisateur des informations travailleurs*.</span><span class="sxs-lookup"><span data-stu-id="10959-124">For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see "Defining a Business Activity View" and "Defining Aggregations" in the *Information Workers User Guide*.</span></span>  
  
2.  <span data-ttu-id="10959-125">Déployez le classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-125">Deploy the workbook.</span></span>  
  
    -   <span data-ttu-id="10959-126">Pour déployer le classeur, suivez les instructions de [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="10959-126">To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
3.  <span data-ttu-id="10959-127">Un développeur de solutions utilise la **DirectEventStream** classe pour importer des événements dans la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="10959-127">A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.</span></span>  

  
4.  <span data-ttu-id="10959-128">Ouvrez la copie de données actives la plus récente du classeur pour afficher les agrégations RTA.</span><span class="sxs-lookup"><span data-stu-id="10959-128">Open the most recent live data copy of the workbook to see the RTAs.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="10959-129">Pour des raisons de sécurité, l'analyse BAM ne supprime pas les copies de données actives existantes du classeur.</span><span class="sxs-lookup"><span data-stu-id="10959-129">For security reasons, BAM does not delete existing live data copies of the workbook.</span></span> <span data-ttu-id="10959-130">Au lieu de cela, elle incrémente le nom de fichier de la copie de données actives.</span><span class="sxs-lookup"><span data-stu-id="10959-130">Instead, BAM increments the file name of the live data copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10959-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10959-131">See Also</span></span>  
 <span data-ttu-id="10959-132">[Lots DTS BAM](../core/bam-dts-packages.md) </span><span class="sxs-lookup"><span data-stu-id="10959-132">[BAM DTS Packages](../core/bam-dts-packages.md) </span></span>  
 <span data-ttu-id="10959-133">[Comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="10959-133">[How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md) </span></span>  
 <span data-ttu-id="10959-134">[Mise à jour des propriétés de chaîne de connexion RTA et OLAP](../core/updating-olap-and-rta-connection-string-properties.md) </span><span class="sxs-lookup"><span data-stu-id="10959-134">[Updating OLAP and RTA Connection String Properties](../core/updating-olap-and-rta-connection-string-properties.md) </span></span>  
 [<span data-ttu-id="10959-135">Gestion de l’Infrastructure dynamique BAM</span><span class="sxs-lookup"><span data-stu-id="10959-135">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)