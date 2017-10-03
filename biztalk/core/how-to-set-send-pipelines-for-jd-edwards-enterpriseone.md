---
title: "Comment configurer l’envoi de Pipelines pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send pipelines
- send pipelines, configuring [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], configuring
- adapters [JD Edwards EnterpriseOne adapters], send pipelines
- JD Edwards EnterpriseOne adapters, configuring
ms.assetid: 4cfcecc1-febe-47c8-b75f-2b84defcdbbc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c9a6337195c8050afca1f12a015ec492db7f7ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-jd-edwards-enterpriseone"></a><span data-ttu-id="cb3d6-102">Définition de pipelines d'envoi pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="cb3d6-102">How to Set Send Pipelines for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="cb3d6-103">L’adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert que vous sélectionnez **XMLTransmit** et **XMLReceive** pour l’envoi et les pipelines de réception respectivement.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne requires that you select **XMLTransmit** and **XMLReceive** for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="cb3d6-104">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="cb3d6-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="cb3d6-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="cb3d6-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="cb3d6-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="cb3d6-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="cb3d6-108">Tapez un nom pour le port d’envoi, par exemple, `SendToJDEEnterpriseOne`.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-108">Type a name for the send port, for example, `SendToJDEEnterpriseOne`.</span></span>  
  
    2.  <span data-ttu-id="cb3d6-109">À partir de la **Type** la liste déroulante, sélectionnez **JDE EnterpriseOne**.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-109">From the **Type** drop-down list, select **JDE EnterpriseOne**.</span></span>  
  
    3.  <span data-ttu-id="cb3d6-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="cb3d6-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="cb3d6-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="cb3d6-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb3d6-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb3d6-114">See Also</span></span>  
 [<span data-ttu-id="cb3d6-115">Création de gestionnaires d’envoi de EnterpriseOne JD Edwards</span><span class="sxs-lookup"><span data-stu-id="cb3d6-115">Creating JD Edwards EnterpriseOne Send Handlers</span></span>](../core/creating-jd-edwards-enterpriseone-send-handlers.md)