---
title: "Modèles d’échange pour les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e505559e-66be-4c32-a2a8-a242cba10000
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf8f36bb128d82a6d6b2e143320f89408f26680
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-receive-adapters"></a><span data-ttu-id="db3b8-102">Remplacement des modèles pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="db3b8-102">Exchange Patterns for Receive Adapters</span></span>
<span data-ttu-id="db3b8-103">Les adaptateurs de réception reçoivent les données au « format câble » et les transmettent sous forme de message à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db3b8-103">Receive adapters receive data from the "wire" and submit it as a message into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="db3b8-104">Ce processus de soumission peut se faire sur un modèle d'échange de message unidirectionnel ou bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="db3b8-104">This submittal process can be a one-way or a two-way message exchange pattern.</span></span>  
  
## <a name="one-way-submit"></a><span data-ttu-id="db3b8-105">Soumission unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="db3b8-105">One-Way Submit</span></span>  
 <span data-ttu-id="db3b8-106">Pour pouvoir soumettre un message au moteur de messagerie BizTalk, l'adaptateur de réception doit d'abord créer un message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="db3b8-106">For a receive adapter to submit a message into the BizTalk Messaging Engine, it first needs to create a new BizTalk message.</span></span> <span data-ttu-id="db3b8-107">L'exemple de code de la rubrique relative à l'interface IBaseMessage montre comment cette création se fait.</span><span class="sxs-lookup"><span data-stu-id="db3b8-107">The code sample in the IBaseMessage topic shows how this is done.</span></span> <span data-ttu-id="db3b8-108">Le flux que l'adaptateur définit en tant que corps de message doit être un flux de transmission vers l'avant uniquement. Cela signifie que l'adaptateur ne doit pas mettre en cache les données qu'il vient de lire.</span><span class="sxs-lookup"><span data-stu-id="db3b8-108">The stream that the adapter sets as the message body should typically be a forward-only stream, meaning that it should not cache the data that it has previously read into memory.</span></span>  
  
 <span data-ttu-id="db3b8-109">Avant de l’adaptateur envoie le message au moteur, il doit écrire la **InboundTransportLocation** propriété de contexte dans l’espace de noms système sur le message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="db3b8-109">Before the adapter submits the message into the engine, it must write the **InboundTransportLocation** message context property in the system namespace onto the BizTalk message.</span></span> <span data-ttu-id="db3b8-110">L'extrait de code suivant l'illustre.</span><span class="sxs-lookup"><span data-stu-id="db3b8-110">This is illustrated in the following code fragment:</span></span>  
  
 `Assembly References:`  
  
 `Microsoft.XLANGs.BaseTypes.dll`  
  
 `Microsoft.BizTalk.Pipeline.dll`  
  
 `Microsoft.BizTalk.GlobalPropertySchemas.dll`  
  
