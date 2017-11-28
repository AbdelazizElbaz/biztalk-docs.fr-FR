---
title: "Opérations de l’adaptateur d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4e0430-e3dc-4884-8411-bbcb579bd21e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444cf4ab7958b0d44838a8331b4b9e6a467baedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-adapter-operations"></a><span data-ttu-id="16060-102">Opérations de l'adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="16060-102">Send Adapter Operations</span></span>
<span data-ttu-id="16060-103">Les adaptateurs d'envoi peuvent effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="16060-103">Send adapters can perform the following operations:</span></span>  
  
-   <span data-ttu-id="16060-104">**Soumettez à nouveau : annulation de renvoi (IBaseMessage msg, DateTime timeStamp).**</span><span class="sxs-lookup"><span data-stu-id="16060-104">**Resubmit: void Resubmit(IBaseMessage msg, DateTime timeStamp).**</span></span> <span data-ttu-id="16060-105">Après un échec de transmission d'un message, l'adaptateur le renvoie s'il y a lieu.</span><span class="sxs-lookup"><span data-stu-id="16060-105">After a transmission failure occurs on a message, an adapter resubmits it when appropriate.</span></span> <span data-ttu-id="16060-106">Il s'agit d'une base par message.</span><span class="sxs-lookup"><span data-stu-id="16060-106">This is called on a per-message basis.</span></span> <span data-ttu-id="16060-107">Si un lot de messages a été envoyé sans succès, l’adaptateur doit déterminer les messages à l’origine de l’échec et renvoie ceux qui n’a pas provoqué d’échec dans des appels séparés à **renvoyer**.</span><span class="sxs-lookup"><span data-stu-id="16060-107">If a batch of messages was submitted unsuccessfully, the adapter must determine the messages causing the failure, and resubmit the ones that did not cause the batch to fail in separate calls to **Resubmit**.</span></span> <span data-ttu-id="16060-108">Il existe plus d’informations sur la façon de conserver les valeurs de propriété de contexte de message lorsque vous appelez à la fin de cette rubrique **renvoyer**.</span><span class="sxs-lookup"><span data-stu-id="16060-108">There is information at the end of this topic about how to preserve message context property values when you call **Resubmit**.</span></span>  
  
-   <span data-ttu-id="16060-109">**Déplacer vers le Transport suivant : void MoveToNextTransport (IBaseMessage msg).**</span><span class="sxs-lookup"><span data-stu-id="16060-109">**Move to Next Transport: void MoveToNextTransport(IBaseMessage msg).**</span></span> <span data-ttu-id="16060-110">Si un message échoue au cours d'un envoi et que le nombre de tentatives de renvois est atteint, l'adaptateur peut envoyer le message au transport configuré suivant pour qu'il soit transmis.</span><span class="sxs-lookup"><span data-stu-id="16060-110">If a message fails during a send operation and its retry attempts have been exhausted, the adapter can send the message to the next configured transport for retransmission.</span></span>  
  
-   <span data-ttu-id="16060-111">**Suspendre : void MoveToSuspendQ (IBaseMessage msg).**</span><span class="sxs-lookup"><span data-stu-id="16060-111">**Suspend: void MoveToSuspendQ(IBaseMessage msg).**</span></span> <span data-ttu-id="16060-112">L'adaptateur déplace un message d'envoi qui a échoué dans la file d'attente des messages interrompus si aucun autre transport secondaire n'est configuré.</span><span class="sxs-lookup"><span data-stu-id="16060-112">The adapter moves a failed send message to the Suspended queue if no additional backup transport is configured.</span></span> <span data-ttu-id="16060-113">Il existe plus d’informations sur la façon de conserver les valeurs de propriété de contexte de message lorsque vous appelez à la fin de cette rubrique **Suspend**.</span><span class="sxs-lookup"><span data-stu-id="16060-113">There is information at the end of this topic about how to preserve message context property values when you call **Suspend**.</span></span>  
  
-   <span data-ttu-id="16060-114">**Suppression : void DeleteMessage (IBaseMessage msg).**</span><span class="sxs-lookup"><span data-stu-id="16060-114">**Delete: void DeleteMessage(IBaseMessage msg).**</span></span> <span data-ttu-id="16060-115">L'adaptateur supprime un message une fois que BizTalk Server l'a informé qu'il a été correctement transmis.</span><span class="sxs-lookup"><span data-stu-id="16060-115">The adapter deletes a message after being notified by BizTalk Server of its successful transmission.</span></span> <span data-ttu-id="16060-116">La suppression d'un message indique à BizTalk Server que l'adaptateur a fini d'utiliser le message.</span><span class="sxs-lookup"><span data-stu-id="16060-116">Deleting a message tells BizTalk Server that the adapter is finished with the message.</span></span> <span data-ttu-id="16060-117">En règle générale le **SubmitResponse** opération est effectuée dans le même lot que qui lui est associée **supprimer** opération.</span><span class="sxs-lookup"><span data-stu-id="16060-117">Generally the **SubmitResponse** operation is done in the same batch as its associated **Delete** operation.</span></span>  
  
