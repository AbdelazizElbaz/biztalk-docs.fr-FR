---
title: "Comment définir les Pipelines JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines
- send pipelines
- setting pipelines
- pipelines, setting
ms.assetid: 821d4081-a2d4-4957-abc0-d6370e719ba8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e45ec6f6eb3be74e150e77de9ef6dbbe461a361a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-jd-edwards-oneworld-pipelines"></a><span data-ttu-id="e826c-102">Configuration des pipelines JD Edwards OneWorld [JDE]</span><span class="sxs-lookup"><span data-stu-id="e826c-102">How to Set JD Edwards OneWorld Pipelines</span></span>
<span data-ttu-id="e826c-103">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld requiert la sélection des options XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e826c-103">Microsoft BizTalk Adapter for JD Edwards OneWorld requires that you select XMLTransmit and XMLReceive for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="e826c-104">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="e826c-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="e826c-105">Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server** , puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e826c-105">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server** , and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="e826c-106">Développez successivement Administration de BizTalk Server, **groupe BizTalk**, développez **Applications**, puis développez l’application souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e826c-106">Expand BizTalk Server Administration, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
3.  <span data-ttu-id="e826c-107">Sélectionnez **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="e826c-107">Select **Send Ports**.</span></span> <span data-ttu-id="e826c-108">Dans le volet de détails, cliquez sur le port d’envoi sélectionné et cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e826c-108">In the details pane, right-click the selected send port and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e826c-109">Dans le **propriétés des Ports d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e826c-109">In the **Send Ports Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e826c-110">Sélectionnez le pipeline d’envoi à partir de la **Pipeline d’envoi** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e826c-110">Select the send pipeline from the **Send Pipeline** drop-down list.</span></span>  
  
    2.  <span data-ttu-id="e826c-111">Sélectionnez le pipeline de réception à partir de la **Pipeline de réception** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e826c-111">Select the Receive pipeline from the **Receive Pipeline** drop-down list.</span></span>  
  
5.  <span data-ttu-id="e826c-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e826c-112">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e826c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e826c-113">See Also</span></span>  
 [<span data-ttu-id="e826c-114">Création de gestionnaires de JD Edwards OneWorld envoi</span><span class="sxs-lookup"><span data-stu-id="e826c-114">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)