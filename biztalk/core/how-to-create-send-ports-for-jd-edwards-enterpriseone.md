---
title: "Comment créer des Ports d’envoi pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send ports
- send ports, creating [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], send ports
- send ports, JD Edwards EnterpriseOne adapters
- creating, send ports [JD Edwards EnterpriseOne adapters]
ms.assetid: 687f9207-ad3e-41ea-8640-5b9b6efbc14e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a3e8d2d3e8e1db230a03d9c4a0351d3a0f8394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a><span data-ttu-id="a7032-102">Création de ports d'envoi pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="a7032-102">How to Create Send Ports for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="a7032-103">À l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a7032-103">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="a7032-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="a7032-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="a7032-105">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a7032-105">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a7032-106">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a7032-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="a7032-107">Avec le bouton droit **Ports d’envoi** et cliquez sur **nouveau**, puis cliquez sur **Port statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="a7032-107">Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.</span></span>  
  
4.  <span data-ttu-id="a7032-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a7032-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    -   <span data-ttu-id="a7032-109">Dans le **nom** , tapez le nom du port d’envoi (par exemple, `SendToJDE`).</span><span class="sxs-lookup"><span data-stu-id="a7032-109">In the **Name** box, type a send port name (for example, `SendToJDE`).</span></span>  
  
    -   <span data-ttu-id="a7032-110">À partir de la **Type** la liste déroulante, sélectionnez **JDEdwards**.</span><span class="sxs-lookup"><span data-stu-id="a7032-110">From the **Type** drop-down list, select **JDEdwards**.</span></span>  
  
    -   <span data-ttu-id="a7032-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’adresse du Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a7032-111">From the **Send handler** drop-down list, select the send handler address.</span></span>  
  
5.  <span data-ttu-id="a7032-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7032-112">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7032-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7032-113">See Also</span></span>  
 [<span data-ttu-id="a7032-114">Création de gestionnaires d’envoi de EnterpriseOne JD Edwards</span><span class="sxs-lookup"><span data-stu-id="a7032-114">Creating JD Edwards EnterpriseOne Send Handlers</span></span>](../core/creating-jd-edwards-enterpriseone-send-handlers.md)