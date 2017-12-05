---
title: Exemple de PrivateInitiator | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f176566-2a71-487d-84c1-5e7767701e8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853b77e24359d6a833d526fc07166384ea946887
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="privateinitiator-sample"></a><span data-ttu-id="6bb62-102">Exemple de PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="6bb62-102">PrivateInitiator Sample</span></span>
<span data-ttu-id="6bb62-103">L’exemple PrivateInitiator.odx contient le code pour le processus privé initiateur installé par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6bb62-103">The PrivateInitiator.odx sample contains the code for the initiator private process installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server.</span></span> <span data-ttu-id="6bb62-104">Il s’agit d’un processus de privée générique qui envoie et reçoit des messages de contenu de service RNIF à partir de la valeur par défaut SQL basé sur un adaptateur d’envoi et ports de réception.</span><span class="sxs-lookup"><span data-stu-id="6bb62-104">This is a generic private process that sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.</span></span>  
  
 <span data-ttu-id="6bb62-105">Par défaut, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe l’exemple dans \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateInitiator.</span><span class="sxs-lookup"><span data-stu-id="6bb62-105">By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateInitiator.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="6bb62-106">Exemple de contenu</span><span class="sxs-lookup"><span data-stu-id="6bb62-106">Sample Contents</span></span>  
 <span data-ttu-id="6bb62-107">Le processus privé initiateur est le processus d’entreprise interne à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="6bb62-107">The initiator private process is the business process that is internal to the initiator.</span></span> <span data-ttu-id="6bb62-108">Le processus privé fournit l’intégration de back-end entre le processus public initiateur et le programme line-of-business back-end.</span><span class="sxs-lookup"><span data-stu-id="6bb62-108">The private process provides back-end integration between the initiator public process and the back-end line-of-business program.</span></span> <span data-ttu-id="6bb62-109">Le processus privé initiateur communique avec le processus public pour initier des messages.</span><span class="sxs-lookup"><span data-stu-id="6bb62-109">The initiator private process communicates with the public process to initiate messages.</span></span>  
  
 <span data-ttu-id="6bb62-110">Le processus privé initiateur est unique pour chaque implémentation.</span><span class="sxs-lookup"><span data-stu-id="6bb62-110">The initiator private process is unique for each implementation.</span></span> <span data-ttu-id="6bb62-111">Vous pouvez personnaliser l’exemple PrivateInitiator.odx à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="6bb62-111">You can customize the PrivateInitiator.odx sample for your purposes.</span></span> <span data-ttu-id="6bb62-112">Vous devez être prudent que vous n’affectez pas porter le fonctionnement du processus publics initiateur.</span><span class="sxs-lookup"><span data-stu-id="6bb62-112">You must be careful that you do not adversely affect the functioning of the initiator public process.</span></span>  
  
 <span data-ttu-id="6bb62-113">Pour plus d’informations, y compris une description du flux de messages, consultez [les processus privés de l’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md).</span><span class="sxs-lookup"><span data-stu-id="6bb62-113">For more information, including a description of the message flow, see [Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb62-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bb62-114">See Also</span></span>  
 <span data-ttu-id="6bb62-115">[Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="6bb62-115">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="6bb62-116">Processus privés</span><span class="sxs-lookup"><span data-stu-id="6bb62-116">Private Processes</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)