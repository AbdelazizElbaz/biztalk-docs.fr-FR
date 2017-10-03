---
title: "Étape 5 : Création de la négociation de Fabrikam 3A2 accord de partenariat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, creating agreements
ms.assetid: a5fafdc6-e9dd-4d15-98a2-8b603901308c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e945223013e80c4f0550a388cbc0811861846ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-creating-the-fabrikam-3a2-trading-partner-agreement"></a><span data-ttu-id="ace8b-102">Étape 5 : Création de l’accord de partenariat commercial Fabrikam 3A2</span><span class="sxs-lookup"><span data-stu-id="ace8b-102">Step 5: Creating the Fabrikam 3A2 Trading Partner Agreement</span></span>
<span data-ttu-id="ace8b-103">Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="ace8b-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="ace8b-104">Vous créez un accord de partenariat commercial pour le 3A2 processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="ace8b-104">You create a new trading partner agreement for the 3A2 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="ace8b-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="ace8b-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="ace8b-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="ace8b-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-3a2-trading-partner-agreement"></a><span data-ttu-id="ace8b-107">Pour créer l’accord de partenariat commercial 3A2</span><span class="sxs-lookup"><span data-stu-id="ace8b-107">To create the 3A2 trading partner agreement</span></span>  
  
1.  <span data-ttu-id="ace8b-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .</span><span class="sxs-lookup"><span data-stu-id="ace8b-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="ace8b-109">Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ace8b-109">In the **New Agreement Properties** dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="ace8b-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ace8b-110">Use this</span></span>|<span data-ttu-id="ace8b-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ace8b-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ace8b-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ace8b-112">**Name**</span></span>|<span data-ttu-id="ace8b-113">Type **Fabrikam_To_Contoso_3A2**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-113">Type **Fabrikam_To_Contoso_3A2**.</span></span>|  
    |<span data-ttu-id="ace8b-114">**Configuration de processus**</span><span class="sxs-lookup"><span data-stu-id="ace8b-114">**Process Configuration**</span></span>|<span data-ttu-id="ace8b-115">Sélectionnez **STD_3A2_R02.00.00A** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-115">Select **STD_3A2_R02.00.00A** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ace8b-116">**Mon organisation**</span><span class="sxs-lookup"><span data-stu-id="ace8b-116">**My Organization**</span></span>|<span data-ttu-id="ace8b-117">Sélectionnez **Fabrikam** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-117">Select **Fabrikam** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ace8b-118">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="ace8b-118">**Partner Organization**</span></span>|<span data-ttu-id="ace8b-119">Sélectionnez **Contoso** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-119">Select **Contoso** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ace8b-120">**Version de RNIF**</span><span class="sxs-lookup"><span data-stu-id="ace8b-120">**RNIF Version**</span></span>|<span data-ttu-id="ace8b-121">Sélectionnez **V02.00.01** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-121">Select **V02.00.01** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ace8b-122">**Rôle de base**</span><span class="sxs-lookup"><span data-stu-id="ace8b-122">**Home Role**</span></span>|<span data-ttu-id="ace8b-123">Sélectionnez **client (initiateur)** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-123">Select **Customer (Initiator)** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ace8b-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="ace8b-124">**Usage**</span></span>|<span data-ttu-id="ace8b-125">Sélectionnez **Test** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ace8b-125">Select **Test** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="ace8b-126">Cliquez sur l'onglet **Ports** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ace8b-126">Click the **Ports** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="ace8b-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="ace8b-127">Use this</span></span>|<span data-ttu-id="ace8b-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ace8b-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ace8b-129">**URL d’action**</span><span class="sxs-lookup"><span data-stu-id="ace8b-129">**Action URL**</span></span>|<span data-ttu-id="ace8b-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="ace8b-131">**URL de signal**</span><span class="sxs-lookup"><span data-stu-id="ace8b-131">**Signal URL**</span></span>|<span data-ttu-id="ace8b-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="ace8b-133">**URL de synchronisation**</span><span class="sxs-lookup"><span data-stu-id="ace8b-133">**Sync URL**</span></span>|<span data-ttu-id="ace8b-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
  
4.  <span data-ttu-id="ace8b-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-135">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ace8b-136">Cliquez sur le **Fabrikam_To_Contoso_3A2** accord, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="ace8b-136">Right-click the **Fabrikam_To_Contoso_3A2** agreement and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace8b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ace8b-137">See Also</span></span>  
 [<span data-ttu-id="ace8b-138">Étape 6 : Création de l’accord de partenariat commercial Fabrikam 3 a 4</span><span class="sxs-lookup"><span data-stu-id="ace8b-138">Step 6: Creating the Fabrikam 3A4 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-creating-the-fabrikam-3a4-trading-partner-agreement.md)