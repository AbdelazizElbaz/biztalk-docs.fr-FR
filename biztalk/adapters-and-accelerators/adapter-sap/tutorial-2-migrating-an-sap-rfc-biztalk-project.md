---
title: "Didacticiel 2 : Migration d’un projet BizTalk RFC SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, BizTalk project from previous version of the SAP adapter
- migration
- migrating, SAP RFC BizTalk project
ms.assetid: b4943613-23d2-4869-b033-ec07daabfac5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80b5d53904b96267b1877310aa3480ce34a1bedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-migrating-an-sap-rfc-biztalk-project"></a><span data-ttu-id="732b6-102">Didacticiel 2 : Migration d’un projet BizTalk RFC SAP</span><span class="sxs-lookup"><span data-stu-id="732b6-102">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>
<span data-ttu-id="732b6-103">La version précédente de l’adaptateur SAP fournis avec Microsoft BizTalk Server est différente de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans nombreux aspects, notamment :</span><span class="sxs-lookup"><span data-stu-id="732b6-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="732b6-104">L’expérience au moment du design de création d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="732b6-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="732b6-105">L’expérience de récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="732b6-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="732b6-106">Nom de fichier de schéma et l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="732b6-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="732b6-107">Mappages de type de données.</span><span class="sxs-lookup"><span data-stu-id="732b6-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="732b6-108">Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="732b6-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="732b6-109">Configuration des ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="732b6-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="732b6-110">Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur SAP](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span><span class="sxs-lookup"><span data-stu-id="732b6-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
 <span data-ttu-id="732b6-111">Toutefois, vous pouvez apporter des modifications au projet BizTalk créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="732b6-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="732b6-112">Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="732b6-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="732b6-113">Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur SAP sera appelée vPrev l’adaptateur SAP.</span><span class="sxs-lookup"><span data-stu-id="732b6-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="732b6-114">De même, un projet BizTalk qui utilise l’adaptateur SAP vPrev est être appelé en tant que projet de BizTalk vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="732b6-115">Exemple utilisé pour le didacticiel</span><span class="sxs-lookup"><span data-stu-id="732b6-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="732b6-116">Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui appelle une commande RFC dans un système SAP (SAP_RFC_Migration).</span><span class="sxs-lookup"><span data-stu-id="732b6-116">This tutorial is based upon a sample (SAP_RFC_Migration) that demonstrates how to migrate a vPrev BizTalk project that invokes an RFC in an SAP system.</span></span> <span data-ttu-id="732b6-117">L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="732b6-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="732b6-118">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="732b6-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="732b6-119">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="732b6-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="732b6-120">Vous devez disposer d’un projet BizTalk de vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="732b6-121">Ce didacticiel implique un projet BizTalk qui appelle la RFC SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="732b6-121">This tutorial involves a BizTalk project that invokes the SD_RFC_CUSTOMER_GET RFC.</span></span>  
  
-   <span data-ttu-id="732b6-122">Vous devez disposer d’un message de demande à effectuer pour appeler le RFC SD_RFC_CUSTOMER_GET à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-122">You must have a request message to perform to invoke the SD_RFC_CUSTOMER_GET RFC using the vPrev SAP adapter.</span></span> <span data-ttu-id="732b6-123">Le message de demande doit être conforme au schéma de la RFC généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-123">The request message must conform to the schema of the RFC generated using the vPrev SAP adapter.</span></span> <span data-ttu-id="732b6-124">L’exemple fourni pour ce didacticiel contient ce message de demande.</span><span class="sxs-lookup"><span data-stu-id="732b6-124">The sample provided for this tutorial contains this request message.</span></span>  
  
