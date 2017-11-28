---
title: Exemple de PrivateResponder | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3137fadd-9582-4cc6-acfb-c44aca636950
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3de3428aa9971ba62b682494cd94c6bb74bcab53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="privateresponder-sample"></a><span data-ttu-id="f166e-102">Exemple de PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="f166e-102">PrivateResponder Sample</span></span>
<span data-ttu-id="f166e-103">L’exemple PrivateResponder.odx contient le code pour le processus privé répondeur installé par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f166e-103">The PrivateResponder.odx sample contains the code for the responder private process installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="f166e-104">Ce processus privé générique envoie et reçoit des messages de contenu de service RNIF à partir de la valeur par défaut SQL basé sur un adaptateur d’envoi et ports de réception.</span><span class="sxs-lookup"><span data-stu-id="f166e-104">This generic private process sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.</span></span>  
  
 <span data-ttu-id="f166e-105">Par défaut, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe l’exemple dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\ PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="f166e-105">By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateResponder.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="f166e-106">Exemple de contenu</span><span class="sxs-lookup"><span data-stu-id="f166e-106">Sample Contents</span></span>  
 <span data-ttu-id="f166e-107">Le processus privé du répondeur est le processus d’entreprise qui est interne au répondeur.</span><span class="sxs-lookup"><span data-stu-id="f166e-107">The responder private process is the business process that is internal to the responder.</span></span> <span data-ttu-id="f166e-108">Le processus privé fournit l’intégration de back-end entre le processus public répondeur et que le programme de line-of-business back-end.</span><span class="sxs-lookup"><span data-stu-id="f166e-108">The private process provides back-end integration between the responder public process and the back-end line-of-business program.</span></span> <span data-ttu-id="f166e-109">Le processus privé répondeur communique avec le processus public pour répondre aux messages.</span><span class="sxs-lookup"><span data-stu-id="f166e-109">The responder private process communicates with the public process to respond to messages.</span></span>  
  
 <span data-ttu-id="f166e-110">Le processus privé du répondeur est unique pour chaque implémentation.</span><span class="sxs-lookup"><span data-stu-id="f166e-110">The responder private process is unique for each implementation.</span></span> <span data-ttu-id="f166e-111">Vous pouvez personnaliser l’exemple PrivateResponder.odx à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="f166e-111">You can customize the PrivateResponder.odx sample for your purposes.</span></span> <span data-ttu-id="f166e-112">Vous devez être prudent que vous n’affectez pas porter le fonctionnement du processus publics répondeur.</span><span class="sxs-lookup"><span data-stu-id="f166e-112">You must be careful that you do not adversely affect the functioning of the responder public process.</span></span>  
  
 <span data-ttu-id="f166e-113">Pour plus d’informations, y compris une description du flux de messages, consultez [répondeur privé processus](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).</span><span class="sxs-lookup"><span data-stu-id="f166e-113">For more information, including a description of the message flow, see [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f166e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f166e-114">See Also</span></span>  
 <span data-ttu-id="f166e-115">[Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="f166e-115">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="f166e-116">Processus privés</span><span class="sxs-lookup"><span data-stu-id="f166e-116">Private Processes</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)