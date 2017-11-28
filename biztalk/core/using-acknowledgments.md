---
title: "À l’aide des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, publishing
- messages, acknowledgements
- BTS.AckSendPortID property
- BTS.AckSendPortName property
- BTS.AckType property
- BTS.AckFailureCode property
- BTS.AckID property
- acknowledgements, positive
- SOAP fault
- BTS.AckReceivePortID property
- BTS.AckReceivePortName property
- BTS.AckInboundTransportLocation property
- BTS.AckOutboundTransportLocation property
- messages, successful transmission
- BTS.AckDescription property
- orchestrations, messages
- acknowledgements, negative
- BTS.CorrelationToken property
- BTS.AckFailureCategory property
- positive acknowledgements (ACK)
- BTS.AckOwnerID property
ms.assetid: 2e5986d4-9633-4b7b-8ff3-fa3da93c5400
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c3a5363ee70a67c5882088af9fa3d2f4b805823
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-acknowledgments"></a><span data-ttu-id="e0908-102">Utilisation des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="e0908-102">Using Acknowledgments</span></span>
<span data-ttu-id="e0908-103">Le moteur de messagerie BizTalk génère des accusés de réception positifs (ACK) et négatifs (NACK) en réponse aux conditions rencontrées pendant le traitement d'un message via un port.</span><span class="sxs-lookup"><span data-stu-id="e0908-103">The BizTalk Messaging Engine generates positive acknowledgments (ACK) and negative acknowledgments (NACK) in response to conditions encountered during the processing of a message through a port.</span></span> <span data-ttu-id="e0908-104">BizTalk Server émet un accusé de réception positif pour indiquer qu’un message a été correctement transmis et un accusé de réception négatif pour indiquer que la transmission a échoué et que le message est suspendu.</span><span class="sxs-lookup"><span data-stu-id="e0908-104">BizTalk Server publishes a positive acknowledgment to indicate successful transmission of a message and a negative acknowledgment to indicate transmission failure and suspension of a message.</span></span>  
  
## <a name="why-use-acknowledgments"></a><span data-ttu-id="e0908-105">Pourquoi utiliser des accusés de réception ?</span><span class="sxs-lookup"><span data-stu-id="e0908-105">Why Use Acknowledgments?</span></span>  
 <span data-ttu-id="e0908-106">Les accusés de réception positifs et négatifs constituent un important retour d’informations vous permettant de déterminer si un message est arrivé à destination ou s'il a rencontré des problèmes au cours de la transmission.</span><span class="sxs-lookup"><span data-stu-id="e0908-106">Positive and negative acknowledgments provide strong feedback that you can use to determine if a message arrived at its destination or encountered one or more problems along the way.</span></span> <span data-ttu-id="e0908-107">Par exemple, les accusés de réception sont utiles lorsque :</span><span class="sxs-lookup"><span data-stu-id="e0908-107">For example, acknowledgments are useful when:</span></span>  
  
-   <span data-ttu-id="e0908-108">vous souhaitez surveiller un port de réception associé à un nouveau partenaire commercial pour une validation de schéma ou la recherche d'erreurs ;</span><span class="sxs-lookup"><span data-stu-id="e0908-108">You want to monitor a receive port for a new trading partner for schema validation and other errors.</span></span>  
  