-   [<span data-ttu-id="732b6-125">Créer le fichier de clé de nom fort et découvrez les outils</span><span class="sxs-lookup"><span data-stu-id="732b6-125">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="732b6-126">Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="732b6-126">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="732b6-127">Les principaux composants d’un projet BizTalk de vPrev pour appeler une commande RFC sont :</span><span class="sxs-lookup"><span data-stu-id="732b6-127">The key constituents of a vPrev BizTalk project to invoke an RFC are:</span></span>  
  
-   <span data-ttu-id="732b6-128">**Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="732b6-128">**BizTalk orchestration**.</span></span> <span data-ttu-id="732b6-129">Il s’agit d’une orchestration simple qui Récupère les messages de demande à partir d’un emplacement de fichier, envoie le message de demande au système SAP à l’aide d’un SAP envoi / réception port, reçoit la réponse et l’enregistre dans un autre emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="732b6-129">This is a simple orchestration that picks request messages from a file location, sends the request message to the SAP system using an SAP send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="732b6-130">**Schéma de la RFC que vous souhaitez appeler dans le système SAP**.</span><span class="sxs-lookup"><span data-stu-id="732b6-130">**Schema for the RFC you want to invoke in the SAP system**.</span></span> <span data-ttu-id="732b6-131">Ce didacticiel implique un projet BizTalk qui appelle la RFC SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="732b6-131">This tutorial involves a BizTalk project that invokes the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="732b6-132">Le schéma généré pour le document RFC est SD_RFC_CUSTOMER_GET__x32003.xsd.</span><span class="sxs-lookup"><span data-stu-id="732b6-132">The schema generated for the RFC is SD_RFC_CUSTOMER_GET__x32003.xsd.</span></span> <span data-ttu-id="732b6-133">Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-133">This schema is generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="732b6-134">**Message de demande**.</span><span class="sxs-lookup"><span data-stu-id="732b6-134">**Request message**.</span></span> <span data-ttu-id="732b6-135">Le message de demande pour appeler le RFC SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="732b6-135">The request message to invoke the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="732b6-136">Le schéma du message de demande est conforme au schéma de la RFC SD_RFC_CUSTOMER_GET comme exposés par l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-136">The schema of the request message conforms to the schema of the SD_RFC_CUSTOMER_GET RFC as surfaced by the vPrev SAP adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="732b6-137">Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="732b6-137">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="732b6-138">L’objectif de ce didacticiel de migration consiste à vous permettent d’envoyer un message de demande, qui est conforme au schéma généré par l’adaptateur SAP vPrev, à l’aide d’un port personnalisé WCF qui peut traiter uniquement les messages conformes à la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="732b6-138">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by the vPrev SAP adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="732b6-139">Par conséquent, en bref, l’exercice de migration implique la configuration du port WCF-Custom pour traiter les messages qui ne sont pas conformes à la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]du schéma.</span><span class="sxs-lookup"><span data-stu-id="732b6-139">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="732b6-140">Toutefois, pour être en mesure de configurer le port WCF-Custom correctement, vous devez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="732b6-140">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="732b6-141">Générer des métadonnées pour la RFC SD_RFC_CUSTOMER_GET à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="732b6-141">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="732b6-142">Mapper le message de demande pour l’appel de la RFC à l’aide de l’adaptateur SAP vPrev à un message de demande pour l’appel de la RFC à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="732b6-142">Map the request message for invoking the RFC using the vPrev SAP adapter to a request message for invoking the RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="732b6-143">Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] au message de réponse pour l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="732b6-143">Map the response message received using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the response message for the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="732b6-144">Créer une SAP de WCF-Custom envoi-port de réception dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="732b6-144">Create a WCF-Custom SAP send-receive port in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="732b6-145">Configurer le port WCF-Custom pour utiliser les mappages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="732b6-145">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="732b6-146">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="732b6-146">In This Section</span></span>  
  
-   [<span data-ttu-id="732b6-147">Étape 1 : Modifier le projet BizTalk vPrev pour appeler une commande RFC</span><span class="sxs-lookup"><span data-stu-id="732b6-147">Step 1: Modify the vPrev BizTalk Project for Invoking an RFC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc.md)  
  
-   [<span data-ttu-id="732b6-148">Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="732b6-148">Step 2: Configure the Orchestration in BizTalk Server Administration Console</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)  
  
-   [<span data-ttu-id="732b6-149">Étape 3 : Tester l’Application migrée</span><span class="sxs-lookup"><span data-stu-id="732b6-149">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md)  
  
## <a name="see-also"></a><span data-ttu-id="732b6-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="732b6-150">See Also</span></span>  
 [<span data-ttu-id="732b6-151">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="732b6-151">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)