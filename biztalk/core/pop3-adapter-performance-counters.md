---
title: "POP3 Compteurs de performances de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f799175e-e9e7-4937-93bd-aaec1c43b75a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0f48879fcc00041ce0fa1cf842a066c6da59804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-performance-counters"></a><span data-ttu-id="96162-102">Compteurs de performances de l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="96162-102">POP3 Adapter Performance Counters</span></span>
<span data-ttu-id="96162-103">Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service.</span><span class="sxs-lookup"><span data-stu-id="96162-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="96162-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="96162-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="96162-105">Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur de réception POP3** catégorie d’objet de performances :</span><span class="sxs-lookup"><span data-stu-id="96162-105">The following performance counters are accessible for each host instance under the **BizTalk:POP3 Receive Adapter** performance object category:</span></span>  
  
|<span data-ttu-id="96162-106">**Catégorie**</span><span class="sxs-lookup"><span data-stu-id="96162-106">**Category**</span></span>|<span data-ttu-id="96162-107">**Compteur**</span><span class="sxs-lookup"><span data-stu-id="96162-107">**Counter**</span></span>|<span data-ttu-id="96162-108">**Description**</span><span class="sxs-lookup"><span data-stu-id="96162-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="96162-109">BizTalk:adaptateur de réception POP3</span><span class="sxs-lookup"><span data-stu-id="96162-109">BizTalk:POP3 Receive Adapter</span></span>|<span data-ttu-id="96162-110">Sessions actives</span><span class="sxs-lookup"><span data-stu-id="96162-110">Active sessions</span></span>|<span data-ttu-id="96162-111">Nombre de connexions POP3 actives que l'adaptateur POP3 gère en même temps.</span><span class="sxs-lookup"><span data-stu-id="96162-111">Number of open POP3 connections the POP3 adapter is managing at a time.</span></span>|  
||<span data-ttu-id="96162-112">Octets reçus</span><span class="sxs-lookup"><span data-stu-id="96162-112">Bytes received</span></span>|<span data-ttu-id="96162-113">Nombre total d'octets téléchargés par l'adaptateur POP3 depuis un serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="96162-113">Total number of bytes downloaded by the POP3 adapter from a mail server.</span></span>|  
||<span data-ttu-id="96162-114">Octets reçus/s</span><span class="sxs-lookup"><span data-stu-id="96162-114">Bytes receive/Sec</span></span>|<span data-ttu-id="96162-115">Nombre d'octets téléchargés par l'adaptateur POP3 depuis un serveur de messagerie par seconde.</span><span class="sxs-lookup"><span data-stu-id="96162-115">Number of bytes downloaded by the POP3 adapter from a mail server per second.</span></span>|  
||<span data-ttu-id="96162-116">Messages reçus</span><span class="sxs-lookup"><span data-stu-id="96162-116">Messages received</span></span>|<span data-ttu-id="96162-117">Nombre total de messages électroniques téléchargés par l'adaptateur POP3 depuis un serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="96162-117">Total number of email messages downloaded by the POP3 adapter from a mail server.</span></span>|  
||<span data-ttu-id="96162-118">Messages reçus/s</span><span class="sxs-lookup"><span data-stu-id="96162-118">Messages received/Sec</span></span>|<span data-ttu-id="96162-119">Nombre de messages électroniques téléchargés par l'adaptateur POP3 depuis un serveur de messagerie par seconde.</span><span class="sxs-lookup"><span data-stu-id="96162-119">Number of email messages downloaded by the POP3 adapter from mail server per second.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="96162-120">Pour accéder aux compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="96162-120">To access performance counters</span></span>  
 <span data-ttu-id="96162-121">Pour accéder aux compteurs de performance de l'adaptateur POP3, procédez comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="96162-121">Follow these steps to access performance counters for the POP3 adapter:</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="96162-122">Si vous exécutez Windows 2008</span><span class="sxs-lookup"><span data-stu-id="96162-122">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="96162-123">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.</span><span class="sxs-lookup"><span data-stu-id="96162-123">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="96162-124">Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="96162-124">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="96162-125">Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **adaptateur de réception POP3** objet compteur de performances et sélectionnez les compteurs à être analysé</span><span class="sxs-lookup"><span data-stu-id="96162-125">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:POP3 Receive Adapter** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="96162-126">Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="96162-126">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="96162-127">Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.</span><span class="sxs-lookup"><span data-stu-id="96162-127">To select all available counter instances, select \<**All instances**>.</span></span>  
  
5.  <span data-ttu-id="96162-128">Après avoir ajouté les compteurs, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="96162-128">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="96162-129">Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.</span><span class="sxs-lookup"><span data-stu-id="96162-129">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96162-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96162-130">See Also</span></span>  
 [<span data-ttu-id="96162-131">Analyse de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="96162-131">Monitoring BizTalk Server</span></span>](../core/monitoring-biztalk-server.md)  
 <span data-ttu-id="96162-132">[Traitement des Messages à parties multiples avec l’adaptateur POP3](../core/processing-multi-part-messages-with-the-pop3-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="96162-132">[Processing Multi Part Messages with the POP3 Adapter](../core/processing-multi-part-messages-with-the-pop3-adapter.md) </span></span>  
 [<span data-ttu-id="96162-133">Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster</span><span class="sxs-lookup"><span data-stu-id="96162-133">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)