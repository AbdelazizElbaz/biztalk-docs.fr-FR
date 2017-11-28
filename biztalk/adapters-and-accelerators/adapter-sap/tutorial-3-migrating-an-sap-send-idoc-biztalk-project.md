---
title: "Didacticiel 3 : Migrer un SAP envoyer l’IDOC BizTalk projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, SAP Send IDOC BizTalk project
- migration
ms.assetid: c0a11432-5388-4054-8996-08a957cc02eb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52f8bc638d1adefe952ce055542706d11e0ca61f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-3-migrating-an-sap-send-idoc-biztalk-project"></a><span data-ttu-id="50ec4-102">Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC</span><span class="sxs-lookup"><span data-stu-id="50ec4-102">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>
<span data-ttu-id="50ec4-103">La version précédente de l’adaptateur SAP fournis avec Microsoft BizTalk Server est différente de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans nombreux aspects, notamment :</span><span class="sxs-lookup"><span data-stu-id="50ec4-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="50ec4-104">L’expérience au moment du design de création d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="50ec4-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="50ec4-105">L’expérience de récupération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="50ec4-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="50ec4-106">Nom de fichier de schéma et l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="50ec4-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="50ec4-107">Mappages de type de données.</span><span class="sxs-lookup"><span data-stu-id="50ec4-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="50ec4-108">Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="50ec4-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="50ec4-109">Configuration des ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="50ec4-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="50ec4-110">Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur SAP](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span><span class="sxs-lookup"><span data-stu-id="50ec4-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
 <span data-ttu-id="50ec4-111">Toutefois, vous pouvez apporter des modifications au projet BizTalk créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50ec4-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="50ec4-112">Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="50ec4-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50ec4-113">Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur SAP sera appelée vPrev l’adaptateur SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="50ec4-114">De même, un projet BizTalk qui utilise l’adaptateur SAP vPrev est être appelé en tant que projet de BizTalk vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="50ec4-115">Exemple utilisé pour le didacticiel</span><span class="sxs-lookup"><span data-stu-id="50ec4-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="50ec4-116">Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui envoie un IDOC à un système SAP (SendIDOC_Migration).</span><span class="sxs-lookup"><span data-stu-id="50ec4-116">This tutorial is based upon a sample (SendIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that sends an IDOC to an SAP system.</span></span> <span data-ttu-id="50ec4-117">L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50ec4-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="50ec4-118">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50ec4-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="50ec4-119">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="50ec4-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="50ec4-120">Vous devez disposer d’un projet BizTalk de vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="50ec4-121">Ce didacticiel implique un projet BizTalk qui envoie un IDOC BOMDOC à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-121">This tutorial involves a BizTalk project that sends a BOMDOC IDOC to an SAP system.</span></span>  
  
-   <span data-ttu-id="50ec4-122">Vous devez disposer d’un format de fichier plat BOMDOC IDOC pour envoyer au système SAP à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-122">You must have a flat-file BOMDOC IDOC to send to the SAP system using the vPrev SAP adapter.</span></span> <span data-ttu-id="50ec4-123">L’exemple fourni pour ce didacticiel contient cet IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50ec4-123">The sample provided for this tutorial contains this flat-file IDOC.</span></span>  
  
