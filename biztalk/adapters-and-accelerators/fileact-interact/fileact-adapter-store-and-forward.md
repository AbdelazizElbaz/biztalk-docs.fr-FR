---
title: "Magasin de l’adaptateur FileAct et son transfert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50110bf0-75c2-426c-9833-65c3117224b2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1201a5ab5cb45ceba2622aa1c269404acec910df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-store-and-forward"></a><span data-ttu-id="14022-102">Magasin de l’adaptateur FileAct et le transfert</span><span class="sxs-lookup"><span data-stu-id="14022-102">FileAct Adapter Store and Forward</span></span>
<span data-ttu-id="14022-103">Dans le magasin de mode de transfert (msng), les fichiers sont remises à la file d’attente au moment de l’envoi et sont récupérées à partir de la file d’attente par la destination.</span><span class="sxs-lookup"><span data-stu-id="14022-103">In Store and Forward (SnF) mode, files are delivered to queue at send time, and are retrieved from the queue by the destination.</span></span> <span data-ttu-id="14022-104">Réponses intermédiaires sont retournés par SWIFTNet à l’expéditeur jusqu'à ce que le fichier est remis en toute sécurité vers la destination.</span><span class="sxs-lookup"><span data-stu-id="14022-104">Intermediate responses are returned by SWIFTNet to the sender until the file is safely delivered to the destination.</span></span>  
  
## <a name="sending-using-snf"></a><span data-ttu-id="14022-105">Envoi à l’aide de MSNG</span><span class="sxs-lookup"><span data-stu-id="14022-105">Sending Using SnF</span></span>  
 <span data-ttu-id="14022-106">Si vous créez un port d’envoi unidirectionnel, l’adaptateur fonctionne en mode de MSNG et envoie des messages à la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="14022-106">If you create a one-way send port, the adapter works in SnF mode and sends messages to the queue.</span></span>  
  
## <a name="receiving-using-snf"></a><span data-ttu-id="14022-107">Réception à l’aide de MSNG</span><span class="sxs-lookup"><span data-stu-id="14022-107">Receiving Using SnF</span></span>  
 <span data-ttu-id="14022-108">SnF FileAct fonctionne en mode Push.</span><span class="sxs-lookup"><span data-stu-id="14022-108">SnF FileAct operates in Push mode.</span></span> <span data-ttu-id="14022-109">Il s’agit d’une option d’exécution.</span><span class="sxs-lookup"><span data-stu-id="14022-109">This is a run-time option.</span></span>  
  
 <span data-ttu-id="14022-110">Avant de pouvoir récupérer les messages d’une file d’attente, SWIFTNet SnF doit recevoir une demande d’acquisition de la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="14022-110">Before being able to retrieve messages from a queue, SWIFTNet SnF should receive a request to acquire the queue.</span></span> <span data-ttu-id="14022-111">Cela est accompli par l’adaptateur de réception appeler le composant COM + out-of-Process.</span><span class="sxs-lookup"><span data-stu-id="14022-111">This is accomplished by the receive adapter invoking the out-of-proc COM+ component.</span></span> <span data-ttu-id="14022-112">Après une acquisition réussie, une session est créée.</span><span class="sxs-lookup"><span data-stu-id="14022-112">After a successful acquire, a session is created.</span></span> <span data-ttu-id="14022-113">La file d’attente, qui s’ouvre dans le mode spécifié dans la demande.</span><span class="sxs-lookup"><span data-stu-id="14022-113">The queue will then be opened in the mode specified in the Request.</span></span> <span data-ttu-id="14022-114">Tous les messages seront affichera sur le nœud physique qui a émis la demande.</span><span class="sxs-lookup"><span data-stu-id="14022-114">All messages will be returned to the physical node which issued the request.</span></span>  
  
 <span data-ttu-id="14022-115">Les messages sont remis dans l’ordre spécifié (Notez que les transmissions interagir et FileAct pouvant comprend également et classées par priorité.) La séquence des messages, toutefois, est dépendante de l’heure à laquelle ils ont été stockés.</span><span class="sxs-lookup"><span data-stu-id="14022-115">Messages are delivered in the order specified (note that InterAct and FileAct transmissions can be interspersed, and arranged by priority.) The sequencing of messages, however, is dependent on the time that they were stored.</span></span> <span data-ttu-id="14022-116">Dans le cas FileAct, il s’agit de l’heure que le stockage de fichier est terminé, pas lors de son démarrage.</span><span class="sxs-lookup"><span data-stu-id="14022-116">In the case of FileAct, this is the time that the file storage is completed, not when it started.</span></span>  
  
### <a name="push-a-file-from-the-queue"></a><span data-ttu-id="14022-117">Push d’un fichier à partir de la file d’attente</span><span class="sxs-lookup"><span data-stu-id="14022-117">Push a File From the Queue</span></span>  
 <span data-ttu-id="14022-118">L’adaptateur FileAct (serveur) reçoit un HandleFileRequest SWIFTNet, contenant les informations de file d’attente, de session et de séquence.</span><span class="sxs-lookup"><span data-stu-id="14022-118">The FileAct adapter (server) receives a HandleFileRequest from SWIFTNet, containing the queue, session and sequence information.</span></span> <span data-ttu-id="14022-119">Le serveur répond avec un HandleFileResponse.</span><span class="sxs-lookup"><span data-stu-id="14022-119">The server responds with a HandleFileResponse.</span></span>  
  
 <span data-ttu-id="14022-120">Le serveur émet FetchFileRequest et le fichier est envoyé au serveur.</span><span class="sxs-lookup"><span data-stu-id="14022-120">The server then issues FetchFileRequest and the file is delivered to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14022-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14022-121">See Also</span></span>  
 <span data-ttu-id="14022-122">[Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="14022-122">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="14022-123">[Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="14022-123">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="14022-124">[Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="14022-124">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="14022-125">[Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="14022-125">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="14022-126">[Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="14022-126">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="14022-127">[Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="14022-127">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="14022-128">[Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="14022-128">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="14022-129">État de l’adaptateur FileAct analyse</span><span class="sxs-lookup"><span data-stu-id="14022-129">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)