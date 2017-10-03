---
title: "Configuration des propriétés de l’accusé de réception de secours (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce33f5dd-fbd5-448c-8ea3-05dd1467131a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 216961dea0bdf4a67c550fba8a599eff2d0c89ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-acknowledgement-properties-x12"></a><span data-ttu-id="9d964-102">Configuration des propriétés de l'accusé de réception de secours (X12)</span><span class="sxs-lookup"><span data-stu-id="9d964-102">Configuring Fallback Acknowledgement Properties (X12)</span></span>
<span data-ttu-id="9d964-103">Dans l'accord de secours, vous pouvez spécifier comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère des accusés de réception en réponse aux échanges X12 reçus du tiers, ainsi que le type d'accusé de réception à renvoyer à un tiers.</span><span class="sxs-lookup"><span data-stu-id="9d964-103">In the fallback agreement, you can specify how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates acknowledgments in response to X12-encoded interchanges received from the party and what type of acknowledgment to return to a party.</span></span> <span data-ttu-id="9d964-104">Cette section fournit des instructions sur la façon de faire de même.</span><span class="sxs-lookup"><span data-stu-id="9d964-104">This section provides instructions on how to do the same.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d964-105">Les propriétés de l'accusé de réception décrites dans cette rubrique s'appliquent également aux accusés de réception HIPAA.</span><span class="sxs-lookup"><span data-stu-id="9d964-105">The acknowledgement properties described here apply also for HIPAA acknowledgements.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9d964-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9d964-106">Prerequisites</span></span>  
 <span data-ttu-id="9d964-107">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d964-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-x12-ack-properties"></a><span data-ttu-id="9d964-108">Pour configurer les propriétés de l'accusé de réception X12</span><span class="sxs-lookup"><span data-stu-id="9d964-108">To configure X12 ACK properties</span></span>  
  
1.  <span data-ttu-id="9d964-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.</span><span class="sxs-lookup"><span data-stu-id="9d964-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="9d964-110">Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **lesaccusésderéception**.</span><span class="sxs-lookup"><span data-stu-id="9d964-110">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="9d964-111">Sélectionnez **TA1 attendu** pour renvoyer un accusé de réception technique (TA1) à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="9d964-111">Select **TA1 Expected** to return a technical (TA1) acknowledgment to the interchange sender.</span></span>  
  
4.  <span data-ttu-id="9d964-112">Sélectionnez **997 attendu** pour renvoyer un accusé de réception fonctionnel (997) à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="9d964-112">Select **997 Expected** to return a functional (997) acknowledgment to the interchange sender.</span></span>  
  
5.  <span data-ttu-id="9d964-113">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="9d964-113">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d964-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d964-114">See Also</span></span>  
 [<span data-ttu-id="9d964-115">Configuration X12 propriétés d’accord de secours pour le traitement de l’échange</span><span class="sxs-lookup"><span data-stu-id="9d964-115">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)