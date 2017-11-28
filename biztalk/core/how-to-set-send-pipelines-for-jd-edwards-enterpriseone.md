---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 263f1f5d9441a30687df3e1a7a1170b7bf35e2fc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-send-pipelines-for-jd-edwards-enterpriseone"></a><span data-ttu-id="9d9fe-101">Définition de pipelines d'envoi pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="9d9fe-101">How to Set Send Pipelines for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="9d9fe-102">L’adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert que vous sélectionnez **XMLTransmit** et **XMLReceive** pour l’envoi et les pipelines de réception respectivement.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-102">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne requires that you select **XMLTransmit** and **XMLReceive** for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="9d9fe-103">Pour définir les pipelines</span><span class="sxs-lookup"><span data-stu-id="9d9fe-103">To set pipelines</span></span>  
  
1.  <span data-ttu-id="9d9fe-104">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="9d9fe-105">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="9d9fe-106">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d9fe-106">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="9d9fe-107">Tapez un nom pour le port d’envoi, par exemple, `SendToJDEEnterpriseOne`.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-107">Type a name for the send port, for example, `SendToJDEEnterpriseOne`.</span></span>  
  
    2.  <span data-ttu-id="9d9fe-108">À partir de la **Type** la liste déroulante, sélectionnez **JDE EnterpriseOne**.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-108">From the **Type** drop-down list, select **JDE EnterpriseOne**.</span></span>  
  
    3.  <span data-ttu-id="9d9fe-109">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-109">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="9d9fe-110">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-110">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="9d9fe-111">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-111">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="9d9fe-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d9fe-112">Click **OK**.</span></span>  
  
