---
title: "Étape 6 : Création d’échanges de 3 a 4 Contoso accord de partenariat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agreements, creating
- creating, agreements
- double action tutorial, creating agreements
ms.assetid: a20e40d8-7e3b-4930-8921-056ffddd08ea
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 531a4b4a5446b51e01800caf582e40ce13bc288f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-6-creating-the-contoso-3a4-trading-partner-agreement"></a><span data-ttu-id="c0e7f-102">Étape 6 : Création de l’accord de partenariat commercial Contoso 3 a 4</span><span class="sxs-lookup"><span data-stu-id="c0e7f-102">Step 6: Creating the Contoso 3A4 Trading Partner Agreement</span></span>
<span data-ttu-id="c0e7f-103">Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="c0e7f-104">Vous créez un accord de partenariat commercial pour les 3 a 4 processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="c0e7f-104">You create a new trading partner agreement for the 3A4 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="c0e7f-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="c0e7f-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="c0e7f-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-3a4-trading-partner-agreement"></a><span data-ttu-id="c0e7f-107">Pour créer l’accord de partenariat commercial 3 a 4</span><span class="sxs-lookup"><span data-stu-id="c0e7f-107">To create the 3A4 trading partner agreement</span></span>  
  
1.  <span data-ttu-id="c0e7f-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .</span><span class="sxs-lookup"><span data-stu-id="c0e7f-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="c0e7f-109">Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0e7f-109">In the New Agreement Properties dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="c0e7f-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="c0e7f-110">Use this</span></span>|<span data-ttu-id="c0e7f-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c0e7f-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c0e7f-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-112">**Name**</span></span>|<span data-ttu-id="c0e7f-113">Type **Fabrikam_To_Contoso_3A4**.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-113">Type **Fabrikam_To_Contoso_3A4**.</span></span>|  
    |<span data-ttu-id="c0e7f-114">**Configuration de processus**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-114">**Process Configuration**</span></span>|<span data-ttu-id="c0e7f-115">Sélectionnez **STD_3A4_V02.02** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-115">Select **STD_3A4_V02.02** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c0e7f-116">**Mon organisation**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-116">**My Organization**</span></span>|<span data-ttu-id="c0e7f-117">Sélectionnez **Contoso** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-117">Select **Contoso** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c0e7f-118">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-118">**Partner Organization**</span></span>|<span data-ttu-id="c0e7f-119">Sélectionnez **Fabrikam** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-119">Select **Fabrikam** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c0e7f-120">**Version de RNIF**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-120">**RNIF Version**</span></span>|<span data-ttu-id="c0e7f-121">Sélectionnez **V02.00.01** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-121">Select **V02.00.01** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c0e7f-122">**Rôle de base**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-122">**Home Role**</span></span>|<span data-ttu-id="c0e7f-123">Sélectionnez **vendeur (récepteur)** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-123">Select **Seller (Responder)** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c0e7f-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-124">**Usage**</span></span>|<span data-ttu-id="c0e7f-125">Sélectionnez **Test** à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-125">Select **Test** from the drop down-list.</span></span>|  
  
3.  <span data-ttu-id="c0e7f-126">Sur le **Ports** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0e7f-126">On the **Ports** tab, do the following:</span></span>  
  
    |<span data-ttu-id="c0e7f-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c0e7f-127">Use this</span></span>|<span data-ttu-id="c0e7f-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c0e7f-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c0e7f-129">**URL d’action**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-129">**Action URL**</span></span>|<span data-ttu-id="c0e7f-130">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-130">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
    |<span data-ttu-id="c0e7f-131">**URL de signal**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-131">**Signal URL**</span></span>|<span data-ttu-id="c0e7f-132">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-132">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
    |<span data-ttu-id="c0e7f-133">**URL de synchronisation**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-133">**Sync URL**</span></span>|<span data-ttu-id="c0e7f-134">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="c0e7f-134">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
  
4.  <span data-ttu-id="c0e7f-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-135">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c0e7f-136">Cliquez sur le **Fabrikam_To_Contoso_3A4** accord, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="c0e7f-136">Right-click the **Fabrikam_To_Contoso_3A4** agreement and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e7f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0e7f-137">See Also</span></span>  
 [<span data-ttu-id="c0e7f-138">Étape 7 : Création et déploiement de l’exemple de SDK DoubleAction</span><span class="sxs-lookup"><span data-stu-id="c0e7f-138">Step 7: Building and Deploying the DoubleAction SDK Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-doubleaction-sdk-sample.md)