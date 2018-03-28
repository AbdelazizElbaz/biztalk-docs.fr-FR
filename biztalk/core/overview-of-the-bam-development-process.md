---
title: Vue d’ensemble du processus de développement BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 098db3f6-2a61-4cc8-88c7-2299c2e2a55e
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78ae5f1c61f2a00359e88acd75c093e2b6c2fb91
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="overview-of-the-bam-development-process"></a><span data-ttu-id="78708-102">Vue d'ensemble du processus de développement BAM</span><span class="sxs-lookup"><span data-stu-id="78708-102">Overview of the BAM Development Process</span></span>
<span data-ttu-id="78708-103">Cette rubrique décrit le processus de développement ainsi que la base de données et les tables où sont stockées les données BAM.</span><span class="sxs-lookup"><span data-stu-id="78708-103">This topic describes the development process and the database and tables that store BAM data.</span></span>  
  
## <a name="prerequisites-for-developing-with-bam"></a><span data-ttu-id="78708-104">Conditions préalables pour le développement à l'aide des outils BAM</span><span class="sxs-lookup"><span data-stu-id="78708-104">Prerequisites for Developing with BAM</span></span>  
 <span data-ttu-id="78708-105">Pour commencer à développer à l'aide des outils BAM, vous devez remplir les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="78708-105">Note the following prerequisites before you begin developing with BAM:</span></span>  
  
-   <span data-ttu-id="78708-106">Pour instrumenter une application, vous devez avoir déployé une activité.</span><span class="sxs-lookup"><span data-stu-id="78708-106">To instrument an application you must have an activity deployed.</span></span>  
  
-   <span data-ttu-id="78708-107">Vous devez disposer de droits DBO dans les bases de données du serveur SQL et être membre du contexte de sécurité BAM Event Writer Role.</span><span class="sxs-lookup"><span data-stu-id="78708-107">You must have DBO rights to the SQL Server databases and be a member of the BAM Event Writer Role security context.</span></span>  
  
-   <span data-ttu-id="78708-108">Vous devez utiliser Microsoft .NET 4 pour développer votre application.</span><span class="sxs-lookup"><span data-stu-id="78708-108">You must use Microsoft .NET 4 to develop your application.</span></span> <span data-ttu-id="78708-109">Bien que vous puissiez utiliser n'importe quel langage .NET, il est recommandé d'utiliser C#.</span><span class="sxs-lookup"><span data-stu-id="78708-109">You can use any .NET language, although we recommend that you use C#.</span></span>  
  
-   <span data-ttu-id="78708-110">Vous devez avoir installé Microsoft.BizTalk.BAM.EventObservation.dll sur votre ordinateur :</span><span class="sxs-lookup"><span data-stu-id="78708-110">You must have the Microsoft.BizTalk.BAM.EventObservation.dll installed on your computer.</span></span> <span data-ttu-id="78708-111">Vous pouvez obtenir le DLL de deux manières :</span><span class="sxs-lookup"><span data-stu-id="78708-111">You can obtain the DLL in two ways:</span></span>  
  
    -   <span data-ttu-id="78708-112">Utilisez le gestionnaire de configuration de BizTalk Server pour installer les outils BAM.</span><span class="sxs-lookup"><span data-stu-id="78708-112">Use the BizTalk Server Configuration Manager to install the BAM tools.</span></span> <span data-ttu-id="78708-113">Nous vous recommandons d'utiliser le gestionnaire de configuration car il inscrit dans le registre des entrées qui simplifient les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="78708-113">We recommend that you use the Configuration Manager because it places appropriate entries in the registry that facilitate upgrades.</span></span> <span data-ttu-id="78708-114">Pour plus d’informations sur la configuration BAM, consultez [configuration BAM Tools Using the Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=70561) (http://go.microsoft.com/fwlink/?LinkId=70561).</span><span class="sxs-lookup"><span data-stu-id="78708-114">For more information about configuring BAM, see [Configuring BAM Tools Using the Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=70561) (http://go.microsoft.com/fwlink/?LinkId=70561).</span></span>  
  
    -   <span data-ttu-id="78708-115">Copiez le DLL à partir d'un ordinateur sur lequel il a déjà été installé.</span><span class="sxs-lookup"><span data-stu-id="78708-115">Copy the DLL from a computer on which they have already been installed.</span></span> <span data-ttu-id="78708-116">Le DLL se trouve dans Microsoft BizTalk Server \<version\>dossier \Tracking.</span><span class="sxs-lookup"><span data-stu-id="78708-116">The DLL resides in the Microsoft BizTalk Server \<version\>\Tracking folder.</span></span>  
  
