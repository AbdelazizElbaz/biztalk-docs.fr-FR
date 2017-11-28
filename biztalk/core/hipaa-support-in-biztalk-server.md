---
title: Prise en charge HIPAA dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ad8c64-6375-4364-80ce-440db943c222
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c34dd17ed875c5927b7a10d8238ec7828ab96c79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-support-in-biztalk-server"></a><span data-ttu-id="d7d19-102">Prise en charge HIPAA dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d7d19-102">HIPAA Support in BizTalk Server</span></span>
<span data-ttu-id="d7d19-103">Cette rubrique fournit une brève présentation de la loi HIPAA et de la manière dont [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] le prend en charge.</span><span class="sxs-lookup"><span data-stu-id="d7d19-103">This topic provides a brief overview of HIPAA and how [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] supports HIPAA.</span></span>  
  
## <a name="introduction-to-hipaa"></a><span data-ttu-id="d7d19-104">Présentation de HIPAA</span><span class="sxs-lookup"><span data-stu-id="d7d19-104">Introduction to HIPAA</span></span>  
 <span data-ttu-id="d7d19-105">La loi américaine HIPAA (Health Insurance Portability Accountability Act) de 1996 impose aux entités concernées d'appliquer des normes spécifiées dans le cadre de l'exécution de transactions électroniques (demandes de prise en charge, de remboursement, d'admissibilité, d'état d'une demande de prise en charge et réponses associées, etc.).</span><span class="sxs-lookup"><span data-stu-id="d7d19-105">The Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires covered entities to use mandated standards when they electronically conduct transactions such as claims, remittance, eligibility, claims status requests and responses, and others.</span></span> <span data-ttu-id="d7d19-106">Loi HIPAA est des plans de contrôle d’intégrité, les chambres de compensation et la plupart des fournisseurs de soins de santé.</span><span class="sxs-lookup"><span data-stu-id="d7d19-106">Covered entities under HIPAA are health plans, clearing houses, and most health care providers.</span></span>  
  
## <a name="hipaa-support-in-biztalk-server"></a><span data-ttu-id="d7d19-107">Prise en charge de la loi HIPAA dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d7d19-107">HIPAA support in BizTalk Server</span></span>  
 <span data-ttu-id="d7d19-108">Microsoft œuvre dans le but d'aider les prestataires de soins de santé et les organisations connexes à améliorer la délivrance et le financement des soins de santé.</span><span class="sxs-lookup"><span data-stu-id="d7d19-108">Microsoft is committed to helping health care and allied organizations improve the way health care is delivered and financed.</span></span> <span data-ttu-id="d7d19-109">Microsoft a pour objectif de réduire les efforts et moyens engagés par ces organisations en vue de se conformer aux réglementations HIPAA.</span><span class="sxs-lookup"><span data-stu-id="d7d19-109">Microsoft intends to reduce the amount of time and money that organizations must spend complying with HIPAA regulations.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7d19-110"> aide les organisations à créer des processus d'entreprise automatisés connectés et interopérables entre différents systèmes de santé.</span><span class="sxs-lookup"><span data-stu-id="d7d19-110"> helps organizations meet the challenges of creating automated business processes that connect and interoperate across diverse healthcare systems.</span></span> <span data-ttu-id="d7d19-111">Les organisations concernées par la loi HIPAA peuvent utiliser les fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer, implémenter et intégrer des solutions de prise en charge des transactions conformes à la réglementation fédérale.</span><span class="sxs-lookup"><span data-stu-id="d7d19-111">Organizations affected by HIPAA can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]’s capabilities to help in developing, implementing, and integrating transaction-compliant solutions which also comply with federal law.</span></span>  
  
