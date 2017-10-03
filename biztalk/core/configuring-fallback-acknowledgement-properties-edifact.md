---
title: "Configuration des propriétés de l’accusé de réception de secours (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6062b881-3214-4e68-acbc-1f8c255fd86b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9369eb7fff1a6217da774aaf62af6e036d0abd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-acknowledgement-properties-edifact"></a><span data-ttu-id="aab52-102">Configuration des propriétés de l'accusé de réception de secours (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="aab52-102">Configuring Fallback Acknowledgement Properties (EDIFACT)</span></span>
<span data-ttu-id="aab52-103">Dans l'accord de secours, vous pouvez définir le type d'accusé de réception à renvoyer à un tiers.</span><span class="sxs-lookup"><span data-stu-id="aab52-103">In the fallback agreement, you can specify what type of acknowledgment to return to a party.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aab52-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="aab52-104">Prerequisites</span></span>  
 <span data-ttu-id="aab52-105">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aab52-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a><span data-ttu-id="aab52-106">Pour configurer les propriétés d'accusé de réception EDIFACT (CONTRL)</span><span class="sxs-lookup"><span data-stu-id="aab52-106">To configure EDIFACT ACK (CONTRL) properties</span></span>  
  
1.  <span data-ttu-id="aab52-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="aab52-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="aab52-108">Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur  **Accusés de réception**.</span><span class="sxs-lookup"><span data-stu-id="aab52-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="aab52-109">Sélectionnez **réception du message (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) technique à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="aab52-109">Select **Receipt of message (CONTRL) expected** to return a technical (CONTRL) acknowledgment to the interchange sender.</span></span>  
  
4.  <span data-ttu-id="aab52-110">Sélectionnez **accusé de réception (CONTRL) attendu** pour renvoyer un accusé de réception (CONTRL) fonctionnel à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="aab52-110">Select **Acknowledgement (CONTRL) expected** to return a functional (CONTRL) acknowledgment to the interchange sender.</span></span>  
  
5.  <span data-ttu-id="aab52-111">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="aab52-111">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab52-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aab52-112">See Also</span></span>  
 [<span data-ttu-id="aab52-113">Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges</span><span class="sxs-lookup"><span data-stu-id="aab52-113">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)