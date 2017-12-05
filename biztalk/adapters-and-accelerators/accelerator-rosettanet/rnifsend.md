---
title: RNIFSend | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 780f7446-56c5-40bf-95e2-25d0cff12f12
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73cf8a832e495944ce7c891421645ae2566e3575
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnifsend"></a><span data-ttu-id="3282b-102">RNIFSend</span><span class="sxs-lookup"><span data-stu-id="3282b-102">RNIFSend</span></span>
<span data-ttu-id="3282b-103">Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fichier fichier RNIFSend.aspx prépare un message pour le traitement RNIF et envoie le message à la page RNIFReceive.aspx au répondeur.</span><span class="sxs-lookup"><span data-stu-id="3282b-103">This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx file that prepares a message for RNIF processing, and sends the message to the RNIFReceive.aspx page at the responder.</span></span> <span data-ttu-id="3282b-104">Vous pouvez personnaliser la page ASPX pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3282b-104">You can customize the ASPX page to do the following:</span></span>  
  
-   <span data-ttu-id="3282b-105">Ajouter ou supprimer des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="3282b-105">Add or remove performance counters</span></span>  
  
-   <span data-ttu-id="3282b-106">Ajouter des fonctionnalités à la page, comme l'écriture de données dans une base de données ou la personnalisation de la fonctionnalité de suivi</span><span class="sxs-lookup"><span data-stu-id="3282b-106">Add functionality to the page, such as writing data to a database or customizing tracking functionality</span></span>  
  
-   <span data-ttu-id="3282b-107">Ajouter la validation à la page</span><span class="sxs-lookup"><span data-stu-id="3282b-107">Add validation to the page</span></span>  
  
 <span data-ttu-id="3282b-108">Cet exemple se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFSender.</span><span class="sxs-lookup"><span data-stu-id="3282b-108">This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFSender.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3282b-109">Montre</span><span class="sxs-lookup"><span data-stu-id="3282b-109">Demonstrates</span></span>  
 <span data-ttu-id="3282b-110">Cet exemple montre comment préparer les messages sortants pour RNIF du traitement, y compris les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3282b-110">This sample demonstrates how to prepare outgoing messages for RNIF processing, including the following:</span></span>  
  
-   <span data-ttu-id="3282b-111">Validation des données pour l’en-tête MIME</span><span class="sxs-lookup"><span data-stu-id="3282b-111">Validating the data for the MIME header</span></span>  
  
-   <span data-ttu-id="3282b-112">Ajout d’un en-tête MIME et limites MIME au message</span><span class="sxs-lookup"><span data-stu-id="3282b-112">Adding a MIME header and MIME boundaries to the message</span></span>  
  
-   <span data-ttu-id="3282b-113">Envoyer le message au fichier de RNIFReceive.aspx du partenaire</span><span class="sxs-lookup"><span data-stu-id="3282b-113">Sending the message to the partner's RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="3282b-114">Traitement d’un message de signal retourné</span><span class="sxs-lookup"><span data-stu-id="3282b-114">Processing a returned signal message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3282b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3282b-115">See Also</span></span>  
 <span data-ttu-id="3282b-116">[Envoyer et recevoir des Pages ASPX](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span><span class="sxs-lookup"><span data-stu-id="3282b-116">[Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span></span>  
 [<span data-ttu-id="3282b-117">Exemples d’applications web</span><span class="sxs-lookup"><span data-stu-id="3282b-117">Web Application Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)