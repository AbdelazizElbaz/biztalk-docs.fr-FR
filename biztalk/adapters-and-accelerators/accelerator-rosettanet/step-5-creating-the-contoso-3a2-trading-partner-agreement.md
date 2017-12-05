---
title: "Étape 5 : Création de la négociation de Contoso 3A2 accord de partenariat | Documents Microsoft"
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
ms.assetid: 5c602c9c-22bd-450f-bb14-6848b1414c03
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624cd67b5a8b07cadcddb52efecafc032882f840
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-5-creating-the-contoso-3a2-trading-partner-agreement"></a><span data-ttu-id="f0a3a-102">Étape 5 : Création de l’accord de partenariat commercial Contoso 3A2</span><span class="sxs-lookup"><span data-stu-id="f0a3a-102">Step 5: Creating the Contoso 3A2 Trading Partner Agreement</span></span>
<span data-ttu-id="f0a3a-103">Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-103">In this step, you create a trading partner agreement between Contoso and Fabrikam using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console.</span></span> <span data-ttu-id="f0a3a-104">Vous créez un accord de partenariat commercial pour le 3A2 processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="f0a3a-104">You create a new trading partner agreement for the 3A2 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="f0a3a-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="f0a3a-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="f0a3a-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-3a2-trading-partner-agreement"></a><span data-ttu-id="f0a3a-107">Pour créer l’accord de partenariat commercial 3A2</span><span class="sxs-lookup"><span data-stu-id="f0a3a-107">To create the 3A2 trading partner agreement</span></span>  
  
1.  <span data-ttu-id="f0a3a-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .</span><span class="sxs-lookup"><span data-stu-id="f0a3a-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="f0a3a-109">Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f0a3a-109">In the **New Agreement Properties** dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="f0a3a-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f0a3a-110">Use this</span></span>|<span data-ttu-id="f0a3a-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f0a3a-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f0a3a-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-112">**Name**</span></span>|<span data-ttu-id="f0a3a-113">Type **Fabrikam_To_Contoso_3A2**.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-113">Type **Fabrikam_To_Contoso_3A2**.</span></span>|  
    |<span data-ttu-id="f0a3a-114">**Configuration de processus**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-114">**Process Configuration**</span></span>|<span data-ttu-id="f0a3a-115">Sélectionnez **STD_3A2_R02.00.00A** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-115">Select **STD_3A2_R02.00.00A** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f0a3a-116">**Mon organisation**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-116">**My Organization**</span></span>|<span data-ttu-id="f0a3a-117">Sélectionnez **Contoso** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-117">Select **Contoso** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f0a3a-118">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-118">**Partner Organization**</span></span>|<span data-ttu-id="f0a3a-119">Sélectionnez **Fabrikam** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-119">Select **Fabrikam** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f0a3a-120">**Version de RNIF**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-120">**RNIF Version**</span></span>|<span data-ttu-id="f0a3a-121">Sélectionnez **V02.00.01** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-121">Select **V02.00.01** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f0a3a-122">**Rôle de base**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-122">**Home Role**</span></span>|<span data-ttu-id="f0a3a-123">Sélectionnez **fournisseur du produit (récepteur)** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-123">Select **Product Supplier (Responder)** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f0a3a-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-124">**Usage**</span></span>|<span data-ttu-id="f0a3a-125">Sélectionnez **Test** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-125">Select **Test** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="f0a3a-126">Cliquez sur l'onglet **Ports** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f0a3a-126">Click the **Ports** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="f0a3a-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="f0a3a-127">Use this</span></span>|<span data-ttu-id="f0a3a-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f0a3a-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f0a3a-129">**URL d’action**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-129">**Action URL**</span></span>|<span data-ttu-id="f0a3a-130">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-130">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
    |<span data-ttu-id="f0a3a-131">**URL de signal**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-131">**Signal URL**</span></span>|<span data-ttu-id="f0a3a-132">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-132">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
    |<span data-ttu-id="f0a3a-133">**URL de synchronisation**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-133">**Sync URL**</span></span>|<span data-ttu-id="f0a3a-134">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span><span class="sxs-lookup"><span data-stu-id="f0a3a-134">Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**</span></span>|  
  
4.  <span data-ttu-id="f0a3a-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-135">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="f0a3a-136">Cliquez sur le **Fabrikam_To_Contoso_3A2** accord, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="f0a3a-136">Right-click the **Fabrikam_To_Contoso_3A2** agreement, and then click **Activate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a3a-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0a3a-137">See Also</span></span>  
 [<span data-ttu-id="f0a3a-138">Étape 6 : Création de l’accord de partenariat commercial Contoso 3A4</span><span class="sxs-lookup"><span data-stu-id="f0a3a-138">Step 6: Creating the Contoso 3A4 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-creating-the-contoso-3a4-trading-partner-agreement.md)