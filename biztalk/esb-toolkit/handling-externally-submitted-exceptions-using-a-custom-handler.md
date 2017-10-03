---
title: "Gestion de l’extérieur soumis les Exceptions à l’aide d’un gestionnaire personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53fa661e-d391-47c0-92d5-1d0c45b5963d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba3fc49756619f77188f0a311ff46eb18e7f0b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-externally-submitted-exceptions-using-a-custom-handler"></a><span data-ttu-id="a577c-102">Gestion de l’extérieur soumis les Exceptions à l’aide d’un gestionnaire personnalisé</span><span class="sxs-lookup"><span data-stu-id="a577c-102">Handling Externally Submitted Exceptions Using a Custom Handler</span></span>
<span data-ttu-id="a577c-103">Dans ce cas de figure, un client externe envoie un message d’exception via un service Web.</span><span class="sxs-lookup"><span data-stu-id="a577c-103">In this use case, an external client submits an exception message through a Web service.</span></span> <span data-ttu-id="a577c-104">Un port d’envoi, préconfiguré avec le composant de pipeline encodeur d’Exception ESB, s’abonne au message d’erreur ; Il traite et l’enregistre dans un fichier de disque que vous pouvez consulter à l’aide de Microsoft InfoPath, comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="a577c-104">A send port, preconfigured with the ESB Exception Encoder pipeline component, subscribes to the fault message; it processes and persists it as a disk file that you can view using Microsoft InfoPath, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="a577c-105">![Gestion des Exceptions externes](../esb-toolkit/media/ch3-handlingexternalexceptions.gif "Ch3-HandlingExternalExceptions")</span><span class="sxs-lookup"><span data-stu-id="a577c-105">![Handling External Exceptions](../esb-toolkit/media/ch3-handlingexternalexceptions.gif "Ch3-HandlingExternalExceptions")</span></span>  
  
 <span data-ttu-id="a577c-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="a577c-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="a577c-107">**La gestion des messages entrants d’exception ou une erreur et la persistance dans un fichier de disque**</span><span class="sxs-lookup"><span data-stu-id="a577c-107">**Handling incoming exception or fault messages and persisting to a disk file**</span></span>  
  
 <span data-ttu-id="a577c-108">L’exemple Exception la gestion des services fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="a577c-108">The Exception Handling Service Sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="a577c-109">Il montre comment utiliser le Service d’Exception ESB comme un mécanisme universel pour envoyer des messages d’erreur à partir d’applications externes qui seront stockés dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] base de données de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="a577c-109">It shows how to use the ESB Exception Service as a universal mechanism to submit fault messages from external applications that will be stored in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exception management database.</span></span> <span data-ttu-id="a577c-110">Pour plus d’informations, consultez [exécution de l’exemple de Service de la gestion des exceptions](../esb-toolkit/running-the-exception-handling-service-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a577c-110">For more information, see [Running the Exception Handling Service Sample](../esb-toolkit/running-the-exception-handling-service-sample.md).</span></span>