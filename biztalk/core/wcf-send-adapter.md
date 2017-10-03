---
title: "Adaptateur d’envoi WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- serializing, SOAP messages
- WCF adapters, extracting information
- messages, extracting information
- SOAP messages, serializing
- WCF adapters, message bodies
- send adapters, WCF adapters
- Web services, headers
- WCF adapters, send adapters
ms.assetid: 226a020a-2e12-41fe-a4a2-6683d9e98219
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70604fbc15f5f15b0a7ff2325debdc28ac3a97c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-send-adapter"></a><span data-ttu-id="a3947-102">adaptateur d'envoi WCF</span><span class="sxs-lookup"><span data-stu-id="a3947-102">WCF Send Adapter</span></span>
<span data-ttu-id="a3947-103">L'adaptateur d'envoi WCF permet d'appeler un service WCF via un contrat sans type.</span><span class="sxs-lookup"><span data-stu-id="a3947-103">The WCF send adapter enables you to call a WCF service through the typeless contract.</span></span>  
  
## <a name="specifying-the-wcf-message-body"></a><span data-ttu-id="a3947-104">Spécification du corps de message WCF</span><span class="sxs-lookup"><span data-stu-id="a3947-104">Specifying the WCF Message Body</span></span>  
 <span data-ttu-id="a3947-105">Le corps de message qui doit être envoyé à partir de BizTalk Server peut être inséré dans le message SOAP à l'aide de l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3947-105">The message body that needs to be sent from BizTalk Server can be inserted into the SOAP message by using one of the following options:</span></span>  
  
-   <span data-ttu-id="a3947-106">Extraire le contenu du corps du message de BizTalk</span><span class="sxs-lookup"><span data-stu-id="a3947-106">Extract the content of the BizTalk message body</span></span>  
  
-   <span data-ttu-id="a3947-107">Spécifier le contenu à l’aide du modèle</span><span class="sxs-lookup"><span data-stu-id="a3947-107">Specify the content by using the template</span></span>  
  
 <span data-ttu-id="a3947-108">Vous pouvez configurer ces options dans la boîte de dialogue des propriétés de transport du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a3947-108">You can configure these options in the send port transport properties dialog box.</span></span>  
  
#### <a name="extract-the-content-of-the-biztalk-message-body"></a><span data-ttu-id="a3947-109">Extraction du contenu du corps de message BizTalk</span><span class="sxs-lookup"><span data-stu-id="a3947-109">Extract the Content of the BizTalk Message Body</span></span>  
 <span data-ttu-id="a3947-110">Lorsque cette option est activée, le contenu du corps de message BizTalk est inséré dans l'élément de corps SOAP du corps du message WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="a3947-110">When this option is selected, the content of the BizTalk message body is inserted into the SOAP Body element for the outbound WCF message body.</span></span>  
  
#### <a name="specify-the-content-by-using-the-template"></a><span data-ttu-id="a3947-111">Spécification du contenu à l'aide du modèle</span><span class="sxs-lookup"><span data-stu-id="a3947-111">Specify the Content by Using the Template</span></span>  
 <span data-ttu-id="a3947-112">Lorsque cette option est activée, le corps de message BizTalk est placé dans l'élément de corps SOAP sous le modèle XML donné pour le corps de message WCF sortant.</span><span class="sxs-lookup"><span data-stu-id="a3947-112">When this option is selected, the BizTalk message body is placed in the SOAP body element under the given XML template for the outbound WCF message body.</span></span>  
  
## <a name="serializing-the-biztalk-message-into-a-soap-message"></a><span data-ttu-id="a3947-113">Sérialisation du message BizTalk en un message SOAP</span><span class="sxs-lookup"><span data-stu-id="a3947-113">Serializing the BizTalk Message into a SOAP Message</span></span>  
 <span data-ttu-id="a3947-114">L'adaptateur d'envoi sérialise le message BizTalk en un message SOAP avant de l'envoyer. Les règles suivantes s'appliquent lors de la sérialisation du message :</span><span class="sxs-lookup"><span data-stu-id="a3947-114">The send adapter serializes the BizTalk message into a SOAP message before sending it out. The following rules apply during serialization of the message:</span></span>  
  
-   <span data-ttu-id="a3947-115">Si le message BizTalk est un message à parties multiples, seul le corps est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a3947-115">If the BizTalk message is a multipart message, then only the body part is used.</span></span>  
  
-   <span data-ttu-id="a3947-116">Si le message BizTalk contient l'ensemble de l'enveloppe SOAP, il est inséré dans une autre enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3947-116">If the BizTalk message contains the entire SOAP envelope, then it is wrapped into another SOAP envelope.</span></span>  
  
-   <span data-ttu-id="a3947-117">Si le message BizTalk contient des données XML arbitraires, il est placé dans l'élément de corps SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3947-117">If the BizTalk message contains arbitrary XML data, then the BizTalk message is placed into the SOAP Body element.</span></span>  
  