<span data-ttu-id="d7d19-112">Les fonctionnalités natives de [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] assurent la prise en charge de la loi HIPAA.</span><span class="sxs-lookup"><span data-stu-id="d7d19-112">[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] includes native functionality providing support for HIPAA.</span></span> <span data-ttu-id="d7d19-113">Il ne s'agit pas d'un complément au produit, comme un adaptateur ou un accélérateur,</span><span class="sxs-lookup"><span data-stu-id="d7d19-113">It is not an add-in to the product, such as an adapter or an accelerator.</span></span> <span data-ttu-id="d7d19-114">mais d'un composant intégré au produit.</span><span class="sxs-lookup"><span data-stu-id="d7d19-114">It is built into the product.</span></span> [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7d19-115">EDI inclut des composants et fonctionnalités qui sont requises pour les deux sont conformes avec les mandats HIPAA et à l’adoption de la réglementation HIPAA sous la forme d’un processus d’entreprise géré et mesuré.</span><span class="sxs-lookup"><span data-stu-id="d7d19-115"> includes the EDI components and capabilities that are required to both comply with the HIPAA mandates and to also embrace HIPAA as a well-managed and measured business process.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7d19-116"> prend en charge les versions 5010 et 4010 de la loi HIPAA.</span><span class="sxs-lookup"><span data-stu-id="d7d19-116"> supports HIPAA version 5010 and 4010.</span></span>  
  
## <a name="hipaa-documentation-in-biztalk-server"></a><span data-ttu-id="d7d19-117">Documentation relative à la loi HIPAA dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d7d19-117">HIPAA documentation in BizTalk Server</span></span>  
 <span data-ttu-id="d7d19-118">X12 (normalisé par ANSI et principalement utilisé en Amérique du Nord) et EDIFACT (normalisé par les Nations-Unies et principalement utilisé hors des États-Unis) sont les principales normes EDI.</span><span class="sxs-lookup"><span data-stu-id="d7d19-118">The primary EDI standards are X12 (standardized by ANSI and primarily used in North America) and EDIFACT (standardized by the United Nations and primarily used outside the U.S.).</span></span> <span data-ttu-id="d7d19-119">HIPAA est une norme dérivée de X12.</span><span class="sxs-lookup"><span data-stu-id="d7d19-119">HIPAA is a standard derived from X12.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7d19-120">Fournit la prise en charge HIPAA dans le cadre de la X12 natif fonctionnalité EDI.</span><span class="sxs-lookup"><span data-stu-id="d7d19-120"> provides HIPAA support as part of the native X12 EDI functionality.</span></span> <span data-ttu-id="d7d19-121">Aussi, les références à la prise en charge X12 dans la documentation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appliquent également au traitement HIPAA, sauf mention explicite contraire.</span><span class="sxs-lookup"><span data-stu-id="d7d19-121">Therefore, where you see references to X12 support in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation, this support also applies to HIPAA processing, unless explicitly stated otherwise.</span></span>  
  
 <span data-ttu-id="d7d19-122">Les sections suivantes du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] incluent des informations spécifiques sur la loi HIPAA.</span><span class="sxs-lookup"><span data-stu-id="d7d19-122">The following sections in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have specific information about HIPAA.</span></span>  
  
 <span data-ttu-id="d7d19-123">**Bien démarrer**</span><span class="sxs-lookup"><span data-stu-id="d7d19-123">**Getting Started**</span></span>  
  
-   [<span data-ttu-id="d7d19-124">Documents informatisés HIPAA</span><span class="sxs-lookup"><span data-stu-id="d7d19-124">HIPAA Transaction Sets</span></span>](../core/hipaa-transaction-sets.md)  
  
 <span data-ttu-id="d7d19-125">**Planification et Architecture**</span><span class="sxs-lookup"><span data-stu-id="d7d19-125">**Planning and Architecture**</span></span>  
  
-   [<span data-ttu-id="d7d19-126">Version de schéma de Document HIPAA 5010</span><span class="sxs-lookup"><span data-stu-id="d7d19-126">HIPAA Document Schema Version 5010</span></span>](../core/hipaa-document-schema-version-5010.md)  
  
