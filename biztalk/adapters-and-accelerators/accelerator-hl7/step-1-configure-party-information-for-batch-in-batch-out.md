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
ms.openlocfilehash: 4cb67fb2e1a232894a0e936bc7827270ca79e6f8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-party-information-for-batch-inbatch-out"></a><span data-ttu-id="24640-102">Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans / hors du lot</span><span class="sxs-lookup"><span data-stu-id="24640-102">Step 1: Configure Party Information for Batch In/Batch Out</span></span>
<span data-ttu-id="24640-103">Dans cette étape, vous désactivez la fragmentation du traitement par lot pour le tiers, l’activation du lot dans / scénario du lot.</span><span class="sxs-lookup"><span data-stu-id="24640-103">In this step, you turn off fragmentation of batching for the party, enabling the Batch In/Batch Out scenario.</span></span> <span data-ttu-id="24640-104">Puis redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour activer la modification de configuration prennent effet.</span><span class="sxs-lookup"><span data-stu-id="24640-104">You then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to enable the configuration change to take effect.</span></span>  
  
### <a name="to-turn-off-fragmentation-of-batching-for-the-party"></a><span data-ttu-id="24640-105">Pour désactiver la fragmentation du traitement par lot pour le tiers</span><span class="sxs-lookup"><span data-stu-id="24640-105">To turn off fragmentation of batching for the party</span></span>  
  
1.  <span data-ttu-id="24640-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur **BTAHL7 Configuration Explorer**.</span><span class="sxs-lookup"><span data-stu-id="24640-106">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
2.  <span data-ttu-id="24640-107">Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans le volet gauche, cliquez sur **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="24640-107">In BTAHL7 Configuration Explorer, on the **Parties** tab in the left-hand pane, click **Tutorial_BatchSource**.</span></span>  
  
3.  <span data-ttu-id="24640-108">Cliquez sur le **définition de lot** onglet.</span><span class="sxs-lookup"><span data-stu-id="24640-108">Click the **Batch Definition** tab.</span></span>  
  
4.  <span data-ttu-id="24640-109">Sélectionnez **non** pour **Fragmentation requise**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="24640-109">Select **No** for **Fragmentation required**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="24640-110">Assurez-vous que **prise en charge de l’échange récupérable nécessaire** liste déroulante **False** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="24640-110">Make sure that in **Recoverable Interchange Support Required** dropdown list **False** is selected.</span></span>  
  
 <span data-ttu-id="24640-111">Passez à [étape 2 : modifier ou créer l’envoi et Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span><span class="sxs-lookup"><span data-stu-id="24640-111">Proceed to [Step 2: Modify or Create the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).</span></span>