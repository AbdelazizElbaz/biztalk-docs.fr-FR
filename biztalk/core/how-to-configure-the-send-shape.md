---
title: Comment configurer la forme envoi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Send shape [Orchestration Designer], delivery notification
- send ports, delivery notifications
- configuring [Orchestration Designer], Send shapes
- Send shape [Orchestration Designer], configuring
- delivery notification
- messages, delivery notification
ms.assetid: 2cf4755b-1cfc-484e-bd9c-c9f3855af556
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c32711b841b915d793e5c8a22ffe9513e2ec28d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-send-shape"></a><span data-ttu-id="79413-102">Configuration de la forme Envoi</span><span class="sxs-lookup"><span data-stu-id="79413-102">How to Configure the Send Shape</span></span>
![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")  
<span data-ttu-id="79413-103">Forme Envoi</span><span class="sxs-lookup"><span data-stu-id="79413-103">Send shape</span></span>  
  
 <span data-ttu-id="79413-104">Si vous vous attendez à recevoir une réponse indirecte ou asynchrone au message envoyé (sans passer par un port de requête-réponse), vous devez mettre le message en corrélation avec l'instance d'orchestration en cours d'exécution, afin que la réponse puisse être dirigée vers l'instance appropriée.</span><span class="sxs-lookup"><span data-stu-id="79413-104">If you expect to receive an indirect or asynchronous response (not using a request-response port) to the message that you have sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance.</span></span> <span data-ttu-id="79413-105">Vous pouvez appliquer un suivant ensemble de corrélations pour le **envoyer** forme pour une corrélation précédemment initialisée, ou vous pouvez appliquer un ensemble de corrélations initial.</span><span class="sxs-lookup"><span data-stu-id="79413-105">You can apply a following correlation set to the **Send** shape for a previously initialized correlation, or you can apply an initializing correlation set.</span></span> <span data-ttu-id="79413-106">Pour plus d’informations, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="79413-106">For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).</span></span>  
  
### <a name="to-configure-a-send-shape"></a><span data-ttu-id="79413-107">Pour configurer une forme Envoi</span><span class="sxs-lookup"><span data-stu-id="79413-107">To configure a Send shape</span></span>  
  
1.  <span data-ttu-id="79413-108">Définissez un message et une opération de port.</span><span class="sxs-lookup"><span data-stu-id="79413-108">Set a message and a port operation.</span></span>  
  
    1.  <span data-ttu-id="79413-109">Dans la fenêtre Vue Orchestration, vérifiez que votre orchestration comporte à la fois un message et une opération de port définis pour le type de message à parties multiples envoyé.</span><span class="sxs-lookup"><span data-stu-id="79413-109">In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the multi-part message type being sent.</span></span>  
  
    2.  <span data-ttu-id="79413-110">Dans la fenêtre Propriétés, sélectionnez le message à envoyer à partir de la **Message** liste de propriétés de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="79413-110">In the Properties window, select the message to send from the **Message** property drop-down list.</span></span>  
  
    3.  <span data-ttu-id="79413-111">Dans la fenêtre Propriétés, sélectionnez l’opération de port qui envoie le message à partir de la **opération de Port** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="79413-111">In the Properties window, select the port operation that sends the message from the **Port Operation** drop-down list.</span></span>  
  
         <span data-ttu-id="79413-112">— Ou :</span><span class="sxs-lookup"><span data-stu-id="79413-112">—Or—</span></span>  
  
         <span data-ttu-id="79413-113">Faites glisser le connecteur d’envoi à partir de la **envoyer** forme pour le socket de port qui envoie le message.</span><span class="sxs-lookup"><span data-stu-id="79413-113">Drag the send connector from the **Send** shape to the port socket that sends the message.</span></span>  
  
