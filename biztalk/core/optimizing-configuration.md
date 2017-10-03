---
title: Optimisation de la Configuration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Concurrent Calls parameter
- optimizing, configuration
- configuring, optimizing
- messages, overload protection
ms.assetid: df0ae17b-fcfa-4e00-893c-63f4972d3822
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72b185d7738ac48d9a1dc3631c7c9faec9ac4b60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-configuration"></a><span data-ttu-id="1c867-102">Optimisation de la Configuration</span><span class="sxs-lookup"><span data-stu-id="1c867-102">Optimizing Configuration</span></span>
<span data-ttu-id="1c867-103">Cette section contient des informations sur l'optimisation de la configuration de l'adaptateur BizTalk pour PeopleSoft Enterprise ainsi que des descriptions de paramètres permettant de configurer celui-ci.</span><span class="sxs-lookup"><span data-stu-id="1c867-103">This section contains information about how to optimize your configuration of BizTalk Adapter for PeopleSoft Enterprise and includes parameter descriptions for setting up the adapter.</span></span>  
  
## <a name="message-overload-protection"></a><span data-ttu-id="1c867-104">Protection contre la surcharge du message</span><span class="sxs-lookup"><span data-stu-id="1c867-104">Message Overload Protection</span></span>  
 <span data-ttu-id="1c867-105">Le paramètre `Max Concurrent Calls` est une fonctionnalité permettant d'optimiser votre configuration.</span><span class="sxs-lookup"><span data-stu-id="1c867-105">The `Max Concurrent Calls` parameter is a feature that enables you to optimize your configuration.</span></span> <span data-ttu-id="1c867-106">Vous pouvez utiliser ce paramètre dans les instances où le débit dépasse les capacités du traitement principal.</span><span class="sxs-lookup"><span data-stu-id="1c867-106">You use this parameter in instances where the throughput exceeds back-end processing capabilities.</span></span> <span data-ttu-id="1c867-107">Vous pouvez ajouter le paramètre aux adaptateurs dans le **propriétés de Port d’envoi** boîte de dialogue pour activer la protection contre les surcharges de message.</span><span class="sxs-lookup"><span data-stu-id="1c867-107">You can add the parameter to the adapters in the **Send Port Transport Properties** dialog box to activate message overload protection.</span></span> <span data-ttu-id="1c867-108">La valeur par défaut est -1 : les messages sont illimités.</span><span class="sxs-lookup"><span data-stu-id="1c867-108">The default is -1, meaning the calls are unlimited.</span></span>  
  
 <span data-ttu-id="1c867-109">Lorsque BizTalk Server envoie des messages à l'adaptateur de transmission, il reçoit tout d'abord un lot de l'adaptateur, puis appelle `TransmitMessage()` sur le lot pour transmettre chaque message.</span><span class="sxs-lookup"><span data-stu-id="1c867-109">When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter and invokes `TransmitMessage()` on the batch to transmit each message.</span></span> <span data-ttu-id="1c867-110">Ensuite, BizTalk Server appelle `Done()` sur le lot et l'adaptateur commence à transmettre les messages au système principal.</span><span class="sxs-lookup"><span data-stu-id="1c867-110">When done, BizTalk Server invokes `Done()` on the batch, and the adapter starts transmitting the messages to the back-end.</span></span> <span data-ttu-id="1c867-111">Si BizTalk Server obtient plusieurs lots avant l'appel de `Done`, la commande `Done` ne peut jamais se produire.</span><span class="sxs-lookup"><span data-stu-id="1c867-111">If BizTalk Server obtains multiple batches before `Done` is invoked, the `Done` command might never occur.</span></span> <span data-ttu-id="1c867-112">En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal.</span><span class="sxs-lookup"><span data-stu-id="1c867-112">By setting the maximum number of messages in a batch, you can control messages to the back-end.</span></span> <span data-ttu-id="1c867-113">La modification de ce paramètre entre en vigueur dans une minute.</span><span class="sxs-lookup"><span data-stu-id="1c867-113">Changing this parameter takes effect in a minute.</span></span> <span data-ttu-id="1c867-114">BizTalk Server doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="1c867-114">BizTalk Server must retrieve the changes to the adapter configuration that is saved in the SQL database.</span></span>  
  
#### <a name="to-change-the-max-concurrent-calls-parameter"></a><span data-ttu-id="1c867-115">Pour modifier le paramètre Nombre maximal d'appels simultanés</span><span class="sxs-lookup"><span data-stu-id="1c867-115">To change the Max Concurrent Calls parameter</span></span>  
  
