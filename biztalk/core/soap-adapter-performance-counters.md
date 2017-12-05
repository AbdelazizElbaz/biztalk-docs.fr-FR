---
title: "Compteurs de performances de l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40b54d4e-0a2e-483f-982a-97ab9fb59202
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 543c982a68d2a940b4800711d757f4fb159611de
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="soap-adapter-performance-counters"></a><span data-ttu-id="ba0f0-102">Compteurs de performances de l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="ba0f0-102">SOAP Adapter Performance Counters</span></span>
<span data-ttu-id="ba0f0-103">Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="ba0f0-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="ba0f0-105">Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception SOAP** et **adaptateur d’envoi SOAP** catégories d’objet de performances :</span><span class="sxs-lookup"><span data-stu-id="ba0f0-105">The following performance counters are accessible for each host instance under the **BizTalk:SOAP Receive Adapter** and the **BizTalk:SOAP Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="ba0f0-106">**Catégorie**</span><span class="sxs-lookup"><span data-stu-id="ba0f0-106">**Category**</span></span>|<span data-ttu-id="ba0f0-107">**Compteur**</span><span class="sxs-lookup"><span data-stu-id="ba0f0-107">**Counter**</span></span>|<span data-ttu-id="ba0f0-108">**Description**</span><span class="sxs-lookup"><span data-stu-id="ba0f0-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="ba0f0-109">BizTalk:adaptateur de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="ba0f0-109">BizTalk:SOAP Receive Adapter</span></span>|<span data-ttu-id="ba0f0-110">Messages reçus</span><span class="sxs-lookup"><span data-stu-id="ba0f0-110">Messages received</span></span>|<span data-ttu-id="ba0f0-111">Nombre total de messages reçus par l'adaptateur de réception SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-111">Total number of messages received by the SOAP receive adapter.</span></span> <span data-ttu-id="ba0f0-112">Le compteur est incrémenté après qu'un message de requête a été lu dans son intégralité par l'adaptateur dans le client SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-112">The counter is incremented after a request message is completely read by the adapter from the SOAP client.</span></span>|  
||<span data-ttu-id="ba0f0-113">Messages reçus/s</span><span class="sxs-lookup"><span data-stu-id="ba0f0-113">Messages received/Sec</span></span>|<span data-ttu-id="ba0f0-114">Nombre total de messages reçus par l'adaptateur de réception SOAP à chaque seconde.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-114">Number of messages received by the SOAP receive adapter per second.</span></span> <span data-ttu-id="ba0f0-115">Le compteur prend uniquement en compte les messages de requête lus dans leur intégralité par l'adaptateur dans le client SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-115">The counter applies only to request messages that have been completely read by the adapter from the SOAP client.</span></span>|  
|<span data-ttu-id="ba0f0-116">BizTalk:adaptateur d'envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="ba0f0-116">BizTalk:SOAP Send Adapter</span></span>|<span data-ttu-id="ba0f0-117">Messages envoyés</span><span class="sxs-lookup"><span data-stu-id="ba0f0-117">Messages sent</span></span>|<span data-ttu-id="ba0f0-118">Nombre total de messages envoyés par l'adaptateur d'envoi SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-118">Total number of messages sent by the SOAP send adapter.</span></span> <span data-ttu-id="ba0f0-119">Le compteur est augmenté uniquement pour les messages ayant atteint l'URL de destination.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-119">The counter is incremented only for messages that have reached the destination URL.</span></span>|  
||<span data-ttu-id="ba0f0-120">Messages envoyés/s</span><span class="sxs-lookup"><span data-stu-id="ba0f0-120">Messages sent/Sec</span></span>|<span data-ttu-id="ba0f0-121">Nombre total de messages envoyés par l'adaptateur d'envoi SOAP à chaque seconde.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-121">Number of messages sent by the SOAP send adapter per second.</span></span> <span data-ttu-id="ba0f0-122">Le compteur prend uniquement en compte les messages qui ont atteint l'URL de destination.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-122">The counter applies only to messages that have reached the destination URL.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="ba0f0-123">Pour accéder aux compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="ba0f0-123">To access performance counters</span></span>  
 <span data-ttu-id="ba0f0-124">Utilisez la procédure suivante pour accéder aux compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-124">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-server-2008"></a><span data-ttu-id="ba0f0-125">Si vous utilisez Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="ba0f0-125">If you are using Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="ba0f0-126">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-126">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="ba0f0-127">Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-127">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="ba0f0-128">Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **SOAP** objet compteur de performance et sélectionnez les compteurs à surveiller</span><span class="sxs-lookup"><span data-stu-id="ba0f0-128">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:SOAP** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="ba0f0-129">Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-129">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span> <span data-ttu-id="ba0f0-130">Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-130">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="ba0f0-131">Après avoir ajouté les compteurs, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-131">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="ba0f0-132">Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.</span><span class="sxs-lookup"><span data-stu-id="ba0f0-132">The selected performance counters appear on the **Performance Monitor** screen.</span></span>