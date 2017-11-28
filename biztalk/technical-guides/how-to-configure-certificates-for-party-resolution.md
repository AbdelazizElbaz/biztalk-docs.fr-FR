---
title: "Comment configurer des certificats pour la résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 060101c1-14f3-4600-a18e-48a160d59bca
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 153c8ccce1fafbe32c51b1c048fad4081f5b0b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-for-party-resolution"></a><span data-ttu-id="e2731-102">Comment configurer des certificats pour la résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="e2731-102">How to Configure Certificates for Party Resolution</span></span>
<span data-ttu-id="e2731-103">Lorsque vous utilisez l’Explorateur BizTalk pour configurer un tiers, vous pouvez configurer le tiers afin que le tiers est résolu à l’aide de sa signature numérique.</span><span class="sxs-lookup"><span data-stu-id="e2731-103">When you use BizTalk Explorer to configure a party, you can configure the party so that the party is resolved by using its digital signature.</span></span> <span data-ttu-id="e2731-104">Si vous configurez la partie de cette façon, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message, il utilisera le certificat de clé publique pour déterminer qui a envoyé le message et pour résoudre l’expéditeur à un tiers connu dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="e2731-104">If you configure the party this way, when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it will use the public key certificate to determine who sent the message, and to resolve the sender to a known party in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e2731-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e2731-105">Prerequisites</span></span>  
 <span data-ttu-id="e2731-106">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="e2731-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-party-resolution-to-use-a-certificate"></a><span data-ttu-id="e2731-107">Pour configurer la résolution de tiers d’utiliser un certificat</span><span class="sxs-lookup"><span data-stu-id="e2731-107">To configure party resolution to use a certificate</span></span>  
  
1.  <span data-ttu-id="e2731-108">Ouvrez le **propriétés de tiers** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e2731-108">Open the **Party Properties** dialog box.</span></span>  
  
2.  <span data-ttu-id="e2731-109">Cliquez sur le **certificat** onglet, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="e2731-109">Click the **Certificate** tab, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="e2731-110">Sélectionnez un certificat.</span><span class="sxs-lookup"><span data-stu-id="e2731-110">Select a certificate.</span></span>  
  
4.  <span data-ttu-id="e2731-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e2731-111">Click **OK**.</span></span>