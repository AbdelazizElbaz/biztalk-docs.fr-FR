---
title: "Étape 8 : configurer les informations de tiers pour le système HI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96338c05-1440-416e-a56a-6f5b19b55a60
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 460840cf3bbbd6556b1684b25851a16778be92b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8b-configure-party-information-for-the-hi-system"></a><span data-ttu-id="d7605-102">Étape 8 : configurer les informations de tiers pour le système HI</span><span class="sxs-lookup"><span data-stu-id="d7605-102">Step 8B: Configure Party Information for the HI System</span></span>
<span data-ttu-id="d7605-103">Dans cette étape, vous configurez les informations de tiers pour le système HI.</span><span class="sxs-lookup"><span data-stu-id="d7605-103">In this step, you configure the party information for the HI System.</span></span>  
  
### <a name="to-configure-the-hi-system-party-information"></a><span data-ttu-id="d7605-104">Pour configurer les informations de tiers HI système</span><span class="sxs-lookup"><span data-stu-id="d7605-104">To configure the HI System party information</span></span>  
  
1.  <span data-ttu-id="d7605-105">Dans la Console Administration de BizTalk, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="d7605-105">In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="d7605-106">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **HIS**.</span><span class="sxs-lookup"><span data-stu-id="d7605-106">In the Party Properties dialog box, in the **Name** field, type **HIS**.</span></span> <span data-ttu-id="d7605-107">(La valeur que vous tapez dans cette zone doit correspondre à l’instance de message HL7 d’origine, QRY^Q01.txt MSH5).</span><span class="sxs-lookup"><span data-stu-id="d7605-107">(The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH5.)</span></span>  
  
3.  <span data-ttu-id="d7605-108">Dans l’arborescence de la Console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="d7605-108">In the Console Tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="d7605-109">Dans le **Port d’envoi** volet, pour **nom** dans la première ligne, sélectionnez **HIS_Send**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7605-109">In the **Send Port** pane, for **Name** in the first row, select **HIS_Send**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="d7605-110">Passez à [étape 9 : redémarrez BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md).</span><span class="sxs-lookup"><span data-stu-id="d7605-110">Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md).</span></span>