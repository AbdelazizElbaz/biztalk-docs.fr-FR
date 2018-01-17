---
title: "Le Gestionnaire du Port d’envoi dynamique est Configurable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eb8f5ef-af95-4b2e-9a43-6f1240b25855
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11dffbe28d44d7665bc86ff0842c17ea01f7b3d3
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dynamic-send-port-handler-is-configurable"></a><span data-ttu-id="80cdd-102">Le Gestionnaire du Port d’envoi dynamique est Configurable</span><span class="sxs-lookup"><span data-stu-id="80cdd-102">Dynamic Send Port Handler is Configurable</span></span>
<span data-ttu-id="80cdd-103">Lors de la création d’un port d’envoi dynamique, un gestionnaire d’envoi d’adaptateur peut être configuré pour *chaque* adaptateur installé.</span><span class="sxs-lookup"><span data-stu-id="80cdd-103">When creating a Dynamic Send Port, an adapter Send Handler is configurable for *every* installed adapter.</span></span> <span data-ttu-id="80cdd-104">Examinez le cas suivant :</span><span class="sxs-lookup"><span data-stu-id="80cdd-104">Consider the following scenario:</span></span>  
  
 <span data-ttu-id="80cdd-105">**Scénario**</span><span class="sxs-lookup"><span data-stu-id="80cdd-105">**Scenario**</span></span>  
  
 <span data-ttu-id="80cdd-106">Il existe deux itinéraires ESB dans une application.</span><span class="sxs-lookup"><span data-stu-id="80cdd-106">There are two ESB itineraries in an application.</span></span> <span data-ttu-id="80cdd-107">L'itinéraire 1 utilise un port d'envoi dynamique pour envoyer des données à un partage de fichier.</span><span class="sxs-lookup"><span data-stu-id="80cdd-107">Itinerary1 uses a Dynamic Send Port to send data to a File share.</span></span> <span data-ttu-id="80cdd-108">L'itinéraire 2 utilise un port d'envoi dynamique pour envoyer un courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="80cdd-108">Itinerary2 uses a Dynamic Send Port to send e-mail.</span></span> <span data-ttu-id="80cdd-109">Avant, les ports d'envoi dynamiques étaient exécutés dans l'hôte par défaut de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="80cdd-109">In the past, Dynamic send ports execute in the adapter's default host.</span></span> <span data-ttu-id="80cdd-110">L'itinéraire 1 est conçu pour cibler un scénario de petit volume de messages de taille élevée.</span><span class="sxs-lookup"><span data-stu-id="80cdd-110">Itinerary1 is designed to target a low volume - big message size scenario.</span></span> <span data-ttu-id="80cdd-111">L'itinéraire 2 cible un scénario de volume élevé de messages de petite taille.</span><span class="sxs-lookup"><span data-stu-id="80cdd-111">Itinerary2 targets a high volume - small message size scenario.</span></span> <span data-ttu-id="80cdd-112">Étant donné qu’il existe uniquement un hôte par défaut pour un adaptateur, tous les messages sont routés à l'aide du même hôte, ce qui réduit les performances.</span><span class="sxs-lookup"><span data-stu-id="80cdd-112">Since there is only one default host for an adapter, all messages are routed using the same host, decreasing the performance.</span></span>  
  
 <span data-ttu-id="80cdd-113">**La modification**</span><span class="sxs-lookup"><span data-stu-id="80cdd-113">**The Change**</span></span>  
  
 <span data-ttu-id="80cdd-114">Pour améliorer les performances des ports d'envoi dynamiques, un gestionnaire d'envoi d'adaptateur peut être configuré pour utiliser un hôte.</span><span class="sxs-lookup"><span data-stu-id="80cdd-114">To improve the performance of Dynamic Send Ports, an adapter Send Handler is configurable to use any host.</span></span> <span data-ttu-id="80cdd-115">Dans le scénario ESB, l'itinéraire 1 utilise HostA pour envoyer des données à un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="80cdd-115">In the ESB scenario, Itinerary1 uses HostA to send data to a File share.</span></span> <span data-ttu-id="80cdd-116">L'itinéraire 2 utilise le port HostB pour envoyer des courriers électroniques.</span><span class="sxs-lookup"><span data-stu-id="80cdd-116">Itinerary2 uses HostB Port to send e-mail.</span></span>  
  
