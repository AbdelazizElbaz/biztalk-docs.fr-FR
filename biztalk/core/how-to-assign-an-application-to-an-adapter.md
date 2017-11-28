---
title: "Comment attribuer une Application à un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ea2773-c53c-40a0-a312-015191746451
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5052d06576988ed71da8458a9d55115fb0b1c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-an-application-to-an-adapter"></a><span data-ttu-id="55ad2-102">Comment attribuer une Application à une carte</span><span class="sxs-lookup"><span data-stu-id="55ad2-102">How to Assign an Application to an Adapter</span></span>
<span data-ttu-id="55ad2-103">Une ou plusieurs applications doivent être affectées à un adaptateur pour qu'il puisse traiter les informations entre une application locale et un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="55ad2-103">To process information between a local application and a remote server, an adapter must have one or more applications assigned to it.</span></span>  
  
### <a name="to-assign-an-application-to-an-adapter"></a><span data-ttu-id="55ad2-104">Pour affecter une application à un adaptateur</span><span class="sxs-lookup"><span data-stu-id="55ad2-104">To assign an application to an adapter</span></span>  
  
1.  <span data-ttu-id="55ad2-105">Ajoutez l'application à l'adaptateur à l'aide d'`ISSOPSAdmin.AssignApplicationToAdapter`.</span><span class="sxs-lookup"><span data-stu-id="55ad2-105">Add the application to the adapter by using `ISSOPSAdmin.AssignApplicationToAdapter`.</span></span>  
  
2.  <span data-ttu-id="55ad2-106">Vous pouvez extraire la liste d'applications actuelle affectée à un adaptateur en utilisant `ISSOAdmin.GetApplicationsForAdapter`.</span><span class="sxs-lookup"><span data-stu-id="55ad2-106">You can retrieve the current list of applications assigned to an adapter by using `ISSOAdmin.GetApplicationsForAdapter`.</span></span>  
  
3.  <span data-ttu-id="55ad2-107">Lorsque vous avez terminé, vous pouvez supprimer une application de l'adaptateur à l'aide d'`ISSOPSAdmin.RemoveApplicationFromAdapter`.</span><span class="sxs-lookup"><span data-stu-id="55ad2-107">Once you are finished, you can remove an application from an adapter by using `ISSOPSAdmin.RemoveApplicationFromAdapter`.</span></span>