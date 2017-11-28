---
title: "Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans le lot hors | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a93d774b-1282-40d9-836f-44abeb65f78e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 982b17fe3826a0e5c5ee2a42030ba020b755ab70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a><span data-ttu-id="6c25c-102">Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans / hors du lot</span><span class="sxs-lookup"><span data-stu-id="6c25c-102">Step 1: Configure Party Information for Batch In/Batch Out</span></span>
<span data-ttu-id="6c25c-103">Dans cette étape, vous désactivez la fragmentation du traitement par lot pour le tiers, l’activation du lot dans / scénario du lot.</span><span class="sxs-lookup"><span data-stu-id="6c25c-103">In this step, you turn off fragmentation of batching for the party, enabling the Batch In/Batch Out scenario.</span></span> <span data-ttu-id="6c25c-104">Puis redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour activer la modification de configuration prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6c25c-104">You then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to enable the configuration change to take effect.</span></span>  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a><span data-ttu-id="6c25c-105">Pour désactiver la fragmentation du traitement par lot pour le tiers</span><span class="sxs-lookup"><span data-stu-id="6c25c-105">To turn off fragmentation of batching for the party</span></span>  
  
1.  <span data-ttu-id="6c25c-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="6c25c-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
2.  <span data-ttu-id="6c25c-107">Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans le volet gauche, cliquez sur **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="6c25c-107">In BTAHL7 Configuration Explorer, on the **Parties** tab in the left-hand pane, click **Tutorial_BatchSource**.</span></span>  
  
3.  <span data-ttu-id="6c25c-108">Cliquez sur le **définition de lot** onglet.</span><span class="sxs-lookup"><span data-stu-id="6c25c-108">Click the **Batch Definition** tab.</span></span>  
  
4.  <span data-ttu-id="6c25c-109">Sélectionnez **non** pour **Fragmentation requise**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="6c25c-109">Select **No** for **Fragmentation required**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="6c25c-110">Assurez-vous que **prise en charge de l’échange récupérable nécessaire** liste déroulante **False** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6c25c-110">Make sure that in **Recoverable Interchange Support Required** dropdown list **False** is selected.</span></span>  
  
 <span data-ttu-id="6c25c-111">Passez à [étape 2 : modifier ou créer l’envoi et Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span><span class="sxs-lookup"><span data-stu-id="6c25c-111">Proceed to [Step 2: Modify or Create the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span></span>