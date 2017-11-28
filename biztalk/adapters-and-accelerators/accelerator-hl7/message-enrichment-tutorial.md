---
title: "Didacticiel d’enrichissement de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial
- message enrichment tutorial, about the tutorial
- messages, tutorial
- tutorials, message enrichment tutorial
ms.assetid: 4ffb047f-457a-4a80-b7ec-4b61ae16f35f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532fc0e8a9aeefbc35a892277c68be8d640b5588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-enrichment-tutorial"></a><span data-ttu-id="53e30-102">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="53e30-102">Message Enrichment Tutorial</span></span>
<span data-ttu-id="53e30-103">Ce didacticiel fournit des instructions détaillées pour l’utilisation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour résoudre un problème commercial particulier : le problème d’enrichissement de message.</span><span class="sxs-lookup"><span data-stu-id="53e30-103">This tutorial provides step-by-step procedures for using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to solve a particular business problem: the message enrichment problem.</span></span> <span data-ttu-id="53e30-104">Le didacticiel d’enrichissement de message décrit une situation dans laquelle vous devez ajouter à ou enrichir un message qui n’est pas conforme HL7 et/ou est incomplète.</span><span class="sxs-lookup"><span data-stu-id="53e30-104">The message enrichment tutorial describes a situation in which you have to add to, or enrich, a message that is not HL7-compliant and/or is incomplete.</span></span> <span data-ttu-id="53e30-105">Cela peut se produire avec une application, telle qu’une application de patients, ou il peut se produire lorsque vous remplissez un message avec des données XML à partir de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53e30-105">This can occur with an application, such as a patient registration application, or it can occur when you are populating a message with XML data from [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="53e30-106">Dans ce didacticiel, vous capturez les messages avec BTAHL7 et fournissez des données manquantes, par exemple, à partir d’une base de données de patients.</span><span class="sxs-lookup"><span data-stu-id="53e30-106">In this tutorial, you capture the messages with BTAHL7, and provide any missing data, for example, from a patient records database.</span></span> <span data-ttu-id="53e30-107">Vous puis convertissez le message et l’envoyez à un laboratoire, d’assurance ou toute hérité line-of-business (LOB) application à l’aide de l’adaptateur MLLP (minimale inférieure Layer Protocol).</span><span class="sxs-lookup"><span data-stu-id="53e30-107">You then convert the message and send it to a laboratory, insurance, or any legacy line-of-business (LOB) application using the MLLP (Minimal Lower Layer Protocol) adapter.</span></span>  
  
 <span data-ttu-id="53e30-108">Dans ce didacticiel, vous utilisez une application client (WSClient.exe) du service Web pour envoyer un message au format XML, dans ce cas, un événement de déclencheur « sonnette » inscrire un Patient, via l’adaptateur SOAP pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avec BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="53e30-108">In this tutorial, you use a Web service client (WSClient.exe) application to send an XML-formatted message, in this case a "doorbell" Register Patient trigger event, through the SOAP adapter to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] with BTAHL7.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="53e30-109">reçoit le message dans un protocole SOAP port de réception et les itinéraires le message à une orchestration publié en tant qu’un service Web.</span><span class="sxs-lookup"><span data-stu-id="53e30-109"> receives the message in a SOAP receive port, and routes the message to an orchestration published as a Web service.</span></span> <span data-ttu-id="53e30-110">Le message XML contient un nom du patient et le numéro de sécurité sociale.</span><span class="sxs-lookup"><span data-stu-id="53e30-110">The XML message contains a patient name and social security number.</span></span> <span data-ttu-id="53e30-111">Vous enrichir le message et utilisez des schémas, une carte et une transformation pour convertir le message au format de HL7.</span><span class="sxs-lookup"><span data-stu-id="53e30-111">You augment the message, and use schemas, a map, and a transform to convert the message into HL7 format.</span></span> <span data-ttu-id="53e30-112">Ensuite vous envoyer via un adaptateur MLLP au laboratoire, d’assurance, ou d’applications métiers.</span><span class="sxs-lookup"><span data-stu-id="53e30-112">You will then send it through an MLLP adapter to the laboratory, insurance, or LOB application.</span></span>  
  
 <span data-ttu-id="53e30-113">La figure suivante illustre le processus du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="53e30-113">The following figure shows the process flow of the tutorial.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")  
  
