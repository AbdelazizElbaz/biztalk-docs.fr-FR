---
title: "Le transfert des informations de prise en charge de l’adaptateur FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc27561-9abb-4496-9db7-f221a6c90738
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5aefba5fe85a8a275d3b2050d8c08cc98f74d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-supporting-information-transfer"></a><span data-ttu-id="67522-102">Transfert des informations de prise en charge de l’adaptateur FileAct</span><span class="sxs-lookup"><span data-stu-id="67522-102">FileAct Adapter Supporting Information Transfer</span></span>
<span data-ttu-id="67522-103">L’adaptateur FileAct autorise le transfert facultatif de prendre en charge les informations des fichiers.</span><span class="sxs-lookup"><span data-stu-id="67522-103">The FileAct adapter permits the optional transfer of supporting information with files.</span></span> <span data-ttu-id="67522-104">Ces informations sont transférées à la discrétion de l’application.</span><span class="sxs-lookup"><span data-stu-id="67522-104">This information is transferred at the discretion of the application.</span></span> <span data-ttu-id="67522-105">L’adaptateur ne tout traitement spécial de ces informations sur le côté d’origine, hormis pour vérifier qu’il est au format correct.</span><span class="sxs-lookup"><span data-stu-id="67522-105">The adapter does not do any special processing of this information on the originating side except to validate that it is in the correct format.</span></span> <span data-ttu-id="67522-106">Les éléments qui composent les informations de prise en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="67522-106">The elements which comprise supporting information include:</span></span>  
  
-   <span data-ttu-id="67522-107">Description du fichier et les informations de fichier</span><span class="sxs-lookup"><span data-stu-id="67522-107">File description and file information</span></span>  
  
-   <span data-ttu-id="67522-108">Description de transfert et de transférer des informations</span><span class="sxs-lookup"><span data-stu-id="67522-108">Transfer description and transfer information</span></span>  
  
-   <span data-ttu-id="67522-109">Description de l’accusé de réception et les informations de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="67522-109">Acknowledgement description and acknowledgement information</span></span>  
  
-   <span data-ttu-id="67522-110">Informations de description ou le refus de rejet</span><span class="sxs-lookup"><span data-stu-id="67522-110">Rejection description and reject information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67522-111">Un des composants d’informations de fichier définit la compression et la décompression.</span><span class="sxs-lookup"><span data-stu-id="67522-111">One of the components of file information defines compression and decompression.</span></span> <span data-ttu-id="67522-112">La compression et décompression sont la responsabilité de l’application, pas sur la carte.</span><span class="sxs-lookup"><span data-stu-id="67522-112">Compression and decompression are the responsibility of the application, not the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67522-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67522-113">See Also</span></span>  
 <span data-ttu-id="67522-114">[Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="67522-114">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="67522-115">[Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="67522-115">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="67522-116">[Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="67522-116">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="67522-117">[Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="67522-117">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="67522-118">[Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="67522-118">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="67522-119">[Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="67522-119">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="67522-120">[Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="67522-120">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="67522-121">État de l’adaptateur FileAct analyse</span><span class="sxs-lookup"><span data-stu-id="67522-121">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)