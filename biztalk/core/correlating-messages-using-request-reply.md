---
title: "Mise en corrélation des Messages à l’aide de la demande-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MQSeries adapters
- messages, correlating
- MQSeries adapters, correlating messages
ms.assetid: 4615b586-663b-41d8-949c-fefb6143c590
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f13d8dea9192e982f597311ca3ea13fa213ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-messages-using-request-reply"></a><span data-ttu-id="38780-102">Corrélation de messages dans un scénario de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="38780-102">Correlating Messages Using Request-Reply</span></span>
<span data-ttu-id="38780-103">Les messages peuvent être corrélés de deux manières dans les orchestrations BizTalk pour le composant IBM WebSphere MQ Server dans les scénarios de requête-réponse de plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="38780-103">There are two ways to correlate messages in BizTalk orchestrations for IBM WebSphere MQ, server component for Windows platforms request-reply scenarios.</span></span> <span data-ttu-id="38780-104">La première consiste à fournir l’identificateur de corrélation en définissant l’identificateur de message (**MQMD_MSGID**) et l’identificateur de corrélation (**MQMD_CorrelId**) sur la même valeur.</span><span class="sxs-lookup"><span data-stu-id="38780-104">The first is to supply the correlation identifier by setting both the MessageID (**MQMD_MSGID**) and the CorrelationID (**MQMD_CorrelId**) to the same value.</span></span> <span data-ttu-id="38780-105">La seconde consiste à utiliser le **BizTalk_CorrelationId** propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="38780-105">The second is to use the **BizTalk_CorrelationId** context property.</span></span>  
  
## <a name="setting-mqmdmsgid-and-mqmdcorrelid-to-the-same-value"></a><span data-ttu-id="38780-106">Définition de MQMD_MsgId et MQMD_CorrelId sur la même valeur</span><span class="sxs-lookup"><span data-stu-id="38780-106">Setting MQMD_MsgId and MQMD_CorrelId to the Same value</span></span>  
 <span data-ttu-id="38780-107">Lorsque vous envoyez le message à un gestionnaire de file d’attente IBM WebSphere MQ, vous pouvez définir l’identificateur de message (**MQMD_MSGID**) et l’identificateur de corrélation (**MQMD_CorrelId**) sur la même valeur dans le message sortant .</span><span class="sxs-lookup"><span data-stu-id="38780-107">When sending the message to an IBM WebSphere MQ Queue Manager, you can set the message identifier (**MQMD_MSGID**) and the correlation identifier (**MQMD_CorrelId**) to the same value in the outgoing message.</span></span> <span data-ttu-id="38780-108">Le gestionnaire de file d'attente IBM WebSphere MQ copie l'identificateur de message dans l'identificateur de corrélation pour le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="38780-108">The IBM WebSphere MQ Queue Manager copies the MessageID to the CorrelationID for the reply message.</span></span> <span data-ttu-id="38780-109">La figure suivante illustre le processus.</span><span class="sxs-lookup"><span data-stu-id="38780-109">The following figure shows the process.</span></span>  
  
 <span data-ttu-id="38780-110">![Corrélation simple](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")</span><span class="sxs-lookup"><span data-stu-id="38780-110">![Simple Correlation](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")</span></span>  
  
 <span data-ttu-id="38780-111">Vous pouvez initialiser les ensembles de corrélations pour le message sortant et suivre les ensembles de corrélations pour le message entrant à l’aide de la valeur de **MQMD_CorrelId**.</span><span class="sxs-lookup"><span data-stu-id="38780-111">You can initialize the correlation sets for the outgoing message and follow the correlation sets for the incoming message using the value of **MQMD_CorrelId**.</span></span>  
  