1.  <span data-ttu-id="1c867-116">Dans le **propriétés de Port d’envoi** boîte de dialogue, entrez un **connexion** valeur.</span><span class="sxs-lookup"><span data-stu-id="1c867-116">In the **Send Port Transport Properties** dialog box, enter a **Connection** value.</span></span>  
  
     <span data-ttu-id="1c867-117">La valeur par défaut est 40 sessions.</span><span class="sxs-lookup"><span data-stu-id="1c867-117">The default value is 40 sessions.</span></span> <span data-ttu-id="1c867-118">Si vous indiquez une valeur inférieure, une dégradation des performances d'exécution peut se produire.</span><span class="sxs-lookup"><span data-stu-id="1c867-118">If you use a smaller value, you might experience degradation in run-time performance.</span></span> <span data-ttu-id="1c867-119">L'inverse est également vrai : une valeur supérieure risque de provoquer le dépassement des capacités du serveur et de générer des erreurs d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1c867-119">The opposite is also true; a bigger value could exceed the ability of the server and result in run-time errors.</span></span>  
  
2.  <span data-ttu-id="1c867-120">Sélectionnez **Oui** pour **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.</span><span class="sxs-lookup"><span data-stu-id="1c867-120">Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span>  
  
     <span data-ttu-id="1c867-121">Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1c867-121">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.</span></span>  
  
     <span data-ttu-id="1c867-122">Le **actualiser l’Agent** paramètre actualise les agents de navigation et les moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1c867-122">The **Refresh Agent** parameter refreshes both the browsing and the run-time agents.</span></span> <span data-ttu-id="1c867-123">Le processus runtimeagent.exe effectue la mise à jour après un délai d'une minute ou à l'appel Envoyer suivant.</span><span class="sxs-lookup"><span data-stu-id="1c867-123">The runtimeagent.exe updates after a delay of one minute or at the next send call.</span></span>  
  
3.  <span data-ttu-id="1c867-124">Renseignez les informations d'identification pour accéder au système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1c867-124">Provide credentials to access the PeopleSoft system.</span></span>  
  
     <span data-ttu-id="1c867-125">Deux méthodes permettent d'accéder au système :</span><span class="sxs-lookup"><span data-stu-id="1c867-125">You can use two methods to access the system:</span></span>  
  
    -   <span data-ttu-id="1c867-126">les informations d'identification de connexion (paramètres de connexion des propriétés du transport) ;</span><span class="sxs-lookup"><span data-stu-id="1c867-126">Login Credentials (Transport Properties Login parameters)</span></span>  
  
    -   <span data-ttu-id="1c867-127">authentification unique (SSO, Single Sign-On)</span><span class="sxs-lookup"><span data-stu-id="1c867-127">Single Sign-On</span></span>  
  
4.  <span data-ttu-id="1c867-128">Sélectionnez **Oui** pour **utiliser SSO** à utiliser l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="1c867-128">Select **Yes** for **Use SSO** to use Single Sign-On.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c867-129">Pour plus d’informations, consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on2.md).</span><span class="sxs-lookup"><span data-stu-id="1c867-129">For more information, see [Using Single Sign-On](../core/using-single-sign-on2.md).</span></span>  
  
5.  <span data-ttu-id="1c867-130">Sélectionnez une application associée sur la liste.</span><span class="sxs-lookup"><span data-stu-id="1c867-130">Select an affiliate application in the list.</span></span>  
  
     <span data-ttu-id="1c867-131">Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1c867-131">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as PeopleSoft.</span></span> <span data-ttu-id="1c867-132">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise utilise les informations d'identification d'un utilisateur d'application.</span><span class="sxs-lookup"><span data-stu-id="1c867-132">Microsoft BizTalk Adapter for PeopleSoft Enterprise uses the credentials of an application user.</span></span> <span data-ttu-id="1c867-133">Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c867-133">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span> <span data-ttu-id="1c867-134">Les informations d'identification sont celles de l'utilisateur (utilisateur de l'application) qui a lancé le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1c867-134">The credentials are those of the user (the application user) who launched the BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c867-135">Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md), ou l’aide en ligne de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1c867-135">For more information about how to create affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md), or the Microsoft BizTalk Server online Help.</span></span>  
  
6.  <span data-ttu-id="1c867-136">Après avoir entré toutes les informations requises pour accepter les informations de connexion, cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1c867-136">After providing all required information to accept the connection information, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1c867-137">Vous devez définir des paramètres de connexion de l'adaptateur BizTalk pour PeopleSoft Enterprise afin d'accéder à PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1c867-137">You must set connection parameters for the BizTalk Adapter for PeopleSoft Enterprise to access PeopleSoft.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c867-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c867-138">See Also</span></span>  
 [<span data-ttu-id="1c867-139">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="1c867-139">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)