---
title: "Création de TIBCO Enterprise Message Service gestionnaires de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive handlers
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83163701f897b782d577351cd08b3f2650ae6fb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-tibco-enterprise-message-service-receive-handlers"></a><span data-ttu-id="c7f80-102">Création des gestionnaires de réception TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="c7f80-102">Creating TIBCO Enterprise Message Service Receive Handlers</span></span>
<span data-ttu-id="c7f80-103">Le récepteur TIBCO Enterprise Message Service est un service de port d'écoute qui enregistre une file d'attente ou une rubrique particulière et reçoit les messages associés.</span><span class="sxs-lookup"><span data-stu-id="c7f80-103">TIBCO Enterprise Message Service receiver is a listener service that registers a particular Queue or Topic and receives the relative messages.</span></span> <span data-ttu-id="c7f80-104">L'adaptateur BizTalk pour TIBCO Enterprise Message Service s'enregistre d'abord auprès de TIBCO Enterprise Message Service en ouvrant une nouvelle session, puis il continue l'interrogation pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="c7f80-104">BizTalk Adapter for TIBCO Enterprise Message Service first registers with TIBCO Enterprise Message Service by opening a new session, and then it continues polling to receive messages..</span></span> <span data-ttu-id="c7f80-105">Cette section décrit la configuration du port de réception pour la connexion à TIBCO Enterprise Message Service et l'utilisation d'un fichier XML dans votre orchestration pour interagir avec TIBCO EMS lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c7f80-105">This section explains how to set the receive port to connect to TIBCO Enterprise Message Service and how to include XML in your orchestration to interact with TIBCO EMS at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7f80-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c7f80-106">In This Section</span></span>  
  
-   [<span data-ttu-id="c7f80-107">Comment créer des Ports de réception dans TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="c7f80-107">How to Create Receive Ports in TIBCO Enterprise Message Service</span></span>](../core/how-to-create-receive-ports-in-tibco-enterprise-message-service.md)  
  
-   [<span data-ttu-id="c7f80-108">Définition des propriétés du Transport TIBCO Enterprise Message Service pour le Port de réception</span><span class="sxs-lookup"><span data-stu-id="c7f80-108">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>](../core/set-tibco-enterprise-message-service-transport-properties-for-the-receive-port.md)  
  
-   [<span data-ttu-id="c7f80-109">Procédure de Pipelines de réception pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="c7f80-109">How to Set Receive Pipelines for TIBCO Enterprise Message Service</span></span>](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)