## <a name="handling-web-services-headers"></a><span data-ttu-id="a3947-118">Traitement des en-têtes des services Web</span><span class="sxs-lookup"><span data-stu-id="a3947-118">Handling Web Services Headers</span></span>  
 <span data-ttu-id="a3947-119">Lors des opérations d'envoi, BizTalk Server n'a pas le contrôle sur les en-têtes standard des services Web.</span><span class="sxs-lookup"><span data-stu-id="a3947-119">During send operations BizTalk Server does not have control over Web services standard headers.</span></span> <span data-ttu-id="a3947-120">Ceux-ci sont définis et traités par le WCF.</span><span class="sxs-lookup"><span data-stu-id="a3947-120">Those headers are set and processed by the WCF.</span></span> <span data-ttu-id="a3947-121">Le seul en-tête standard qui peut être modifié par l’application BizTalk Server est la **un : Action** en-tête.</span><span class="sxs-lookup"><span data-stu-id="a3947-121">The only standard header that can be modified by the BizTalk Server application is the **a:Action** header.</span></span> <span data-ttu-id="a3947-122">Si la propriété de contexte **Action** est spécifié sur l’espace de noms de carte, l’adaptateur d’envoi WCF utilise la valeur de la propriété pour définir le **Action** sur le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3947-122">If the context property **Action** is specified on the adapter namespace, then the WCF send adapter will use the value of the property to set the **Action** on the SOAP message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3947-123">Dynamique ports d’envoi, si **Action** est spécifié dans le **OutboundHeaders**, la propriété de contexte que vous définissez pour le **WCF. Action** sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="a3947-123">For dynamic send ports, if **Action** is specified in the **OutboundHeaders**, the context property you set for the **WCF.Action** will be ignored.</span></span>  
  
## <a name="specifying-the-btsisdynamicsend-context-property"></a><span data-ttu-id="a3947-124">Spécification de la propriété de contexte BTS.IsDynamicSend</span><span class="sxs-lookup"><span data-stu-id="a3947-124">Specifying the BTS.IsDynamicSend Context Property</span></span>  
 <span data-ttu-id="a3947-125">L'adaptateur d'envoi WCF met en cache la configuration pour les ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a3947-125">The WCF send adapter caches the configuration for send ports.</span></span> <span data-ttu-id="a3947-126">Si le **BTS. IsDynamicSend** est définie sur true, l’envoi WCF adaptateur n’utilise pas la configuration de mise en cache, mais au lieu de cela lit toutes les informations de configuration à partir du message des propriétés de contexte des messages sortants.</span><span class="sxs-lookup"><span data-stu-id="a3947-126">If the **BTS.IsDynamicSend** property is set to true, the WCF send adapter does not use the cached configuration, but instead reads all configuration information from the message context properties of the outbound messages.</span></span> <span data-ttu-id="a3947-127">Sur un port d’envoi statique, WCF adaptateur d’envoi utilise **BTS. SPLastUpdatedTime**, qui est l’heure à laquelle les paramètres de port d’envoi statique de la dernière modification, pour détecter s’il existe toute configuration de port d’envoi modifications sur la méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a3947-127">On a static send port, the WCF send adapter uses **BTS.SPLastUpdatedTime**, which is the time that the static send port settings were last modified, to detect if there are any configuration changes on the static send port.</span></span> <span data-ttu-id="a3947-128">Ainsi, l'adaptateur d'envoi WCF n'a pas besoin de lire tous les paramètres de chaque contexte de message.</span><span class="sxs-lookup"><span data-stu-id="a3947-128">In this way the WCF send adapter does not need to read all of the settings from every message context.</span></span>  
  
 <span data-ttu-id="a3947-129">Si vous souhaitez remplacer les propriétés de port d’envoi statique autre que le **WCF. Action** propriété dans un pipeline d’envoi, vous devez définir le **BTS. IsDynamicSend** propriété la valeur true afin que l’adaptateur d’envoi WCF n’utilise pas de la configuration de mise en cache même si la dernière mise à jour d’horodatage n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="a3947-129">If you want to override the static send port properties other than the **WCF.Action** property in a send pipeline, you need to set the **BTS.IsDynamicSend** property to true so that the WCF send adapter will not use the cached configuration even though the last updated timestamp has not changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3947-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3947-130">See Also</span></span>  
 <span data-ttu-id="a3947-131">[En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="a3947-131">[Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span></span>  
 <span data-ttu-id="a3947-132">[Adaptateur de réception WCF](../core/wcf-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="a3947-132">[WCF Receive Adapter](../core/wcf-receive-adapter.md) </span></span>  
 <span data-ttu-id="a3947-133">[Quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="a3947-133">[What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md) </span></span>  
 [<span data-ttu-id="a3947-134">Comment utiliser les propriétés de contexte de Message</span><span class="sxs-lookup"><span data-stu-id="a3947-134">How to Use Message Context Properties</span></span>](../core/how-to-use-message-context-properties.md)