## <a name="bam-development-process"></a><span data-ttu-id="78708-117">Processus de développement BAM</span><span class="sxs-lookup"><span data-stu-id="78708-117">BAM Development Process</span></span>  
 <span data-ttu-id="78708-118">L'illustration suivante décrit le flux de développement BAM.</span><span class="sxs-lookup"><span data-stu-id="78708-118">The following figure describes the BAM development flow.</span></span>  
  
 <span data-ttu-id="78708-119">![Flux de travail de développement BAM](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")</span><span class="sxs-lookup"><span data-stu-id="78708-119">![BAM development work flow](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")</span></span>  
  
 <span data-ttu-id="78708-120">La procédure suivante décrit les étapes de développement de base d'une solution à l'aide des outils BAM.</span><span class="sxs-lookup"><span data-stu-id="78708-120">The following procedure lists the basic steps for developing a solution with BAM.</span></span>  
  
#### <a name="to-develop-a-bam-enabled-solution"></a><span data-ttu-id="78708-121">Pour développer une solution BAM</span><span class="sxs-lookup"><span data-stu-id="78708-121">To develop a BAM-enabled solution</span></span>  
  
1.  <span data-ttu-id="78708-122">Créez un modèle d'observation à l'aide du complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="78708-122">Create an observation model with the BAM Add-in for Excel.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78708-123">Exemples des étapes de cette procédure sont accessibles dans l’API BAM (exemple BizTalk Server) à [ http://go.microsoft.com/fwlink/?LinkId=69968 ](http://go.microsoft.com/fwlink/?LinkId=69968).</span><span class="sxs-lookup"><span data-stu-id="78708-123">Examples of the steps noted in this procedure can be found in the BAM API (BizTalk Server sample) at [http://go.microsoft.com/fwlink/?LinkId=69968](http://go.microsoft.com/fwlink/?LinkId=69968).</span></span>  
  
2.  <span data-ttu-id="78708-124">Utilisez l'utilitaire de gestion de l'analyse BAM pour déployer l'activité dans la PID.</span><span class="sxs-lookup"><span data-stu-id="78708-124">Use the BAM Management utility to deploy the activity to the PID.</span></span>  
  
3.  <span data-ttu-id="78708-125">Instrumentez l'application en ajoutant votre code BAM EventStream.</span><span class="sxs-lookup"><span data-stu-id="78708-125">Instrument the application by adding your BAM EventStream code.</span></span>  
  
4.  <span data-ttu-id="78708-126">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="78708-126">Run the application.</span></span> <span data-ttu-id="78708-127">À ce moment-là, le code va :</span><span class="sxs-lookup"><span data-stu-id="78708-127">When you do this, the code will:</span></span>  
  
    -   <span data-ttu-id="78708-128">Ajouter un enregistrement de l’espace réservé dans la table BAM_\<*nom de l’activité*\>_Active table.</span><span class="sxs-lookup"><span data-stu-id="78708-128">Add a placeholder record to the BAM_\<*activity name*\>_Active table.</span></span>  
  
    -   <span data-ttu-id="78708-129">Mettre à jour les éléments de données dans l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="78708-129">Update the data items in the record.</span></span>  
  
    -   <span data-ttu-id="78708-130">Terminer l’activité et déplacer l’enregistrement dans la table BAM_\<\* nom d’activité \*\*\>_terminée.</span><span class="sxs-lookup"><span data-stu-id="78708-130">End the activity and move the record to the BAM_\<\*activity name\*\*\>_completed table.</span></span>  
  