-   <span data-ttu-id="e0908-109">vous voulez marquer l'état d’une demande de prêt envoyée pour approbation comme étant « en cours de traitement » si l'envoi à un partenaire pour approbation a abouti ou comme « échec » si la transmission a échoué (par exemple, si le serveur du partenaire est arrêté) ;</span><span class="sxs-lookup"><span data-stu-id="e0908-109">You want to mark the status of a loan request sent out for approval as "in process" if it is successfully sent to a partner for approval or "failed" if transmission fails (for example, if the partner's server is down).</span></span>  
  
-   <span data-ttu-id="e0908-110">vous traitez les échanges contenant plusieurs bons de commande et voulez suivre le nombre de commandes ayant été transmises ou dont la transmission a échoué.</span><span class="sxs-lookup"><span data-stu-id="e0908-110">You process interchanges containing multiple purchase orders and want to track the number of orders that are transmitted or fail transmission.</span></span>  
  
 <span data-ttu-id="e0908-111">Pour réaliser chacun de ces scénarios, vous pouvez vous servir des accusés de réception et du routage basé sur le contenu utilisant des filtres.</span><span class="sxs-lookup"><span data-stu-id="e0908-111">You can accomplish each of these scenarios by using acknowledgments and content-based routing that uses filters.</span></span>  
  
## <a name="routing-acknowledgments"></a><span data-ttu-id="e0908-112">Acheminement des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="e0908-112">Routing Acknowledgments</span></span>  
 <span data-ttu-id="e0908-113">Lorsqu'un ACK ou un NACK est publié, toutes les propriétés de contexte de message provenant du message ayant provoqué l'accusé ACK/NACK sont rétrogradées.</span><span class="sxs-lookup"><span data-stu-id="e0908-113">When an ACK or NACK is published, all of the message context properties from the message that caused the ACK/NACK are demoted.</span></span> <span data-ttu-id="e0908-114">Aucune propriété promue n'est transmise à l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="e0908-114">Any properties that were promoted do not flow to the acknowledgment.</span></span> <span data-ttu-id="e0908-115">Pour acheminer un accusé de réception, créer un filtre utilisant les propriétés suivantes à partir de la **BTS** espace de noms :</span><span class="sxs-lookup"><span data-stu-id="e0908-115">To route an acknowledgment, build a filter using the following properties from the **BTS** namespace:</span></span>  
  
|<span data-ttu-id="e0908-116">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="e0908-116">Property name</span></span>|<span data-ttu-id="e0908-117">Type de données</span><span class="sxs-lookup"><span data-stu-id="e0908-117">Data type</span></span>|<span data-ttu-id="e0908-118"> Description</span><span class="sxs-lookup"><span data-stu-id="e0908-118">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="e0908-119">BTS.AckFailureCategory</span><span class="sxs-lookup"><span data-stu-id="e0908-119">BTS.AckFailureCategory</span></span>|<span data-ttu-id="e0908-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="e0908-120">xs:int</span></span>|<span data-ttu-id="e0908-121">Identifie la **ErrorCategory**, ce qui donne le lieu et la raison de l’interruption.</span><span class="sxs-lookup"><span data-stu-id="e0908-121">Identifies the **ErrorCategory**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="e0908-122">BTS.AckFailureCode</span><span class="sxs-lookup"><span data-stu-id="e0908-122">BTS.AckFailureCode</span></span>|<span data-ttu-id="e0908-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-123">xs:string</span></span>|<span data-ttu-id="e0908-124">Identifie la **ErrorCode**, ce qui donne le lieu et la raison de l’interruption.</span><span class="sxs-lookup"><span data-stu-id="e0908-124">Identifies the **ErrorCode**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="e0908-125">BTS.AckType</span><span class="sxs-lookup"><span data-stu-id="e0908-125">BTS.AckType</span></span>|<span data-ttu-id="e0908-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-126">xs:string</span></span>|<span data-ttu-id="e0908-127">La valeur est ACK pour un accusé de réception positif et NACK pour un accusé de réception négatif.</span><span class="sxs-lookup"><span data-stu-id="e0908-127">Value is ACK for a positive acknowledgment and NACK for a negative acknowledgment.</span></span>|  
|<span data-ttu-id="e0908-128">BTS.AckID</span><span class="sxs-lookup"><span data-stu-id="e0908-128">BTS.AckID</span></span>|<span data-ttu-id="e0908-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-129">xs:string</span></span>|<span data-ttu-id="e0908-130">Identifie la **MessageID** du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-130">Identifies the **MessageID** of the original message.</span></span>|  
|<span data-ttu-id="e0908-131">BTS.AckOwnerID</span><span class="sxs-lookup"><span data-stu-id="e0908-131">BTS.AckOwnerID</span></span>|<span data-ttu-id="e0908-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-132">xs:string</span></span>|<span data-ttu-id="e0908-133">Identifie l'ID d'instance du message d'origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-133">Identifies the instance ID from the original message.</span></span>|  
|<span data-ttu-id="e0908-134">BTS.CorrelationToken</span><span class="sxs-lookup"><span data-stu-id="e0908-134">BTS.CorrelationToken</span></span>|<span data-ttu-id="e0908-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-135">xs:string</span></span>|<span data-ttu-id="e0908-136">Identifie le jeton de corrélation du message d'origine s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="e0908-136">Identifies the correlation token from the original message if one is present.</span></span>|  
|<span data-ttu-id="e0908-137">BTS.AckDescription</span><span class="sxs-lookup"><span data-stu-id="e0908-137">BTS.AckDescription</span></span>|<span data-ttu-id="e0908-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-138">xs:string</span></span>|<span data-ttu-id="e0908-139">Identifie la **ErrorDescription**, ce qui donne le lieu et la raison de l’interruption.</span><span class="sxs-lookup"><span data-stu-id="e0908-139">Identifies the **ErrorDescription**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="e0908-140">BTS.AckSendPortID</span><span class="sxs-lookup"><span data-stu-id="e0908-140">BTS.AckSendPortID</span></span>|<span data-ttu-id="e0908-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-141">xs:string</span></span>|<span data-ttu-id="e0908-142">Identifie la **SendPortID** à partir du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-142">Identifies the **SendPortID** from the original message.</span></span>|  
|<span data-ttu-id="e0908-143">BTS.AckSendPortName</span><span class="sxs-lookup"><span data-stu-id="e0908-143">BTS.AckSendPortName</span></span>|<span data-ttu-id="e0908-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-144">xs:string</span></span>|<span data-ttu-id="e0908-145">Identifie la **SendPortName** à partir du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-145">Identifies the **SendPortName** from the original message.</span></span>|  
|<span data-ttu-id="e0908-146">BTS.AckOutboundTransportLocation</span><span class="sxs-lookup"><span data-stu-id="e0908-146">BTS.AckOutboundTransportLocation</span></span>|<span data-ttu-id="e0908-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-147">xs:string</span></span>|<span data-ttu-id="e0908-148">Identifie la **OutboundTransportLocation** à partir du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-148">Identifies the **OutboundTransportLocation** from the original message.</span></span>|  
|<span data-ttu-id="e0908-149">BTS.AckReceivePortID</span><span class="sxs-lookup"><span data-stu-id="e0908-149">BTS.AckReceivePortID</span></span>|<span data-ttu-id="e0908-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-150">xs:string</span></span>|<span data-ttu-id="e0908-151">Identifie la **ReceivePortID** à partir du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-151">Identifies the **ReceivePortID** from the original message.</span></span>|  
|<span data-ttu-id="e0908-152">BTS.AckReceivePortName</span><span class="sxs-lookup"><span data-stu-id="e0908-152">BTS.AckReceivePortName</span></span>|<span data-ttu-id="e0908-153">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-153">xs:string</span></span>|<span data-ttu-id="e0908-154">Identifie la **ReceivePortName** du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-154">Identifies the **ReceivePortName** from the original message.</span></span>|  
|<span data-ttu-id="e0908-155">BTS.AckInboundTransportLocation</span><span class="sxs-lookup"><span data-stu-id="e0908-155">BTS.AckInboundTransportLocation</span></span>|<span data-ttu-id="e0908-156">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0908-156">xs:string</span></span>|<span data-ttu-id="e0908-157">Identifie la **InboundTransportLocation** du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="e0908-157">Identifies the **InboundTransportLocation** from the original message.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e0908-158">Les propriétés contenant des informations sur l'erreur ne figurent pas dans les accusés ACK, car ces derniers signalent une remise positive.</span><span class="sxs-lookup"><span data-stu-id="e0908-158">The properties that contain error information are not present in ACKs because they signal a positive delivery.</span></span>  
  
## <a name="negative-acknowledgment-message-body"></a><span data-ttu-id="e0908-159">Corps de message d'accusé de réception négatif</span><span class="sxs-lookup"><span data-stu-id="e0908-159">Negative Acknowledgment Message Body</span></span>  
 <span data-ttu-id="e0908-160">Une grande partie des informations importantes concernant l’accusé de réception positif ou négatif figurent dans les propriétés de contexte.</span><span class="sxs-lookup"><span data-stu-id="e0908-160">Much of the important information about a positive or negative acknowledgment is contained in the context properties.</span></span> <span data-ttu-id="e0908-161">Outre les propriétés de contexte, les accusés NACK contiennent également un corps de message comportant une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0908-161">In addition to the context properties, NACKs also contain a message body part containing a SOAP fault.</span></span> <span data-ttu-id="e0908-162">Le format de l’erreur SOAP est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e0908-162">The format of the SOAP fault is as follows:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
  <SOAP:Body>  
    <SOAP:Fault>  
      <faultcode>Microsoft BizTalk Server Negative Acknowledgment </faultcode>  
      <faultstring>An error occurred while processing the message, refer to the details section for more information </faultstring>  
      <faultactor>C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml</faultactor>  
      <detail>  
        <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
          <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
          <ErrorCode>0xc0c01658</ErrorCode>  
          <ErrorCategory>0</ErrorCategory>  
          <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".  </ErrorDescription>  
        </ns0:NACK>  
      </detail>  
    </SOAP:Fault>  
  </SOAP:Body>  
</SOAP:Envelope>  
```  
  
 <span data-ttu-id="e0908-163">Le message d'exception déclenché par l’adaptateur se trouve dans la section relative aux détails SOAP de l'élément ErrorDescription.</span><span class="sxs-lookup"><span data-stu-id="e0908-163">The exception message raised by the adapter is in the SOAP Detail section in the ErrorDescription element.</span></span>  
  
### <a name="accessing-the-message-body-from-an-orchestration"></a><span data-ttu-id="e0908-164">Accès au corps de message à partir d’une orchestration</span><span class="sxs-lookup"><span data-stu-id="e0908-164">Accessing the Message Body from an Orchestration</span></span>  
 <span data-ttu-id="e0908-165">Si un port d'orchestration nécessite un accusé de réception, l'exception DeliveryFailureException émise en cas d'échec de transmission est désérialisée de l'erreur SOAP contenue dans le corps du message NACK.</span><span class="sxs-lookup"><span data-stu-id="e0908-165">If you have an orchestration port that requires delivery notification, the DeliveryFailureException that is thrown on a transmission failure is deserialized from the SOAP fault that is contained in the NACK message body.</span></span> <span data-ttu-id="e0908-166">Pour accéder à la chaîne du message d'exception depuis votre orchestration, convertissez l'exception DeliveryFailureException en une exception SoapException, puis accédez à InnerXml comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e0908-166">To access the exception message string from within your orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml as shown in the following code:</span></span>  
  
```  
// Cast the DeliveryFailureException to a SoapException…  
System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
//e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
//object type created in an Exception handler  
```  
  
 <span data-ttu-id="e0908-167">L'échantillon de code précédent renvoie un fragment XML semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e0908-167">The preceding code sample returns an XML fragment similar to the following:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
  <ErrorCode>0xc0c01658</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".</ErrorDescription>  
</ns0:NACK>  
```  
  
## <a name="when-is-an-acknowledgment-published"></a><span data-ttu-id="e0908-168">À quel moment un accusé de réception est-il publié ?</span><span class="sxs-lookup"><span data-stu-id="e0908-168">When Is an Acknowledgment Published?</span></span>  
 <span data-ttu-id="e0908-169">Les accusés de réception positifs (ACK) et négatifs (NACK) sont publiés dans la base de données MessageBox au moment de l'échec, à condition qu'il existe au moins un abonnement correspondant.</span><span class="sxs-lookup"><span data-stu-id="e0908-169">Both positive (ACK) and negative (NACK) acknowledgments are published to the MessageBox database at the point of failure provided there is at least one matching subscription.</span></span> <span data-ttu-id="e0908-170">Par exemple, si BizTalk Server ne peut pas trouver de schéma correspondant pour un message lu depuis un port de réception, et qu'il n'existe aucun abonnement NACK, le message est suspendu (si le routage des messages ayant échoué n’a pas été activé) et aucun NACK n’est publié.</span><span class="sxs-lookup"><span data-stu-id="e0908-170">For example, if BizTalk Server cannot find a matching schema for a message read from a receive port and there are no NACK subscriptions, it suspends the message (if failed message routing has not been enabled) and does not publish a NACK</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0908-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0908-171">See Also</span></span>  
 <span data-ttu-id="e0908-172">[Gestion des erreurs](../core/error-handling.md) </span><span class="sxs-lookup"><span data-stu-id="e0908-172">[Error Handling](../core/error-handling.md) </span></span>  
 [<span data-ttu-id="e0908-173">À l’aide de routage des messages ayant échoué</span><span class="sxs-lookup"><span data-stu-id="e0908-173">Using Failed Message Routing</span></span>](../core/using-failed-message-routing.md)