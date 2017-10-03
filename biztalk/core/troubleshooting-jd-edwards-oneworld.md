---
title: "Résolution des problèmes de JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, troubleshooting
- troubleshooting [JD Edwards OneWorld adapters]
ms.assetid: 15d73c2a-c6ee-46bf-8837-9c6ae3b098d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b79e1bab85b52f816788b4e5e3550a5fa8059a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-jd-edwards-oneworld"></a><span data-ttu-id="9b0c6-102">Dépannage de l'adaptateur JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="9b0c6-102">Troubleshooting JD Edwards OneWorld</span></span>
<span data-ttu-id="9b0c6-103">Cette section décrit les problèmes et messages d'erreur courants que vous pouvez rencontrer dans l'adaptateur BizTalk pour JD Edwards OneWorld, et indique les corrections possibles.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-103">This section describes common issues and error messages that you might encounter in BizTalk Adapter for JD Edwards OneWorld, and provides possible corrections.</span></span> <span data-ttu-id="9b0c6-104">Elle décrit également l'utilisation de l'outil Suivi d'événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="9b0c6-104">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="9b0c6-105">Vous pouvez utiliser les outils de débogage/suivi suivants pour dépanner l'adaptateur :</span><span class="sxs-lookup"><span data-stu-id="9b0c6-105">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="9b0c6-106">débogage BizTalk Server natif (par exemple, type de suivi sur votre port ou débogueur d'orchestration) ;</span><span class="sxs-lookup"><span data-stu-id="9b0c6-106">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="9b0c6-107">messages d'erreur envoyés au journal des événements ;</span><span class="sxs-lookup"><span data-stu-id="9b0c6-107">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="9b0c6-108">capture des messages de l'émetteur, du récepteur et de gestion via BTAJDEOneWorldTrace.cmd et un outil qui convertit les fichiers .etl (tels que tracerpt.exe ou tracedmp.exe).</span><span class="sxs-lookup"><span data-stu-id="9b0c6-108">The capture of transmitter, receiver, and management messages through BTAJDEOneWorldTrace.cmd and a tool that converts the .etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b0c6-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b0c6-109">In This Section</span></span>  
  
-   [<span data-ttu-id="9b0c6-110">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="9b0c6-110">Error Messages</span></span>](../core/error-messages2.md)  
  
-   [<span data-ttu-id="9b0c6-111">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="9b0c6-111">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows2.md)  
  
-   [<span data-ttu-id="9b0c6-112">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="9b0c6-112">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter3.md)