```  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.XLANGs.BaseTypes;  
  
private static readonly PropertyBase InboundTransportLocationProp =   
new BTS.InboundTransportLocation();  
  
private void StampMsgCtxProps(  
IBaseMessage msg, string uri, string adapterType)  
{  
msg.Context.Write(  
 InboundTransportLocationProp.Name.Name,   
 InboundTransportLocationProperty.Name.Namespace,   
  uri);  
}  
```  
  
 <span data-ttu-id="db3b8-111">En outre, l'adaptateur peut définir ses propres schémas de propriété et écrire les propriétés de contexte de message associées au point de terminaison par lequel il a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="db3b8-111">In addition, the adapter may define its own property schemas and write message context properties pertaining to the endpoint over which it received the message.</span></span> <span data-ttu-id="db3b8-112">Par exemple, un adaptateur HTTP peut écrire les en-têtes HTTP dans le contexte de message et un récepteur SMTP peut écrire le sujet du message dans le contexte de message.</span><span class="sxs-lookup"><span data-stu-id="db3b8-112">For example, an HTTP adapter might write the HTTP headers to the message context, and an SMTP receiver might write the subject of the mail to the message context.</span></span> <span data-ttu-id="db3b8-113">Ces informations peuvent être utiles pour intercepter en aval des composants tels que des composants de pipeline, des planifications d'orchestration ou un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="db3b8-113">This information may be useful to downstream components such as pipeline components, orchestration schedules, or a send adapter.</span></span>  
  
 <span data-ttu-id="db3b8-114">Une fois les messages préparés, ils peuvent être soumis au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="db3b8-114">After the messages are prepared, they can be submitted into the Messaging Engine.</span></span> <span data-ttu-id="db3b8-115">Pour voir comment un adaptateur de réception unidirectionnel peut envoyer un message au moteur, consultez l’exemple de code [SubmitDirect (exemple BizTalk Server)](../core/submitdirect-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="db3b8-115">To see how a one-way receive adapter might submit a message into the engine, see the code sample [SubmitDirect (BizTalk Server Sample)](../core/submitdirect-biztalk-server-sample.md).</span></span>  
  
## <a name="request-response"></a><span data-ttu-id="db3b8-116">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="db3b8-116">Request-Response</span></span>  
 <span data-ttu-id="db3b8-117">Les adaptateurs de réception bidirectionnels sont généralement utilisés sur des ports de réception unidirectionnels ou bidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="db3b8-117">Two-way receive adapters are typically used on one-way or two-way receive ports.</span></span> <span data-ttu-id="db3b8-118">L'adaptateur détermine si l'emplacement de réception pour lequel il fonctionne est un port unidirectionnel ou bidirectionnel en examinant le jeu de propriétés de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db3b8-118">The adapter determines whether the receive location it is servicing is a one-way or two-way port by inspecting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration property bag.</span></span> <span data-ttu-id="db3b8-119">Ce processus est expliqué dans la **méthode IBTTransportConfig.AddReceiveEndpoint (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="db3b8-119">This process is explained in the **IBTTransportConfig.AddReceiveEndpoint Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="db3b8-120">Le diagramme d'interaction d'objets suivant présente le processus d'échange d'un message de type requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="db3b8-120">The following object interaction diagram illustrates the process of performing a request-response message exchange.</span></span> <span data-ttu-id="db3b8-121">L’adaptateur demande un nouveau lot du proxy de transport et transmet les références à la **IBTTransmitter** interface via le **SubmitRequestMessage** (méthode).</span><span class="sxs-lookup"><span data-stu-id="db3b8-121">The adapter requests a new batch from the transport proxy and passes in its reference to the **IBTTransmitter** interface through the **SubmitRequestMessage** method.</span></span> <span data-ttu-id="db3b8-122">Le moteur de messagerie remet le message de réponse sur cette interface à l’aide de la **TransmitMessage** (méthode).</span><span class="sxs-lookup"><span data-stu-id="db3b8-122">The Messaging Engine delivers the response message on this interface by using the **TransmitMessage** method.</span></span>  
  
 <span data-ttu-id="db3b8-123">Étant donné que le moteur de messagerie traite les messages de façon asynchrone, les configurations suivantes sont possibles :</span><span class="sxs-lookup"><span data-stu-id="db3b8-123">Because the engine is processing messages asynchronously, it is possible for the following to happen:</span></span>  
  
-   <span data-ttu-id="db3b8-124">Le **BatchComplete** rappel peut se produire avant **fait** a retourné.</span><span class="sxs-lookup"><span data-stu-id="db3b8-124">The **BatchComplete** callback might occur before **Done** has returned.</span></span>  
  
-   <span data-ttu-id="db3b8-125">L'appel de la méthode TransmitMessage doit être lancé avant le rappel BatchComplete et le renvoi de Done.</span><span class="sxs-lookup"><span data-stu-id="db3b8-125">The call to TransmitMessage might be made before BatchComplete and even before Done.</span></span>  
  
 <span data-ttu-id="db3b8-126">Bien que ces deux scénarios soient rares, il est préférable de protéger l'adaptateur contre de telles éventualités.</span><span class="sxs-lookup"><span data-stu-id="db3b8-126">While both of these scenarios are rare, the adapter should protect itself against this.</span></span>  
  
 <span data-ttu-id="db3b8-127">Il vaut mieux que le message de réponse soit transmis à l'aide d'un appel asynchrone sans blocage.</span><span class="sxs-lookup"><span data-stu-id="db3b8-127">It is recommended that the response message is transmitted using an asynchronous non-blocking call.</span></span>  
  
 <span data-ttu-id="db3b8-128">Le projet BaseAdapter dispose d’une classe utilitaire, **StandardRequestResponseHandler**, qui encapsule la sémantique de requête-réponse expliquée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="db3b8-128">The BaseAdapter project has a utility class, **StandardRequestResponseHandler**, that encapsulates the request-response semantics explained in this topic.</span></span>  
  
## <a name="request-response-message-time-outs"></a><span data-ttu-id="db3b8-129">Expirations du délai des messages de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="db3b8-129">Request-Response Message Time-Outs</span></span>  
 <span data-ttu-id="db3b8-130">Lorsqu’un adaptateur envoie un message demande-réponse, il doit spécifier le délai d’expiration du message de demande sur le **méthode IBTTransportBatch.SubmitRequestMessage (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="db3b8-130">When an adapter submits a request-request message, it needs to specify the time-out of the request message on the **IBTTransportBatch.SubmitRequestMessage Method (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="db3b8-131">Un message de réponse n'est ensuite remis à l'adaptateur que dans le délai spécifié.</span><span class="sxs-lookup"><span data-stu-id="db3b8-131">A response message will be delivered to the adapter only within this time-out period.</span></span> <span data-ttu-id="db3b8-132">Une fois ce délai expiré, un accusé de réception négatif (NACK) est transmis à l'adaptateur à la place du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="db3b8-132">After the time-out expires, a negative acknowledgment (NACK) will be delivered to the adapter instead of the response message.</span></span> <span data-ttu-id="db3b8-133">Si aucun délai d'expiration n'est indiqué pour l'adaptateur, le moteur de messagerie respecte le délai par défaut qui est de 20 minutes.</span><span class="sxs-lookup"><span data-stu-id="db3b8-133">If the adapter does not specify a time-out value, the engine uses the default value of 20 minutes.</span></span>  
  
 <span data-ttu-id="db3b8-134">Le délai d'expiration par défaut pour les messages de type requête-réponse peut être contrôlé à l'aide de la clé de registre suivante pour les adaptateurs de réception en cours de traitement :</span><span class="sxs-lookup"><span data-stu-id="db3b8-134">The default time-out for request-response messages may be controlled by using the following registry key for in-process receive adapters:</span></span>  
  
 <span data-ttu-id="db3b8-135">**DWORD**</span><span class="sxs-lookup"><span data-stu-id="db3b8-135">**DWORD**</span></span>  
  
 <span data-ttu-id="db3b8-136">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc {Guid hôte} \MessagingReqRespTTL**</span><span class="sxs-lookup"><span data-stu-id="db3b8-136">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingReqRespTTL**</span></span>  
  
 <span data-ttu-id="db3b8-137">La clé de registre se trouve à un emplacement différent pour les adaptateurs de réception isolés :</span><span class="sxs-lookup"><span data-stu-id="db3b8-137">The registry key is in a different location for isolated receive adapters:</span></span>  
  
 <span data-ttu-id="db3b8-138">**DWORD**</span><span class="sxs-lookup"><span data-stu-id="db3b8-138">**DWORD**</span></span>  
  
 <span data-ttu-id="db3b8-139">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**</span><span class="sxs-lookup"><span data-stu-id="db3b8-139">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**</span></span>  
  
 <span data-ttu-id="db3b8-140">Les accusés de réception négatifs sont des erreurs SOAP qu'il est possible de traiter de deux façons.</span><span class="sxs-lookup"><span data-stu-id="db3b8-140">NACKs (Negative ACKnowledgements) are SOAP faults and there are two ways to handle them.</span></span> <span data-ttu-id="db3b8-141">En général, l'adaptateur renvoie l'accusé négatif au client pour qu'il le traite.</span><span class="sxs-lookup"><span data-stu-id="db3b8-141">Typically the adapter returns the NACK to the client and the client handles the NACK.</span></span> <span data-ttu-id="db3b8-142">Sinon, le pipeline de transmission qui traite le message de réponse peut être configuré de manière que le contenu du message de réponse soit modifié à l'aide d'un mappage ou d'un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="db3b8-142">Alternatively the transmit pipeline handling the response message may be configured to change the contents of the response message, by using either a map or a custom pipeline component.</span></span>