-   <span data-ttu-id="16060-118">**Envoyer la réponse : void SubmitResponseMessage (IBaseMessage solicitMsgSent, IBaseMessage responseMsgToSubmit).**</span><span class="sxs-lookup"><span data-stu-id="16060-118">**Submit Response: void SubmitResponseMessage(IBaseMessage solicitMsgSent, IBaseMessage responseMsgToSubmit).**</span></span> <span data-ttu-id="16060-119">L'adaptateur envoie une réponse au lot à renvoyer à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="16060-119">The adapter submits a response to the batch to be sent back to BizTalk Server.</span></span> <span data-ttu-id="16060-120">Cette opération inclut le message d'origine dans l'appel avec la réponse afin que BizTalk Server puisse les mettre en corrélation.</span><span class="sxs-lookup"><span data-stu-id="16060-120">This operation includes the original message in the call along with the response so that BizTalk Server can correlate them.</span></span>  
  
-   <span data-ttu-id="16060-121">**Réponse de l’annuler : void CancelResponseMessages (string correlationToken).**</span><span class="sxs-lookup"><span data-stu-id="16060-121">**Cancel Response: void CancelResponseMessages(string correlationToken).**</span></span> <span data-ttu-id="16060-122">Si l’envoi d’un message de réponse doit être annulé avant que le lot est soumis, la **CancelResponseMessages** méthode est utilisée, transmettant le jeton de corrélation pour le message de réponse associé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="16060-122">If the sending of a response message needs to be canceled before the batch is submitted, the **CancelResponseMessages** method is used, passing in the correlation token for the associated response message to be deleted.</span></span>  
  
 <span data-ttu-id="16060-123">Lors de l’appel **renvoyer** ou **Suspend** sur un message que vous souhaitez conserver les valeurs de certaines propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="16060-123">When calling **Resubmit** or **Suspend** on a message you may want to preserve the values of certain message context properties.</span></span> <span data-ttu-id="16060-124">Vous pouvez enregistrer ces valeurs de propriétés au format XML.</span><span class="sxs-lookup"><span data-stu-id="16060-124">You can do this by saving property values in XML format.</span></span> <span data-ttu-id="16060-125">Lorsque le message est renvoyé ou suspendu, les propriétés correspondantes restent disponibles dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="16060-125">When the message is resubmitted or suspended the corresponding properties remain available in the message context.</span></span>  
  
 <span data-ttu-id="16060-126">La chaîne XML suivante décrit le format auquel les informations sont enregistrées :</span><span class="sxs-lookup"><span data-stu-id="16060-126">The following XML string describes the format in which the information is stored:</span></span>  
  
```  
<PropertiesToUpdate>  
<Property name="StringProperty" nameSpace="http://MyNamespace1" vt="8">SomeString</Property>  
<Property name="IntProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="3">4</Property>  
<Property name="BoolProperty" nameSpace="http://schemas.microsoft.com/BizTalk/2005/test-properties" vt="11">0</Property>  
</PropertiesToUpdate>  
```  
  
 <span data-ttu-id="16060-127">La chaîne XML est générée par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="16060-127">This XML string is generated by the following code:</span></span>  
  
```  
private string GetPropsToUpdateXml(int nextRetryAttempt)  
{  
string result = "<PropertiesToUpdate><Property name=\"RetryAttempts\" nameSpace=\"http://schemas.microsoft.com/BizTalk/2005/test-properties\" vt=\"3\">" + nextRetryAttempt.ToString() + "</Property></PropertiesToUpdate>";  
return result;  
}  
```  
  
 <span data-ttu-id="16060-128">Cette chaîne est ensuite enregistrée dans le contexte du message à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="16060-128">This string is then saved to the message context by using this code:</span></span>  
  
```  
Message.Context.Write("PropertiesToUpdate", "http://schemas.microsoft.com/BizTalk/2003/system-properties", GetPropsToUpdateXml(++retryAttempt));  
```  
  
 <span data-ttu-id="16060-129">Lorsque le message est renvoyé, l'adaptateur peut lire cette propriété à l'aide de la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="16060-129">When the message is resubmitted, the adapter can read this property by using the following line of code:</span></span>  
  
```  
propValue = inmsg.Context.Read("RetryAttempts", "http://schemas.microsoft.com/BizTalk/2005/test-properties");  
```