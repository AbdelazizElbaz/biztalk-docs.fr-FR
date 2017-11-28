---
title: "Étape 1 : Créer et déployer le projet BizTalk vPrev pour envoyer un IDOC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, building and deploying previous version of BizTalk project for sending an IDOC
- migration
ms.assetid: 1982b318-45d1-464e-b7e4-65d459c439e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9089e90fc3a429d6d594a18b0e1fb6e94d4f72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc"></a><span data-ttu-id="78f9e-102">Étape 1 : Créer et déployer le projet BizTalk vPrev pour envoyer un IDOC</span><span class="sxs-lookup"><span data-stu-id="78f9e-102">Step 1: Build and Deploy the vPrev BizTalk Project for Sending an IDOC</span></span>
<span data-ttu-id="78f9e-103">![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="78f9e-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="78f9e-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="78f9e-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="78f9e-105">**Objectif :** dans cette étape, vous générez et déployez votre projet BizTalk de vPrev existant pour envoyer un IDOC à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="78f9e-105">**Objective:** In this step, you build and deploy your existing vPrev BizTalk project to send an IDOC to an SAP system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78f9e-106">Vous n’avez pas besoin d’apporter de modification au projet BizTalk vPrev.</span><span class="sxs-lookup"><span data-stu-id="78f9e-106">You do not need to make any change to the vPrev BizTalk project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78f9e-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="78f9e-107">Prerequisites</span></span>  
 <span data-ttu-id="78f9e-108">Vous devez disposer d’un projet BizTalk de vPrev pour envoyer un IDOC BOMDOC à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="78f9e-108">You must have a vPrev BizTalk project to send a BOMDOC IDOC to an SAP system.</span></span>  
  
### <a name="to-build-and-deploy-the-vprev-biztalk-project"></a><span data-ttu-id="78f9e-109">Pour générer et déployer le projet BizTalk vPrev</span><span class="sxs-lookup"><span data-stu-id="78f9e-109">To build and deploy the vPrev BizTalk project</span></span>  
  
1.  <span data-ttu-id="78f9e-110">Créer un fichier de clé de nom fort requis pour générer et déployer la solution.</span><span class="sxs-lookup"><span data-stu-id="78f9e-110">Create a strong-name key file required to build and deploy the solution.</span></span> <span data-ttu-id="78f9e-111">Pour créer un fichier de clé de nom fort, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="78f9e-111">To create a strong-name key file, do the following:</span></span>  
  
    1.  <span data-ttu-id="78f9e-112">Démarrez l’invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78f9e-112">Start Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="78f9e-113">À l’invite de commandes, accédez au dossier où vous souhaitez créer le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="78f9e-113">At the command prompt navigate to the folder where you want to create the key file.</span></span> <span data-ttu-id="78f9e-114">Par exemple, tapez **cd C:\Sample**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="78f9e-114">For example, type **cd C:\Sample**, and then press ENTER.</span></span>  
  
    3.  <span data-ttu-id="78f9e-115">À l’invite de commandes, tapez **sn -k \<nom de fichier de clé > .snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="78f9e-115">At the command prompt, type **sn -k \<key file name>.snk**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="78f9e-116">Cliquez sur le nom de la solution BizTalk dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-116">Right-click the BizTalk solution name in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="78f9e-117">Dans le **Pages de propriétés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="78f9e-117">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="78f9e-118">Cliquez sur les propriétés de Configuration dans le volet gauche et assurez-vous que les cases à cocher dans la **générer** et **déployer** les colonnes sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="78f9e-118">Click Configuration Properties from the left pane, and make sure the check boxes in the **Build** and **Deploy** columns are selected.</span></span>  
  
    2.  <span data-ttu-id="78f9e-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-119">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="78f9e-120">Cliquez sur le projet BizTalk dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-120">Right-click the BizTalk project in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="78f9e-121">Dans le **Pages de propriétés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="78f9e-121">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="78f9e-122">Dans le volet gauche, développez **propriétés communes**, puis cliquez sur Assembly.</span><span class="sxs-lookup"><span data-stu-id="78f9e-122">In the left pane, expand **Common Properties**, and then click Assembly.</span></span>  
  
    2.  <span data-ttu-id="78f9e-123">Dans le volet droit, sous la **nom fort** catégorie, pour le **fichier de clé d’Assembly** propriété, fournissez le chemin d’accès au fichier de clé d’assembly vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="78f9e-123">In the right pane, under the **Strong name** category, for the **Assembly Key File** property, provide the path to the assembly key file you created earlier.</span></span>  
  
    3.  <span data-ttu-id="78f9e-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-124">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="78f9e-125">Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-125">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="78f9e-126">Une fois la solution générée avec succès, cliquez sur le nom de la solution, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="78f9e-126">After the solution successfully builds, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="78f9e-127">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="78f9e-127">Next Steps</span></span>  
 <span data-ttu-id="78f9e-128">Créer et configurer un port d’envoi WCF-Custom et le configurer pour envoyer des IDOC à un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], comme décrit dans [étape 2 : configurer un Port d’envoi unidirectionnel WCF-Custom](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="78f9e-128">Create and configure a WCF-Custom send port and configure it to send IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], as described in [Step 2: Configure a WCF-Custom One-way Send Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f9e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78f9e-129">See Also</span></span>  
 [<span data-ttu-id="78f9e-130">Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC</span><span class="sxs-lookup"><span data-stu-id="78f9e-130">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)