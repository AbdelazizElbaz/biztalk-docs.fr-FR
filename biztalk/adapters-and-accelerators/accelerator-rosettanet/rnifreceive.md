---
title: RNIFReceive | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1253b0-ceca-4e7a-91ed-3837bd904472
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57af8140157b901d7e6265fc26249c7fbfef0c46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnifreceive"></a><span data-ttu-id="b3bd4-102">RNIFReceive</span><span class="sxs-lookup"><span data-stu-id="b3bd4-102">RNIFReceive</span></span>
<span data-ttu-id="b3bd4-103">Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fichier RNIFReceive.aspx qui reçoit un message RNIF et le prépare pour le traitement par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus public.</span><span class="sxs-lookup"><span data-stu-id="b3bd4-103">This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx file that receives an RNIF message, and prepares it for processing by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public process.</span></span> <span data-ttu-id="b3bd4-104">Vous pouvez personnaliser la page ASPX pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3bd4-104">You can customize the ASPX page to do the following:</span></span>  
  
-   <span data-ttu-id="b3bd4-105">Ajouter ou supprimer des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="b3bd4-105">Add or remove performance counters</span></span>  
  
-   <span data-ttu-id="b3bd4-106">Ajouter des fonctionnalités à la page, comme l'écriture de données dans une base de données ou la personnalisation de la fonctionnalité de suivi</span><span class="sxs-lookup"><span data-stu-id="b3bd4-106">Add functionality to the page, such as writing data to a database or customizing tracking functionality</span></span>  
  
-   <span data-ttu-id="b3bd4-107">Ajouter la validation à la page</span><span class="sxs-lookup"><span data-stu-id="b3bd4-107">Add validation to the page</span></span>  
  
 <span data-ttu-id="b3bd4-108">Cet exemple se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver.</span><span class="sxs-lookup"><span data-stu-id="b3bd4-108">This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b3bd4-109">Montre</span><span class="sxs-lookup"><span data-stu-id="b3bd4-109">Demonstrates</span></span>  
 <span data-ttu-id="b3bd4-110">Cet exemple montre comment préparer les messages entrants pour le processus public, notamment les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3bd4-110">This sample demonstrates how to prepare incoming messages for the public process, including the following:</span></span>  
  
-   <span data-ttu-id="b3bd4-111">Réception du message à partir du fichier RNIFSend.aspx du partenaire</span><span class="sxs-lookup"><span data-stu-id="b3bd4-111">Receiving the message from the partner's RNIFSend.aspx</span></span>  
  
-   <span data-ttu-id="b3bd4-112">Validation de l'en-tête MIME</span><span class="sxs-lookup"><span data-stu-id="b3bd4-112">Validating the MIME header</span></span>  
  
-   <span data-ttu-id="b3bd4-113">Suppression de l'en-tête MIME et des limites du message</span><span class="sxs-lookup"><span data-stu-id="b3bd4-113">Removing the MIME header and boundaries from the message</span></span>  
  
-   <span data-ttu-id="b3bd4-114">Routage du message vers le fichier RNIFReceive.aspx du partenaire</span><span class="sxs-lookup"><span data-stu-id="b3bd4-114">Routing the message to the partner's RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="b3bd4-115">Retour d'un message de signal</span><span class="sxs-lookup"><span data-stu-id="b3bd4-115">Returning a signal message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bd4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3bd4-116">See Also</span></span>  
 <span data-ttu-id="b3bd4-117">[Envoyer et recevoir des Pages ASPX](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span><span class="sxs-lookup"><span data-stu-id="b3bd4-117">[Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span></span>  
 [<span data-ttu-id="b3bd4-118">Exemples d’applications web</span><span class="sxs-lookup"><span data-stu-id="b3bd4-118">Web Application Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)