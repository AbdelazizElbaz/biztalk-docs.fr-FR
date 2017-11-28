---
title: "Définition de délais d’expiration pour une Orchestration de processus publics et d’un adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, HTTP adapters
- public processes, orchestrations
- orchestrations, time-outs
- public processes, time-outs
- orchestrations, public-process orchestrations
- HTTP adapters, public processes
- HTTP adapters, time-outs
ms.assetid: 82fd64ac-6191-410c-94b3-8a3d1ff2611f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8f7f15d01759704af6b6b3134c9d36f0e64f8e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-time-outs-for-a-public-process-orchestration-and-an-http-adapter"></a><span data-ttu-id="2a052-102">Définition de délais d’expiration pour une Orchestration de processus publics et d’un adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="2a052-102">Setting Time-Outs for a Public-Process Orchestration and an HTTP Adapter</span></span>
<span data-ttu-id="2a052-103">Lorsque vous utilisez une orchestration de processus publics avec un adaptateur HTTP dans un scénario synchrone, vous devez définir correctement les délais d’expiration pour chacun.</span><span class="sxs-lookup"><span data-stu-id="2a052-103">When you use a public-process orchestration with an HTTP adapter in a synchronous scenario, you must set the time-outs for each appropriately.</span></span> <span data-ttu-id="2a052-104">Le paramètre de délai d’attente pour l’orchestration (durée des) doit être plus petit que le délai d’attente de l’adaptateur HTTP (délai de demande).</span><span class="sxs-lookup"><span data-stu-id="2a052-104">The time-out setting for the orchestration (Time to Perform) must be smaller than the time-out for the HTTP adapter (Request Timeout).</span></span> <span data-ttu-id="2a052-105">Il s’agit, car si le paramètre de l’adaptateur HTTP est inférieure, l’adaptateur peut expirer avant de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="2a052-105">This is because if the setting for the HTTP adapter is smaller, the adapter could time out before the orchestration.</span></span> <span data-ttu-id="2a052-106">Ainsi, le contrôle de l’adaptateur du processus.</span><span class="sxs-lookup"><span data-stu-id="2a052-106">This gives the adapter control of the process.</span></span> <span data-ttu-id="2a052-107">L’orchestration doit être dans le contrôle du processus ; Par conséquent, sa valeur de délai d’attente doit être plus petite.</span><span class="sxs-lookup"><span data-stu-id="2a052-107">The orchestration must be in control of the process; therefore, its time-out setting must be smaller.</span></span>  
  
### <a name="to-set-the-time-out-setting-for-the-http-adapter"></a><span data-ttu-id="2a052-108">Pour définir le paramètre de délai d’attente de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="2a052-108">To set the time-out setting for the HTTP adapter</span></span>  
  
1.  <span data-ttu-id="2a052-109">Dans l’Explorateur BizTalk, développez **ports d’envoi**, puis double-cliquez sur le port d’envoi HTTP utilisé avec l’orchestration de processus publics.</span><span class="sxs-lookup"><span data-stu-id="2a052-109">In BizTalk Explorer, expand **Send ports**, and then double-click the HTTP send port used with the public-process orchestration.</span></span>  
  
2.  <span data-ttu-id="2a052-110">Dans la fenêtre Propriétés de Port d’envoi, cliquez sur le bouton de sélection (**...** ) pour **adresse (URI)**.</span><span class="sxs-lookup"><span data-stu-id="2a052-110">In the Send Port Properties window, click the ellipsis button (**...**) for **Address (URI)**.</span></span>  
  
3.  <span data-ttu-id="2a052-111">Dans la fenêtre Propriétés du Transport HTTP, dans le volet Général, dans le **(s) de délai de demande** , tapez une valeur appropriée pour le délai d’attente. Cette valeur doit être supérieure à la **temps des** définition pour le pertinentes processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="2a052-111">In the HTTP Transport Properties window, in the General pane, in the **Request timeout (sec.)** box, type an appropriate value for the time-out. This value must be larger than the **Time to Perform** setting for the relevant Partner Interface Process (PIP).</span></span>  
  
4.  <span data-ttu-id="2a052-112">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="2a052-112">Click **OK**, and then click **OK** again.</span></span>  
  
### <a name="to-set-the-time-out-setting-for-the-public-process-orchestration"></a><span data-ttu-id="2a052-113">Pour définir le paramètre de délai d’attente pour l’orchestration de processus publics</span><span class="sxs-lookup"><span data-stu-id="2a052-113">To set the time-out setting for the public-process orchestration</span></span>  
  
1.  <span data-ttu-id="2a052-114">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **BizTalk Accelerator for RosettaNet Management Console**.</span><span class="sxs-lookup"><span data-stu-id="2a052-114">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for RosettaNet**, and then click  **BizTalk Accelerator for RosettaNet Management Console**.</span></span>  
  
2.  <span data-ttu-id="2a052-115">Développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur **les paramètres de Configuration de processus**.</span><span class="sxs-lookup"><span data-stu-id="2a052-115">Expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Process Configuration Settings**.</span></span>  
  
3.  <span data-ttu-id="2a052-116">Cliquez sur le PIP que vous souhaitez définir le délai défini pour, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2a052-116">Right-click the PIP that you want to set the time-out setting for, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2a052-117">Dans la boîte de dialogue Edges, sur le **activité** sous l’onglet du **temps des** zone, tapez une valeur appropriée est plus petite que le délai d’attente de l’adaptateur HTTP définition, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a052-117">In theProperties dialog box, on the **Activity** tab, in the **Time to Perform** box, type an appropriate value that is smaller than the HTTP adapter time-out setting, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a052-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a052-118">See Also</span></span>  
 [<span data-ttu-id="2a052-119">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="2a052-119">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)