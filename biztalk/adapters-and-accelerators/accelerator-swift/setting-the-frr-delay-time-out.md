---
title: Définir le délai d’expiration de délai FRR | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring delay time-out
ms.assetid: 62209bf6-56c8-483a-96d5-328bffc8b680
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf4c08984876627c0f11f935b0be3e32769b5f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-frr-delay-time-out"></a><span data-ttu-id="274ce-102">Définir le délai d’expiration du délai FRR</span><span class="sxs-lookup"><span data-stu-id="274ce-102">Setting the FRR Delay Time-Out</span></span>
<span data-ttu-id="274ce-103">Vous devez configurer l’orchestration FRR expire après une durée, donc il n’attendra pas la réponse FNN indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="274ce-103">You must configure the FRR orchestration to time out after some duration, so it will not wait for the FNN response indefinitely.</span></span> <span data-ttu-id="274ce-104">Si la durée du délai d’attente expire, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publie les messages expiré à un gestionnaire de délai d’attente personnalisée.</span><span class="sxs-lookup"><span data-stu-id="274ce-104">If the time-out duration expires, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publishes the timed-out messages to a custom time-out handler.</span></span>  
  
### <a name="to-set-the-frr-delay-time-out"></a><span data-ttu-id="274ce-105">Pour définir le délai d’expiration du délai FRR</span><span class="sxs-lookup"><span data-stu-id="274ce-105">To set the FRR delay time-out</span></span>  
  
1.  <span data-ttu-id="274ce-106">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="274ce-106">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="274ce-107">Dans le volet gauche de l’Éditeur du Registre, déplacez à mon ordinateur/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator pour SWIFT/FRR.</span><span class="sxs-lookup"><span data-stu-id="274ce-107">In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="274ce-108">Le rôle sera ajouté à la position dans le flux de travail qui est défini dans le nœud rôles.</span><span class="sxs-lookup"><span data-stu-id="274ce-108">The role will be added in the position in the workflow that is defined in the Roles node.</span></span> <span data-ttu-id="274ce-109">Pour modifier cet emplacement, vous devez effectuer l’étape 8 pour modifier l’ordre des rôles dans le nœud rôles.</span><span class="sxs-lookup"><span data-stu-id="274ce-109">To change that position, you need to perform step 8 to change the order of the roles in the Roles node.</span></span>  
  
3.  <span data-ttu-id="274ce-110">Dans le volet droit de l’Éditeur du Registre, double-cliquez sur **DelayTimeout**.</span><span class="sxs-lookup"><span data-stu-id="274ce-110">In the right pane of the Registry Editor, double-click **DelayTimeout**.</span></span>  
  
4.  <span data-ttu-id="274ce-111">Dans le **modifier la valeur DWORD** boîte de dialogue le **données de la valeur** , tapez la durée du délai d’expiration au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="274ce-111">In the **Edit DWORD Value** dialog box, in the **Value data** box, type the time-out duration in hexadecimal format.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="274ce-112">La valeur par défaut pour le **FRR DelayTimeout** propriété est de 600 secondes (258 hexadécimal).</span><span class="sxs-lookup"><span data-stu-id="274ce-112">The default value for the **FRR DelayTimeout** property is 600 seconds (258 Hexadecimal).</span></span>  
  
5.  <span data-ttu-id="274ce-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="274ce-113">Click **OK**.</span></span>