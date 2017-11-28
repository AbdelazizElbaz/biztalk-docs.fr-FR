---
title: "Étape 1 : Création de l’organisation Contoso accueil | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating home organizations
- creating, home organizations
- home organizations, creating
ms.assetid: 0e7a53b9-ae59-4cd1-88bd-0ada7e65acba
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21e6afcc3aca274d968b15f2bbe93c2226e54a48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-the-contoso-home-organization"></a><span data-ttu-id="1a66c-102">Étape 1 : Création de l’organisation d’accueil de Contoso</span><span class="sxs-lookup"><span data-stu-id="1a66c-102">Step 1: Creating the Contoso Home Organization</span></span>
<span data-ttu-id="1a66c-103">Dans cette étape, vous utilisez la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion pour créer l’organisation d’origine Contoso.</span><span class="sxs-lookup"><span data-stu-id="1a66c-103">In this step, you use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console to create the Contoso home organization.</span></span>  
  
### <a name="to-start-the-btarn-management-console"></a><span data-ttu-id="1a66c-104">Pour démarrer la console de gestion BTARN</span><span class="sxs-lookup"><span data-stu-id="1a66c-104">To start the BTARN Management Console</span></span>  
  
-   <span data-ttu-id="1a66c-105">Sur l’ordinateur Contoso, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet** puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="1a66c-105">On the Contoso computer, click **Start**, point to **All Programs**, point to **Microsoft  BizTalk \<version> Accelerator for RosettaNet** and then click **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console.</span></span>  
  
### <a name="to-create-the-home-organization"></a><span data-ttu-id="1a66c-106">Pour créer l'organisation d'origine</span><span class="sxs-lookup"><span data-stu-id="1a66c-106">To create the home organization</span></span>  
  
1.  <span data-ttu-id="1a66c-107">Dans le [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accueil organisations**, pointez sur **nouveau**, puis cliquez sur **organisation d’origine**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-107">In the [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], right-click **Home Organizations**, point to **New**, and then click **Home Organization**.</span></span>  
  
2.  <span data-ttu-id="1a66c-108">Dans la boîte de dialogue Nouvelle accueil propriétés de l’organisation, sur le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1a66c-108">In the New Home Organization Properties dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="1a66c-109">Utiliser</span><span class="sxs-lookup"><span data-stu-id="1a66c-109">Use this</span></span>|<span data-ttu-id="1a66c-110">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="1a66c-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1a66c-111">**Nom**</span><span class="sxs-lookup"><span data-stu-id="1a66c-111">**Name**</span></span>|<span data-ttu-id="1a66c-112">Tapez **CONTOSO**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-112">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="1a66c-113">**GBI**</span><span class="sxs-lookup"><span data-stu-id="1a66c-113">**GBI**</span></span>|<span data-ttu-id="1a66c-114">Tapez **123456789**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-114">Type **123456789**.</span></span> <span data-ttu-id="1a66c-115">**Remarque :** si vous avez exécuté le didacticiel de bouclage sur le même ordinateur, vous devez entrer une valeur pour GBI est différent de « 123456789 ».</span><span class="sxs-lookup"><span data-stu-id="1a66c-115">**Note:**  If you have run the Loopback tutorial on the same computer, you will have to enter a value for GBI that is different than "123456789".</span></span>|  
    |<span data-ttu-id="1a66c-116">**Classification de l’organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="1a66c-116">**Home Organization Classification**</span></span>|<span data-ttu-id="1a66c-117">Sélectionnez **Fabricant** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="1a66c-117">Select **Manufacturer** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="1a66c-118">Cliquez sur l'onglet **Propriétés du contact** , puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1a66c-118">Click the **Contact Properties** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="1a66c-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="1a66c-119">Use this</span></span>|<span data-ttu-id="1a66c-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="1a66c-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1a66c-121">**Nom du contact**</span><span class="sxs-lookup"><span data-stu-id="1a66c-121">**Contact Name**</span></span>|<span data-ttu-id="1a66c-122">Tapez **Olivier Renaud**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-122">Type **John Doe**.</span></span>|  
    |<span data-ttu-id="1a66c-123">**E-mail Address**</span><span class="sxs-lookup"><span data-stu-id="1a66c-123">**E-mail Address**</span></span>|<span data-ttu-id="1a66c-124">Type  **jdoe@contoso.com** .</span><span class="sxs-lookup"><span data-stu-id="1a66c-124">Type **jdoe@contoso.com**.</span></span>|  
    |<span data-ttu-id="1a66c-125">**Numéro de téléphone**</span><span class="sxs-lookup"><span data-stu-id="1a66c-125">**Telephone Number**</span></span>|<span data-ttu-id="1a66c-126">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-126">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="1a66c-127">**Numéro de télécopie**</span><span class="sxs-lookup"><span data-stu-id="1a66c-127">**Fax Number**</span></span>|<span data-ttu-id="1a66c-128">Tapez **555-555-5555**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-128">Type **555-555-5555**.</span></span>|  
    |<span data-ttu-id="1a66c-129">**Code de la chaîne logistique**</span><span class="sxs-lookup"><span data-stu-id="1a66c-129">**Supply Chain Code**</span></span>|<span data-ttu-id="1a66c-130">Tapez **Electronic Components**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-130">Type **Electronic Components**.</span></span>|  
  
4.  <span data-ttu-id="1a66c-131">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a66c-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a66c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a66c-132">See Also</span></span>  
 [<span data-ttu-id="1a66c-133">Étape 2 : Création de l’organisation partenaire Fabrikam</span><span class="sxs-lookup"><span data-stu-id="1a66c-133">Step 2: Creating the Fabrikam Partner Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-the-fabrikam-partner-organization.md)