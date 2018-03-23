---
title: Utiliser un adaptateur WCF LOB Adapter SDK dans un projet BizTalk Server | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84f81d23b56c2631879f366e6fe502840408a0d7
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a><span data-ttu-id="85dc1-102">Utiliser un adaptateur WCF LOB Adapter SDK dans un projet BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="85dc1-102">Consume a WCF LOB Adapter SDK adapter in a BizTalk Server project</span></span>
<span data-ttu-id="85dc1-103">Cette rubrique décrit comment utiliser un adaptateur créé à l’aide de la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dc1-103">This topic describes how to consume an adapter built using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85dc1-104">Pour pouvoir utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous devez installer le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] outils sur le même ordinateur qui héberge [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dc1-104">In order to use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you must install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tools on the same computer hosting [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 
## <a name="use-the-consume-adapter-service-add-in"></a><span data-ttu-id="85dc1-105">Utilisez le Consume Adapter Service Add-in</span><span class="sxs-lookup"><span data-stu-id="85dc1-105">Use the Consume Adapter Service Add-in</span></span>  
 
  
1.  <span data-ttu-id="85dc1-106">Ouvrez votre application .NET dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dc1-106">Open your .NET application in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="85dc1-107">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **projet** volet, avec le bouton droit votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] de projet, puis choisissez **ajouter**&#124;**ajouter les éléments générés** &#124;  **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="85dc1-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in the **Project** pane, right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project, and then choose **Add**&#124;**Add Generated Items** &#124; **Consume Adapter Service**.</span></span>  
  
3.  <span data-ttu-id="85dc1-108">Dans la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] , sélectionnez une liaison de la carte.</span><span class="sxs-lookup"><span data-stu-id="85dc1-108">In the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] screen, select an adapter binding.</span></span>  
  
4.  <span data-ttu-id="85dc1-109">Cliquez sur **configurer** pour configurer l’URI de connexion pour la liaison de la carte sélectionnée et fournir toutes les informations d’identification, les propriétés d’URI et les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="85dc1-109">Click **Configure** to configure the connection URI for the selected adapter binding and to provide any credentials, URI properties, and binding properties.</span></span> <span data-ttu-id="85dc1-110">La configuration requise réelle varie en fonction de la liaison de la carte sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="85dc1-110">Actual requirements will vary based on the selected adapter binding.</span></span>  
  
5.  <span data-ttu-id="85dc1-111">Cliquez sur **OK** lorsque vous avez configuré l’URI.</span><span class="sxs-lookup"><span data-stu-id="85dc1-111">Click **OK** when you have configured the URI.</span></span>  
  
6.  <span data-ttu-id="85dc1-112">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="85dc1-112">Click **Connect**.</span></span> <span data-ttu-id="85dc1-113">Si l’URI de connexion est valide et les informations d’identification de client (le cas échéant) sont acceptées, la **catégorie** volet doit être rempli avec les catégories et les opérations fournies par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="85dc1-113">If the connection URI is valid and client credentials (if any) are accepted, the **Category** pane should be populated with the categories and operations provided by the adapter.</span></span>  
  
7.  <span data-ttu-id="85dc1-114">Si l’adaptateur prend en charge la recherche, le champ de recherche sera actif.</span><span class="sxs-lookup"><span data-stu-id="85dc1-114">If the adapter support search, the search field will be active.</span></span> <span data-ttu-id="85dc1-115">Sinon, vous pouvez filtrer par type de contrat et Explorer les types et les opérations en cliquant sur les nœuds dans le **catégorie** volet.</span><span class="sxs-lookup"><span data-stu-id="85dc1-115">Otherwise, you can filter by contract type and explore types and operations by clicking nodes in the **Category** pane.</span></span>  
  