-   [<span data-ttu-id="50ec4-124">Créer le fichier de clé de nom fort et découvrez les outils</span><span class="sxs-lookup"><span data-stu-id="50ec4-124">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="50ec4-125">Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="50ec4-125">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="50ec4-126">Les principaux composants d’un projet BizTalk de vPrev pour envoyer un IDOC sont :</span><span class="sxs-lookup"><span data-stu-id="50ec4-126">The key constituents of a vPrev BizTalk project to send an IDOC are:</span></span>  
  
-   <span data-ttu-id="50ec4-127">**Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="50ec4-127">**BizTalk orchestration**.</span></span> <span data-ttu-id="50ec4-128">Il s’agit d’une orchestration simple qui sélectionne un IDOC de fichier plat à partir d’un emplacement de fichier et envoie le port d’envoi l’IDOC au système SAP à l’aide d’un SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-128">This is a simple orchestration that picks a flat-file IDOC from a file location and sends the IDOC to the SAP system using an SAP send port.</span></span> <span data-ttu-id="50ec4-129">Le projet BizTalk contient un désassembleur de fichier plat pour convertir le format de fichier plat IDOC XML, afin qu’il peut être utilisé dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="50ec4-129">The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration.</span></span> <span data-ttu-id="50ec4-130">Avant l’IDOC XML est consommé par le port d’envoi de SAP de vPrev, il est converti en un IDOC de fichier plat à l’aide d’un assembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50ec4-130">Before the XML IDOC is consumed by the vPrev SAP send port, it is converted back into a flat-file IDOC using a flat-file assembler.</span></span>  
  
-   <span data-ttu-id="50ec4-131">**Schéma pour l’IDOC à envoyer au système SAP**.</span><span class="sxs-lookup"><span data-stu-id="50ec4-131">**Schema for the IDOC you want to send to the SAP system**.</span></span> <span data-ttu-id="50ec4-132">Pour ce didacticiel, vous prenez un projet BizTalk qui envoie BOMDOC01 IDOC au système SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-132">For this tutorial, you take a BizTalk project that sends BOMDOC01 IDOC to the SAP system.</span></span> <span data-ttu-id="50ec4-133">Le schéma généré pour l’IDOC est BOMDOC01.xsd.</span><span class="sxs-lookup"><span data-stu-id="50ec4-133">The schema generated for the IDOC is BOMDOC01.xsd.</span></span> <span data-ttu-id="50ec4-134">Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-134">This schema is generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="50ec4-135">**Le format de fichier plat IDOC**.</span><span class="sxs-lookup"><span data-stu-id="50ec4-135">**The flat-file IDOC**.</span></span> <span data-ttu-id="50ec4-136">Il s’agit de l’IDOC de fichier plat envoyé au système SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-136">This is the flat-file IDOC that is sent to the SAP system.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="50ec4-137">Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="50ec4-137">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="50ec4-138">L’objectif de ce didacticiel de migration est pour vous permettre d’envoyer un IDOC de fichier plat à un système SAP à l’aide d’un port d’envoi WCF-Custom à la place le port d’envoi pour l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-138">The goal of this migration tutorial is to enable you to send a flat-file IDOC to an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter.</span></span> <span data-ttu-id="50ec4-139">Avant la présentation des paramètres qui sont nécessaires pour le port d’envoi WCF-Custom, vous devez d’abord comprendre quels ports physiques sont requis pour l’orchestration de IDOC vPrev envoi :</span><span class="sxs-lookup"><span data-stu-id="50ec4-139">Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration:</span></span>  
  
-   <span data-ttu-id="50ec4-140">Un fichier de port de réception qui Récupère l’IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50ec4-140">A file receive port that picks the flat-file IDOC.</span></span> <span data-ttu-id="50ec4-141">Ce port utilise le pipeline désassembleur de fichier plat, disponible dans l’application BizTalk, pour convertir le format de fichier plat dans un document XML conforme au schéma (BOMDOC01.xsd) généré à l’aide de l’adaptateur SAP vPrev.</span><span class="sxs-lookup"><span data-stu-id="50ec4-141">This port uses the flat-file disassembler pipeline, available in the BizTalk application, to convert the flat-file into an XML that conforms to the schema (BOMDOC01.xsd) generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="50ec4-142">Une SAP vPrev port d’envoi qui envoie l’IDOC de fichier plat au système SAP.</span><span class="sxs-lookup"><span data-stu-id="50ec4-142">A vPrev SAP send port that sends the flat-file IDOC to the SAP system.</span></span> <span data-ttu-id="50ec4-143">Avant d’envoyer le format de fichier plat, le port utilise l’assembleur de fichier plat pour convertir l’IDOC XML en un IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50ec4-143">Before sending the flat-file, the port uses the flat-file assembler to convert the XML IDOC into a flat-file IDOC.</span></span>  
  
 <span data-ttu-id="50ec4-144">Pour migrer votre projet BizTalk de vPrev existant, vous n’avez pas besoin de modifier le fichier port de réception qui Récupère l’IDOC de fichier plat et convertit l’IDOC de fichier plat au format XML à l’aide d’un désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50ec4-144">To migrate your existing vPrev BizTalk project, you do not need to change the file receive port that picks the flat-file IDOC and converts the flat-file IDOC to XML using a flat-file disassembler.</span></span> <span data-ttu-id="50ec4-145">Vous devez uniquement configurer un port d’envoi WCF-Custom avec les paramètres de configuration de droite.</span><span class="sxs-lookup"><span data-stu-id="50ec4-145">You only need to configure a new WCF-Custom send port with the right configuration settings.</span></span> <span data-ttu-id="50ec4-146">Ce didacticiel montre comment configurer le port d’envoi WCF-Custom pour envoyer des IDOC à un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50ec4-146">This tutorial demonstrates how to configure the WCF-Custom send port to send IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50ec4-147">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="50ec4-147">In This Section</span></span>  
  
-   [<span data-ttu-id="50ec4-148">Étape 1 : Créer et déployer le projet BizTalk vPrev pour envoyer un IDOC</span><span class="sxs-lookup"><span data-stu-id="50ec4-148">Step 1: Build and Deploy the vPrev BizTalk Project for Sending an IDOC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc.md)  
  
-   [<span data-ttu-id="50ec4-149">Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="50ec4-149">Step 2: Configure a WCF-Custom One-way Send Port</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)  
  
-   [<span data-ttu-id="50ec4-150">Étape 3 : Tester l’Application migrée</span><span class="sxs-lookup"><span data-stu-id="50ec4-150">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)  
  
## <a name="see-also"></a><span data-ttu-id="50ec4-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50ec4-151">See Also</span></span>  
 [<span data-ttu-id="50ec4-152">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="50ec4-152">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)