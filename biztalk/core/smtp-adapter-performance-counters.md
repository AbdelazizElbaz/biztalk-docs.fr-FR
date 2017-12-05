---
title: "Compteurs de Performance de l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c7aa7dd-1674-4bbb-b22f-92204d55c4b8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3503b5a37a7b2ab48be2478879cc61187895029
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="smtp-adapter-performance-counters"></a><span data-ttu-id="1a29b-102">Compteurs de performances de l'adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="1a29b-102">SMTP Adapter Performance Counters</span></span>
<span data-ttu-id="1a29b-103">Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service.</span><span class="sxs-lookup"><span data-stu-id="1a29b-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="1a29b-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="1a29b-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="1a29b-105">Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **adaptateur d’envoi SMTP** catégorie d’objet de performances :</span><span class="sxs-lookup"><span data-stu-id="1a29b-105">The following performance counters are accessible for each host instance under the **BizTalk:SMTP Send Adapter** performance object category:</span></span>  
  
|<span data-ttu-id="1a29b-106">**Catégorie**</span><span class="sxs-lookup"><span data-stu-id="1a29b-106">**Category**</span></span>|<span data-ttu-id="1a29b-107">**Compteur**</span><span class="sxs-lookup"><span data-stu-id="1a29b-107">**Counter**</span></span>|<span data-ttu-id="1a29b-108">**Description**</span><span class="sxs-lookup"><span data-stu-id="1a29b-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="1a29b-109">BizTalk:adaptateur d'envoi SMTP</span><span class="sxs-lookup"><span data-stu-id="1a29b-109">BizTalk:SMTP Send Adapter</span></span>|<span data-ttu-id="1a29b-110">Messages envoyés</span><span class="sxs-lookup"><span data-stu-id="1a29b-110">Messages sent</span></span>|<span data-ttu-id="1a29b-111">Nombre total de messages envoyés par l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="1a29b-111">Total number of messages sent by the SMTP adapter.</span></span> <span data-ttu-id="1a29b-112">Le compteur prend en compte uniquement les messages qui ont été transmis au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="1a29b-112">The counter is incremented only for messages that have been transmitted to the SMTP server.</span></span>|  
||<span data-ttu-id="1a29b-113">Messages envoyés/s</span><span class="sxs-lookup"><span data-stu-id="1a29b-113">Messages sent/Sec</span></span>|<span data-ttu-id="1a29b-114">Nombre de messages envoyés par l'adaptateur SMTP à chaque seconde.</span><span class="sxs-lookup"><span data-stu-id="1a29b-114">Number of messages sent by the SMTP adapter per second.</span></span> <span data-ttu-id="1a29b-115">Le compteur s'applique uniquement aux messages qui ont été transmis au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="1a29b-115">The counter applies only to messages that have been transmitted to the SMTP server.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="1a29b-116">Pour accéder aux compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="1a29b-116">To access performance counters</span></span>  
 <span data-ttu-id="1a29b-117">Utilisez la procédure suivante pour accéder aux compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="1a29b-117">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="1a29b-118">Si vous exécutez Windows 2008</span><span class="sxs-lookup"><span data-stu-id="1a29b-118">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="1a29b-119">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.</span><span class="sxs-lookup"><span data-stu-id="1a29b-119">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="1a29b-120">Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1a29b-120">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="1a29b-121">Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **adaptateur d’envoi SMTP**objet compteur de performances et sélectionnez les compteurs à être analysé</span><span class="sxs-lookup"><span data-stu-id="1a29b-121">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:SMTP Send Adapter**performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="1a29b-122">Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1a29b-122">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="1a29b-123">Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**\>.</span><span class="sxs-lookup"><span data-stu-id="1a29b-123">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="1a29b-124">Après avoir ajouté les compteurs, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a29b-124">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="1a29b-125">Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.</span><span class="sxs-lookup"><span data-stu-id="1a29b-125">The selected performance counters appear on the **Performance Monitor** screen.</span></span>