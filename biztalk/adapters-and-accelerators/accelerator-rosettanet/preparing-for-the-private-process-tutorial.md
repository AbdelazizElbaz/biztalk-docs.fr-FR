---
title: "Configuration requise pour le didacticiel sur les processus de RosettaNet privé dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel les processus privés pour l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
caps.latest.revision: "7"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
ms.author: mandia
ms.openlocfilehash: 580edcc7a8d779067895fb5aac99d81a1ad76872
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="prepare-for-the-private-process-tutorial"></a><span data-ttu-id="1d70f-103">Préparer pour le didacticiel sur les processus privés</span><span class="sxs-lookup"><span data-stu-id="1d70f-103">Prepare for the Private Process tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d70f-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="1d70f-104">Prerequisites</span></span>
<span data-ttu-id="1d70f-105">Avant de commencer le didacticiel :</span><span class="sxs-lookup"><span data-stu-id="1d70f-105">Before starting the tutorial:</span></span>
  
-   <span data-ttu-id="1d70f-106">Effectuez une installation complète de BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1d70f-106">Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers.</span></span> <span data-ttu-id="1d70f-107">Pour plus d’informations, consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).</span><span class="sxs-lookup"><span data-stu-id="1d70f-107">For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1d70f-108">Veillez à configurer entièrement l’accélérateur RosettaNet, y compris le démarrage des orchestrations BTARN.</span><span class="sxs-lookup"><span data-stu-id="1d70f-108">Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations.</span></span> <span data-ttu-id="1d70f-109">Consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).</span><span class="sxs-lookup"><span data-stu-id="1d70f-109">See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span> <span data-ttu-id="1d70f-110">Vous devrez peut-être également ajouter le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] des répertoires virtuels (y compris les btarnhttpreceive) à la liste d’exclusion du chemin d’accès géré Microsoft Windows® SharePoint™ Services.</span><span class="sxs-lookup"><span data-stu-id="1d70f-110">You may also have to add the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] virtual directories (including btarnhttpreceive) to the Microsoft Windows® SharePoint™ Services managed path exclusion list.</span></span> 
  
-   <span data-ttu-id="1d70f-111">Ce didacticiel simule un scénario réel à l’aide de deux ordinateurs au lieu d’un seul ordinateur avec un accord de bouclage.</span><span class="sxs-lookup"><span data-stu-id="1d70f-111">This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loop-back agreement.</span></span> <span data-ttu-id="1d70f-112">Chaque fois que ce didacticiel utilise des noms d’ordinateur, il utilise un espace réservé comme nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d70f-112">Whenever this tutorial uses computer names, it uses a placeholder as the computer name.</span></span> <span data-ttu-id="1d70f-113">Remplacez cet espace réservé par le nom réel de l’ordinateur choisi.</span><span class="sxs-lookup"><span data-stu-id="1d70f-113">Replace that placeholder with the actual computer name you chose.</span></span> <span data-ttu-id="1d70f-114">Par exemple, si l’ordinateur qui exécute votre solution de Contoso est nommé **Contoso**, remplacez toutes les occurrences dans le didacticiel de \\ \\< contoso**_**  *ordinateur* \> portant ce nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d70f-114">For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*\> with that computer name.</span></span>  
  
 <span data-ttu-id="1d70f-115">Ce didacticiel favorise une communication sécurisée au moyen de certificats entre Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="1d70f-115">This tutorial promotes secure communication through certificates between Contoso and Fabrikam.</span></span> <span data-ttu-id="1d70f-116">Vous devez générer des certificats que vous avez besoin et les installer sur les ordinateurs respectifs.</span><span class="sxs-lookup"><span data-stu-id="1d70f-116">You must generate any certificates you require, and install them on the respective computers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1d70f-117">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1d70f-117">Next steps</span></span>
  
-   [<span data-ttu-id="1d70f-118">Restauration de la base de données Contoso</span><span class="sxs-lookup"><span data-stu-id="1d70f-118">Restoring the Contoso Database</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [<span data-ttu-id="1d70f-119">Génération et activation de certificats</span><span class="sxs-lookup"><span data-stu-id="1d70f-119">Generating and Enabling Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)