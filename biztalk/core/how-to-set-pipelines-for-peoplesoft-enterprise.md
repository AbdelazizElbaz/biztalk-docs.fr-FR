---
title: "La définition de Pipelines pour PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting pipelines
- pipelines, setting
ms.assetid: 36914615-eac0-47b6-9e66-deeb40d21f10
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69bebce2dadf0bb038b0e8c56ffa544ad02c78ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-pipelines-for-peoplesoft-enterprise"></a><span data-ttu-id="fa1a9-102">Définition de pipelines pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="fa1a9-102">How to Set Pipelines for PeopleSoft Enterprise</span></span>
<span data-ttu-id="fa1a9-103">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise requiert la sélection d'un pipeline approprié.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise requires that you select an appropriate pipeline.</span></span>  
  
## <a name="setting-pipelines"></a><span data-ttu-id="fa1a9-104">Configuration des pipelines</span><span class="sxs-lookup"><span data-stu-id="fa1a9-104">Setting Pipelines</span></span>  
  
#### <a name="to-set-pipelines"></a><span data-ttu-id="fa1a9-105">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="fa1a9-105">To set pipelines</span></span>  
  
1.  <span data-ttu-id="fa1a9-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="fa1a9-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="fa1a9-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fa1a9-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="fa1a9-109">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-109">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="fa1a9-110">À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-110">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="fa1a9-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="fa1a9-112">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="fa1a9-113">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="fa1a9-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fa1a9-114">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1a9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa1a9-115">See Also</span></span>  
 [<span data-ttu-id="fa1a9-116">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="fa1a9-116">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)