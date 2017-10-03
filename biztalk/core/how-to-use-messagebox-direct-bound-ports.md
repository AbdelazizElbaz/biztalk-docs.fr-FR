---
title: "Comment utiliser des Ports à liaison directe MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1839184b-408e-4ac6-94a4-a0eb708183f6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fbe52d46847bdaa7caffbb4402ce8d380a73f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-messagebox-direct-bound-ports"></a><span data-ttu-id="e692f-102">Utilisation des ports à liaison directe MessageBox</span><span class="sxs-lookup"><span data-stu-id="e692f-102">How to Use MessageBox Direct Bound Ports</span></span>
<span data-ttu-id="e692f-103">Les ports à liaison directe MessageBox vous permettent de laisser des messages directement dans la base de données MessageBox sans destinataire précis, et de vous abonner aux messages qui répondent à certains critères plutôt qu'aux messages provenant d'un expéditeur particulier.</span><span class="sxs-lookup"><span data-stu-id="e692f-103">MessageBox direct bound ports enable you to drop messages directly into the MessageBox database without an explicit recipient, and to subscribe to messages that meet certain criteria rather than messages that come from a particular sender.</span></span>  
  
 <span data-ttu-id="e692f-104">Envoyer un message vers un port à liaison directe MessageBox équivaut à publier le message dans un bus de messages (dans le cas précis, dans la base de données MessageBox).</span><span class="sxs-lookup"><span data-stu-id="e692f-104">Sending a message on a MessageBox direct bound port is equivalent to publishing the message to a message bus—in this case, to the MessageBox database.</span></span> <span data-ttu-id="e692f-105">Il peut y avoir un nombre illimité d'abonnés à un message publié, et si aucun abonné n'est intéressé par un message au moment de sa publication, l'exception « abonnement introuvable » sera générée.</span><span class="sxs-lookup"><span data-stu-id="e692f-105">There can be any number of subscribers for any published message, and if there are no subscribers interested in the message at the time you publish it, a "subscription not found" exception will be thrown.</span></span> <span data-ttu-id="e692f-106">Si vous envoyez un message via un port à liaison directe MessageBox avec un destinataire particulier, n’oubliez pas, il pouvez que vous souhaitez définir des propriétés à des valeurs spécifiques dans le **assignation du Message** forme votre abonné à rechercher.</span><span class="sxs-lookup"><span data-stu-id="e692f-106">If you send a message through a MessageBox direct bound port with a particular recipient in mind, you may want to set properties to particular values in the **Message Assignment** shape for your intended subscriber to look for.</span></span> <span data-ttu-id="e692f-107">Vous pouvez définir les propriétés en fonction des définitions prédéfinies de BizTalk Server ou des définitions de votre choix.</span><span class="sxs-lookup"><span data-stu-id="e692f-107">You can set the properties based on BizTalk Server predefined property definitions or on your own property definitions.</span></span> <span data-ttu-id="e692f-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e692f-108">For example:</span></span>  
  
