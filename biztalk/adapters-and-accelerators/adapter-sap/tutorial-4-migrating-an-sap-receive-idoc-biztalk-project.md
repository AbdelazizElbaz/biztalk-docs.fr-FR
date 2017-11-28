---
title: "Didacticiel 4 : Migration d’un SAP de réception IDOC BizTalk projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, SAP Receive IDOC BizTalk project
- migrating, SAP Receive IDOC BizTalk project
- migration
ms.assetid: 74b667d8-2d8c-4c15-9dd2-f13521404b85
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943c80e84bc192330fd870a45c0b5fb60761a33d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-4-migrating-an-sap-receive-idoc-biztalk-project"></a><span data-ttu-id="d1999-102">Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC</span><span class="sxs-lookup"><span data-stu-id="d1999-102">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>
<span data-ttu-id="d1999-103">La version précédente de l’adaptateur SAP fournis avec Microsoft BizTalk Server est différente de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans nombreux aspects, notamment :</span><span class="sxs-lookup"><span data-stu-id="d1999-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="d1999-104">L’expérience au moment du design de création d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d1999-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="d1999-105">L’expérience de récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d1999-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="d1999-106">Nom de fichier de schéma et l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d1999-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="d1999-107">Mappages de type de données.</span><span class="sxs-lookup"><span data-stu-id="d1999-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="d1999-108">Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d1999-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="d1999-109">Configuration des ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d1999-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="d1999-110">Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur SAP](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span><span class="sxs-lookup"><span data-stu-id="d1999-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
 <span data-ttu-id="d1999-111">Toutefois, vous pouvez apporter des modifications au projet BizTalk créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1999-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="d1999-112">Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="d1999-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1999-113">Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur SAP sera appelée vPrev l’adaptateur SAP.</span><span class="sxs-lookup"><span data-stu-id="d1999-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="d1999-114">De même, un projet BizTalk qui utilise l’adaptateur SAP vPrev est être appelé en tant que projet de BizTalk vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="d1999-115">Exemple utilisé pour le didacticiel</span><span class="sxs-lookup"><span data-stu-id="d1999-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="d1999-116">Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui reçoit un IDOC de fichier plat à partir d’un système SAP (ReceiveIDOC_Migration).</span><span class="sxs-lookup"><span data-stu-id="d1999-116">This tutorial is based upon a sample (ReceiveIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="d1999-117">L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1999-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="d1999-118">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1999-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d1999-119">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d1999-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="d1999-120">Vous devez disposer d’un projet BizTalk de vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="d1999-121">Ce didacticiel implique un projet BizTalk qui reçoit un IDOC ORDERS03 à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="d1999-121">This tutorial involves a BizTalk project that receives an ORDERS03 IDOC from an SAP system.</span></span>  
  
-   [<span data-ttu-id="d1999-122">Créer le fichier de clé de nom fort et découvrez les outils</span><span class="sxs-lookup"><span data-stu-id="d1999-122">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="d1999-123">Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="d1999-123">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="d1999-124">Les principaux composants d’un projet BizTalk de vPrev pour recevoir un IDOC sont :</span><span class="sxs-lookup"><span data-stu-id="d1999-124">The key constituents of a vPrev BizTalk project to receive an IDOC are:</span></span>  
  
-   <span data-ttu-id="d1999-125">**Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="d1999-125">**BizTalk orchestration**.</span></span> <span data-ttu-id="d1999-126">Il s’agit d’un simple orchestration qui se compose d’un SAP port de réception qui reçoit un IDOC de fichier plat à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="d1999-126">This is a simple orchestration that consists of an SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="d1999-127">Le projet BizTalk contient un désassembleur de fichier plat pour convertir le format de fichier plat IDOC XML, afin qu’il peut être utilisé dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d1999-127">The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration.</span></span> <span data-ttu-id="d1999-128">Avant l’IDOC XML est copié vers un emplacement de fichier via un port de fichier, il est converti en un IDOC de fichier plat à l’aide d’un assembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="d1999-128">Before the XML IDOC is copied to a file location through a file port, it is converted back into a flat-file IDOC using a flat-file assembler.</span></span>  
  
-   <span data-ttu-id="d1999-129">**Schéma pour l’IDOC à envoyer au système SAP**.</span><span class="sxs-lookup"><span data-stu-id="d1999-129">**Schema for the IDOC you want to send to the SAP system**.</span></span> <span data-ttu-id="d1999-130">Ce didacticiel implique un projet BizTalk qui reçoit les IDOC ORDERS03 à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="d1999-130">This tutorial involves a BizTalk project that receives ORDERS03 IDOC from the SAP system.</span></span> <span data-ttu-id="d1999-131">Le schéma généré pour l’IDOC est ORDERS03.xsd.</span><span class="sxs-lookup"><span data-stu-id="d1999-131">The schema generated for the IDOC is ORDERS03.xsd.</span></span> <span data-ttu-id="d1999-132">Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-132">This schema is generated using the vPrev SAP adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="d1999-133">Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="d1999-133">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="d1999-134">L’objectif de ce didacticiel de migration est pour vous permettre de recevoir un IDOC de fichier plat à partir d’un système SAP à l’aide d’un port d’envoi WCF-Custom à la place le port d’envoi pour l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-134">The goal of this migration tutorial is to enable you to receive a flat-file IDOC from an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter.</span></span> <span data-ttu-id="d1999-135">Avant la présentation des paramètres qui sont nécessaires pour le port d’envoi WCF-Custom, vous devez d’abord comprendre quels ports physiques sont requis pour l’orchestration de IDOC vPrev envoi.</span><span class="sxs-lookup"><span data-stu-id="d1999-135">Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration.</span></span>  
  
-   <span data-ttu-id="d1999-136">Une SAP vPrev port de réception qui reçoit un IDOC de fichier plat à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="d1999-136">A vPrev SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="d1999-137">Le port convertit également en un IDOC XML à l’aide d’un désassembleur de fichier plat, qui est disponible dans le cadre de l’application BizTalk vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-137">The port also converts this to an XML IDOC using a flat-file disassembler, which is available as part of the vPrev BizTalk application.</span></span> <span data-ttu-id="d1999-138">L’IDOC XML conforme au schéma (ORDERS03.xsd) que vous avez généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="d1999-138">The XML IDOC conforms to the schema (ORDERS03.xsd) that you generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="d1999-139">Un port d’envoi file qui copie l’IDOC au dossier.</span><span class="sxs-lookup"><span data-stu-id="d1999-139">A file send port which copies the IDOC to folder.</span></span> <span data-ttu-id="d1999-140">Ce port utilise également le pipeline assembleur de fichier plat, disponible dans l’application BizTalk, pour convertir l’IDOC XML en un IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="d1999-140">This port also uses the flat-file assembler pipeline, available in the BizTalk application, to convert the XML IDOC to a flat-file IDOC.</span></span>  
  
 <span data-ttu-id="d1999-141">Pour migrer votre projet BizTalk de vPrev existant, vous n’avez pas besoin modifier le port d’envoi file qui copie l’IDOC de fichier plat dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="d1999-141">To migrate your existing vPrev BizTalk project, you do not need to change the file send port that copies the flat-file IDOC to a folder.</span></span> <span data-ttu-id="d1999-142">Vous devez uniquement configurer un nouveau port avec les paramètres de configuration à droite de réception WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="d1999-142">You only need to configure a new WCF-Custom receive port with the right configuration settings.</span></span> <span data-ttu-id="d1999-143">Ce didacticiel montre comment configurer WCF-Custom port de réception pour recevoir des IDOC à partir d’un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1999-143">This tutorial demonstrates how to configure the WCF-Custom receive port to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1999-144">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d1999-144">In This Section</span></span>  
  
-   [<span data-ttu-id="d1999-145">Étape 1 : Créer et déployer le projet BizTalk vPrev pour la réception d’un IDOC</span><span class="sxs-lookup"><span data-stu-id="d1999-145">Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [<span data-ttu-id="d1999-146">Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception</span><span class="sxs-lookup"><span data-stu-id="d1999-146">Step 2: Configure a WCF-Custom One-way Receive Port</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [<span data-ttu-id="d1999-147">Étape 3 : Tester l’Application migrée</span><span class="sxs-lookup"><span data-stu-id="d1999-147">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1999-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1999-148">See Also</span></span>  
 [<span data-ttu-id="d1999-149">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="d1999-149">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)