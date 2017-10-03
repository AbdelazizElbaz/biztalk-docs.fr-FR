---
title: "Conditions préalables pour le didacticiel Double Action de RosettaNet dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel Double Action pour l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87e2750a16d2c65b5838b6d61f27cbd2b2ff9885
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-double-action-tutorial"></a><span data-ttu-id="3eddf-103">Préparer pour le didacticiel Double Action</span><span class="sxs-lookup"><span data-stu-id="3eddf-103">Prepare for the Double Action tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3eddf-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3eddf-104">Prerequisites</span></span>
<span data-ttu-id="3eddf-105">Avant de commencer le didacticiel :</span><span class="sxs-lookup"><span data-stu-id="3eddf-105">Before starting the tutorial:</span></span>
  
-   <span data-ttu-id="3eddf-106">Effectuez une installation complète de BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3eddf-106">Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers.</span></span> <span data-ttu-id="3eddf-107">Pour plus d’informations, consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).</span><span class="sxs-lookup"><span data-stu-id="3eddf-107">For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3eddf-108">Veillez à configurer entièrement l’accélérateur RosettaNet, y compris le démarrage des orchestrations BTARN.</span><span class="sxs-lookup"><span data-stu-id="3eddf-108">Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations.</span></span> <span data-ttu-id="3eddf-109">Consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).</span><span class="sxs-lookup"><span data-stu-id="3eddf-109">See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>
  
-   <span data-ttu-id="3eddf-110">Ce didacticiel simule un scénario réel à l’aide de deux ordinateurs au lieu d’un seul ordinateur avec un accord de bouclage.</span><span class="sxs-lookup"><span data-stu-id="3eddf-110">This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loopback agreement.</span></span> <span data-ttu-id="3eddf-111">Chaque fois que ce didacticiel utilise des noms d’ordinateur, il utilise un espace réservé.</span><span class="sxs-lookup"><span data-stu-id="3eddf-111">Whenever this tutorial uses computer names, it uses a placeholder.</span></span> <span data-ttu-id="3eddf-112">Remplacez cet espace réservé par le nom réel de l’ordinateur choisi.</span><span class="sxs-lookup"><span data-stu-id="3eddf-112">Replace that placeholder with the actual computer name you chose.</span></span> <span data-ttu-id="3eddf-113">Par exemple, si l’ordinateur qui exécute votre solution de Contoso est nommé **Contoso**, remplacez toutes les occurrences dans le didacticiel de \\ \\< contoso**_**  *ordinateur*> portant ce nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3eddf-113">For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*> with that computer name.</span></span>  
  
-   <span data-ttu-id="3eddf-114">Ce didacticiel favorise une communication sécurisée au moyen de certificats entre Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="3eddf-114">This tutorial promotes secure communication through certificates between Contoso and Fabrikam.</span></span> <span data-ttu-id="3eddf-115">Vous devez générer des certificats que vous avez besoin et les installer sur leurs ordinateurs respectifs.</span><span class="sxs-lookup"><span data-stu-id="3eddf-115">You must generate any certificates you require, and install them on their respective computers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3eddf-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3eddf-116">Next steps</span></span> 
  
-   [<span data-ttu-id="3eddf-117">Étape 1 : Création d’une autorité de Certification</span><span class="sxs-lookup"><span data-stu-id="3eddf-117">Step 1: Creating a Certification Authority</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [<span data-ttu-id="3eddf-118">Étape 2 : Création publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="3eddf-118">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="3eddf-119">Étape 3 : Importation publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="3eddf-119">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="3eddf-120">Étape 4 : Sécurisé Sockets Layer dans IIS</span><span class="sxs-lookup"><span data-stu-id="3eddf-120">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)