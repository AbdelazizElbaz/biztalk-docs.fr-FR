---
title: "Résolution des problèmes de JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, troubleshooting
- adapters [JD Edwards EnterpriseOne adapters], troubleshooting
ms.assetid: 7b3e68fa-b81d-4767-ab62-3200ce89d81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d32a4db56dc60d3a57d6e43985cc30a2868098bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-jd-edwards-enterpriseone"></a><span data-ttu-id="2c0f0-102">Dépannage de JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="2c0f0-102">Troubleshooting JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="2c0f0-103">Cette section décrit les problèmes et messages d'erreur courants que vous pouvez rencontrer dans l'adaptateur BizTalk pour JD Edwards EnterpriseOne, et indique les corrections possibles.</span><span class="sxs-lookup"><span data-stu-id="2c0f0-103">This section describes common issues and error messages you might encounter in BizTalk Adapter for JD Edwards EnterpriseOne and provides possible corrections for them.</span></span> <span data-ttu-id="2c0f0-104">Elle décrit également l'utilisation de l'outil Suivi d'événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="2c0f0-104">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="2c0f0-105">Vous pouvez utiliser les outils de débogage/suivi suivants pour dépanner l'adaptateur :</span><span class="sxs-lookup"><span data-stu-id="2c0f0-105">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="2c0f0-106">débogage BizTalk Server natif (par exemple, type de suivi sur votre port ou débogueur d'orchestration) ;</span><span class="sxs-lookup"><span data-stu-id="2c0f0-106">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="2c0f0-107">messages d'erreur envoyés au journal des événements ;</span><span class="sxs-lookup"><span data-stu-id="2c0f0-107">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="2c0f0-108">capture des messages de l'émetteur, du récepteur et de gestion via BTAJDEEnterpriseOneTrace.cmd et un outil qui convertit les fichiers .etl (tels que tracerpt.exe ou tracedmp.exe).</span><span class="sxs-lookup"><span data-stu-id="2c0f0-108">The capture of transmitter, receiver, and management messages through BTAJDEEnterpriseOneTrace.cmd and a tool that converts.etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c0f0-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2c0f0-109">In This Section</span></span>  
  
-   [<span data-ttu-id="2c0f0-110">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="2c0f0-110">Error Messages</span></span>](../core/error-messages1.md)  
  
-   [<span data-ttu-id="2c0f0-111">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="2c0f0-111">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows4.md)  
  
-   [<span data-ttu-id="2c0f0-112">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="2c0f0-112">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter1.md)