```  
myMessage(PropertyNamespace.PropertyName) = "My Property")  
```  
  
 <span data-ttu-id="e692f-109">Recevoir un message via un port à liaison directe MessageBox équivaut à s'abonner à un bus de messages avec des critères de filtrage.</span><span class="sxs-lookup"><span data-stu-id="e692f-109">Receiving a message through a MessageBox direct bound port is equivalent to subscribing to a message bus with filter criteria.</span></span> <span data-ttu-id="e692f-110">Les destinataires du message peuvent être tout type de service pouvant s'abonner à des messages, y compris des orchestrations et des ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="e692f-110">Recipients of the message can be any type of service that can subscribe to messages, which includes orchestrations and send ports.</span></span> <span data-ttu-id="e692f-111">Pour une activation **réception** forme l’abonnement est le type de message et l’expression de filtre et pour une forme **réception** forme l’abonnement est le type de message et la corrélation défini.</span><span class="sxs-lookup"><span data-stu-id="e692f-111">For an activating **Receive** shape the subscription is the message type and the filter expression, and for a non-activating **Receive** shape the subscription is the message type and the correlation set.</span></span> <span data-ttu-id="e692f-112">Chaque **réception** forme inclut toujours le type de message dans le cadre de son abonnement.</span><span class="sxs-lookup"><span data-stu-id="e692f-112">Every **Receive** shape always includes the message type as part of its subscription.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e692f-113">Vous devez utiliser une expression de filtre si vous avez une activation **réception** forme réception d’un message de type **System.Xml.XmlDocument** ou **Microsoft.XLANGs.BaseTypes.Any** sur un port à liaison directe avec routage défini par l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="e692f-113">You must use a filter expression if you have an activating **Receive** shape receiving a message of type **System.Xml.XmlDocument** or **Microsoft.XLANGs.BaseTypes.Any** on a direct bound port with subscription-defined routing.</span></span>  
  
 <span data-ttu-id="e692f-114">Si vous ne spécifiez pas de critères de filtre dans l’activation **réception** forme connectée à un port à liaison directe MessageBox, puis l’abonnement doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e692f-114">If you did not specify any filter criteria in the activating **Receive** shape connected to a MessageBox direct bound port, then the subscription will look similar to the following:</span></span>  
  
```  
http://schemas.microsoft.com/BizTalk/2003/system-properties.ReceivePortID == {2F6A80E1-2518-4A69-9C28-401C2DB1CBF6} And  
http://schemas.microsoft.com/BizTalk/2003/system-properties.MessageType == http://MyMessageType  
```  
  
 <span data-ttu-id="e692f-115">Dans l'exemple précédent, le port de réception à liaison directe MessageBox recevra tous les messages correspondant au type de message pour lequel le fonctionnement du port a été configuré.</span><span class="sxs-lookup"><span data-stu-id="e692f-115">In the preceding example, the MessageBox direct bound receive port will receive every message that matches the message type that the port’s operation is configured for.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e692f-116">Lorsque vous utilisez les ports de réception à liaison directe MessageBox, vous devez affiner le filtre autant que possible.</span><span class="sxs-lookup"><span data-stu-id="e692f-116">When using MessageBox direct bound receive ports, you should make the filter as specific as possible.</span></span> <span data-ttu-id="e692f-117">Si le filtre n'est pas suffisamment spécifique, votre orchestration risque de recevoir des messages non désirés.</span><span class="sxs-lookup"><span data-stu-id="e692f-117">If you do not make the filter specific enough, your orchestration may receive unwanted messages.</span></span>  
  
 <span data-ttu-id="e692f-118">Pour configurer un port à liaison directe MessageBox, sélectionnez **routage entre les ports est défini par les expressions de filtre sur les messages entrants dans la base de données de la boîte de Message** dans l’Assistant Configuration du Port.</span><span class="sxs-lookup"><span data-stu-id="e692f-118">To configure a MessageBox direct bound port, select **Routing between ports will be defined by filter expressions on incoming messages in the Message Box database** in the Port Configuration Wizard.</span></span>  
  
 <span data-ttu-id="e692f-119">Pour obtenir un exemple montrant comment utiliser les ports à liaison directe MessageBox, consultez l’exemple SDK « Direct de liaison à la MessageBox Database in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="e692f-119">For an example of how to use MessageBox direct bound ports, see the SDK sample "Direct Binding to the MessageBox Database in Orchestrations" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e692f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e692f-120">See Also</span></span>  
 <span data-ttu-id="e692f-121">[Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md) </span><span class="sxs-lookup"><span data-stu-id="e692f-121">[How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md) </span></span>  
 [<span data-ttu-id="e692f-122">Ports de liaison de l’utilisation directe de Orchestration du partenaire</span><span class="sxs-lookup"><span data-stu-id="e692f-122">How to Use Partner Orchestration Direct Bound Ports</span></span>](../core/how-to-use-partner-orchestration-direct-bound-ports.md)