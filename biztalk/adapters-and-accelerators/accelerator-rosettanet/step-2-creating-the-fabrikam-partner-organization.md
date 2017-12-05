---
title: "Étape 2 : Création de l’organisation partenaire Fabrikam | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- double action tutorial, creating partner organizations
- trading partners, partner organization
ms.assetid: 4d2ddc4c-2275-4faf-9a36-8a912cc06527
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de00977edecb97420742a6510c3290cfe3c76ea5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-creating-the-fabrikam-partner-organization"></a><span data-ttu-id="45217-102">Étape 2 : Création de l’organisation partenaire Fabrikam</span><span class="sxs-lookup"><span data-stu-id="45217-102">Step 2: Creating the Fabrikam Partner Organization</span></span>
<span data-ttu-id="45217-103">Dans cette étape, vous utilisez la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion pour créer un nouveau partenaire commercial.</span><span class="sxs-lookup"><span data-stu-id="45217-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create a new trading partner.</span></span> <span data-ttu-id="45217-104">Le partenaire commercial pour ce didacticiel est de l’organisation de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="45217-104">The trading partner for this tutorial is the Fabrikam organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="45217-105">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="45217-105">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="45217-106">Sur l’ordinateur Contoso, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="45217-106">On the Contoso computer, click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a><span data-ttu-id="45217-107">Pour créer le partenaire commercial Fabrikam</span><span class="sxs-lookup"><span data-stu-id="45217-107">To create Fabrikam as a trading partner</span></span>  
  
1.  <span data-ttu-id="45217-108">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **partenaires**, pointez sur **nouveau**, puis cliquez sur **partenaire**.</span><span class="sxs-lookup"><span data-stu-id="45217-108">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Partners**, point to **New**, and then click **Partner**.</span></span>  
  
2.  <span data-ttu-id="45217-109">Dans la boîte de dialogue Propriétés du nouveau partenaire, sous l'onglet **Général** , procédez comme suit**:**</span><span class="sxs-lookup"><span data-stu-id="45217-109">In the New Partner Properties dialog box, on the **General** tab, do the following**:**</span></span>  
  
    |<span data-ttu-id="45217-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="45217-110">Use this</span></span>|<span data-ttu-id="45217-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="45217-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="45217-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="45217-112">**Name**</span></span>|<span data-ttu-id="45217-113">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="45217-113">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="45217-114">**GBI**</span><span class="sxs-lookup"><span data-stu-id="45217-114">**GBI**</span></span>|<span data-ttu-id="45217-115">Tapez **987654321**.</span><span class="sxs-lookup"><span data-stu-id="45217-115">Type **987654321**.</span></span> <span data-ttu-id="45217-116">**Remarque :** si vous avez exécuté le didacticiel de bouclage sur le même ordinateur, vous devez entrer une valeur pour GBI est différent de « 987654321 ».</span><span class="sxs-lookup"><span data-stu-id="45217-116">**Note:**  If you have run the Loopback tutorial on the same computer, you will have to enter a value for GBI that is different than "987654321".</span></span>|  
    |<span data-ttu-id="45217-117">**Classification du partenaire**</span><span class="sxs-lookup"><span data-stu-id="45217-117">**Partner Classification**</span></span>|<span data-ttu-id="45217-118">Sélectionnez **Acheteur** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="45217-118">Select **Shopper** from the drop-down list.</span></span>|  
    |<span data-ttu-id="45217-119">**Certificat de signature**</span><span class="sxs-lookup"><span data-stu-id="45217-119">**Signature Certificate**</span></span>|<span data-ttu-id="45217-120">Sélectionnez **Fabrikam Signature [Thumbprint]** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="45217-120">Select **Fabrikam Signature [Thumbprint]** from the drop-down list.</span></span>|  
    |<span data-ttu-id="45217-121">**Certificat de chiffrement**</span><span class="sxs-lookup"><span data-stu-id="45217-121">**Encryption Certificate**</span></span>|<span data-ttu-id="45217-122">Sélectionnez **Fabrikam chiffrement [Thumbprint]** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="45217-122">Select **Fabrikam Encryption [Thumbprint]** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="45217-123">Cliquez sur l'onglet **Propriétés du contact** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="45217-123">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="45217-124">Propriété</span><span class="sxs-lookup"><span data-stu-id="45217-124">Use this</span></span>|<span data-ttu-id="45217-125">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="45217-125">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="45217-126">**Nom du contact**</span><span class="sxs-lookup"><span data-stu-id="45217-126">**Contact Name**</span></span>|<span data-ttu-id="45217-127">Tapez **Jane Doe**.</span><span class="sxs-lookup"><span data-stu-id="45217-127">Type **Jane Doe**.</span></span>|  
    |<span data-ttu-id="45217-128">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="45217-128">**E-mail Address**</span></span>|<span data-ttu-id="45217-129">Type  **jdoe@fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="45217-129">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="45217-130">**Numéro de téléphone**</span><span class="sxs-lookup"><span data-stu-id="45217-130">**Telephone Number**</span></span>|<span data-ttu-id="45217-131">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="45217-131">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="45217-132">**Numéro de télécopie**</span><span class="sxs-lookup"><span data-stu-id="45217-132">**Fax Number**</span></span>|<span data-ttu-id="45217-133">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="45217-133">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="45217-134">**Code de la chaîne logistique**</span><span class="sxs-lookup"><span data-stu-id="45217-134">**Supply chain code**</span></span>|<span data-ttu-id="45217-135">Tapez **Electronic Components**.</span><span class="sxs-lookup"><span data-stu-id="45217-135">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="45217-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="45217-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45217-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45217-137">See Also</span></span>  
 [<span data-ttu-id="45217-138">Étape 3 : Création de l’accord de partenariat commercial Contoso 0C2</span><span class="sxs-lookup"><span data-stu-id="45217-138">Step 3: Creating the Contoso 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-contoso-0c2-trading-partner-agreement.md)