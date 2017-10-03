---
title: Planifier le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, scheduling
- scheduling batching
ms.assetid: 037626f1-1b3b-43e6-80eb-5fb900cdbd46
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08337171897a4a78e605054e9126e8c8238d5fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduling-batching"></a><span data-ttu-id="173c7-102">Planification de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="173c7-102">Scheduling Batching</span></span>
<span data-ttu-id="173c7-103">Vous utilisez [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Explorer de Configuration pour activer, de demande ou de mettre fin à un lot sortant.</span><span class="sxs-lookup"><span data-stu-id="173c7-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to activate, request, or terminate an outbound batch.</span></span> <span data-ttu-id="173c7-104">Activation d’un lot sortant comprend deux étapes : configuration temporels ou message compter les critères et avant de démarrer l’orchestration de traitement par lot sortante.</span><span class="sxs-lookup"><span data-stu-id="173c7-104">Activating an outbound batch consists of two steps: configuring time-based or message count criteria and then starting the outbound batching orchestration.</span></span>  
  
 <span data-ttu-id="173c7-105">L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **planification par lot** onglet.</span><span class="sxs-lookup"><span data-stu-id="173c7-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Schedule** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")  
  
 <span data-ttu-id="173c7-106">Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et la planification de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="173c7-106">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and schedule batching.</span></span>  
  
### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="173c7-107">Pour ouvrir l’Explorateur de Configuration de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="173c7-107">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="173c7-108">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="173c7-108">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-schedule-message-batching"></a><span data-ttu-id="173c7-109">Pour planifier le traitement par lots du message</span><span class="sxs-lookup"><span data-stu-id="173c7-109">To schedule message batching</span></span>  
  
1.  <span data-ttu-id="173c7-110">Ouvrez l’Explorateur de Configuration de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="173c7-110">Open BTAHL7 Configuration Explorer.</span></span>  
  
2.  <span data-ttu-id="173c7-111">Dans l’Explorateur de Configuration de BTAHL7, dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **lot planification** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="173c7-111">In BTAHL7 Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Schedule** tab, do the following:</span></span>  
  
    |<span data-ttu-id="173c7-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="173c7-112">Use this</span></span>|<span data-ttu-id="173c7-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="173c7-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="173c7-114">**Heures avant tout d’abord du lot**</span><span class="sxs-lookup"><span data-stu-id="173c7-114">**Hours before first batch**</span></span>|<span data-ttu-id="173c7-115">Tapez le nombre d’heures avant le premier traitement consiste à démarrer.</span><span class="sxs-lookup"><span data-stu-id="173c7-115">Type the number of hours before the first batch is to start.</span></span>|  
    |<span data-ttu-id="173c7-116">**Répétez le traitement par lots après**</span><span class="sxs-lookup"><span data-stu-id="173c7-116">**Repeat Batch After**</span></span>|<span data-ttu-id="173c7-117">Sélectionnez l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="173c7-117">Select one of the following:</span></span><br /><br /> <span data-ttu-id="173c7-118">-   **Heures**.</span><span class="sxs-lookup"><span data-stu-id="173c7-118">-   **Hours**.</span></span> <span data-ttu-id="173c7-119">Tapez le nombre d’heures de répéter le processus de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="173c7-119">Type the number of hours to repeat the batch process.</span></span><br /><span data-ttu-id="173c7-120">-   **Messages**.</span><span class="sxs-lookup"><span data-stu-id="173c7-120">-   **Messages**.</span></span> <span data-ttu-id="173c7-121">Tapez le nombre de messages à traiter avant que le processus de traitement suivant commence.</span><span class="sxs-lookup"><span data-stu-id="173c7-121">Type the number of messages you want to process before the next batch process begins.</span></span>|  
    |<span data-ttu-id="173c7-122">**Contrôle de traitement par lots**</span><span class="sxs-lookup"><span data-stu-id="173c7-122">**Batch Control**</span></span>|<span data-ttu-id="173c7-123">Sélectionnez l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="173c7-123">Select one of the following:</span></span><br /><br /> <span data-ttu-id="173c7-124">-   **Démarrer la planification**: sélectionnez cette option pour démarrer la planification par lot.</span><span class="sxs-lookup"><span data-stu-id="173c7-124">-   **Start Schedule**: Select to start the batch schedule.</span></span><br /><span data-ttu-id="173c7-125">-   **Envoyer maintenant**: sélectionnez cette option pour démarrer le traitement est immédiatement traité.</span><span class="sxs-lookup"><span data-stu-id="173c7-125">-   **Send Now**: Select to start the batch process immediately.</span></span><br /><span data-ttu-id="173c7-126">-   **Arrêter planification**: sélectionnez cette option pour arrêter la planification du lot actuel.</span><span class="sxs-lookup"><span data-stu-id="173c7-126">-   **Stop Schedule**: Select to stop the current batch schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="173c7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="173c7-127">See Also</span></span>  
 [<span data-ttu-id="173c7-128">Configuration des accusés de réception de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="173c7-128">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)