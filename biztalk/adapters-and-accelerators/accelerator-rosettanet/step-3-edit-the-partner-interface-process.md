---
title: "Étape 3 : Modifier le Partner Interface Process | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, PIPs
- PIPs, modifying
- loopback tutorial, modifying PIPs
ms.assetid: 4d03c598-8ed4-4135-9748-ede101997fd0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9640f542a55d028f3df8715c49df0e9e9ad370
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-edit-the-partner-interface-process"></a><span data-ttu-id="48091-102">Étape 3 : Modifier le Partner Interface Process</span><span class="sxs-lookup"><span data-stu-id="48091-102">Step 3: Edit the Partner Interface Process</span></span>
<span data-ttu-id="48091-103">Dans cette étape, vous modifiez les paramètres de configuration de processus PIP (Partner Interface) pour désactiver le transport sécurisé si vous n’avez pas d’un certificat SSL Secure Sockets Layer () configuré dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="48091-103">In this step, you edit the Partner Interface Process (PIP) configuration settings to disable secure transport if you do not have a Secure Sockets Layer (SSL) certificate configured in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS).</span></span> <span data-ttu-id="48091-104">Étant donné que le scénario de bouclage ne prend pas en charge la signature des messages entrants et sortants, vous devez modifier les paramètres par défaut pour continuer le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="48091-104">Because the loopback scenario does not support signing for both incoming and outgoing messages, you must change the default settings to continue with the tutorial.</span></span> <span data-ttu-id="48091-105">Vous modifiez le PIP STD_0C1_R01.02.</span><span class="sxs-lookup"><span data-stu-id="48091-105">You modify the STD_0C1_R01.02 PIP.</span></span>  
  
### <a name="to-edit-the-std0c1r0102-pip"></a><span data-ttu-id="48091-106">Pour modifier le PIP STD_0C1_R01.02</span><span class="sxs-lookup"><span data-stu-id="48091-106">To edit the STD_0C1_R01.02 PIP</span></span>  
  
1.  <span data-ttu-id="48091-107">Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez **BizTalk \<version > Accelerator for RosettaNet**, cliquez sur **paramètres de Configuration de processus**, avec le bouton droit **STD_0C1_R01.02**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="48091-107">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version> Accelerator for RosettaNet**, click **Process Configuration Settings**, right-click **STD_0C1_R01.02**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="48091-108">Dans la boîte de dialogue STD_0C1_R01.02Properties sur le **activité** onglet, définissez la **Transport est sécurisé requis** option `False`.</span><span class="sxs-lookup"><span data-stu-id="48091-108">In the STD_0C1_R01.02Properties dialog box, on the **Activity** tab, set the **Is Secure Transport Required** option to `False`.</span></span> <span data-ttu-id="48091-109">Effectuez cette étape uniquement si vous n’avez pas d’un certificat SSL sur votre serveur Web IIS.</span><span class="sxs-lookup"><span data-stu-id="48091-109">Perform this step only if you do not have a SSL certificate on your IIS Web server.</span></span>  
  
3.  <span data-ttu-id="48091-110">Définir le **non-répudiation requis** à `False`, définissez **autorisation obligatoire** à `False`, définissez **non-répudiation de l’origine et du contenu** à `False`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48091-110">Set the **Non-Repudiation Required** to `False`, set **Is Authorization Required** to `False`, set **Non-Repudiation of Origin and Content** to `False`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="48091-111">Cela désactive la non répudiation et l’utilisation de certificats pour la signature des messages.</span><span class="sxs-lookup"><span data-stu-id="48091-111">This disables non-repudiation and the use of certificates for signing messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48091-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48091-112">See Also</span></span>  
 <span data-ttu-id="48091-113">[Étape 4 : Créer un accord commercial](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="48091-113">[Step 4: Create a Trade Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span></span>  
 [<span data-ttu-id="48091-114">Propriétés d’autorisation et de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="48091-114">Authorization and Non-Repudiation Properties</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)