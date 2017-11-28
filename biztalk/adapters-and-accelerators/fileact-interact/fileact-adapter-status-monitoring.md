---
title: "État de l’adaptateur FileAct surveillance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15833004-4276-4975-a0e7-8fff3c82576b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5b717a02631d47b864cc9180cba2fba673c5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-status-monitoring"></a><span data-ttu-id="ddf63-102">État de l’adaptateur FileAct analyse</span><span class="sxs-lookup"><span data-stu-id="ddf63-102">FileAct Adapter Status Monitoring</span></span>
<span data-ttu-id="ddf63-103">Les états possibles d’un transfert de fichiers et les transitions entre ces États sont illustrées dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="ddf63-103">The possible states of a file transfer and the transitions between those states are illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="ddf63-104">![États de transfert de fichier de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")</span><span class="sxs-lookup"><span data-stu-id="ddf63-104">![FileAct adapter file transfer states](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")</span></span>  
  
 <span data-ttu-id="ddf63-105">Les États de transfert de fichier sont :</span><span class="sxs-lookup"><span data-stu-id="ddf63-105">The file transfer states are:</span></span>  
  
-   <span data-ttu-id="ddf63-106">**Lancé** : le client a envoyé le message de négociation pour le serveur, mais n’a pas encore reçu la réponse.</span><span class="sxs-lookup"><span data-stu-id="ddf63-106">**Initiated** – The client has sent the negotiation message to the server, but has not yet received the response.</span></span> <span data-ttu-id="ddf63-107">Le serveur a reçu la demande de négociation mais n’a pas encore envoyé la réponse.</span><span class="sxs-lookup"><span data-stu-id="ddf63-107">The server has received the negotiation request, but has not yet sent the response.</span></span>  
  
-   <span data-ttu-id="ddf63-108">**Accepté** : le serveur a accepté la demande et a envoyé la TransferAnswer dans le message de réponse et le transfert est toujours en cours.</span><span class="sxs-lookup"><span data-stu-id="ddf63-108">**Accepted** – The server has accepted the request and has sent the TransferAnswer in the response message, and the transfer is still in progress.</span></span>  
  
-   <span data-ttu-id="ddf63-109">**Rejeté** : le serveur a rejeté la demande et a la TransferAnswer dans le message de réponse et le transfert s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="ddf63-109">**Rejected** – The server has rejected the request and has the TransferAnswer in the response message, and has terminated the transfer.</span></span>  
  
-   <span data-ttu-id="ddf63-110">**En cours** – le transfert est en cours d’exécution et qu’il est en cours (renouvelé régulièrement comme indiqué ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="ddf63-110">**Ongoing** – The transfer is in progress and is proceeding (renewed periodically as above).</span></span>  
  
-   <span data-ttu-id="ddf63-111">**Terminé** – le transfert de fichiers est terminée en ce côté du transfert est concerné, y compris la comparaison de la valeur digest.</span><span class="sxs-lookup"><span data-stu-id="ddf63-111">**Completed** – The file transfer has completed successfully as far as that side of the transfer is concerned, including the comparison of the digest value.</span></span>  
  
-   <span data-ttu-id="ddf63-112">**Échec de** – le transfert de fichiers a échoué en raison d’un accès aux données, le traitement, l’exception de communication ou de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="ddf63-112">**Failed** – The file transfer has failed because of a data access, processing, communications or timeout exception.</span></span> <span data-ttu-id="ddf63-113">(Remarque : délai d’attente est appliquée par SWIFTNet lien, et la valeur est déterminée par SWIFT).</span><span class="sxs-lookup"><span data-stu-id="ddf63-113">(Note: Timeout is enforced by SWIFTNet Link, and the value is determined by SWIFT).</span></span>  
  
-   <span data-ttu-id="ddf63-114">**Abandonnée** – le transfert de fichiers a été annulé (soit côté mon problème l’abandon).</span><span class="sxs-lookup"><span data-stu-id="ddf63-114">**Aborted** – The file transfer has been aborted (either side my issue the abort).</span></span>  
  
-   <span data-ttu-id="ddf63-115">**Inconnu et en double** – cet état se produit uniquement en raison de la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="ddf63-115">**Unknown and Duplicated** – This state occurs only because of timing.</span></span> <span data-ttu-id="ddf63-116">Dans le cas d’un expéditeur, le fichier doit être envoyé à nouveau la mention éventuellement dupliqué (PDIndicator).</span><span class="sxs-lookup"><span data-stu-id="ddf63-116">In the case of a sender, the file should be re-sent marked as possibly duplicated (PDIndicator).</span></span> <span data-ttu-id="ddf63-117">Dans le cas d’un récepteur, lorsque le PDIndicator implique que le fichier peut ont déjà reçu, l’adaptateur FileAct recherche la duplication et si trouvée, renvoie une TransferAnswer de dupliqués, ce qui mettra fin à la tentative en cours.</span><span class="sxs-lookup"><span data-stu-id="ddf63-117">In the case of a receiver, when the PDIndicator implies that the file might have already been sent, the FileAct Adapter will check for the duplication, and if found, will return a TransferAnswer of Duplicated, which will terminate the current attempt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf63-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddf63-118">See Also</span></span>  
 <span data-ttu-id="ddf63-119">[Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-119">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="ddf63-120">[Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-120">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="ddf63-121">[Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-121">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="ddf63-122">[Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-122">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="ddf63-123">[Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-123">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="ddf63-124">[Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-124">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="ddf63-125">[Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="ddf63-125">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 [<span data-ttu-id="ddf63-126">Notification de remise de l’adaptateur FileAct</span><span class="sxs-lookup"><span data-stu-id="ddf63-126">FileAct Adapter Delivery Notification</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)