## <a name="where-bam-data-is-stored"></a><span data-ttu-id="78708-131">Espace de stockage des données BAM</span><span class="sxs-lookup"><span data-stu-id="78708-131">Where BAM Data Is Stored</span></span>  
 <span data-ttu-id="78708-132">L'analyse BAM fournit l'espace de noms EventObservation qui contient les classes EventStream utilisées dans la gestion des événements BAM.</span><span class="sxs-lookup"><span data-stu-id="78708-132">BAM provides the EventObservation namespace that contains the EventStream classes that are used to handle BAM events.</span></span>  
  
 <span data-ttu-id="78708-133">Les données de suivi BAM sont stockées dans la base de données d'importation principale BAM (PID).</span><span class="sxs-lookup"><span data-stu-id="78708-133">BAM tracking data is stored in the BAM Primary Import database (PID).</span></span> <span data-ttu-id="78708-134">Lorsque vous déployez un modèle d'observation à l'aide de l'utilitaire de gestion de l'analyse BAM, les cinq tables suivantes sont créées dans la PID.</span><span class="sxs-lookup"><span data-stu-id="78708-134">When you deploy an observation model using the BAM Management utility, the following five tables are created in the PID.</span></span>  
  
|<span data-ttu-id="78708-135">Nom</span><span class="sxs-lookup"><span data-stu-id="78708-135">Name</span></span>|<span data-ttu-id="78708-136"> Description</span><span class="sxs-lookup"><span data-stu-id="78708-136">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="78708-137">Table active</span><span class="sxs-lookup"><span data-stu-id="78708-137">Active table</span></span>|<span data-ttu-id="78708-138">Nommée bam_\<*nom de l’activité*\>_Active, cette table contient les activités de ce type qui n’ont pas encore terminée.</span><span class="sxs-lookup"><span data-stu-id="78708-138">Named bam_\<*activity name*\>_Active, this table holds the activities of this type that have not yet completed.</span></span>|  
|<span data-ttu-id="78708-139">Table des relations actives</span><span class="sxs-lookup"><span data-stu-id="78708-139">Active relationships table</span></span>|<span data-ttu-id="78708-140">Nommée bam_\<*nom de l’activité*\>_relationsactives, cette table contient les activités associées à l’activité qui n’ont pas encore terminée.</span><span class="sxs-lookup"><span data-stu-id="78708-140">Named bam_\<*activity name*\>_ActiveRelationships, this table contains the related activities for the activity that have not yet completed.</span></span>|  
|<span data-ttu-id="78708-141">Table des continuations</span><span class="sxs-lookup"><span data-stu-id="78708-141">Continuations table</span></span>|<span data-ttu-id="78708-142">Nommée bam_\<*nom de l’activité*\>_continuations, ce tableau répertorie les activités de continuation pour l’activité.</span><span class="sxs-lookup"><span data-stu-id="78708-142">Named bam_\<*activity name*\>_continuations, this table lists the continuations activities for the activity.</span></span>|  
|<span data-ttu-id="78708-143">Table terminée</span><span class="sxs-lookup"><span data-stu-id="78708-143">Completed table</span></span>|<span data-ttu-id="78708-144">Nommée bam_\<*nom de l’activité*\>_completed.</span><span class="sxs-lookup"><span data-stu-id="78708-144">Named bam_\<*activity name*\>_completed.</span></span>|  
|<span data-ttu-id="78708-145">Table des relations terminées</span><span class="sxs-lookup"><span data-stu-id="78708-145">Completed Relationships table</span></span>|<span data-ttu-id="78708-146">Nommée bam_\<*nom de l’activité*\>_relationsterminées, cette table contient les activités terminées associées à l’activité.</span><span class="sxs-lookup"><span data-stu-id="78708-146">Named bam_\<*activity name*\>_CompletedRelationships, this table contains the completed related activities for the activity.</span></span>|  
  
 <span data-ttu-id="78708-147">Vous pouvez capturer quatre types de données dans une activité BAM :</span><span class="sxs-lookup"><span data-stu-id="78708-147">You capture four types of data in a BAM activity:</span></span>  
  
-   <span data-ttu-id="78708-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="78708-148">String</span></span>  
  
-   <span data-ttu-id="78708-149">Données/Heure (communément appelées étapes majeures)</span><span class="sxs-lookup"><span data-stu-id="78708-149">Data/Time (commonly referred to as milestones)</span></span>  
  
-   <span data-ttu-id="78708-150">Entier</span><span class="sxs-lookup"><span data-stu-id="78708-150">Integer</span></span>  
  
-   <span data-ttu-id="78708-151">Float</span><span class="sxs-lookup"><span data-stu-id="78708-151">Float</span></span>