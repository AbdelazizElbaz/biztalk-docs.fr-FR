---
title: "Étape 3 : Création de l’accord de partenariat commercial 2 Fabrikam 0C | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, creating agreements
ms.assetid: 4552f712-f226-423f-b06d-98e943e8efd4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea6d86369b692a85102a4b267f857b41a0eafb21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-creating-the-fabrikam-0c2-trading-partner-agreement"></a><span data-ttu-id="89b8f-102">Étape 3 : Création de l’accord de partenariat commercial 2 Fabrikam 0C</span><span class="sxs-lookup"><span data-stu-id="89b8f-102">Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement</span></span>
<span data-ttu-id="89b8f-103">Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="89b8f-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="89b8f-104">Vous créez un accord de partenariat commercial pour le C 0 2 processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="89b8f-104">You create a new trading partner agreement for the 0C2 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="89b8f-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="89b8f-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="89b8f-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="89b8f-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-0c2-trading-partner-agreement"></a><span data-ttu-id="89b8f-107">Pour créer le 0C accord de partenariat commercial de 2</span><span class="sxs-lookup"><span data-stu-id="89b8f-107">To create the 0C2 trading partner agreement</span></span>  
  
1.  <span data-ttu-id="89b8f-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .</span><span class="sxs-lookup"><span data-stu-id="89b8f-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="89b8f-109">Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="89b8f-109">In the New Agreement Properties dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="89b8f-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="89b8f-110">Use this</span></span>|<span data-ttu-id="89b8f-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="89b8f-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="89b8f-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="89b8f-112">**Name**</span></span>|<span data-ttu-id="89b8f-113">Type **Fabrikam_To_Contoso_0C2**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-113">Type **Fabrikam_To_Contoso_0C2**.</span></span>|  
    |<span data-ttu-id="89b8f-114">**Configuration de processus**</span><span class="sxs-lookup"><span data-stu-id="89b8f-114">**Process Configuration**</span></span>|<span data-ttu-id="89b8f-115">Sélectionnez **STD_0C2_R01.02** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-115">Select **STD_0C2_R01.02** from the drop-down list.</span></span>|  
    |<span data-ttu-id="89b8f-116">**Mon organisation**</span><span class="sxs-lookup"><span data-stu-id="89b8f-116">**My Organization**</span></span>|<span data-ttu-id="89b8f-117">Sélectionnez **Fabrikam** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-117">Select **Fabrikam** from the drop-down list.</span></span>|  
    |<span data-ttu-id="89b8f-118">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="89b8f-118">**Partner Organization**</span></span>|<span data-ttu-id="89b8f-119">Sélectionnez **Contoso** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-119">Select **Contoso** from the drop-down list.</span></span>|  
    |<span data-ttu-id="89b8f-120">**Version de RNIF**</span><span class="sxs-lookup"><span data-stu-id="89b8f-120">**RNIF Version**</span></span>|<span data-ttu-id="89b8f-121">Sélectionnez **V02.00.01** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-121">Select **V02.00.01** from the drop-down list.</span></span>|  
    |<span data-ttu-id="89b8f-122">**Rôle de base**</span><span class="sxs-lookup"><span data-stu-id="89b8f-122">**Home Role**</span></span>|<span data-ttu-id="89b8f-123">Sélectionnez **initiateur (initiateur)** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-123">Select **Initiator (Initiator)** from the drop-down list.</span></span>|  
    |<span data-ttu-id="89b8f-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89b8f-124">**Usage**</span></span>|<span data-ttu-id="89b8f-125">Sélectionnez **Test** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="89b8f-125">Select **Test** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="89b8f-126">Cliquez sur l'onglet **Ports** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="89b8f-126">Click the **Ports** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="89b8f-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="89b8f-127">Use this</span></span>|<span data-ttu-id="89b8f-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="89b8f-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="89b8f-129">**URL d’action**</span><span class="sxs-lookup"><span data-stu-id="89b8f-129">**Action URL**</span></span>|<span data-ttu-id="89b8f-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="89b8f-131">**URL de signal**</span><span class="sxs-lookup"><span data-stu-id="89b8f-131">**Signal URL**</span></span>|<span data-ttu-id="89b8f-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="89b8f-133">**URL de synchronisation**</span><span class="sxs-lookup"><span data-stu-id="89b8f-133">**Sync URL**</span></span>|<span data-ttu-id="89b8f-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
  
4.  <span data-ttu-id="89b8f-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-135">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="89b8f-136">Cliquez sur le **Fabrikam_To_Contoso_0C2** accord, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="89b8f-136">Right-click the **Fabrikam_To_Contoso_0C2** agreement, and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b8f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b8f-137">See Also</span></span>  
 [<span data-ttu-id="89b8f-138">Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C</span><span class="sxs-lookup"><span data-stu-id="89b8f-138">Step 4: Creating the Fabrikam 0C4 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-fabrikam-0c4-trading-partner-agreement.md)