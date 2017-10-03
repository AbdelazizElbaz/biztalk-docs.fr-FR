---
title: "La gestion des flux de données entrantes dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b7c4f7-99ba-4bfa-89ab-1fabfe0845d1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20fc34da3a5c8e65f81cd6bbbb699f52506cdc6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-incoming-data-streams-in-pipeline-components"></a><span data-ttu-id="73b92-102">Gestion des flux de données entrantes dans les composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="73b92-102">Handling Incoming Data Streams in Pipeline Components</span></span>
<span data-ttu-id="73b92-103">Vous devez tenir compte des points suivants lorsque vous écrivez du code de désassembleur personnalisé pour les composants du pipeline dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73b92-103">The following considerations should be made when writing custom disassembler code for pipeline components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="do-not-close-the-incoming-data-stream-in-custom-dissasember-code"></a><span data-ttu-id="73b92-104">Ne fermez pas le flux de données entrantes dans le code de désassembleur personnalisé</span><span class="sxs-lookup"><span data-stu-id="73b92-104">Do not close the incoming data stream in custom dissasember code</span></span>  
 <span data-ttu-id="73b92-105">Lorsque vous écrivez du code de désassembleur personnalisé pour les composants du pipeline dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous de ne pas fermer le flux de données entrantes dans ce code.</span><span class="sxs-lookup"><span data-stu-id="73b92-105">When you write custom disassembler code for pipeline components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure that you do not close the incoming data stream in the disassembler code.</span></span> <span data-ttu-id="73b92-106">Le flux de données entrantes du message d'entrée est une ressource partagée.</span><span class="sxs-lookup"><span data-stu-id="73b92-106">The incoming stream from the input message is a shared resource.</span></span> <span data-ttu-id="73b92-107">Il est également utilisé par le composant de suivi du corps du message dans le moteur de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73b92-107">The incoming stream is also used by the message body tracking component in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message engine.</span></span>  
  
 <span data-ttu-id="73b92-108">Si vous fermez de manière implicite ou explicite le flux de données entrant, vous risquez de perdre des données de suivi et de ne pas pouvoir observer les données de flux à l'aide du suivi des événements de messages et des instances de service dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73b92-108">If you either implicitly or explicitly close the incoming stream, tracking data may be lost and you will be unable to examine the stream data using message event and service instance tracking in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="use-the-seek-method-of-the-stream-class-to-set-the-data-stream-pointer-to-the-start-of-the-stream"></a><span data-ttu-id="73b92-109">Utilisez la méthode Seek de la classe Stream pour orienter le pointeur de flux sur le début du flux</span><span class="sxs-lookup"><span data-stu-id="73b92-109">Use the Seek method of the Stream class to set the data stream pointer to the start of the stream</span></span>  
 <span data-ttu-id="73b92-110">Assurez-vous que la lecture du flux de données entrantes s'effectue jusqu'à la fin du flux.</span><span class="sxs-lookup"><span data-stu-id="73b92-110">Ensure that you read from the incoming data stream until the end of the stream is reached.</span></span> <span data-ttu-id="73b92-111">Par exemple, si le code personnalisé lance une requête de lecture pour 300 Ko de données et que le code ne reçoit que 34 Ko de données, ne pensez pas que la fin du flux a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="73b92-111">For example, if custom code makes a read request for 300 KB of data and the code only receives 34 KB of data, do not assume that the end of the stream has been reached.</span></span> <span data-ttu-id="73b92-112">Le code personnalisé doit toujours lire le flux de données entrantes jusqu'à ce qu'il renvoie 0 octet.</span><span class="sxs-lookup"><span data-stu-id="73b92-112">The custom code should always read from the incoming stream until 0 bytes is returned.</span></span>  
  
 <span data-ttu-id="73b92-113">Avant de renvoyer le flux de données dans la logique de composant personnalisée, paramétrez le pointeur de flux de données à nouveau sur le début du flux.</span><span class="sxs-lookup"><span data-stu-id="73b92-113">Before returning the data stream in the custom component logic, set the data stream pointer back to the start of the stream.</span></span> <span data-ttu-id="73b92-114">Par exemple, le code suivant illustre la logique d'utilisation de la méthode Seek pour orienter le pointeur vers le début du flux avant de renvoyer ce dernier.</span><span class="sxs-lookup"><span data-stu-id="73b92-114">For example, this code illustrates logic to use the seek method to point to the beginning of the stream before returning the stream:</span></span>  
  
```  
myDataStream.Seek(0, SeekOrigin.Begin);  
return myDataStream;  
```  
  
 <span data-ttu-id="73b92-115">Si vous ne procédez pas ainsi et que le flux est lu jusqu'à la fin dans le composant en cours, le composant suivant reçoit un flux qui paraît vide car le pointeur n'a pas été paramétré sur le début du flux.</span><span class="sxs-lookup"><span data-stu-id="73b92-115">If you do not do this and the stream is read to the end in the current component, the next component receives what appears to be an empty stream because the data stream pointer was not set to the start of the stream.</span></span> <span data-ttu-id="73b92-116">Ceci peut entraîner des erreurs d'analyse et de validation inattendues dans les composants de pipeline suivants.</span><span class="sxs-lookup"><span data-stu-id="73b92-116">This can cause unexpected parsing and validation errors in subsequent pipeline components.</span></span>