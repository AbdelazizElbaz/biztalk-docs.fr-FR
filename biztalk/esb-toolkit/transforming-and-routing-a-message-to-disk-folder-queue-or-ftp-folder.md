---
title: "Transformer et acheminer les messages vers le dossier de disque, de file d’attente ou de dossier FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bfdbc38-6663-4d95-a0ed-57fec0245b9f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eb767b588f5531e033ec0c867ee2c6dfad02bc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transforming-and-routing-a-message-to-disk-folder-queue-or-ftp-folder"></a><span data-ttu-id="c45dd-102">Transformer et acheminer les messages vers le dossier de disque, de file d’attente ou de dossier FTP</span><span class="sxs-lookup"><span data-stu-id="c45dd-102">Transforming and Routing a Message to Disk Folder, Queue, or FTP Folder</span></span>
<span data-ttu-id="c45dd-103">Dans ce cas de figure, l’architecture ESB transforme un message envoyé via le service Web de la feuille de route ou toute rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c45dd-103">In this use case, the ESB transforms a message submitted through the Itinerary Web service or any on-ramp.</span></span> <span data-ttu-id="c45dd-104">Une recherche de résolution dynamique de type FILE, FTP ni d’emplacement de la file d’attente détermine le nom de mappage (pour la transformation) et le point de terminaison cible pour le message, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="c45dd-104">A dynamic resolution lookup of type FILE, FTP, or queue location determines the map name (for transformation) and the target endpoint for the message, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="c45dd-105">![Transformation de dossier de disque](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3-TransformingDiskFolder")</span><span class="sxs-lookup"><span data-stu-id="c45dd-105">![Transforming Disk Folder](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3-TransformingDiskFolder")</span></span>  
  
 <span data-ttu-id="c45dd-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="c45dd-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="c45dd-107">**Transformer et acheminer les messages vers un dossier de disque**</span><span class="sxs-lookup"><span data-stu-id="c45dd-107">**Transforming and routing a message to a disk folder**</span></span>  
  
 <span data-ttu-id="c45dd-108">L’exemple de résolution dynamique fourni avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="c45dd-108">The Dynamic Resolution sample included with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="c45dd-109">Il montre comment utiliser les composants pour dynamiquement résoudre l’emplacement du point de terminaison, définir des propriétés de routage et résoudre et exécuter [!INCLUDE[prague](../includes/prague-md.md)] mappe au niveau de la messagerie, sans l’aide d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="c45dd-109">It shows how to use the components to dynamically resolve endpoint location, set routing properties, and resolve and execute [!INCLUDE[prague](../includes/prague-md.md)] maps at the messaging level, without using an orchestration.</span></span> <span data-ttu-id="c45dd-110">Il montre également les modèles de messagerie unidirectionnels ou bidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="c45dd-110">It also demonstrates both one-way and two-way messaging patterns.</span></span>  
  
 <span data-ttu-id="c45dd-111">Une extension de ce cas de figure est une solution de routage simple qui achemine un message entrant à un fichier, FTP ou emplacement de la file d’attente sans cette étape supplémentaire de transformation.</span><span class="sxs-lookup"><span data-stu-id="c45dd-111">An extension of this use case is a simple routing solution that routes an incoming message to a file, FTP, or queue location without the additional step of transformation.</span></span>  
  
 <span data-ttu-id="c45dd-112">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c45dd-112">For more information, see [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span></span>