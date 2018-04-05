---
title: 'Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: a99c2cd1-0d42-4fae-a380-a53d77cd87d0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb980ae879f06beaf468ba9b526ddc4ba83b5b06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-creating-the-fabrikam-0c4-trading-partner-agreement"></a><span data-ttu-id="39962-102">Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C</span><span class="sxs-lookup"><span data-stu-id="39962-102">Step 4: Creating the Fabrikam 0C4 Trading Partner Agreement</span></span>
<span data-ttu-id="39962-103">Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="39962-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="39962-104">Vous allez créer un accord de partenariat commercial pour le processus PIP (Partner Interface Process) 0C4.</span><span class="sxs-lookup"><span data-stu-id="39962-104">You create a new trading partner agreement for the 0C4 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="39962-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="39962-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="39962-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="39962-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-0c4-trading-partner-agreement"></a><span data-ttu-id="39962-107">Pour créer l'accord de partenariat commercial 0C4</span><span class="sxs-lookup"><span data-stu-id="39962-107">To create the 0C4 trading partner agreement</span></span>  
  
1.  <span data-ttu-id="39962-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .</span><span class="sxs-lookup"><span data-stu-id="39962-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="39962-109">Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="39962-109">In the New Agreement Properties dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="39962-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="39962-110">Use this</span></span>|<span data-ttu-id="39962-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="39962-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="39962-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="39962-112">**Name**</span></span>|<span data-ttu-id="39962-113">Tapez **Fabrikam_To_Contoso_0C4**.</span><span class="sxs-lookup"><span data-stu-id="39962-113">Type **Fabrikam_To_Contoso_0C4**.</span></span>|  
    |<span data-ttu-id="39962-114">**Configuration de processus**</span><span class="sxs-lookup"><span data-stu-id="39962-114">**Process Configuration**</span></span>|<span data-ttu-id="39962-115">Sélectionnez **STD_0C4_R01.02** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-115">Select **STD_0C4_R01.02** from the drop-down list.</span></span>|  
    |<span data-ttu-id="39962-116">**Mon organisation**</span><span class="sxs-lookup"><span data-stu-id="39962-116">**My Organization**</span></span>|<span data-ttu-id="39962-117">Sélectionnez **Fabrikam** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-117">Select **Fabrikam** from the drop-down list.</span></span>|  
    |<span data-ttu-id="39962-118">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="39962-118">**Partner Organization**</span></span>|<span data-ttu-id="39962-119">Sélectionnez **Contoso** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-119">Select **Contoso** from the drop-down list.</span></span>|  
    |<span data-ttu-id="39962-120">**Version de RNIF**</span><span class="sxs-lookup"><span data-stu-id="39962-120">**RNIF Version**</span></span>|<span data-ttu-id="39962-121">Sélectionnez **V02.00.01** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-121">Select **V02.00.01** from the drop-down list.</span></span>|  
    |<span data-ttu-id="39962-122">**Rôle de base**</span><span class="sxs-lookup"><span data-stu-id="39962-122">**Home Role**</span></span>|<span data-ttu-id="39962-123">Sélectionnez **initiateur (initiateur)** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-123">Select **Initiator (Initiator)** from the drop-down list.</span></span>|  
    |<span data-ttu-id="39962-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="39962-124">**Usage**</span></span>|<span data-ttu-id="39962-125">Sélectionnez **Test** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="39962-125">Select **Test** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="39962-126">Cliquez sur l'onglet **Ports** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="39962-126">Click the **Ports** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="39962-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="39962-127">Use this</span></span>|<span data-ttu-id="39962-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="39962-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="39962-129">**URL d’action**</span><span class="sxs-lookup"><span data-stu-id="39962-129">**Action URL**</span></span>|<span data-ttu-id="39962-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="39962-130">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="39962-131">**URL de signal**</span><span class="sxs-lookup"><span data-stu-id="39962-131">**Signal URL**</span></span>|<span data-ttu-id="39962-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="39962-132">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
    |<span data-ttu-id="39962-133">**URL de synchronisation**</span><span class="sxs-lookup"><span data-stu-id="39962-133">**Sync URL**</span></span>|<span data-ttu-id="39962-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span><span class="sxs-lookup"><span data-stu-id="39962-134">Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.</span></span>|  
  
4.  <span data-ttu-id="39962-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="39962-135">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="39962-136">Cliquez avec le bouton droit sur l'accord **Fabrikam_To_Contoso_0C4** , puis cliquez sur **Activer**.</span><span class="sxs-lookup"><span data-stu-id="39962-136">Right-click the **Fabrikam_To_Contoso_0C4** agreement, and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39962-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39962-137">See Also</span></span>  
 [<span data-ttu-id="39962-138">Étape 5 : Création de l’accord de partenariat commercial Fabrikam 3A2</span><span class="sxs-lookup"><span data-stu-id="39962-138">Step 5: Creating the Fabrikam 3A2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)