> [!NOTE]
>  <span data-ttu-id="53e30-114">Ce didacticiel requiert Windows Server Standard, Enterprise, Datacenter ou Web Edition et une installation personnalisée de BTAHL7 qui inclut le MLLP des outils de test.</span><span class="sxs-lookup"><span data-stu-id="53e30-114">This tutorial requires Windows Server Standard, Enterprise, Datacenter, or Web Edition, and a custom BTAHL7 installation that includes the MLLP test tools.</span></span> <span data-ttu-id="53e30-115">En outre, vous devez être familiarisé avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] développement dans [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] et les informations présentes dans [en savoir plus sur l’accélérateur HL7 et les outils BizTalk disponibles](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span><span class="sxs-lookup"><span data-stu-id="53e30-115">Additionally, you should be familiar with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] and the information found in [learn about the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53e30-116">Vous pouvez éviter des erreurs par l’annulation du déploiement des assemblys, l’arrêt des ports d’envoi, et la désactivation des emplacements que vous avez utilisé dans les didacticiels précédents de réception.</span><span class="sxs-lookup"><span data-stu-id="53e30-116">You can avoid errors by undeploying assemblies, stopping send ports, and disabling receive locations that you used in previous tutorials.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53e30-117">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="53e30-117">In this section</span></span>  
  
-   [<span data-ttu-id="53e30-118">Étape 1 : Configurer l’identité du Pool d’applications</span><span class="sxs-lookup"><span data-stu-id="53e30-118">Step 1: Configure Application Pool Identity</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [<span data-ttu-id="53e30-119">Étape 2 : Créer un nouveau projet</span><span class="sxs-lookup"><span data-stu-id="53e30-119">Step 2: Create a New Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [<span data-ttu-id="53e30-120">Étape 3 : Assigner un nom fort à l’Assembly</span><span class="sxs-lookup"><span data-stu-id="53e30-120">Step 3: Assign a Strong Name to the Assembly</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [<span data-ttu-id="53e30-121">Étape 4 : Créer les schémas</span><span class="sxs-lookup"><span data-stu-id="53e30-121">Step 4: Create the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [<span data-ttu-id="53e30-122">Étape 5 : Promouvoir les propriétés de schéma</span><span class="sxs-lookup"><span data-stu-id="53e30-122">Step 5: Promote Schema Properties</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [<span data-ttu-id="53e30-123">Étape 6 : Valider les schémas</span><span class="sxs-lookup"><span data-stu-id="53e30-123">Step 6: Validate the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [<span data-ttu-id="53e30-124">Étape 7 : Signer et générer des projets</span><span class="sxs-lookup"><span data-stu-id="53e30-124">Step 7: Sign and Build the Projects</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [<span data-ttu-id="53e30-125">Étape 8 : Créer un mappage avec le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="53e30-125">Step 8: Create a Map with BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [<span data-ttu-id="53e30-126">Étape 9 : Valider et générez le projet de carte</span><span class="sxs-lookup"><span data-stu-id="53e30-126">Step 9: Validate and Build the Map Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [<span data-ttu-id="53e30-127">Étape 10 : Créer une Orchestration</span><span class="sxs-lookup"><span data-stu-id="53e30-127">Step 10: Create an Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [<span data-ttu-id="53e30-128">Étape 11 : Créer des Variables d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="53e30-128">Step 11: Create Orchestration Variables</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [<span data-ttu-id="53e30-129">Étape 12 : Configurer les formes d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="53e30-129">Step 12: Configure Orchestration Shapes</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [<span data-ttu-id="53e30-130">Étape 13 : Créer et configurer des Ports</span><span class="sxs-lookup"><span data-stu-id="53e30-130">Step 13: Create and Configure Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [<span data-ttu-id="53e30-131">Étape 14 : Publier l’Orchestration en tant que Service Web</span><span class="sxs-lookup"><span data-stu-id="53e30-131">Step 14: Publish the Orchestration as a Web Service</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [<span data-ttu-id="53e30-132">Étape 15 : Configurer l’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="53e30-132">Step 15: Configure the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="53e30-133">Étape 16 : Démarrer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="53e30-133">Step 16: Start the Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [<span data-ttu-id="53e30-134">Étape 17 : Créer l’Application WSClient</span><span class="sxs-lookup"><span data-stu-id="53e30-134">Step 17: Create the WSClient Application</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [<span data-ttu-id="53e30-135">Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message</span><span class="sxs-lookup"><span data-stu-id="53e30-135">Step 18: Test Your New Message Enrichment Solution</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)