## <a name="select-a-send-handler"></a><span data-ttu-id="80cdd-117">Sélection d'un gestionnaire d'envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-117">Select a Send Handler</span></span>  
 <span data-ttu-id="80cdd-118">Lors de la création d'un port d'envoi unidirectionnel dynamique ou d'un port d'envoi dynamique avec sollicitation-réponse, le gestionnaire d'envoi peut être configuré pour chaque adaptateur installé.</span><span class="sxs-lookup"><span data-stu-id="80cdd-118">When creating a Dynamic One-Way Send Port or Dynamic Solicit-Response Send Port, the Send Handler is configurable for every installed adapter.</span></span> <span data-ttu-id="80cdd-119">Étapes :</span><span class="sxs-lookup"><span data-stu-id="80cdd-119">Steps:</span></span>  
  
1.  <span data-ttu-id="80cdd-120">Dans le **Administration de BizTalk Server** de la console, développez **groupe BizTalk [*GroupName*]**, développez **Applications**, puis développez l’application pour contenir le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="80cdd-120">In the **BizTalk Server Administration** console, expand **BizTalk Group [*GroupName*]**, expand **Applications**, and then expand the application to contain the send port.</span></span>  
  
2.  <span data-ttu-id="80cdd-121">Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel dynamique** ou **Port d’envoi dynamique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="80cdd-121">Right-click **Send Ports**, click **New**, and then click **Dynamic One-way Send Port** or **Dynamic Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="80cdd-122">Dans **propriétés**, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="80cdd-122">In  **Properties**, click **Configure**.</span></span>  
  
     <span data-ttu-id="80cdd-123">Les adaptateurs sont répertoriés avec le gestionnaire d'envoi par défaut.</span><span class="sxs-lookup"><span data-stu-id="80cdd-123">The adapters are listed with the default Send Handler.</span></span> <span data-ttu-id="80cdd-124">Cliquez sur la flèche pointant vers le bas pour sélectionner un autre hôte.</span><span class="sxs-lookup"><span data-stu-id="80cdd-124">Click the down arrow to select a different host.</span></span>  
  
4.  <span data-ttu-id="80cdd-125">Cliquez sur **OK** enregistrer les paramètres.</span><span class="sxs-lookup"><span data-stu-id="80cdd-125">Click **OK** save the settings.</span></span>  
  
5.  <span data-ttu-id="80cdd-126">Désinscrivez, puis réinscrivez le nouveau port d'envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="80cdd-126">Unenlist and reenlist the new dynamic send port.</span></span>  
  
6.  <span data-ttu-id="80cdd-127">Redémarrez l'instance de l'hôte d'origine.</span><span class="sxs-lookup"><span data-stu-id="80cdd-127">Restart the original host instance.</span></span>  
  
7.  <span data-ttu-id="80cdd-128">Redémarrez la nouvelle instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="80cdd-128">Restart the new host instance.</span></span>  
  
 <span data-ttu-id="80cdd-129">Autres options de configuration du port d'envoi :</span><span class="sxs-lookup"><span data-stu-id="80cdd-129">Additional Send Port configuration options include:</span></span>  
  
-   [<span data-ttu-id="80cdd-130">Configuration des options avancées de transport pour un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-130">How to Configure Transport Advanced Options for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267697)  
  
-   [<span data-ttu-id="80cdd-131">Comment configurer les Options de Transport secondaire pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-131">How to Configure Backup Transport Options for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267698)  
  
-   [<span data-ttu-id="80cdd-132">Comment configurer les mappages sortants pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-132">How to Configure Outbound Maps for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267699)  
  
-   [<span data-ttu-id="80cdd-133">Comment configurer des filtres pour un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-133">How to Configure Filters for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267700)  
  
-   [<span data-ttu-id="80cdd-134">Comment attribuer un certificat à un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-134">How to Assign a Certificate to a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267701)  
  
-   [<span data-ttu-id="80cdd-135">Comment configurer le suivi d’un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="80cdd-135">How to Configure Tracking for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267702)  
  
 <span data-ttu-id="80cdd-136">Les hôtes différents peuvent être ajustés.</span><span class="sxs-lookup"><span data-stu-id="80cdd-136">The different hosts can be fine-tuned.</span></span> <span data-ttu-id="80cdd-137">Les liens suivants traitent de l'optimisation des performances :</span><span class="sxs-lookup"><span data-stu-id="80cdd-137">The following links discuss performance optimization:</span></span>  
  
 [<span data-ttu-id="80cdd-138">Optimisations générales de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="80cdd-138">General BizTalk Server Optimizations</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267703)  
  
 [<span data-ttu-id="80cdd-139">Gestion des paramètres de performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="80cdd-139">Managing BizTalk Server Performance Settings</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267704)