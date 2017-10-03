---
title: "La désactivation de suivi BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, disabling BAM tracking
- BAM tracking
ms.assetid: ea5fef0e-7a96-46f5-81d8-9b1d8a5d24d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4e734bd31147ecacc8bbbe98d98297edfb4f0de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disabling-bam-tracking"></a><span data-ttu-id="772d5-102">La désactivation de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="772d5-102">Disabling BAM Tracking</span></span>
<span data-ttu-id="772d5-103">Par défaut, le suivi BAM est activé pour le rapprochement de réponse de FIN.</span><span class="sxs-lookup"><span data-stu-id="772d5-103">By default, BAM tracking is enabled for FIN Response Reconciliation.</span></span> <span data-ttu-id="772d5-104">Vous pouvez le désactiver comme suit.</span><span class="sxs-lookup"><span data-stu-id="772d5-104">You can disable it as follows.</span></span>  
  
### <a name="to-disable-bam-tracking-for-frr"></a><span data-ttu-id="772d5-105">Pour désactiver le suivi pour FRR BAM</span><span class="sxs-lookup"><span data-stu-id="772d5-105">To disable BAM tracking for FRR</span></span>  
  
1.  <span data-ttu-id="772d5-106">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="772d5-106">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="772d5-107">Dans le volet gauche de l’Éditeur du Registre, déplacez à mon ordinateur/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator pour SWIFT/FRR.</span><span class="sxs-lookup"><span data-stu-id="772d5-107">In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="772d5-108">Cette entrée de Registre doit être modifiée sur chaque ordinateur rapprochement de réponse de FIN est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="772d5-108">This registry entry must be modified on each computer that FIN Response Reconciliation is running on.</span></span>  
  
3.  <span data-ttu-id="772d5-109">Dans le volet droit de l’Éditeur du Registre, double-cliquez sur **BAMTrackingEnabled**.</span><span class="sxs-lookup"><span data-stu-id="772d5-109">In the right pane of the Registry Editor, double-click **BAMTrackingEnabled**.</span></span>  
  
4.  <span data-ttu-id="772d5-110">Dans le **modifier la valeur DWORD** boîte de dialogue le **données de la valeur** , tapez **0** pour désactiver le suivi BAM.</span><span class="sxs-lookup"><span data-stu-id="772d5-110">In the **Edit DWORD Value** dialog box, in the **Value data** box, type **0** to disable BAM tracking.</span></span>  
  
5.  <span data-ttu-id="772d5-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="772d5-111">Click **OK**.</span></span>