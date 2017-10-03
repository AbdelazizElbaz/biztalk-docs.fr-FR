---
title: OrchestrationEventStream | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7c63610-6344-4b71-8d65-3add7883bc79
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1fd0dc229c38b3a060c75a9c584259175d72fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrationeventstream"></a><span data-ttu-id="748fb-102">OrchestrationEventStream</span><span class="sxs-lookup"><span data-stu-id="748fb-102">OrchestrationEventStream</span></span>
<span data-ttu-id="748fb-103">Vous utilisez l'API OrchestrationEventStream (OES) lorsque votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé et que vous assurez le suivi d'éléments qui font partie de transactions d'orchestrations BizTalk.</span><span class="sxs-lookup"><span data-stu-id="748fb-103">You use the OrchestrationEventStream (OES) API when your application runs on a computer on which BizTalk Server is installed and you are tracking items that are part of BizTalk orchestration transactions.</span></span>  
  
 <span data-ttu-id="748fb-104">L'API OES stocke les données de suivi tout d'abord dans la base de données MessageBox BizTalk.</span><span class="sxs-lookup"><span data-stu-id="748fb-104">The OES API stores tracking data first in the BizTalk MessageBox database.</span></span> <span data-ttu-id="748fb-105">Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).</span><span class="sxs-lookup"><span data-stu-id="748fb-105">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
 <span data-ttu-id="748fb-106">L'API OES se trouve dans l'espace de noms Microsoft.BizTalk.Bam.EventObservation.</span><span class="sxs-lookup"><span data-stu-id="748fb-106">The OES API is found in the Microsoft.BizTalk.Bam.EventObservation namespace.</span></span> <span data-ttu-id="748fb-107">Pour utiliser cette API, vous devez ajouter Microsoft.Biztalk.BAM.Xlangs.dll à votre projet.</span><span class="sxs-lookup"><span data-stu-id="748fb-107">To use the API you must add the Microsoft.Biztalk.BAM.Xlangs.dll to your project.</span></span>  
  
## <a name="oes-members"></a><span data-ttu-id="748fb-108">Membres OES</span><span class="sxs-lookup"><span data-stu-id="748fb-108">OES Members</span></span>  
 <span data-ttu-id="748fb-109">L'API OES est dérivée de la classe [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) .</span><span class="sxs-lookup"><span data-stu-id="748fb-109">The OES API is derived from the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) class.</span></span>  
  
 <span data-ttu-id="748fb-110">Elle implémente toutes les méthodes de la classe EventStream, mais présente l'exception suivante dans les comportements :</span><span class="sxs-lookup"><span data-stu-id="748fb-110">OES implements all of the methods within the EventStream class, but has the  following exception in behaviors:</span></span>  
  
 <span data-ttu-id="748fb-111">**Clear() de void statique publique ;**</span><span class="sxs-lookup"><span data-stu-id="748fb-111">**public static void Clear();**</span></span>  
  
 <span data-ttu-id="748fb-112">Pas d'opération.</span><span class="sxs-lookup"><span data-stu-id="748fb-112">No operation.</span></span>  
  
 <span data-ttu-id="748fb-113">**Flush() de void statique publique ;**</span><span class="sxs-lookup"><span data-stu-id="748fb-113">**public static void Flush();**</span></span>  
  
 <span data-ttu-id="748fb-114">Pas d'opération.</span><span class="sxs-lookup"><span data-stu-id="748fb-114">No operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748fb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="748fb-115">See Also</span></span>  
 [<span data-ttu-id="748fb-116">Classes EventStream</span><span class="sxs-lookup"><span data-stu-id="748fb-116">EventStream Classes</span></span>](../core/eventstream-classes.md)