## <a name="using-the-mqseriesbiztalkcorrelationid-context-property"></a><span data-ttu-id="38780-112">Utilisation de la propriété de contexte MQSeries.BizTalk_CorrelationId</span><span class="sxs-lookup"><span data-stu-id="38780-112">Using the MQSeries.BizTalk_CorrelationId Context Property</span></span>  
 <span data-ttu-id="38780-113">Au lieu de définir le message et corrélation sur la même valeur dans le message sortant, vous pouvez utiliser la **BizTalk_CorrelationID** port de l’adaptateur MQSeries d’envoi de propriété de contexte avec une sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="38780-113">Instead of setting the MessageID and CorrelationID to the same value in the outgoing message, you can use the **BizTalk_CorrelationID** context property with a solicit-response send port of the MQSeries adapter.</span></span> <span data-ttu-id="38780-114">Ce processus est représenté dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="38780-114">The following figure shows this process.</span></span>  
  
 <span data-ttu-id="38780-115">![À l’aide de sollicitation &#45; Réponse pour générer CorrelationID](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")</span><span class="sxs-lookup"><span data-stu-id="38780-115">![Using Solicit&#45;Response to generate CorrelationID](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")</span></span>  
  
 <span data-ttu-id="38780-116">Pour utiliser les identificateurs fournis par IBM WebSphere MQ Server pour les corrélations dans votre orchestration BizTalk, BizTalk Server doit d'abord obtenir l'identificateur.</span><span class="sxs-lookup"><span data-stu-id="38780-116">To use identifiers provided by IBM WebSphere MQ Server for correlations in your BizTalk orchestration, BizTalk Server must first obtain the identifier.</span></span> <span data-ttu-id="38780-117">Pour ce faire, votre application utilise une demande de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="38780-117">Your application does this through a solicit-response request.</span></span> <span data-ttu-id="38780-118">BizTalk Server envoie une demande de sollicitation-réponse au serveur IBM WebSphere MQ Server à l'aide de l'adaptateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="38780-118">BizTalk Server sends a solicit-response request to the IBM WebSphere MQ Server by using the MQSeries adapter.</span></span> <span data-ttu-id="38780-119">En retour, il reçoit une réponse avec l’identificateur de message (**MQMD_MSGId**) et l’identificateur de corrélation (**MQMD_CorrelId**).</span><span class="sxs-lookup"><span data-stu-id="38780-119">In return, it receives a response with the message identifier (**MQMD_MSGId**) and the correlation identifier (**MQMD_CorrelId**).</span></span>  
  
 <span data-ttu-id="38780-120">Pour le message sortant dans un port d’envoi de sollicitation-réponse, l’adaptateur copie le **MQMD_MSGID** généré par IBM WebSphere MQ Server dans le **MQSeries.BizTalk_CorrelationId** propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="38780-120">For the outgoing message in a solicit-response send port, the adapter copies the **MQMD_MSGID** generated by IBM WebSphere MQ Server to the **MQSeries.BizTalk_CorrelationId** context property.</span></span>  
  
 <span data-ttu-id="38780-121">Lors de la réception des messages, l’adaptateur copie le **MQMD_CorrelId** à la **MQSeries.BizTalk_CorrelationId**.</span><span class="sxs-lookup"><span data-stu-id="38780-121">When receiving messages, the adapter copies the **MQMD_CorrelId** to the **MQSeries.BizTalk_CorrelationId**.</span></span> <span data-ttu-id="38780-122">Dans ce cas, à l’aide des ensembles de corrélations, vous pouvez initialiser les ensembles de corrélations pour le message sortant et suivre les ensembles de corrélations pour le message entrant à l’aide du **MQSeries.BizTalk_CorrelationId**.</span><span class="sxs-lookup"><span data-stu-id="38780-122">In this case, using correlation sets, you can initialize the correlation sets for the outgoing message and follow the correlation sets for the incoming message using the **MQSeries.BizTalk_CorrelationId**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38780-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38780-123">See Also</span></span>  
 [<span data-ttu-id="38780-124">MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="38780-124">MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample)</span></span>](../core/mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample.md)