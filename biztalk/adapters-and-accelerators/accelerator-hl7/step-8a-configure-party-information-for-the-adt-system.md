---
title: "Étape 8 : configurer les informations de tiers pour le système ADT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0d750c2-a3c6-4571-a4e1-0d0aaaa4d400
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42b92e3b55cd4de181103e28526abf3ecde29412
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-8a-configure-party-information-for-the-adt-system"></a><span data-ttu-id="108d0-102">Étape 8 : configurer les informations de tiers pour le système ADT</span><span class="sxs-lookup"><span data-stu-id="108d0-102">Step 8A: Configure Party Information for the ADT System</span></span>
<span data-ttu-id="108d0-103">Dans cette étape, vous configurez les informations de tiers pour le système ADT.</span><span class="sxs-lookup"><span data-stu-id="108d0-103">In this step, you configure the party information for the ADT System.</span></span>  
  
### <a name="to-configure-the-adt-system-party-information"></a><span data-ttu-id="108d0-104">Pour configurer les informations de tiers ADT système</span><span class="sxs-lookup"><span data-stu-id="108d0-104">To configure the ADT System party information</span></span>  
  
1.  <span data-ttu-id="108d0-105">Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="108d0-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="108d0-106">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_ADTSystem**.</span><span class="sxs-lookup"><span data-stu-id="108d0-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_ADTSystem**.</span></span> <span data-ttu-id="108d0-107">(La valeur que vous tapez dans cette zone est à partir de l’instance de message HL7 d’origine, ADT^A03.txt MSH3.)</span><span class="sxs-lookup"><span data-stu-id="108d0-107">(The value you type in this box is from the original HL7 message instance, ADT^A03.txt MSH3.)</span></span>  
  
3.  <span data-ttu-id="108d0-108">Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="108d0-108">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="108d0-109">Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_sendAck_ADT**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="108d0-109">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_sendAck_ADT**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="108d0-110">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.</span><span class="sxs-lookup"><span data-stu-id="108d0-110">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="108d0-111">Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **accusé de réception** onglet. Pour **type d’accusé de réception**, sélectionnez **EnhancedMode**.</span><span class="sxs-lookup"><span data-stu-id="108d0-111">In the BTAHL7 Configuration Explorer, select the **Acknowledgment** tab. For **Acknowledgment type**, select **EnhancedMode**.</span></span>  
  
7.  <span data-ttu-id="108d0-112">Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="108d0-112">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
 <span data-ttu-id="108d0-113">Passez à [étape 8 : configurer les informations de tiers pour le système RX](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md).</span><span class="sxs-lookup"><span data-stu-id="108d0-113">Proceed to [Step 8B: Configure Party Information for the RX System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md).</span></span>