---
title: "Étape 2 : Création de l’organisation partenaire Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, creating partner organizations
ms.assetid: ebb3b166-3781-40b9-89d4-2ca0c83d05f3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5d3f29a2a369f37589f3356da1a1183d8cb91b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-creating-the-contoso-partner-organization"></a><span data-ttu-id="aa58d-102">Étape 2 : Création de l’organisation partenaire Contoso</span><span class="sxs-lookup"><span data-stu-id="aa58d-102">Step 2: Creating the Contoso Partner Organization</span></span>
<span data-ttu-id="aa58d-103">Dans cette étape, vous utilisez la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion pour créer un nouveau partenaire commercial.</span><span class="sxs-lookup"><span data-stu-id="aa58d-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner.</span></span> <span data-ttu-id="aa58d-104">Le partenaire commercial pour ce didacticiel est l'organisation Contoso.</span><span class="sxs-lookup"><span data-stu-id="aa58d-104">The trading partner for this tutorial is the Contoso organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="aa58d-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="aa58d-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="aa58d-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="aa58d-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a><span data-ttu-id="aa58d-107">Pour créer le partenaire commercial Fabrikam</span><span class="sxs-lookup"><span data-stu-id="aa58d-107">To create Fabrikam as a trading partner</span></span>  
  
1.  <span data-ttu-id="aa58d-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **partenaires**, pointez sur **nouveau**, puis cliquez sur **partenaire**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.</span></span>  
  
2.  <span data-ttu-id="aa58d-109">Dans la boîte de dialogue Propriétés du nouveau partenaire, sous l'onglet **Général** , procédez comme suit**:**</span><span class="sxs-lookup"><span data-stu-id="aa58d-109">In the New Partner Properties dialog box, on the **General** tab, do the following**:**</span></span>  
  
    |<span data-ttu-id="aa58d-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="aa58d-110">Use this</span></span>|<span data-ttu-id="aa58d-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="aa58d-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aa58d-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="aa58d-112">**Name**</span></span>|<span data-ttu-id="aa58d-113">Tapez **CONTOSO**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-113">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="aa58d-114">**GBI**</span><span class="sxs-lookup"><span data-stu-id="aa58d-114">**GBI**</span></span>|<span data-ttu-id="aa58d-115">Tapez **123456789**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-115">Type **123456789**.</span></span>|  
    |<span data-ttu-id="aa58d-116">**Classification du partenaire**</span><span class="sxs-lookup"><span data-stu-id="aa58d-116">**Partner Classification**</span></span>|<span data-ttu-id="aa58d-117">Sélectionnez **Fabricant** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="aa58d-117">Select **Manufacturer** from the drop-down list.</span></span>|  
    |<span data-ttu-id="aa58d-118">**Certificat de signature**</span><span class="sxs-lookup"><span data-stu-id="aa58d-118">**Signature Certificate**</span></span>|<span data-ttu-id="aa58d-119">Sélectionnez **Signature Contoso [Thumbprint]** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="aa58d-119">Select **Contoso Signature [Thumbprint]** from the drop-down list.</span></span>|  
    |<span data-ttu-id="aa58d-120">**Certificat de chiffrement**</span><span class="sxs-lookup"><span data-stu-id="aa58d-120">**Encryption Certificate**</span></span>|<span data-ttu-id="aa58d-121">Sélectionnez **Chiffrement Contoso [Thumbprint]** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="aa58d-121">Select **Contoso Encryption [Thumbprint]** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="aa58d-122">Cliquez sur l'onglet **Propriétés du contact** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aa58d-122">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="aa58d-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="aa58d-123">Use this</span></span>|<span data-ttu-id="aa58d-124">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="aa58d-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aa58d-125">**Nom du contact**</span><span class="sxs-lookup"><span data-stu-id="aa58d-125">**Contact Name**</span></span>|<span data-ttu-id="aa58d-126">Tapez **Olivier Renaud**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-126">Type **John Doe**.</span></span>|  
    |<span data-ttu-id="aa58d-127">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="aa58d-127">**E-mail Address**</span></span>|<span data-ttu-id="aa58d-128">Type  **jdoe@contoso.com** .</span><span class="sxs-lookup"><span data-stu-id="aa58d-128">Type **jdoe@contoso.com**.</span></span>|  
    |<span data-ttu-id="aa58d-129">**Numéro de téléphone**</span><span class="sxs-lookup"><span data-stu-id="aa58d-129">**Telephone Number**</span></span>|<span data-ttu-id="aa58d-130">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-130">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="aa58d-131">**Numéro de télécopie**</span><span class="sxs-lookup"><span data-stu-id="aa58d-131">**Fax Number**</span></span>|<span data-ttu-id="aa58d-132">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-132">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="aa58d-133">**Code de la chaîne logistique**</span><span class="sxs-lookup"><span data-stu-id="aa58d-133">**Supply chain code**</span></span>|<span data-ttu-id="aa58d-134">Tapez **Electronic Components**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-134">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="aa58d-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa58d-135">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa58d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa58d-136">See Also</span></span>  
 [<span data-ttu-id="aa58d-137">Étape 3 : Création de l’accord de partenariat commercial Fabrikam 0C2</span><span class="sxs-lookup"><span data-stu-id="aa58d-137">Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)