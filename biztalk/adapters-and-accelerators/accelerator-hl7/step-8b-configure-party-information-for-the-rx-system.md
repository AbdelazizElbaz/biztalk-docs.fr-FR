---
title: "Étape 8 : configurer les informations de tiers pour le système RX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0b34ec9-220d-4a6b-9712-54c8099b663b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29ab7194e0e1b81a773c61123de9171f1c65eb0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8b-configure-party-information-for-the-rx-system"></a><span data-ttu-id="60a46-102">Étape 8 : configurer les informations de tiers pour le système RX</span><span class="sxs-lookup"><span data-stu-id="60a46-102">Step 8B: Configure Party Information for the RX System</span></span>
<span data-ttu-id="60a46-103">Dans cette étape, vous configurez les informations de tiers pour le système RX.</span><span class="sxs-lookup"><span data-stu-id="60a46-103">In this step, you configure the party information for the RX System.</span></span>  
  
### <a name="to-configure-the-rx-system-party-information"></a><span data-ttu-id="60a46-104">Pour configurer les informations de tiers RX système</span><span class="sxs-lookup"><span data-stu-id="60a46-104">To configure the RX System party information</span></span>  
  
1.  <span data-ttu-id="60a46-105">Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="60a46-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="60a46-106">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_RXSystem**.</span><span class="sxs-lookup"><span data-stu-id="60a46-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_RXSystem**.</span></span>  
  
3.  <span data-ttu-id="60a46-107">Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="60a46-107">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="60a46-108">Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_sendMsg_RX**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="60a46-108">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendMsg_RX**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="60a46-109">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="60a46-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="60a46-110">Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **MSH carte** onglet, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="60a46-110">In the BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="60a46-111">Utiliser</span><span class="sxs-lookup"><span data-stu-id="60a46-111">Use this</span></span>|<span data-ttu-id="60a46-112">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="60a46-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="60a46-113">**MSH3**</span><span class="sxs-lookup"><span data-stu-id="60a46-113">**MSH3**</span></span>|<span data-ttu-id="60a46-114">Type **BTAHL7** dans la zone de texte de gauche.</span><span class="sxs-lookup"><span data-stu-id="60a46-114">Type **BTAHL7** in the left text box.</span></span>|  
    |<span data-ttu-id="60a46-115">**MSH5**</span><span class="sxs-lookup"><span data-stu-id="60a46-115">**MSH5**</span></span>|<span data-ttu-id="60a46-116">Type **Tutorial_RXSystem** dans la zone de texte de gauche.</span><span class="sxs-lookup"><span data-stu-id="60a46-116">Type **Tutorial_RXSystem** in the left text box.</span></span>|  
  
7.  <span data-ttu-id="60a46-117">Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="60a46-117">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
 <span data-ttu-id="60a46-118">Passez à [étape 8C : configurer les informations de tiers pour le système HI](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md).</span><span class="sxs-lookup"><span data-stu-id="60a46-118">Proceed to [Step 8C: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md).</span></span>