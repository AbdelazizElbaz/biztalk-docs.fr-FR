---
title: "Configuration de l’adaptateur WCF pour intercepter les données BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd705c27-5d04-47e5-9bb2-61235f8fe544
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f418512ecd0a3e38f884965d1698579fb300dd74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-wcf-adapter-to-intercept-bam-data"></a><span data-ttu-id="a008f-102">Configuration de l'adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="a008f-102">Configuring the WCF Adapter to Intercept BAM Data</span></span>
<span data-ttu-id="a008f-103">Cette section contient des informations sur les étapes à suivre pour configurer l'adaptateur WCF de BizTalk, afin de l'utiliser avec un intercepteur WCF BAM.</span><span class="sxs-lookup"><span data-stu-id="a008f-103">This section contains information about the steps you must take to configure the BizTalk WCF adapter to work with the BAM WCF interceptor.</span></span>  
  
 <span data-ttu-id="a008f-104">Les étapes de base sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a008f-104">The basic steps are as follows:</span></span>  
  
-   <span data-ttu-id="a008f-105">ajout du comportement BAM au fichier machine.config ;</span><span class="sxs-lookup"><span data-stu-id="a008f-105">Add the BAM behavior to the machine.config file.</span></span>  
  
-   <span data-ttu-id="a008f-106">création d'un adaptateur WCF BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="a008f-106">Create a BizTalk WCF adapter.</span></span>  
  
-   <span data-ttu-id="a008f-107">configuration de l'interception WCF BAM.</span><span class="sxs-lookup"><span data-stu-id="a008f-107">Configure the BAM WCF interception.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a008f-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a008f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="a008f-109">Comment ajouter le comportement de l’intercepteur BAM au fichier Machine.config</span><span class="sxs-lookup"><span data-stu-id="a008f-109">How to Add the BAM Interceptor Behavior to the Machine.config File</span></span>](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md)  
  
-   [<span data-ttu-id="a008f-110">Comment créer un adaptateur WCF pour BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a008f-110">How to Create a WCF Adapter for BizTalk Server</span></span>](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md)  
  
-   [<span data-ttu-id="a008f-111">La configuration de réception et emplacements et les Ports d’envoi pour l’Interception WCF BAM</span><span class="sxs-lookup"><span data-stu-id="a008f-111">How to Configure Receive and Send Locations and Ports for BAM WCF Interception</span></span>](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md)  
  
-   [<span data-ttu-id="a008f-112">Comment configurer l’Interception WCF BAM</span><span class="sxs-lookup"><span data-stu-id="a008f-112">How to Configure the BAM WCF Interception</span></span>](../core/how-to-configure-the-bam-wcf-interception.md)  
  
-   [<span data-ttu-id="a008f-113">À l’aide de la gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="a008f-113">Using Fault Handling</span></span>](../core/using-fault-handling.md)