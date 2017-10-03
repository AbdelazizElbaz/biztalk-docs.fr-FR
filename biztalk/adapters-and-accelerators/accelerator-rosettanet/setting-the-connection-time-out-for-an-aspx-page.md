---
title: "Définir le délai de connexion pour une Page ASPX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, connection time-out
- connections, time-out
ms.assetid: 61d9c996-caf4-48bd-bda7-52f2797a941b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e083b9f2f0262095e58b4ed9842627888773dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-connection-time-out-for-an-aspx-page"></a><span data-ttu-id="4565e-102">Définir le délai de connexion pour une Page ASPX</span><span class="sxs-lookup"><span data-stu-id="4565e-102">Setting the Connection Time-Out for an ASPX Page</span></span>
<span data-ttu-id="4565e-103">Lorsque vous utilisez une page ASPX pour des messages synchrones, vous devez augmenter le délai d’expiration de connexion de la page ASPX afin qu’il peut attendre le message attendu.</span><span class="sxs-lookup"><span data-stu-id="4565e-103">When you use an ASPX page for synchronous messages, you must increase the connection time-out for the ASPX page so that it can wait for the expected message.</span></span>  
  
 <span data-ttu-id="4565e-104">Augmenter le délai de connexion pour la page ASPX peut avoir des conséquences inattendues.</span><span class="sxs-lookup"><span data-stu-id="4565e-104">Increasing the connection time-out for the ASPX page can have unintended consequences.</span></span> <span data-ttu-id="4565e-105">Tout d’abord, il augmente le risque d’une attaque par déni de service et de la menace d’épuiser la réserve de threads.</span><span class="sxs-lookup"><span data-stu-id="4565e-105">First, it increases the risk of a denial-of-service attack and the threat of exhausting the thread pool.</span></span> <span data-ttu-id="4565e-106">En second lieu, s’il y a trop de connexions synchrones sur la page ASPX, le système risque de se bloquer.</span><span class="sxs-lookup"><span data-stu-id="4565e-106">Second, if there are too many synchronous connections on the ASPX page, the system can lock up.</span></span> <span data-ttu-id="4565e-107">Pendant que vous devez augmenter le délai de connexion, donc veiller à ne pas augmenter de trop.</span><span class="sxs-lookup"><span data-stu-id="4565e-107">Therefore, while you must increase the connection time-out, be careful not to increase it too much.</span></span>  
  
 <span data-ttu-id="4565e-108">Définir le délai de connexion à la valeur minimale autorisée par l’organisation RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="4565e-108">Set the connection time-out to the minimum allowed by the RosettaNet organization.</span></span> <span data-ttu-id="4565e-109">Pour plus d’informations sur les paramètres de synchronisation pour un processus PIP (Partner Interface), reportez-vous au tableau 4-3 : contrôles Exchange de Message, dans la spécification PIP RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="4565e-109">For more information about the timing parameters for a Partner Interface Process (PIP), see Table 4-3: Message Exchange Controls, in the RosettaNet PIP Specification.</span></span>  
  
### <a name="to-set-the-connection-time-out-for-the-aspx-page"></a><span data-ttu-id="4565e-110">Pour définir le délai de connexion de la page ASPX</span><span class="sxs-lookup"><span data-stu-id="4565e-110">To set the connection time-out for the ASPX page</span></span>  
  
1.  <span data-ttu-id="4565e-111">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="4565e-111">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="4565e-112">Dans le Gestionnaire IIS, développez le nœud pour l’ordinateur local, puis **Sites Web**.</span><span class="sxs-lookup"><span data-stu-id="4565e-112">In IIS Manager, expand the node for the local computer, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="4565e-113">Cliquez avec le bouton droit sur **Site Web par défaut**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4565e-113">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="4565e-114">Dans la boîte de dialogue Propriétés du Site Web par défaut sur le **Site Web** sous l’onglet du **délai de connexion** zone, tapez une valeur appropriée, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4565e-114">In the Default Web Site Properties dialog box, on the **Web Site** tab, in the **Connection Timeout** box, type an appropriate value, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4565e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4565e-115">See Also</span></span>  
 [<span data-ttu-id="4565e-116">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="4565e-116">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)