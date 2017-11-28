---
title: "L’adaptateur JD Edwards EnterpriseOne dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3e68fa-b81d-4767-ab62-3200ce89d81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d46fd3375f49f9fabd6ce8028cc226bce5885db
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-jd-edwards-enterpriseone"></a><span data-ttu-id="2e805-102">Dépannage de JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="2e805-102">Troubleshooting JD Edwards EnterpriseOne</span></span>

## <a name="overview"></a><span data-ttu-id="2e805-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2e805-103">Overview</span></span>
<span data-ttu-id="2e805-104">Cette section décrit les problèmes et messages d'erreur courants que vous pouvez rencontrer dans l'adaptateur BizTalk pour JD Edwards EnterpriseOne, et indique les corrections possibles.</span><span class="sxs-lookup"><span data-stu-id="2e805-104">This section describes common issues and error messages you might encounter in BizTalk Adapter for JD Edwards EnterpriseOne and provides possible corrections for them.</span></span> <span data-ttu-id="2e805-105">Elle décrit également l'utilisation de l'outil Suivi d'événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="2e805-105">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="2e805-106">Vous pouvez utiliser les outils de débogage/suivi suivants pour dépanner l'adaptateur :</span><span class="sxs-lookup"><span data-stu-id="2e805-106">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="2e805-107">débogage BizTalk Server natif (par exemple, type de suivi sur votre port ou débogueur d'orchestration) ;</span><span class="sxs-lookup"><span data-stu-id="2e805-107">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="2e805-108">messages d'erreur envoyés au journal des événements ;</span><span class="sxs-lookup"><span data-stu-id="2e805-108">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="2e805-109">capture des messages de l'émetteur, du récepteur et de gestion via BTAJDEEnterpriseOneTrace.cmd et un outil qui convertit les fichiers .etl (tels que tracerpt.exe ou tracedmp.exe).</span><span class="sxs-lookup"><span data-stu-id="2e805-109">The capture of transmitter, receiver, and management messages through BTAJDEEnterpriseOneTrace.cmd and a tool that converts.etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2e805-110">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2e805-110">Next steps</span></span>
  
-   [<span data-ttu-id="2e805-111">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="2e805-111">Error Messages</span></span>](../core/error-messages1.md)  
  
-   [<span data-ttu-id="2e805-112">Utilisation de l’outil Suivi des événements pour Windows</span><span class="sxs-lookup"><span data-stu-id="2e805-112">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows4.md)  
  
-   [<span data-ttu-id="2e805-113">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="2e805-113">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter1.md)