8.  <span data-ttu-id="85dc1-116">Cliquez sur **OK** pour générer les artefacts de proxy.</span><span class="sxs-lookup"><span data-stu-id="85dc1-116">Click **OK** to generate the proxy artifacts.</span></span> <span data-ttu-id="85dc1-117">Le nombre d’artefacts varie en fonction du type de contrat :</span><span class="sxs-lookup"><span data-stu-id="85dc1-117">The number of artifacts varies based on the contract type:</span></span>  
  
    |<span data-ttu-id="85dc1-118">Type de contrat</span><span class="sxs-lookup"><span data-stu-id="85dc1-118">Contract Type</span></span>|<span data-ttu-id="85dc1-119">Artefact</span><span class="sxs-lookup"><span data-stu-id="85dc1-119">Artifact</span></span>|<span data-ttu-id="85dc1-120"> Description</span><span class="sxs-lookup"><span data-stu-id="85dc1-120">Description</span></span>||  
    |-------------------|--------------|-----------------|-|  
    |<span data-ttu-id="85dc1-121">Sortant</span><span class="sxs-lookup"><span data-stu-id="85dc1-121">Outbound</span></span>|<span data-ttu-id="85dc1-122">Schémas XML</span><span class="sxs-lookup"><span data-stu-id="85dc1-122">XML Schemas</span></span>|<span data-ttu-id="85dc1-123">Contient les schémas pour les types sélectionnés et les opérations.</span><span class="sxs-lookup"><span data-stu-id="85dc1-123">Contains the schemas for the selected types and operations.</span></span>||  
    |<span data-ttu-id="85dc1-124">Sortant</span><span class="sxs-lookup"><span data-stu-id="85dc1-124">Outbound</span></span>||<span data-ttu-id="85dc1-125">Informations de liaison de port XML d’envoi WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="85dc1-125">WCF-Custom send port binding information XML</span></span>|<span data-ttu-id="85dc1-126">Contient la configuration XML pour le port d’envoi WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="85dc1-126">Contains configuration XML for the WCF-Custom send port.</span></span>|  
    |<span data-ttu-id="85dc1-127">Trafic entrant</span><span class="sxs-lookup"><span data-stu-id="85dc1-127">Inbound</span></span>|<span data-ttu-id="85dc1-128">Schémas XML</span><span class="sxs-lookup"><span data-stu-id="85dc1-128">XML Schemas</span></span>|<span data-ttu-id="85dc1-129">Contient les schémas pour les types sélectionnés et les opérations.</span><span class="sxs-lookup"><span data-stu-id="85dc1-129">Contains the schemas for the selected types and operations.</span></span>||  
    |<span data-ttu-id="85dc1-130">Trafic entrant</span><span class="sxs-lookup"><span data-stu-id="85dc1-130">Inbound</span></span>||<span data-ttu-id="85dc1-131">Informations de liaison de port XML de réception WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="85dc1-131">WCF-Custom receive port binding information XML</span></span>|<span data-ttu-id="85dc1-132">Contient le fichier XML de configuration pour le port de réception WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="85dc1-132">Contains configuration XML for the WCF-Custom receive port.</span></span>|  
  
9. <span data-ttu-id="85dc1-133">Vous pouvez maintenant utiliser des fichiers de schéma XML dans votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="85dc1-133">You can now use the XML Schema files in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="deploy-the-biztalk-server-project"></a><span data-ttu-id="85dc1-134">Déployer le projet BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="85dc1-134">Deploy the BizTalk Server project</span></span>  
  
1.  <span data-ttu-id="85dc1-135">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="85dc1-135">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="85dc1-136">Importez les fichiers XML de liaison de port pour créer les ports physiques.</span><span class="sxs-lookup"><span data-stu-id="85dc1-136">Import the port binding XML file(s) to create the physical ports.</span></span> <span data-ttu-id="85dc1-137">Avec le bouton droit de votre application sous le **Applications** groupe, sélectionnez **importer les liaisons**, puis accédez à et sélectionnez les informations de liaison de port approprié ou les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="85dc1-137">Right-click your application under the **Applications** group, select **Import Bindings**, and then navigate to and select the appropriate port binding information XML file(s).</span></span>  
  
3.  <span data-ttu-id="85dc1-138">Mapper les ports logiques définis dans votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations aux ports physiques nouvellement créés.</span><span class="sxs-lookup"><span data-stu-id="85dc1-138">Map the logical ports defined in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations to the newly created physical ports.</span></span>  
  
4.  <span data-ttu-id="85dc1-139">Cliquez sur **Orchestrations** sous votre application, cliquez sur l’orchestration à inscrire, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="85dc1-139">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Enlist**.</span></span>  
  
5.  <span data-ttu-id="85dc1-140">Cliquez sur **Orchestrations** sous votre application, cliquez sur l’orchestration à inscrire, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="85dc1-140">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Start**.</span></span>  
  
6.  <span data-ttu-id="85dc1-141">Cliquez sur votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, puis sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="85dc1-141">Right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, and then click **Start**.</span></span>  
  
## <a name="generate-multiple-schemas"></a><span data-ttu-id="85dc1-142">Générer plusieurs schémas</span><span class="sxs-lookup"><span data-stu-id="85dc1-142">Generate Multiple Schemas</span></span>  
 <span data-ttu-id="85dc1-143">Si vous utilisez l’Assistant consommer de Service d’adaptateur pour générer plusieurs schémas, un ou plusieurs éléments peuvent être dupliqués dans les schémas, ce qui entraîne un échec de la compilation pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="85dc1-143">If you use the Consume Adapter Service Wizard to generate multiple schemas, one or more elements may be duplicated in the schemas resulting in compilation failure for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="85dc1-144">Vous pouvez éviter cela en sélectionnant le **générer le Type de schéma Unique** case à cocher pour vous assurer que les types de schéma sont générés avec des espaces de noms uniques.</span><span class="sxs-lookup"><span data-stu-id="85dc1-144">You can avoid this by selecting the **Generate Unique Schema Type** check box to ensure that schema types are generated with unique namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85dc1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85dc1-145">See Also</span></span>  
 [<span data-ttu-id="85dc1-146">Utiliser un adaptateur créé à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="85dc1-146">Consume an adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)