2.  <span data-ttu-id="79413-114">Spécifier les ensembles de corrélations pour limiter les messages le **envoyer** forme enverra ou pour initialiser les valeurs dans un ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="79413-114">Specify correlation sets to restrict the messages the **Send** shape will send or to initialize the values in a correlation set.</span></span>  
  
    1.  <span data-ttu-id="79413-115">Pour chaque ensemble de corrélations que vous souhaitez utiliser, vérifiez une corrélation défini dans la liste déroulante sur le **ensembles de corrélations suivants** propriété.</span><span class="sxs-lookup"><span data-stu-id="79413-115">For each correlation set you want to use, check a correlation set from the drop-down on the **Following Correlation Sets** property.</span></span>  
  
    2.  <span data-ttu-id="79413-116">Pour chaque correspondance de jeu que vous souhaitez initialiser, vérifiez une corrélation défini dans la liste déroulante sur le **l’initialisation des ensembles de corrélations** propriété.</span><span class="sxs-lookup"><span data-stu-id="79413-116">For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.</span></span>  
  
## <a name="delivery-notification"></a><span data-ttu-id="79413-117">Accusé de réception</span><span class="sxs-lookup"><span data-stu-id="79413-117">Delivery Notification</span></span>  
 <span data-ttu-id="79413-118">Pour vérifier qu'un message a été envoyé correctement sur un port d'envoi, procédez selon les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="79413-118">To test whether you have successfully sent a message over a send port, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="79413-119">Placez votre forme Envoi dans une étendue non transactionnelle, à long terme ou atomique.</span><span class="sxs-lookup"><span data-stu-id="79413-119">Put your Send shape in a non-transactional, long-running or atomic scope.</span></span>  
  
2.  <span data-ttu-id="79413-120">Sur votre port d’envoi, définissez la propriété accusé de réception **transmis**.</span><span class="sxs-lookup"><span data-stu-id="79413-120">On your send port, set the DeliveryNotification property to **Transmitted**.</span></span>  
  
3.  <span data-ttu-id="79413-121">Ajoutez un gestionnaire catch à votre étendue pour gérer une exception DeliveryFailureException.</span><span class="sxs-lookup"><span data-stu-id="79413-121">Add a catch handler to your scope to handle a DeliveryFailureException.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79413-122">Si la forme envoi est contenue dans une étendue atomique, l’exception DeliveryFailureException peut toujours être interceptée, mais nécessite une forme étendue externe être ajoutés à un Type de Transaction que la valeur **Long terme** ou **aucun** .</span><span class="sxs-lookup"><span data-stu-id="79413-122">If the Send shape is contained within an atomic scope, the DeliveryFailureException can still be caught, but will require an outer scope shape be added with a Transaction Type set to **Long Running** or **None**.</span></span> <span data-ttu-id="79413-123">Les étendues atomiques ne sont pas en mesure d’intercepter les exceptions directement.</span><span class="sxs-lookup"><span data-stu-id="79413-123">Atomic scopes are not able to catch exceptions directly.</span></span>  
  
 <span data-ttu-id="79413-124">L’orchestration attend l’accusé de réception à la fin de l'étendue non atomique associée, ou à la fin de l'orchestration, pour recevoir l’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="79413-124">The orchestration waits for acknowledgment at the end of the enclosing non-atomic scope, or the end of the orchestration, to receive the acknowledgment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79413-125">Cela s'applique uniquement aux opérations unidirectionnelles ; un échec dans une opération bidirectionnelle (requête-réponse) donne lieu à une exception SoapException (accusé de réception négatif) même sans qu'un attribut de port ne soit défini.</span><span class="sxs-lookup"><span data-stu-id="79413-125">This applies only to one-way operations; failure in two-way (request-response) operations results in a SoapException (negative acknowledgement) even without the port attribute being set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79413-126">L'accusé de réception n'est pas pris en charge pour la liaison directe.</span><span class="sxs-lookup"><span data-stu-id="79413-126">Delivery notification is not supported for direct binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79413-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79413-127">See Also</span></span>  
 [<span data-ttu-id="79413-128">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="79413-128">Error Handling</span></span>](../core/error-handling.md)