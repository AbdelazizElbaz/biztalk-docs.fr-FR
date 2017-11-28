---
title: "Génération et l’activation de certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, enabling
- private process tutorial, creating certificates
- private process tutorial, enabling certificates
ms.assetid: a36d9725-d57c-499d-948d-558096709d67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93293939ae509dcb2af04e17fcdd35e9cf6d03cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-and-enabling-certificates"></a><span data-ttu-id="ba226-102">Génération et l’activation de certificats</span><span class="sxs-lookup"><span data-stu-id="ba226-102">Generating and Enabling Certificates</span></span>
<span data-ttu-id="ba226-103">Ce didacticiel utilise des certificats pour signer et chiffrer les messages envoyés par les organisations de Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ba226-103">This tutorial uses certificates to sign and encrypt messages sent by the Contoso and Fabrikam organizations.</span></span> <span data-ttu-id="ba226-104">Si vous avez déjà effectué le didacticiel Double Action, vous pouvez ignorer cette étape et passez à [création de la Contoso Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md).</span><span class="sxs-lookup"><span data-stu-id="ba226-104">If you have already completed the Double Action Tutorial, you may skip this step and move on to [Creating the Contoso Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md).</span></span> <span data-ttu-id="ba226-105">Pour générer et utiliser des certificats pour ce didacticiel, les procédures décrites dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba226-105">To generate and use certificates for this tutorial, follow the procedures in the following topics:</span></span>  
  
-   [<span data-ttu-id="ba226-106">Étape 1 : Création d’une autorité de Certification</span><span class="sxs-lookup"><span data-stu-id="ba226-106">Step 1: Creating a Certification Authority</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [<span data-ttu-id="ba226-107">Étape 2 : Création publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="ba226-107">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="ba226-108">Étape 3 : Importation publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="ba226-108">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="ba226-109">Étape 4 : Sécurisé Sockets Layer dans IIS</span><span class="sxs-lookup"><span data-stu-id="ba226-109">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba226-110">Ces étapes sont décrites dans le didacticiel Double Action.</span><span class="sxs-lookup"><span data-stu-id="ba226-110">These steps are in the Double Action Tutorial.</span></span> <span data-ttu-id="ba226-111">À l’issue de chaque étape, revenez sur cette rubrique pour continuer le didacticiel sur les processus privés.</span><span class="sxs-lookup"><span data-stu-id="ba226-111">After completing each step, return to this topic to continue the Private Process Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba226-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba226-112">See Also</span></span>  
 [<span data-ttu-id="ba226-113">Création de la Solution de Contoso</span><span class="sxs-lookup"><span data-stu-id="ba226-113">Creating the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md)