-   [<span data-ttu-id="d7d19-127">Annotations des champs déclencheurs HIPAA schéma</span><span class="sxs-lookup"><span data-stu-id="d7d19-127">HIPAA Schema Trigger Field Annotations</span></span>](../core/hipaa-schema-trigger-field-annotations.md)  
  
-   [<span data-ttu-id="d7d19-128">Fractionnement de sous-documents HIPAA</span><span class="sxs-lookup"><span data-stu-id="d7d19-128">Splitting HIPAA Subdocuments</span></span>](../core/splitting-hipaa-subdocuments.md)  
  
 <span data-ttu-id="d7d19-129">**Développement**</span><span class="sxs-lookup"><span data-stu-id="d7d19-129">**Development**</span></span>  
  
-   [<span data-ttu-id="d7d19-130">Modification des schémas EDI</span><span class="sxs-lookup"><span data-stu-id="d7d19-130">Modifying EDI Schemas</span></span>](../core/modifying-edi-schemas.md) 

- [<span data-ttu-id="d7d19-131">Personnalisation des énumérations dans le schéma d’enveloppe</span><span class="sxs-lookup"><span data-stu-id="d7d19-131">Customizing Enumerations in the Envelope Schema</span></span>](../core/customizing-enumerations-in-the-envelope-schema.md)

- [<span data-ttu-id="d7d19-132">Configuration de la Validation de champ croisé</span><span class="sxs-lookup"><span data-stu-id="d7d19-132">Configuring Cross-Field Validation</span></span>](../core/configuring-cross-field-validation.md)

  
 <span data-ttu-id="d7d19-133">**Dépannage**</span><span class="sxs-lookup"><span data-stu-id="d7d19-133">**Troubleshooting**</span></span>  
  
-   [<span data-ttu-id="d7d19-134">Problèmes connus avec EDI de traitement de réception</span><span class="sxs-lookup"><span data-stu-id="d7d19-134">Known Issues with EDI Receive Processing</span></span>](../core/known-issues-with-edi-receive-processing.md)  
  
-   [<span data-ttu-id="d7d19-135">Problèmes connus avec les outils XML utilisés avec les Solutions EDI</span><span class="sxs-lookup"><span data-stu-id="d7d19-135">Known Issues with XML Tools Used with EDI Solutions</span></span>](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)  
  
## <a name="more-information-about-hipaa"></a><span data-ttu-id="d7d19-136">Plus d’informations sur la loi HIPAA</span><span class="sxs-lookup"><span data-stu-id="d7d19-136">More information about HIPAA</span></span>  
  
-   <span data-ttu-id="d7d19-137">Pour plus d’informations sur l’American National Standards Institute, Accredited Standards Committee pour l’échange de données informatisé, accédez à [ASC X12 accueil](http://www.x12.org/).</span><span class="sxs-lookup"><span data-stu-id="d7d19-137">For information about the American National Standards Institute, Accredited Standards Committee for Electronic Data Interchange, go to [ASC X12 home](http://www.x12.org/).</span></span>  
  
-   <span data-ttu-id="d7d19-138">Pour plus d’informations sur le sous-comité d’assurance de X12 et leur implémentation repères adoptés dans le cadre de HIPAA, accédez à [Washington Publishing Company HIPAA EDI Guide](http://www.wpc-edi.com/).</span><span class="sxs-lookup"><span data-stu-id="d7d19-138">For information about X12's Insurance Subcommittee and their implementation guides adopted under HIPAA, go to [Washington Publishing Company's HIPAA EDI guides](http://www.wpc-edi.com/).</span></span>
  
-   <span data-ttu-id="d7d19-139">Pour plus d’informations sur le groupe de travail pour l’échange de données informatisé, accédez à [Workgroup for Electronic Data Interchange page d’accueil](http://www.wedi.org/).</span><span class="sxs-lookup"><span data-stu-id="d7d19-139">For information about the Workgroup for Electronic Data Interchange, go to [Workgroup for Electronic Data Interchange home page](http://www.wedi.org/).</span></span>