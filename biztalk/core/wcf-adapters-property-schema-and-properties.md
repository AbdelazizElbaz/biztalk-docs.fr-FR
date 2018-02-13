---
title: "Propriétés et schéma de propriété des adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 02/09/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2093745e-86c0-4276-a7cc-a0187391ca4a
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04bb48f54347eabeb886d91fa245bae18c34de55
ms.sourcegitcommit: 50798e04fdcaf5dce5288aa18608e2a981b162fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="wcf-adapters-property-schema-and-properties"></a><span data-ttu-id="af756-102">Propriétés et schéma de propriété des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="af756-102">WCF Adapters Property Schema and Properties</span></span>
<span data-ttu-id="af756-103">Informations sur les propriétés promues dans le schéma de propriété de l’adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-103">Read about the promoted properties in the WCF adapter property schema.</span></span> <span data-ttu-id="af756-104">Les adaptateurs WCF attribuent des valeurs aux propriétés que vous pouvez utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="af756-104">The WCF adapters assign values to the properties that you can use in your application.</span></span> <span data-ttu-id="af756-105">L'adaptateur WCF offre également un mécanisme permettant d'écrire (mais non de promouvoir) les propriétés personnalisées dans le contexte de message BizTalk et un mécanisme permettant de promouvoir les propriétés personnalisées dans le contexte de message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="af756-105">WCF adapter also provides a mechanism to write but not promote the custom properties to the BizTalk message context, and a mechanism to promote the custom properties to the BizTalk message context.</span></span> <span data-ttu-id="af756-106">Pour plus d’informations, consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="af756-106">For more details, see [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md).</span></span>  

## <a name="promoted-properties"></a><span data-ttu-id="af756-107">Propriétés promues</span><span class="sxs-lookup"><span data-stu-id="af756-107">Promoted properties</span></span>  
<span data-ttu-id="af756-108">**Namespace:** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties</span><span class="sxs-lookup"><span data-stu-id="af756-108">**Namespace:** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties</span></span>  

#### <a name="action"></a><span data-ttu-id="af756-109">Action</span><span class="sxs-lookup"><span data-stu-id="af756-109">Action</span></span>
<span data-ttu-id="af756-110">Spécifiez le **SOAPAction** champ d’en-tête pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="af756-110">Specify the **SOAPAction** header field for outgoing messages.</span></span> <span data-ttu-id="af756-111">Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action.</span><span class="sxs-lookup"><span data-stu-id="af756-111">You can specify this value in two different ways: the single action format and the action mapping format.</span></span> <span data-ttu-id="af756-112">Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1 : le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-112">If you set this property in the single action format—for example, http://contoso.com/Svc/Op1 — the **SOAPAction** header for outgoing messages is always set to the value specified in this property.</span></span>

<span data-ttu-id="af756-113">Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="af756-113">If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property.</span></span> <span data-ttu-id="af756-114">Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise `http://contoso.com/Svc/Op1` pour sortant **SOAPAction** en-tête.</span><span class="sxs-lookup"><span data-stu-id="af756-114">For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses `http://contoso.com/Svc/Op1` for the outgoing **SOAPAction** header.</span></span>

```
<BtsActionMapping>
<Operation Name="Op1" Action="http://contoso.com/Svc/Op1">
<Operation Name="Op2" Action="http://contoso.com/Svc/Op2">
</BtsActionMapping>
```

<span data-ttu-id="af756-115">Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port.</span><span class="sxs-lookup"><span data-stu-id="af756-115">If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port.</span></span> <span data-ttu-id="af756-116">Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="af756-116">If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.</span></span>
<span data-ttu-id="af756-117">Cette propriété est automatiquement promue à partir de messages entrants, avec le format d'action unique.</span><span class="sxs-lookup"><span data-stu-id="af756-117">This property is automatically promoted from incoming messages with the single action format.</span></span>

<span data-ttu-id="af756-118">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-118">Type: String</span></span>  
<span data-ttu-id="af756-119">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-119">Default value: An empty string</span></span>  
<span data-ttu-id="af756-120">S’applique à : WCF tous les adaptateurs d’envoi</span><span class="sxs-lookup"><span data-stu-id="af756-120">Applies to: All WCF send adapters</span></span>

#### <a name="affiliateapplicationname"></a><span data-ttu-id="af756-121">AffiliateApplicationName</span><span class="sxs-lookup"><span data-stu-id="af756-121">AffiliateApplicationName</span></span>
<span data-ttu-id="af756-122">Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="af756-122">Specify the affiliate application to use for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="af756-123">Cette propriété est requise si le **UseSSO** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="af756-123">This property is required if the **UseSSO** property is set to **True**.</span></span> 

<span data-ttu-id="af756-124">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-124">Type: String</span></span>  
<span data-ttu-id="af756-125">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-125">Default value: An empty string</span></span>  
<span data-ttu-id="af756-126">S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-126">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="algorithmsuite"></a><span data-ttu-id="af756-127">AlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="af756-127">AlgorithmSuite</span></span>
<span data-ttu-id="af756-128">Spécifier les algorithmes de chiffrement et Key Wrap du message.</span><span class="sxs-lookup"><span data-stu-id="af756-128">Specify the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="af756-129">Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="af756-129">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>

<span data-ttu-id="af756-130">Pour plus d’informations sur les valeurs applicables pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte de dialogue Propriétés du Transport WCF-NetTcp, envoi, Sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="af756-130">For more information about the applicable values for the **AlgorithmSuite** property, see the **Algorithm suite** property in the **WCF-NetTcp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="af756-131">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-131">Type: String</span></span>  
<span data-ttu-id="af756-132">Valeur par défaut : **Basic256**</span><span class="sxs-lookup"><span data-stu-id="af756-132">Default value: **Basic256**</span></span>  
<span data-ttu-id="af756-133">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-133">Applies to:</span></span> 

- <span data-ttu-id="af756-134">Adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="af756-134">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="af756-135">Adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-135">WCF-NetMsmq adapter</span></span>
- <span data-ttu-id="af756-136">Adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-136">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="af756-137">Adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-137">WCF-WSHttp adapter</span></span>

#### <a name="bindingconfiguration"></a><span data-ttu-id="af756-138">BindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="af756-138">BindingConfiguration</span></span>
<span data-ttu-id="af756-139">Spécifiez une chaîne XML avec la  **\<liaison\>**  élément pour configurer différents types de liaisons prédéfinies fournis par Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="af756-139">Specify an XML string with the **\<binding\>** element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="af756-140">Pour plus d'informations sur la liaison fournie par le système et la liaison personnalisée, consultez les rubriques correspondantes de la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="af756-140">For more information about the system-provided binding and custom binding, see the appropriate topics in See Also.</span></span>

<span data-ttu-id="af756-141">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-141">Example:</span></span>

```
<binding name="wsHttpBinding" transactionFlow="true">
<security><message clientCredentialType="UserName"></security>
</binding>
```

<span data-ttu-id="af756-142">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-142">Type: String</span></span>  
<span data-ttu-id="af756-143">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-143">Default value: An empty string</span></span>  
<span data-ttu-id="af756-144">S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-144">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="bindingtype"></a><span data-ttu-id="af756-145">BindingType</span><span class="sxs-lookup"><span data-stu-id="af756-145">BindingType</span></span>
<span data-ttu-id="af756-146">Spécifiez le type de liaison à utiliser pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="af756-146">Specify the type of the binding to use for the endpoint.</span></span> <span data-ttu-id="af756-147">Pour plus d’informations sur les valeurs applicables pour le **BindingType** propriété, consultez le **Type de liaison** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="af756-147">For more information about the applicable values for the **BindingType** property, see the **Binding Type** property in the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="af756-148">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-148">Type: String</span></span>  
<span data-ttu-id="af756-149">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-149">Default value: An empty string</span></span>  
<span data-ttu-id="af756-150">S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-150">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="clientcertificate"></a><span data-ttu-id="af756-151">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="af756-151">ClientCertificate</span></span>
<span data-ttu-id="af756-152">Spécifiez l'empreinte du certificat X.509 pour l'authentification de ce port d'envoi auprès des services.</span><span class="sxs-lookup"><span data-stu-id="af756-152">Specify the thumbprint of the X.509 certificate for authenticating this send port to services.</span></span> <span data-ttu-id="af756-153">Cette propriété est requise si le **ClientCredentialsType** est définie sur **certificat**.</span><span class="sxs-lookup"><span data-stu-id="af756-153">This property is required if the **ClientCredentialsType** property is set to **Certificate**.</span></span> <span data-ttu-id="af756-154">Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.</span><span class="sxs-lookup"><span data-stu-id="af756-154">The certificate to be used for this property must be installed into the **My** store in the **Current User** location.</span></span>

<span data-ttu-id="af756-155">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-155">Type: String</span></span>  
<span data-ttu-id="af756-156">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-156">Default value: An empty string</span></span>  
<span data-ttu-id="af756-157">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-157">Applies to:</span></span> 

- <span data-ttu-id="af756-158">Adaptateur d'envoi WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="af756-158">WCF-BasicHttp send adapter</span></span>
- <span data-ttu-id="af756-159">Adaptateur d'envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-159">WCF-WSHttp send adapter</span></span>
- <span data-ttu-id="af756-160">Adaptateur d’envoi WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-160">WCF-NetTcp send adapter</span></span>
- <span data-ttu-id="af756-161">Adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-161">WCF-NetMsmq send adapter</span></span>

#### <a name="closetimeout"></a><span data-ttu-id="af756-162">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="af756-162">CloseTimeout</span></span>
<span data-ttu-id="af756-163">Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.</span><span class="sxs-lookup"><span data-stu-id="af756-163">Specify a time span value that indicates the interval of time provided for a channel close operation to complete.</span></span>

<span data-ttu-id="af756-164">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-164">Type: String</span></span>  
<span data-ttu-id="af756-165">Valeur par défaut : 00:01:00</span><span class="sxs-lookup"><span data-stu-id="af756-165">Default value: 00:01:00</span></span>  
<span data-ttu-id="af756-166">S’applique à : tous les adaptateurs WCF *sauf* WCF-Custom et WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-166">Applies to: All WCF adapters *except* WCF-Custom and WCF-CustomIsolated</span></span>

#### <a name="customdeadletterqueue"></a><span data-ttu-id="af756-167">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="af756-167">CustomDeadLetterQueue</span></span>
<span data-ttu-id="af756-168">Spécifiez l’adresse URI complète avec le **net.msmq** schéma pour l’emplacement de la file d’attente de lettres mortes par application, où sont placés les messages qui ont expiré ou dont le transfert ou la remise a échoué.</span><span class="sxs-lookup"><span data-stu-id="af756-168">Specify the fully qualified URI with the **net.msmq** scheme for the location of the per-application dead-letter queue, where messages that have expired or that have failed transfer or delivery are placed.</span></span> <span data-ttu-id="af756-169">Par exemple, net.msmq://localhost/deadLetterQueueName.</span><span class="sxs-lookup"><span data-stu-id="af756-169">For example, net.msmq://localhost/deadLetterQueueName.</span></span> <span data-ttu-id="af756-170">La file d'attente des messages non distribués fait partie du gestionnaire de file d'attente de l'application émettrice. Elle est réservée aux messages expirés n'ayant pu être remis à leur destinataire.</span><span class="sxs-lookup"><span data-stu-id="af756-170">The dead-letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered.</span></span> <span data-ttu-id="af756-171">Cette propriété est requise si le **DeadLetterQueue** est définie sur **personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="af756-171">This property is required if the **DeadLetterQueue** property is set to **Custom**.</span></span>

<span data-ttu-id="af756-172">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-172">Type: String</span></span>  
<span data-ttu-id="af756-173">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-173">Default value: An empty string</span></span>  
<span data-ttu-id="af756-174">S’applique à : adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-174">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="deadletterqueue"></a><span data-ttu-id="af756-175">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="af756-175">DeadLetterQueue</span></span>
<span data-ttu-id="af756-176">Spécifiez la file d'attente des messages non distribués vers laquelle seront transférés les messages qui n'ont pas pu être remis à l'application.</span><span class="sxs-lookup"><span data-stu-id="af756-176">Specify the dead-letter queue where messages that have failed to be delivered to the application will be transferred.</span></span> <span data-ttu-id="af756-177">Pour plus d’informations sur les messages remis à la file d’attente de lettres mortes, consultez le **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="af756-177">For more information about the messages delivered to the dead-letter queue, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="af756-178">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-178">Type: String</span></span>  
<span data-ttu-id="af756-179">Valeur par défaut : **système**</span><span class="sxs-lookup"><span data-stu-id="af756-179">Default value: **System**</span></span>  
<span data-ttu-id="af756-180">S’applique à : adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-180">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="disablelocationonfailure"></a><span data-ttu-id="af756-181">DisableLocationOnFailure</span><span class="sxs-lookup"><span data-stu-id="af756-181">DisableLocationOnFailure</span></span>
<span data-ttu-id="af756-182">Spécifiez s'il faut désactiver l'emplacement de réception pour lequel le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.</span><span class="sxs-lookup"><span data-stu-id="af756-182">Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.</span></span> <span data-ttu-id="af756-183">Souhaité définir cette propriété sur **True** quand recevoir les emplacements peuvent être désactivés et le déni de Service (DoS) n’est pas un problème.</span><span class="sxs-lookup"><span data-stu-id="af756-183">You may want to set this property to **True** when receive locations can be disabled and Denial-of-Service (DoS) is not a concern.</span></span>

<span data-ttu-id="af756-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-184">For example:</span></span>  
- <span data-ttu-id="af756-185">Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **netMsmqBinding**.</span><span class="sxs-lookup"><span data-stu-id="af756-185">WCF-Custom adapter: When the **BindingType** property is set to **netMsmqBinding**.</span></span>
- <span data-ttu-id="af756-186">Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur les transports en file d’attente, tels que MSMQ.</span><span class="sxs-lookup"><span data-stu-id="af756-186">WCF-Custom adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on queued transports such as MSMQ.</span></span>
- <span data-ttu-id="af756-187">Adaptateur WCF-CustomIsolated : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur des transports en file d’attente, tels que MSMQ</span><span class="sxs-lookup"><span data-stu-id="af756-187">WCF-CustomIsolated adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on queued transports such as MSMQ</span></span>
- <span data-ttu-id="af756-188">Adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-188">WCF-NetMsmq adapter</span></span>

<span data-ttu-id="af756-189">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-189">Type: Boolean</span></span>  
<span data-ttu-id="af756-190">Valeur par défaut : **False**</span><span class="sxs-lookup"><span data-stu-id="af756-190">Default: **False**</span></span>  
<span data-ttu-id="af756-191">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-191">Applies to:</span></span>  
- <span data-ttu-id="af756-192">Adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-192">WCF-NetMsmq receive adapter</span></span>
- <span data-ttu-id="af756-193">Adaptateur de réception WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="af756-193">WCF-Custom receive adapter</span></span>
- <span data-ttu-id="af756-194">Adaptateur de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-194">WCF-CustomIsolated receive adapter</span></span>

#### <a name="enabletransaction"></a><span data-ttu-id="af756-195">EnableTransaction</span><span class="sxs-lookup"><span data-stu-id="af756-195">EnableTransaction</span></span>
<span data-ttu-id="af756-196">L'effet de cette propriété varie selon l'adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-196">The effect of this property varies depending on the WCF adapter.</span></span> <span data-ttu-id="af756-197">Pour plus d’informations sur cette propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-197">For more information about this property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="af756-198">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-198">Type: Boolean</span></span>  
<span data-ttu-id="af756-199">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-199">Applies to:</span></span> 

- <span data-ttu-id="af756-200">Adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-200">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="af756-201">Adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-201">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="af756-202">Adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-202">WCF-NetNamedPipe adapter</span></span>
- <span data-ttu-id="af756-203">Adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-203">WCF-NetMsmq adapter</span></span>

#### <a name="endpointbehaviorconfiguration"></a><span data-ttu-id="af756-204">EndpointBehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="af756-204">EndpointBehaviorConfiguration</span></span>
<span data-ttu-id="af756-205">Spécifier une chaîne XML avec la  **\<comportement\>**  élément de la  **\<endpointBehaviors\>**  élément pour configurer les paramètres de comportement d’un Point de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-205">Specify an XML string with the **\<behavior\>** element of the **\<endpointBehaviors\>** element to configure the behavior settings of a WCF endpoint.</span></span> <span data-ttu-id="af756-206">Pour plus d’informations sur la  **\<endpointBehaviors\>**  élément, consultez la rubrique appropriée dans Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="af756-206">For more information about the **\<endpointBehaviors\>** element, see the appropriate topic in See Also.</span></span>

<span data-ttu-id="af756-207">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-207">Example:</span></span> 
```
<behavior name="sampleBehavior"><callbackTimeouts/></behavior>
```

<span data-ttu-id="af756-208">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-208">Type: String</span></span>  
<span data-ttu-id="af756-209">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-209">Default value: An empty string</span></span>  
<span data-ttu-id="af756-210">S’applique à : adaptateur d’envoi WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="af756-210">Applies to: WCF-Custom send adapter</span></span>

#### <a name="establishsecuritycontext"></a><span data-ttu-id="af756-211">EstablishSecurityContext</span><span class="sxs-lookup"><span data-stu-id="af756-211">EstablishSecurityContext</span></span>
<span data-ttu-id="af756-212">Spécifiez si le canal de sécurité établit une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="af756-212">Specify whether the security channel establishes a secure session.</span></span> <span data-ttu-id="af756-213">Une session sécurisée établit un jeton de contexte de sécurité (SCT, Security Context Token) avant d'échanger les messages d'application.</span><span class="sxs-lookup"><span data-stu-id="af756-213">A secure session establishes a Security Context Token (SCT) before exchanging the application messages.</span></span>

<span data-ttu-id="af756-214">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-214">Type: Boolean</span></span>  
<span data-ttu-id="af756-215">Valeur par défaut : True</span><span class="sxs-lookup"><span data-stu-id="af756-215">Default value: True</span></span>  
<span data-ttu-id="af756-216">Appliqué aux : l’adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-216">Applied to: WCF-WSHttp adapter</span></span>

#### <a name="fromaddress"></a><span data-ttu-id="af756-217">FromAddress</span><span class="sxs-lookup"><span data-stu-id="af756-217">FromAddress</span></span>
<span data-ttu-id="af756-218">Indiquez l'adresse du point de terminaison source par le biais duquel les messages WCF entrants sont envoyés.</span><span class="sxs-lookup"><span data-stu-id="af756-218">Indicate the source endpoint address through which the incoming WCF messages are sent.</span></span> <span data-ttu-id="af756-219">La propriété est automatiquement promue à partir de messages entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-219">The property is automatically promoted from incoming messages.</span></span>

<span data-ttu-id="af756-220">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-220">Type: String</span></span>  
<span data-ttu-id="af756-221">S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-221">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>
  
#### <a name="headers"></a><span data-ttu-id="af756-222">En-têtes</span><span class="sxs-lookup"><span data-stu-id="af756-222">Headers</span></span>
<span data-ttu-id="af756-223">Spécifiez les références de point de terminaison utilisées pour fournir des informations d'adressage supplémentaires au-delà de l'URI.</span><span class="sxs-lookup"><span data-stu-id="af756-223">Specify the endpoint references used to provide additional addressing information beyond the URI.</span></span> <span data-ttu-id="af756-224">Lorsque cette propriété est utilisée, cette propriété doit avoir la \< **en-têtes** \> élément comme élément racine.</span><span class="sxs-lookup"><span data-stu-id="af756-224">When this property is used, this property must have the \<**headers**\> element as the root element.</span></span> <span data-ttu-id="af756-225">Tous les en-têtes d’adresse doivent être placé à l’intérieur de la \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="af756-225">All of the address headers must be placed inside the \<**headers**\> element.</span></span> <span data-ttu-id="af756-226">Cette propriété est automatiquement promue pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-226">This property is automatically promoted for incoming messages.</span></span>

<span data-ttu-id="af756-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-227">Example:</span></span>
```
<headers>
<Region xmlns="Uri">"String"</Region>
<Member xmlns="Uri">"String"</Member> 
</headers>
```

<span data-ttu-id="af756-228">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-228">Type: String</span></span>  
<span data-ttu-id="af756-229">S’applique à : tous les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="af756-229">Applies to: All WCF adapters</span></span>
  
#### <a name="identity"></a><span data-ttu-id="af756-230">Identity</span><span class="sxs-lookup"><span data-stu-id="af756-230">Identity</span></span>
<span data-ttu-id="af756-231">Spécifiez l'identité du service fourni par un emplacement de réception ou attendu par un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="af756-231">Specify the identity of the service that a receive location provides or a send port expects.</span></span> <span data-ttu-id="af756-232">Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité.</span><span class="sxs-lookup"><span data-stu-id="af756-232">The values that can be specified for the **Identity** property differ according to the security configuration.</span></span> <span data-ttu-id="af756-233">Ces paramètres permettent aux clients d'authentifier les services.</span><span class="sxs-lookup"><span data-stu-id="af756-233">These settings enable clients to authenticate services.</span></span> <span data-ttu-id="af756-234">Lors du processus d'établissement de liaison entre les clients et les services, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité des services correspond aux valeurs des clients.</span><span class="sxs-lookup"><span data-stu-id="af756-234">In the handshake process between clients and services, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the services matches the values of the clients.</span></span>

<span data-ttu-id="af756-235">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-235">Example:</span></span>
```
<identity>
<userPrincipalName value="username@contoso.com"/>
</identity>
```

<span data-ttu-id="af756-236">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-236">Type: String</span></span>  
<span data-ttu-id="af756-237">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-237">Default value: An empty string</span></span>  
<span data-ttu-id="af756-238">S’applique à : tous les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="af756-238">Applies to: All WCF adapters</span></span>

#### <a name="inboundbodylocation"></a><span data-ttu-id="af756-239">InboundBodyLocation</span><span class="sxs-lookup"><span data-stu-id="af756-239">InboundBodyLocation</span></span>
<span data-ttu-id="af756-240">Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-240">Specify the data selection for the SOAP **Body** element of incoming WCF messages.</span></span> <span data-ttu-id="af756-241">Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-241">For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="af756-242">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-242">Type: String</span></span>  
<span data-ttu-id="af756-243">Valeur par défaut : UseBodyElement</span><span class="sxs-lookup"><span data-stu-id="af756-243">Default value: UseBodyElement</span></span>  

    Applicable values are:  
        - UseBodyElement: Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.
        - UseEnvelope: Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.
        - UseBodyPath: Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.  

<span data-ttu-id="af756-244">S’applique à : tous les adaptateurs WCF *sauf* envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-244">Applies to: All WCF adapters *except* WCF-NetMsmq send</span></span>  

#### <a name="inboundbodypathexpression"></a><span data-ttu-id="af756-245">InboundBodyPathExpression</span><span class="sxs-lookup"><span data-stu-id="af756-245">InboundBodyPathExpression</span></span>
<span data-ttu-id="af756-246">Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="af756-246">Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part.</span></span> <span data-ttu-id="af756-247">Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant.</span><span class="sxs-lookup"><span data-stu-id="af756-247">This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message.</span></span> <span data-ttu-id="af756-248">Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="af756-248">If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part.</span></span> <span data-ttu-id="af756-249">Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.</span><span class="sxs-lookup"><span data-stu-id="af756-249">This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.</span></span> <span data-ttu-id="af756-250">Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).</span><span class="sxs-lookup"><span data-stu-id="af756-250">For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).</span></span>

<span data-ttu-id="af756-251">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-251">Type: String</span></span>  
<span data-ttu-id="af756-252">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-252">Default value: An empty string</span></span>  
<span data-ttu-id="af756-253">S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-253">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="inboundheaders"></a><span data-ttu-id="af756-254">InboundHeaders</span><span class="sxs-lookup"><span data-stu-id="af756-254">InboundHeaders</span></span>
<span data-ttu-id="af756-255">Utilisez le **InboundHeaders** propriété pour accéder aux en-têtes SOAP des messages WCF entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-255">Use the **InboundHeaders** property to access the SOAP headers of incoming WCF messages.</span></span> <span data-ttu-id="af756-256">Les adaptateurs WCF copient toutes les valeurs d'en-tête SOAP des messages entrants dans cette propriété, ce qui inclut les en-têtes SOAP personnalisés et les en-têtes SOAP standard utilisés par l'infrastructure WCF, par exemple, pour WS-Addressing, WS-Security et WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="af756-256">The WCF adapters copy all the SOAP header values in inbound messages to this property, which include custom SOAP headers and standard SOAP headers that the WCF infrastructure uses for such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="af756-257">La valeur contenue dans la propriété de contexte est une chaîne contenant des données XML avec le \< **en-têtes** \> élément racine et les en-têtes SOAP entrants sont copiés comme éléments enfants de la \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="af756-257">The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element.</span></span> <span data-ttu-id="af756-258">Pour plus d’informations sur l’accès aux en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="af756-258">For more information about how to access SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>

<span data-ttu-id="af756-259">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-259">Type: String</span></span>  
<span data-ttu-id="af756-260">S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-260">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="inboundnodeencoding"></a><span data-ttu-id="af756-261">InboundNodeEncoding</span><span class="sxs-lookup"><span data-stu-id="af756-261">InboundNodeEncoding</span></span>
<span data-ttu-id="af756-262">Spécifiez le type de codage que WCF adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**.</span><span class="sxs-lookup"><span data-stu-id="af756-262">Specify the type of encoding that the WCF receive adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**.</span></span> <span data-ttu-id="af756-263">Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.</span><span class="sxs-lookup"><span data-stu-id="af756-263">This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.</span></span>

<span data-ttu-id="af756-264">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-264">Type: String</span></span>  
<span data-ttu-id="af756-265">Valeur par défaut : XML</span><span class="sxs-lookup"><span data-stu-id="af756-265">Default value: XML</span></span>  

    Applicable values are:  
        - Base64: Base64 encoding
        - Hex: Hexadecimal encoding
        - String: Text encoding - UTF-8
        - XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.  

<span data-ttu-id="af756-266">S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-266">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="isfault"></a><span data-ttu-id="af756-267">IsFault</span><span class="sxs-lookup"><span data-stu-id="af756-267">IsFault</span></span>
<span data-ttu-id="af756-268">Indiquez si les messages d'erreur SOAP sont reçus.</span><span class="sxs-lookup"><span data-stu-id="af756-268">Indicate whether SOAP fault messages are received.</span></span> <span data-ttu-id="af756-269">La propriété est automatiquement promue à partir de messages entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-269">The property is automatically promoted from incoming messages.</span></span> 

<span data-ttu-id="af756-270">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-270">**Note**</span></span>  
<span data-ttu-id="af756-271">Le **IsFault** propriété ne peut pas être utilisée pour vérifier les messages reçus pour les erreurs de transport tels que l’erreur HTTP 404 (fichier ou répertoire introuvable).</span><span class="sxs-lookup"><span data-stu-id="af756-271">The **IsFault** property cannot be used to check the received messages for transport errors such as the HTTP 404 (File or Directory Not Found) error.</span></span>

<span data-ttu-id="af756-272">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-272">Type: Boolean</span></span>  
<span data-ttu-id="af756-273">S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-273">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="leasetimeout"></a><span data-ttu-id="af756-274">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="af756-274">LeaseTimeout</span></span>
<span data-ttu-id="af756-275">Spécifiez la durée de vie maximale d'une connexion active placée dans le pool.</span><span class="sxs-lookup"><span data-stu-id="af756-275">Specify the maximum lifetime of an active pooled connection.</span></span> <span data-ttu-id="af756-276">Une fois le temps spécifié écoulé, la connexion est fermée une fois la demande en cours traitée.</span><span class="sxs-lookup"><span data-stu-id="af756-276">After the specified time elapses, the connection closes after the current request is serviced.</span></span>

<span data-ttu-id="af756-277">L’adaptateur WCF-NetTcp tire parti du [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) classe pour communiquer avec un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="af756-277">The WCF-NetTcp adapter leverages the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) class to communicate with an endpoint.</span></span> <span data-ttu-id="af756-278">Lorsque vous utilisez la [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) dans les scénarios de charge équilibrée, réduisez le délai d’expiration du bail par défaut. Pour plus d’informations sur l’équilibrage de charge lorsque vous utilisez la [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087), consultez la rubrique appropriée dans Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="af756-278">When using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) in load-balanced scenarios, consider reducing the default lease time-out. For more information about load balancing when using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087), see the appropriate topic in See Also.</span></span>

<span data-ttu-id="af756-279">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-279">Type: String</span></span>  
<span data-ttu-id="af756-280">Valeur par défaut : 00:05:00</span><span class="sxs-lookup"><span data-stu-id="af756-280">Default value: 00:05:00</span></span>  
<span data-ttu-id="af756-281">S’applique à : adaptateur de réception WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-281">Applies to: WCF-NetTcp receive adapter</span></span>  

#### <a name="maxconcurrentcalls"></a><span data-ttu-id="af756-282">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="af756-282">MaxConcurrentCalls</span></span>
<span data-ttu-id="af756-283">Spécifier le nombre d'appels simultanés par instance de service unique.</span><span class="sxs-lookup"><span data-stu-id="af756-283">Specify the number of concurrent calls to a single service instance.</span></span> <span data-ttu-id="af756-284">Les appels excédentaires sont mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="af756-284">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="af756-285">La définition de cette valeur sur 0 équivaut à la définir sur **Int32.MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="af756-285">Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.</span></span> 

<span data-ttu-id="af756-286">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-286">**Note**</span></span>  
<span data-ttu-id="af756-287">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-287">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="af756-288">Type : entier</span><span class="sxs-lookup"><span data-stu-id="af756-288">Type: Integer</span></span>  
<span data-ttu-id="af756-289">Valeur par défaut : 200</span><span class="sxs-lookup"><span data-stu-id="af756-289">Default value: 200</span></span>  
<span data-ttu-id="af756-290">S’applique à : WCF tous les adaptateurs de réception *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-290">Applies to: All WCF receive adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="maxconnections"></a><span data-ttu-id="af756-291">MaxConnections</span><span class="sxs-lookup"><span data-stu-id="af756-291">MaxConnections</span></span>
<span data-ttu-id="af756-292">Spécifier un nombre maximal de connexions que l’écouteur peut mettre en attente d’acceptation par l’application.</span><span class="sxs-lookup"><span data-stu-id="af756-292">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="af756-293">Lorsque ce quota est dépassé, les nouvelles connexions entrantes sont interrompues plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="af756-293">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> 

<span data-ttu-id="af756-294">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-294">**Note**</span></span>  
<span data-ttu-id="af756-295">Comme il s'agit d'une propriété du gestionnaire d'adaptateur, elle ne peut pas être configurée dans les composants de pipeline et les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="af756-295">Because this is an adapter handler property, this property cannot be configured in pipeline components and orchestrations.</span></span> 

<span data-ttu-id="af756-296">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-296">**Note**</span></span>  
<span data-ttu-id="af756-297">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-297">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="af756-298">Type : entier</span><span class="sxs-lookup"><span data-stu-id="af756-298">Type: Integer</span></span>  
<span data-ttu-id="af756-299">Valeur par défaut : 10</span><span class="sxs-lookup"><span data-stu-id="af756-299">Default value: 10</span></span>  
<span data-ttu-id="af756-300">S’applique à : l’adaptateur WCF-NetNamedPipe, l’adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-300">Applies to: WCF-NetNamedPipe adapter, WCF-NetTcp adapter</span></span>  

#### <a name="maxreceivedmessagesize"></a><span data-ttu-id="af756-301">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="af756-301">MaxReceivedMessageSize</span></span>
<span data-ttu-id="af756-302">Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble.</span><span class="sxs-lookup"><span data-stu-id="af756-302">Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire.</span></span> <span data-ttu-id="af756-303">La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux.</span><span class="sxs-lookup"><span data-stu-id="af756-303">The size of the messages is bounded by the amount of memory allocated for each message.</span></span> <span data-ttu-id="af756-304">Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.</span><span class="sxs-lookup"><span data-stu-id="af756-304">You can use this property to limit exposure to denial of service (DoS) attacks.</span></span>

<span data-ttu-id="af756-305">Type : entier</span><span class="sxs-lookup"><span data-stu-id="af756-305">Type: Integer</span></span>  
<span data-ttu-id="af756-306">Valeur par défaut : 65536</span><span class="sxs-lookup"><span data-stu-id="af756-306">Default value: 65536</span></span>  
<span data-ttu-id="af756-307">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-307">Applies to:</span></span> 
- <span data-ttu-id="af756-308">Adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="af756-308">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="af756-309">Adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-309">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="af756-310">Adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-310">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="af756-311">Adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-311">WCF-NetNamedPipe adapter</span></span>
- <span data-ttu-id="af756-312">Adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-312">WCF-NetMsmq receive adapter</span></span>

#### <a name="messageclientcredentialtype"></a><span data-ttu-id="af756-313">MessageClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="af756-313">MessageClientCredentialType</span></span>
<span data-ttu-id="af756-314">Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.</span><span class="sxs-lookup"><span data-stu-id="af756-314">Specify the type of credential to be used when performing client authentication using message-based security.</span></span>

<span data-ttu-id="af756-315">Les valeurs applicables diffèrent pour chaque adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-315">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="af756-316">Pour plus d’informations sur la **MessageClientCredentialType** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-316">For more information about the **MessageClientCredentialType** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="af756-317">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-317">Type: String</span></span>  
<span data-ttu-id="af756-318">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-318">Applies to:</span></span> 
- <span data-ttu-id="af756-319">Adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="af756-319">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="af756-320">Adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-320">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="af756-321">Adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-321">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="af756-322">Adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-322">WCF-NetNamedPipe adapter</span></span>

#### <a name="messageencoding"></a><span data-ttu-id="af756-323">MessageEncoding</span><span class="sxs-lookup"><span data-stu-id="af756-323">MessageEncoding</span></span>
<span data-ttu-id="af756-324">Indiquer l’encodeur utilisé pour coder le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="af756-324">Specify the encoder used to encode the SOAP message.</span></span>

<span data-ttu-id="af756-325">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-325">Type: String</span></span>  
<span data-ttu-id="af756-326">Valeur par défaut : texte</span><span class="sxs-lookup"><span data-stu-id="af756-326">Default value: Text</span></span>  

    Applicable values: 
        - Text: Use a text message encoder
        - Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder  

<span data-ttu-id="af756-327">S’applique à : l’adaptateur WCF-BasicHttp, l’adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-327">Applies to: WCF-BasicHttp adapter, WCF-WSHttp adapter</span></span>


#### <a name="msmqauthenticationmode"></a><span data-ttu-id="af756-328">MsmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="af756-328">MsmqAuthenticationMode</span></span>
<span data-ttu-id="af756-329">Spécifiez le mode d'authentification du message par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="af756-329">Specify how the message must be authenticated by the MSMQ transport.</span></span>

<span data-ttu-id="af756-330">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-330">Type: String</span></span>  
<span data-ttu-id="af756-331">Valeur par défaut : **WindowsDomain**</span><span class="sxs-lookup"><span data-stu-id="af756-331">Default value: **WindowsDomain**</span></span>  
    <span data-ttu-id="af756-332">Pour plus d’informations sur les valeurs applicables pour le **MsmqAuthenticationMode** propriété, consultez le **mode d’authentification MSMQ** propriété dans le **propriétés du Transport WCF-NetMsmq Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="af756-332">For more information about the applicable values for the **MsmqAuthenticationMode** property, see the **MSMQ authentication mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
<span data-ttu-id="af756-333">S’applique à : l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-333">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqencryptionalgorithm"></a><span data-ttu-id="af756-334">MsmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="af756-334">MsmqEncryptionAlgorithm</span></span>
<span data-ttu-id="af756-335">Spécifiez l'algorithme à utiliser pour le chiffrement des messages lors de leur transfert entre les gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="af756-335">Specify the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="af756-336">Cette propriété est disponible uniquement si le **MsmqProtectionLevel** est définie sur **EncryptAndSign**.</span><span class="sxs-lookup"><span data-stu-id="af756-336">This property is available only if the **MsmqProtectionLevel** property is set to **EncryptAndSign**.</span></span>

<span data-ttu-id="af756-337">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-337">Type: String</span></span>  
<span data-ttu-id="af756-338">Valeur par défaut : **RC4Stream**</span><span class="sxs-lookup"><span data-stu-id="af756-338">Default value: **RC4Stream**</span></span>  

    Applicable values are: RC4Stream, AES

<span data-ttu-id="af756-339">S’applique à : l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-339">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqprotectionlevel"></a><span data-ttu-id="af756-340">MsmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="af756-340">MsmqProtectionLevel</span></span>
<span data-ttu-id="af756-341">Spécifier le mode de sécurisation des messages au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="af756-341">Specify the way messages are secured at the level of the MSMQ transport.</span></span>

<span data-ttu-id="af756-342">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-342">Type: String</span></span>  
<span data-ttu-id="af756-343">Valeur par défaut : **signe**</span><span class="sxs-lookup"><span data-stu-id="af756-343">Default value: **Sign**</span></span>  

    Applicable values are:
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**  

<span data-ttu-id="af756-344">S’applique à : l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-344">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqsecurehashalgorithm"></a><span data-ttu-id="af756-345">MsmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="af756-345">MsmqSecureHashAlgorithm</span></span>
<span data-ttu-id="af756-346">Spécifiez l'algorithme de hachage à utiliser pour traiter la synthèse du message.</span><span class="sxs-lookup"><span data-stu-id="af756-346">Specify the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="af756-347">Cette propriété n’est pas disponible si le **MsmqProtectionLevel** est définie sur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="af756-347">This property is not available if the **MsmqProtectionLevel** property is set to **None**.</span></span>

<span data-ttu-id="af756-348">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-348">Type: String</span></span>  
<span data-ttu-id="af756-349">Valeur par défaut : **SHA1**</span><span class="sxs-lookup"><span data-stu-id="af756-349">Default value: **SHA1**</span></span>  

    Applicable values are: MD5, SHA1, SHA25, SHA512  

<span data-ttu-id="af756-350">S’applique à : l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-350">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="negotiateservicecredential"></a><span data-ttu-id="af756-351">NegotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="af756-351">NegotiateServiceCredential</span></span>
<span data-ttu-id="af756-352">Spécifiez si les informations d'identification du service sont générées au niveau du client hors bande ou sont obtenues à partir du service sur ce client via un processus de négociation.</span><span class="sxs-lookup"><span data-stu-id="af756-352">Specify whether the service credential is provisioned at the client out of band, or is obtained from the service to the client through a process of negotiation.</span></span> <span data-ttu-id="af756-353">Une négociation de ce type est un précurseur de l'échange classique des messages.</span><span class="sxs-lookup"><span data-stu-id="af756-353">Such a negotiation is a precursor to the usual message exchange.</span></span>

<span data-ttu-id="af756-354">Si le **MessageClientCredentialType** égal à la propriété **aucun**, **nom d’utilisateur**, ou **certificat**, définir cette propriété sur  **False** implique que le certificat de service est disponible au niveau du client hors bande et que le client spécifier le certificat de service.</span><span class="sxs-lookup"><span data-stu-id="af756-354">If the **MessageClientCredentialType** property equals **None**, **Username**, or **Certificate**, setting this property to **False** implies that the service certificate is available at the client out of band and that the client needs to specify the service certificate.</span></span> <span data-ttu-id="af756-355">Ce mode est interopérable avec les piles SOAP qui implémentent WS-Trust et WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="af756-355">This mode is interoperable with SOAP stacks that implement WS-Trust and WS-SecureConversation.</span></span>

<span data-ttu-id="af756-356">Si le **MessageClientCredentialType** est définie sur **Windows**, si cette propriété **False** Spécifie l’authentification Kerberos.</span><span class="sxs-lookup"><span data-stu-id="af756-356">If the **MessageClientCredentialType** property is set to **Windows**, setting this property to **False** specifies Kerberos-based authentication.</span></span> <span data-ttu-id="af756-357">Cela implique que le client et le service fassent partie du même domaine Kerberos.</span><span class="sxs-lookup"><span data-stu-id="af756-357">This means that the client and service must be part of the same Kerberos domain.</span></span> <span data-ttu-id="af756-358">Ce mode est interopérable avec les piles SOAP qui implémentent le profil de jeton Kerberos (tel que défini au niveau OASIS WSS TC) ainsi que WS-Trust et WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="af756-358">This mode is interoperable with SOAP stacks that implement the Kerberos token profile (as defined at OASIS WSS TC) as well as WS-Trust and WS-SecureConversation.</span></span>

<span data-ttu-id="af756-359">Lorsque cette propriété est **True**, elle génère une négociation .NET SOAP qui utilise l’échange SPNego sur les messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="af756-359">When this property is **True**, it causes a .NET SOAP negotiation that tunnels SPNego exchange over SOAP messages.</span></span>

<span data-ttu-id="af756-360">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-360">Type: Boolean</span></span>  
<span data-ttu-id="af756-361">Valeur par défaut : True</span><span class="sxs-lookup"><span data-stu-id="af756-361">Default value: True</span></span>  
<span data-ttu-id="af756-362">S’applique à : l’adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-362">Applies to: WCF-WSHttp adapter</span></span>  

#### <a name="opentimeout"></a><span data-ttu-id="af756-363">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="af756-363">OpenTimeout</span></span>
<span data-ttu-id="af756-364">Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.</span><span class="sxs-lookup"><span data-stu-id="af756-364">Specify a time span value that indicates the interval of time provided for a channel open operation to complete.</span></span> 

<span data-ttu-id="af756-365">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-365">**Note**</span></span>  
<span data-ttu-id="af756-366">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-366">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="af756-367">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-367">Type: String</span></span>  
<span data-ttu-id="af756-368">Valeur par défaut : 00:01:00</span><span class="sxs-lookup"><span data-stu-id="af756-368">Default value: 00:01:00</span></span>  
<span data-ttu-id="af756-369">S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-369">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="orderedprocessing"></a><span data-ttu-id="af756-370">OrderedProcessing</span><span class="sxs-lookup"><span data-stu-id="af756-370">OrderedProcessing</span></span>
<span data-ttu-id="af756-371">Spécifier si vous voulez traiter les messages par séries.</span><span class="sxs-lookup"><span data-stu-id="af756-371">Specify whether to process messages serially.</span></span> <span data-ttu-id="af756-372">Lorsque cette propriété est activée, cet emplacement de réception livraison chronologique des messages lorsqu’il est utilisé conjointement avec une orchestration ou la messagerie port d’envoi BizTalk a prend en charge la **livraison chronologique des messages** option définie sur `True`.</span><span class="sxs-lookup"><span data-stu-id="af756-372">When this property is selected, this receive location accommodates ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the **Ordered Delivery** option set to `True`.</span></span> <span data-ttu-id="af756-373">Pour plus d’informations sur la **livraison chronologique des messages** option, consultez les rubriques correspondantes dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="af756-373">For more information about the **Ordered Delivery** option, see the appropriate topics in See Also.</span></span>

<span data-ttu-id="af756-374">Cette propriété est applicable dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="af756-374">This property is applicable in the following cases:</span></span>
- <span data-ttu-id="af756-375">Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **netMsmqBinding**</span><span class="sxs-lookup"><span data-stu-id="af756-375">WCF-Custom adapter: When the **BindingType** property is set to **netMsmqBinding**</span></span>
- <span data-ttu-id="af756-376">Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur des transports prenant en charge la livraison chronologique des messages, tels que MSMQ.</span><span class="sxs-lookup"><span data-stu-id="af756-376">WCF-Custom adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on transports supporting ordered delivery such as MSMQ.</span></span>
- <span data-ttu-id="af756-377">Adaptateur WCF-CustomIsolated : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur les transports prenant en charge la livraison chronologique des messages.</span><span class="sxs-lookup"><span data-stu-id="af756-377">WCF-CustomIsolated adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on transports supporting ordered delivery.</span></span>
- <span data-ttu-id="af756-378">Adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-378">WCF-NetMsmq adapter</span></span>

<span data-ttu-id="af756-379">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-379">Type: String</span></span>  
<span data-ttu-id="af756-380">Valeur par défaut : **False**</span><span class="sxs-lookup"><span data-stu-id="af756-380">Default value: **False**</span></span>  
<span data-ttu-id="af756-381">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-381">Applies to:</span></span> 
- <span data-ttu-id="af756-382">Adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-382">WCF-NetMsmq receive adapter</span></span>
- <span data-ttu-id="af756-383">Adaptateur de réception WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="af756-383">WCF-Custom receive adapter</span></span>
- <span data-ttu-id="af756-384">Adaptateur de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-384">WCF-CustomIsolated receive adapter</span></span>

#### <a name="outboundbodylocation"></a><span data-ttu-id="af756-385">OutboundBodyLocation</span><span class="sxs-lookup"><span data-stu-id="af756-385">OutboundBodyLocation</span></span>
<span data-ttu-id="af756-386">Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.</span><span class="sxs-lookup"><span data-stu-id="af756-386">Specify the data selection for the SOAP **Body** element of outgoing WCF messages.</span></span> <span data-ttu-id="af756-387">Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-387">For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="af756-388">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-388">Type: String</span></span>  
<span data-ttu-id="af756-389">Valeur par défaut : UseBodyElement</span><span class="sxs-lookup"><span data-stu-id="af756-389">Default value: UseBodyElement</span></span>  

    Applicable values are:
        - UseBodyElement: Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message
        - **UseTem****plate**: Use the template supplied in the OutboundXMLTemplate property to create the content of the SOAP **Body** element for an outgoing message

<span data-ttu-id="af756-390">S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-390">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="outboundcustomheaders"></a><span data-ttu-id="af756-391">OutboundCustomHeaders</span><span class="sxs-lookup"><span data-stu-id="af756-391">OutboundCustomHeaders</span></span>
<span data-ttu-id="af756-392">Spécifiez les en-têtes SOAP personnalisés pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="af756-392">Specify the custom SOAP headers for outgoing messages.</span></span> <span data-ttu-id="af756-393">Lorsque cette propriété est utilisée, la propriété doit avoir la \< **en-têtes** \> élément comme élément racine.</span><span class="sxs-lookup"><span data-stu-id="af756-393">When this property is used, the property must have the \<**headers**\> element as the root element.</span></span> <span data-ttu-id="af756-394">Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="af756-394">All of the custom SOAP headers must be placed inside the \<**headers**\> element.</span></span> <span data-ttu-id="af756-395">Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**\>\</**en-têtes** \> ou \< **en-têtes** \> à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-395">If the custom SOAP header value is an empty string, you must assign \<**headers**\>\</**headers**\> or \<**headers**\> to this property.</span></span> <span data-ttu-id="af756-396">Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="af756-396">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>

<span data-ttu-id="af756-397">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-397">Type: String</span></span>  
<span data-ttu-id="af756-398">S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-398">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="outboundxmltemplate"></a><span data-ttu-id="af756-399">OutboundXmlTemplate</span><span class="sxs-lookup"><span data-stu-id="af756-399">OutboundXmlTemplate</span></span>
<span data-ttu-id="af756-400">Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant.</span><span class="sxs-lookup"><span data-stu-id="af756-400">Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message.</span></span> <span data-ttu-id="af756-401">Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.</span><span class="sxs-lookup"><span data-stu-id="af756-401">This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.</span></span> <span data-ttu-id="af756-402">Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-402">For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="af756-403">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-403">Type: String</span></span>  
<span data-ttu-id="af756-404">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-404">Default value: An empty string</span></span>  
<span data-ttu-id="af756-405">S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-405">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="password"></a><span data-ttu-id="af756-406">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="af756-406">Password</span></span>
<span data-ttu-id="af756-407">Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="af756-407">Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.</span></span>

<span data-ttu-id="af756-408">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-408">Type: String</span></span>  
<span data-ttu-id="af756-409">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-409">Default value: An empty string</span></span>  
<span data-ttu-id="af756-410">S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-410">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>  

#### <a name="propagatefaultmessage"></a><span data-ttu-id="af756-411">PropagateFaultMessage</span><span class="sxs-lookup"><span data-stu-id="af756-411">PropagateFaultMessage</span></span>
<span data-ttu-id="af756-412">Spécifiez si les messages dont le traitement sortant a échoué sont acheminés ou interrompus.</span><span class="sxs-lookup"><span data-stu-id="af756-412">Specify whether to route or suspend messages that fail in outbound processing.</span></span> <span data-ttu-id="af756-413">Cette propriété est valide uniquement pour des ports de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="af756-413">This property is valid only for solicit-response ports.</span></span> 

<span data-ttu-id="af756-414">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-414">**Note**</span></span>  
<span data-ttu-id="af756-415">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-415">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span>

<span data-ttu-id="af756-416">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-416">Type: Boolean</span></span>  
<span data-ttu-id="af756-417">Valeur par défaut : **True**</span><span class="sxs-lookup"><span data-stu-id="af756-417">Default value: **True**</span></span>  

    Applicable values are:  
        - True: Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule)
        - False: Suspend failed messages and generate a negative acknowledgment (NACK)

<span data-ttu-id="af756-418">S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-418">Applies to: All WCF send adapters *except* the WCF-NetMsmq adapter</span></span>
  
#### <a name="proxyaddress"></a><span data-ttu-id="af756-419">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="af756-419">ProxyAddress</span></span>
<span data-ttu-id="af756-420">Indiquer l’adresse du serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="af756-420">Specify the address of the proxy server.</span></span> <span data-ttu-id="af756-421">Utilisez le **https** ou **http** schéma selon la configuration de sécurité.</span><span class="sxs-lookup"><span data-stu-id="af756-421">Use the **https** or the **http** scheme depending on the security configuration.</span></span> <span data-ttu-id="af756-422">Cette adresse peut être suivie d'un deux-points et du numéro de port.</span><span class="sxs-lookup"><span data-stu-id="af756-422">This address can be followed by a colon and the port number.</span></span> <span data-ttu-id="af756-423">La propriété est requise si le **ProxyToUse** est définie sur **UserSpecified** (par exemple, http://127.0.0.1 : 8080)</span><span class="sxs-lookup"><span data-stu-id="af756-423">The property is required if the **ProxyToUse** property is set to **UserSpecified** (For example, http://127.0.0.1:8080)</span></span>

<span data-ttu-id="af756-424">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-424">Type: String</span></span>  
<span data-ttu-id="af756-425">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-425">Default value: An empty string</span></span>  
<span data-ttu-id="af756-426">S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-426">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>  

#### <a name="proxypassword"></a><span data-ttu-id="af756-427">ProxyPassword</span><span class="sxs-lookup"><span data-stu-id="af756-427">ProxyPassword</span></span>
<span data-ttu-id="af756-428">Spécifiez le mot de passe à utiliser pour le serveur proxy spécifié dans le **ProxyAddress** propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-428">Specify the password to use for the proxy server specified in the **ProxyAddress** property.</span></span>

<span data-ttu-id="af756-429">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-429">Type: String</span></span>  
<span data-ttu-id="af756-430">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-430">Default value: An empty string</span></span>  
<span data-ttu-id="af756-431">S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-431">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>

#### <a name="proxytouse"></a><span data-ttu-id="af756-432">ProxyToUse</span><span class="sxs-lookup"><span data-stu-id="af756-432">ProxyToUse</span></span>
<span data-ttu-id="af756-433">Spécifiez le serveur proxy à utiliser pour le trafic HTTP sortant.</span><span class="sxs-lookup"><span data-stu-id="af756-433">Specify which proxy server to use for outgoing HTTP traffic.</span></span>

<span data-ttu-id="af756-434">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-434">Type: String</span></span>  
<span data-ttu-id="af756-435">Valeur par défaut : **None**</span><span class="sxs-lookup"><span data-stu-id="af756-435">Default value: **None**</span></span>  

    Applicable values are:  
        - None: Do not use a proxy server for this send port
        - Default: Use the proxy settings in the send handler hosting this send port
        - UserSpecified: Use the proxy server specified in the **ProxyAddress** property

<span data-ttu-id="af756-436">S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-436">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>  

#### <a name="proxyusername"></a><span data-ttu-id="af756-437">ProxyUserName</span><span class="sxs-lookup"><span data-stu-id="af756-437">ProxyUserName</span></span>
<span data-ttu-id="af756-438">Spécifiez le nom d’utilisateur à utiliser pour le serveur proxy spécifié dans le **ProxyAddress** propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-438">Specify the user name to use for the proxy server specified in the **ProxyAddress** property.</span></span> <span data-ttu-id="af756-439">La propriété est requise si le **ProxyToUse** est définie sur **UserSpecified**.</span><span class="sxs-lookup"><span data-stu-id="af756-439">The property is required if the **ProxyToUse** property is set to **UserSpecified**.</span></span>

<span data-ttu-id="af756-440">Pour plus d’informations sur cette propriété, consultez [comment configurer un Port d’envoi WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-send-port.md) et [comment configurer un Port d’envoi WCF-BasicHttp](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f).</span><span class="sxs-lookup"><span data-stu-id="af756-440">For more information about this property, see [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md) and [How to Configure a WCF-BasicHttp Send Port](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f).</span></span>

<span data-ttu-id="af756-441">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-441">Type: String</span></span>  
<span data-ttu-id="af756-442">S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-442">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>

#### <a name="replytoaddress"></a><span data-ttu-id="af756-443">ReplyToAddress</span><span class="sxs-lookup"><span data-stu-id="af756-443">ReplyToAddress</span></span>
<span data-ttu-id="af756-444">Indiquez l'adresse du point de terminaison de réponse pour les messages WCF sortants qui correspondent aux messages entrants reçus par les emplacements de réception de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="af756-444">Indicate the reply endpoint address for the outgoing WCF messages corresponding to incoming messages received through the request-response receive locations.</span></span> <span data-ttu-id="af756-445">La propriété est automatiquement promue à partir de messages entrants.</span><span class="sxs-lookup"><span data-stu-id="af756-445">The property is automatically promoted from incoming messages.</span></span>

<span data-ttu-id="af756-446">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-446">Type: String</span></span>  
<span data-ttu-id="af756-447">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-447">Default value: An empty string</span></span>  
<span data-ttu-id="af756-448">S’applique à : tous les adaptateurs WCF *sauf* l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-448">Applies to: All WCF adapters *except* the WCF-NetMsmq adapter</span></span>

#### <a name="securitymode"></a><span data-ttu-id="af756-449">SecurityMode</span><span class="sxs-lookup"><span data-stu-id="af756-449">SecurityMode</span></span>
<span data-ttu-id="af756-450">Spécifier le type de sécurité utilisé.</span><span class="sxs-lookup"><span data-stu-id="af756-450">Specify the type of security that is used.</span></span> <span data-ttu-id="af756-451">Les valeurs applicables diffèrent pour chaque adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-451">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="af756-452">Pour plus d’informations sur la **SecurityMode** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-452">For more information about the **SecurityMode** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span> 

<span data-ttu-id="af756-453">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-453">**Note**</span></span>  
<span data-ttu-id="af756-454">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-454">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span>

<span data-ttu-id="af756-455">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-455">Type: String</span></span>  
<span data-ttu-id="af756-456">S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-456">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="sendtimeout"></a><span data-ttu-id="af756-457">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="af756-457">SendTimeout</span></span>
<span data-ttu-id="af756-458">Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée.</span><span class="sxs-lookup"><span data-stu-id="af756-458">Specify a time span value that indicates the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="af756-459">Cette valeur spécifie une période pour l'exécution de toute l'interaction, même si le correspondant envoie un message volumineux.</span><span class="sxs-lookup"><span data-stu-id="af756-459">This value specifies a time span for the whole interaction to complete, even if the correspondent sends a large message.</span></span>

<span data-ttu-id="af756-460">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-460">Type: String</span></span>  
<span data-ttu-id="af756-461">Valeur par défaut : 00:01:00</span><span class="sxs-lookup"><span data-stu-id="af756-461">Default value: 00:01:00</span></span>  
<span data-ttu-id="af756-462">S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-462">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="servicebehaviorconfiguration"></a><span data-ttu-id="af756-463">ServiceBehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="af756-463">ServiceBehaviorConfiguration</span></span>
<span data-ttu-id="af756-464">Spécifiez une chaîne XML avec la  **\<comportement\>**  élément de la  **\<serviceBehaviors\>**  élément pour configurer les paramètres de comportement d’un service WCF service.</span><span class="sxs-lookup"><span data-stu-id="af756-464">Specify an XML string with the **\<behavior\>** element of the **\<serviceBehaviors\>** element to configure the behavior settings of a WCF service.</span></span> <span data-ttu-id="af756-465">Pour plus d’informations sur la  **\<serviceBehaviors\>**  élément, consultez la rubrique appropriée dans Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="af756-465">For more information about the **\<serviceBehaviors\>** element, see the appropriate topic in See Also.</span></span>

<span data-ttu-id="af756-466">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-466">Example:</span></span>

```
<behavior name="SampleServiceBehavior">
<serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
<serviceCredentials>
<serviceCertificate findValue="539d9ab3089bb6dc187fa7dbb382cf01f8d78f5f" storeLocation="CurrentUser" x509FindType="FindByThumbprint"/>
</serviceCredentials>
<serviceMetadata httpGetEnabled="true"/>
</behavior>
```

<span data-ttu-id="af756-467">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-467">Type: String</span></span>  
<span data-ttu-id="af756-468">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-468">Default value: An empty string</span></span>  
<span data-ttu-id="af756-469">S’applique à : l’adaptateur WCF-CustomIsolated, l’adaptateur de réception WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="af756-469">Applies to: WCF-Custom receive adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="servicecertificate"></a><span data-ttu-id="af756-470">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="af756-470">ServiceCertificate</span></span>
<span data-ttu-id="af756-471">Si cette propriété est utilisée pour les emplacements de réception, spécifiez l'empreinte du certificat X.509 pour les emplacements de réception que les clients utilisent pour authentifier le service.</span><span class="sxs-lookup"><span data-stu-id="af756-471">If this property is used for receive locations, specify the thumbprint of the X.509 certificate for the receive locations that clients use to authenticate the service.</span></span> <span data-ttu-id="af756-472">Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.</span><span class="sxs-lookup"><span data-stu-id="af756-472">The certificate to be used for this property must be installed into the **My** store in the **Current User** location.</span></span>

<span data-ttu-id="af756-473">Si cette propriété est utilisée pour les ports d'envoi, spécifiez l'empreinte du certificat X.509 pour l'authentification du service auquel ce port d'envoi envoie des messages.</span><span class="sxs-lookup"><span data-stu-id="af756-473">If this property is used for send ports, specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages.</span></span> <span data-ttu-id="af756-474">Le certificat à utiliser pour cette propriété doit être installé dans le **autres personnes** stocker dans le **ordinateur Local** emplacement.</span><span class="sxs-lookup"><span data-stu-id="af756-474">The certificate to be used for this property must be installed into the **Other People** store in the **Local Machine** location.</span></span>

<span data-ttu-id="af756-475">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-475">Type: String</span></span>  
<span data-ttu-id="af756-476">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-476">Default value: An empty string</span></span>  
<span data-ttu-id="af756-477">S'applique à :</span><span class="sxs-lookup"><span data-stu-id="af756-477">Applies to:</span></span> 
- <span data-ttu-id="af756-478">Adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="af756-478">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="af756-479">Adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-479">WCF-NetMsmq adapter</span></span>
- <span data-ttu-id="af756-480">Adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-480">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="af756-481">Adaptateur de réception WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-481">WCF-NetTcp receive adapter</span></span>

#### <a name="suspendmessageonfailure"></a><span data-ttu-id="af756-482">SuspendMessageOnFailure</span><span class="sxs-lookup"><span data-stu-id="af756-482">SuspendMessageOnFailure</span></span>
<span data-ttu-id="af756-483">Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.</span><span class="sxs-lookup"><span data-stu-id="af756-483">Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.</span></span>

<span data-ttu-id="af756-484">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-484">Type: Boolean</span></span>  
<span data-ttu-id="af756-485">Valeur par défaut : True</span><span class="sxs-lookup"><span data-stu-id="af756-485">Default value: True</span></span>  
<span data-ttu-id="af756-486">S’applique à : WCF tous les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="af756-486">Applies to: All WCF receive adapters</span></span>  

#### <a name="textencoding"></a><span data-ttu-id="af756-487">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="af756-487">TextEncoding</span></span>
<span data-ttu-id="af756-488">Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**.</span><span class="sxs-lookup"><span data-stu-id="af756-488">Specify the character set encoding to be used for emitting messages on the binding when the **MessageEncoding** property is set to **Text**.</span></span> 

<span data-ttu-id="af756-489">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-489">**Note**</span></span>  
<span data-ttu-id="af756-490">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-490">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="af756-491">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-491">Type: String</span></span>  
<span data-ttu-id="af756-492">Valeur par défaut : utf-8</span><span class="sxs-lookup"><span data-stu-id="af756-492">Default value: utf-8</span></span>  

    Applicable values are:  
        - unicodeFFF: Unicode BigEndian encoding
        - utf-16: 16-bit encoding
        - utf-8: 8-bit encoding

<span data-ttu-id="af756-493">S’applique à : l’adaptateur WCF-BasicHttp, l’adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-493">Applies to: WCF-BasicHttp adapter, WCF-WSHttp adapter</span></span>
  
#### <a name="timetolive"></a><span data-ttu-id="af756-494">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="af756-494">TimeToLive</span></span>
<span data-ttu-id="af756-495">Spécifiez une durée de validité des messages avant qu'ils ne soient considérés comme expirés et placés dans la file d'attente des messages non distribués.</span><span class="sxs-lookup"><span data-stu-id="af756-495">Specify a time span for how long the messages are valid before they are expired and put into the dead-letter queue.</span></span> <span data-ttu-id="af756-496">Cette propriété permet de s'assurer que les messages, pour lesquels le temps est un paramètre crucial, ne deviennent pas obsolètes avant leur traitement par un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="af756-496">This property is set to ensure that time-sensitive messages do not become stale before they are processed by a send port.</span></span> <span data-ttu-id="af756-497">Tout message d'une file d'attente qui n'aurait pas été utilisé par ce port d'envoi dans le délai spécifié est déclaré comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="af756-497">A message in a queue that is not consumed by this send port within the time interval specified is said to be expired.</span></span> <span data-ttu-id="af756-498">Ces messages expirés sont envoyés vers une file d'attente spéciale, appelée file d'attente des messages non distribués.</span><span class="sxs-lookup"><span data-stu-id="af756-498">Expired messages are sent to special queue called the dead-letter queue.</span></span> <span data-ttu-id="af756-499">L’emplacement de la file d’attente de lettres mortes est défini avec la **DeadLetterQueue** propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-499">The location of the dead-letter queue is set with the **DeadLetterQueue** property.</span></span>

<span data-ttu-id="af756-500">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-500">Type: String</span></span>  
<span data-ttu-id="af756-501">Valeur par défaut : 1.00:00:00</span><span class="sxs-lookup"><span data-stu-id="af756-501">Default value: 1.00:00:00</span></span>  
<span data-ttu-id="af756-502">S’applique à : adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-502">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="to"></a><span data-ttu-id="af756-503">Pour</span><span class="sxs-lookup"><span data-stu-id="af756-503">To</span></span>
<span data-ttu-id="af756-504">Spécifiez l'adresse du point de terminaison de destination pour les messages WCF sortants qu'envoient les ports d'envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-504">Specify the destination endpoint address for outgoing WCF messages that the WCF send ports send.</span></span>

<span data-ttu-id="af756-505">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-505">Type: String</span></span>  
<span data-ttu-id="af756-506">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-506">Default value: An empty string</span></span>  
<span data-ttu-id="af756-507">S’applique à : WCF tous les adaptateurs d’envoi</span><span class="sxs-lookup"><span data-stu-id="af756-507">Applies to: All WCF send adapters</span></span>  

#### <a name="transactionprotocol"></a><span data-ttu-id="af756-508">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="af756-508">TransactionProtocol</span></span>
<span data-ttu-id="af756-509">Spécifiez le protocole de transaction à utiliser avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="af756-509">Specify the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="af756-510">Cette propriété est requise si le **EnableTransaction** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="af756-510">This property is required if the **EnableTransaction** property is set to **True**.</span></span>

<span data-ttu-id="af756-511">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-511">Type: String</span></span>  
<span data-ttu-id="af756-512">Valeur par défaut : OleTransaction</span><span class="sxs-lookup"><span data-stu-id="af756-512">Default value: OleTransaction</span></span>  

    Applicable values are: OleTransaction, WS-AtomicTransaction

<span data-ttu-id="af756-513">S’applique à : l’adaptateur WCF-NetNamedPipe, l’adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="af756-513">Applies to: WCF-NetNamedPipe adapter,  WCF-NetTcp adapter</span></span>  

#### <a name="transportclientcredentialtype"></a><span data-ttu-id="af756-514">TransportClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="af756-514">TransportClientCredentialType</span></span>
<span data-ttu-id="af756-515">Spécifier le type d'informations d'identification à utiliser lors de l'authentification du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="af756-515">Specify the type of credential to be used when performing the send port authentication.</span></span> <span data-ttu-id="af756-516">Les valeurs applicables diffèrent pour chaque adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="af756-516">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="af756-517">Pour plus d’informations sur la **TransportClientCredentialType** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="af756-517">For more information about the **TransportClientCredentialType** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="af756-518">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-518">Type: String</span></span>  
<span data-ttu-id="af756-519">S’applique à : l’adaptateur WCF-Basic, l’adaptateur WCF-NetTcp, l’adaptateur WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="af756-519">Applies to: WCF-Basic adapter, WCF-NetTcp adapter, WCF-WSHttp adapter</span></span>  

#### <a name="transportprotectionlevel"></a><span data-ttu-id="af756-520">TransportProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="af756-520">TransportProtectionLevel</span></span>
<span data-ttu-id="af756-521">Définissez la sécurité au niveau du transport TCP.</span><span class="sxs-lookup"><span data-stu-id="af756-521">Specify security at the level of the TCP transport.</span></span> <span data-ttu-id="af756-522">La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert.</span><span class="sxs-lookup"><span data-stu-id="af756-522">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="af756-523">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="af756-523">Encryption provides data-level privacy during transport.</span></span>

<span data-ttu-id="af756-524">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-524">Type: String</span></span>  
<span data-ttu-id="af756-525">Valeur par défaut : **EncryptAndSign**</span><span class="sxs-lookup"><span data-stu-id="af756-525">Default value: **EncryptAndSign**</span></span>  

    Applicable values are:  
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed

<span data-ttu-id="af756-526">S’applique à : l’adaptateur WCF-NetTcp, l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-526">Applies to: WCF-NetTcp adapter, WCF-NetNamedPipe adapter</span></span>  

#### <a name="username"></a><span data-ttu-id="af756-527">UserName</span><span class="sxs-lookup"><span data-stu-id="af756-527">UserName</span></span>
<span data-ttu-id="af756-528">Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="af756-528">Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**.</span></span> <span data-ttu-id="af756-529">Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-529">You do not have to use the domain\user format for this property.</span></span>

<span data-ttu-id="af756-530">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-530">Type: String</span></span>  
<span data-ttu-id="af756-531">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-531">Default value: An empty string</span></span>  
<span data-ttu-id="af756-532">S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-532">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="usesourcejournal"></a><span data-ttu-id="af756-533">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="af756-533">UseSourceJournal</span></span>
<span data-ttu-id="af756-534">Spécifiez si les copies des messages traités par ce port d'envoi doivent être stockées dans la file d'attente des journaux sources.</span><span class="sxs-lookup"><span data-stu-id="af756-534">Specify whether copies of messages processed by this send port should be stored in the source journal queue.</span></span>

<span data-ttu-id="af756-535">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-535">Type: Boolean</span></span>  
<span data-ttu-id="af756-536">Valeur par défaut : False</span><span class="sxs-lookup"><span data-stu-id="af756-536">Default value: False</span></span>  
<span data-ttu-id="af756-537">S’applique à : adaptateur d’envoi WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="af756-537">Applies to: WCF-NetMsmq send adapter</span></span>  

#### <a name="usesso"></a><span data-ttu-id="af756-538">UseSSO</span><span class="sxs-lookup"><span data-stu-id="af756-538">UseSSO</span></span>
<span data-ttu-id="af756-539">Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="af756-539">Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.</span></span> 

<span data-ttu-id="af756-540">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-540">**Note**</span></span>  
<span data-ttu-id="af756-541">Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="af756-541">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="af756-542">Type : booléen</span><span class="sxs-lookup"><span data-stu-id="af756-542">Type: Boolean</span></span>  
<span data-ttu-id="af756-543">Valeur par défaut : False</span><span class="sxs-lookup"><span data-stu-id="af756-543">Default value: False</span></span>  
<span data-ttu-id="af756-544">S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="af756-544">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="referencedbindings"></a><span data-ttu-id="af756-545">ReferencedBindings</span><span class="sxs-lookup"><span data-stu-id="af756-545">ReferencedBindings</span></span>
<span data-ttu-id="af756-546">Spécifier les configurations de liaison référencées par le **bindingConfiguration** attribut de la  **\<émetteur\>**  , élément pour les  **wsFederationHttpBinding** et **customBinding**, ce qui indique le Service STS (Security Token) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="af756-546">Specify the binding configurations referenced by the **bindingConfiguration** attribute of the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding**, which indicates the Security Token Service (STS) that issues security tokens.</span></span> <span data-ttu-id="af756-547">Pour plus d’informations sur la  **\<émetteur\>**  élément, consultez la rubrique «\<émetteur\>» à [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).</span><span class="sxs-lookup"><span data-stu-id="af756-547">For more information about the **\<issuer\>** element, see the topic, "\<issuer\>" at [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).</span></span>

<span data-ttu-id="af756-548">Les informations de liaison, y compris le  **\<émetteur\>**  , élément pour les **wsFederationHttpBinding** et **customBinding** peut être configuré via la **BindingConfiguration** propriété des adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="af756-548">The binding information including the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding** can be configured through the **BindingConfiguration** property of the WCF-Custom and WCF-CustomIsolated adapters.</span></span> <span data-ttu-id="af756-549">Toutes les configurations de liaison référencées pour cette propriété doivent être placé dans le formulaire de la [ \<liaisons\> ](http://go.microsoft.com/fwlink/?LinkID=80878) élément.</span><span class="sxs-lookup"><span data-stu-id="af756-549">All of the referenced binding configurations for this property must be placed in the form of the [\<bindings\>](http://go.microsoft.com/fwlink/?LinkID=80878) element.</span></span> 

<span data-ttu-id="af756-550">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-550">**Note**</span></span>  
<span data-ttu-id="af756-551">Le **bindingConfiguration** attribut de la  **\<émetteur\>**  doit faire référence à un nom de liaison valide dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-551">The **bindingConfiguration** attribute of the **\<issuer\>** element must refer to a valid binding name in this property.</span></span> 

<span data-ttu-id="af756-552">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-552">**Note**</span></span>  
<span data-ttu-id="af756-553">Le  **\<émetteur\>**  élément dans les configurations de liaison référencées peut également faire référence à une configuration de liaison différents dans cette propriété si cette chaîne de référence n’est pas une dépendance circulaire.</span><span class="sxs-lookup"><span data-stu-id="af756-553">The **\<issuer\>** element in the referenced binding configurations can also refer to a different binding configuration in this property if this reference chain does not make a circular dependency.</span></span> 

<span data-ttu-id="af756-554">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af756-554">Example:</span></span> 

```
WCF.BindingConfiguration = @"<wsFederationHttpBinding>
<binding name=""sampleBinding"">
<security mode=""Message"">
<message issuedKeyType=""AsymmetricKey"">
<issuer address=""http://www.contoso.com/samplests"" binding=""wsFederationHttpBinding"" bindingConfiguration=""**contosoSTSBinding**""/>
</message>
</security>
</binding>
</wsFederationHttpBinding>";
WCF.ReferencedBinding =@"<bindings>
<wsFederationHttpBinding>
<binding name=""**contosoSTSBinding**"">
<security mode=""Message"">
<message negotiateServiceCredential=""false"">
<issuer address=""http://northwind.com/samplests"" bindingConfiguration=""**northwindBinding**"" binding=""wsHttpBinding"">
</issuer>
</message>
</security>
</binding>
</wsFederationHttpBinding>
<wsHttpBinding>
<binding name=""**northwindBinding**"">
<security mode=""Message"">
<message clientCredentialType=""Certificate""/>
</security>
</binding>
</wsHttpBinding>
</bindings>" 
``` 

<span data-ttu-id="af756-555">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="af756-555">**Note**</span></span>  
<span data-ttu-id="af756-556">**ReferencedBinding** propriété ne doit pas contenir la configuration de liaison utilisée dans les **BindingConfiguration** propriété.</span><span class="sxs-lookup"><span data-stu-id="af756-556">**ReferencedBinding** property must not contain the binding configuration used in the **BindingConfiguration** property.</span></span>

<span data-ttu-id="af756-557">Type : Chaîne</span><span class="sxs-lookup"><span data-stu-id="af756-557">Type: String</span></span>  
<span data-ttu-id="af756-558">Valeur par défaut : une chaîne vide</span><span class="sxs-lookup"><span data-stu-id="af756-558">Default value: An empty string</span></span>  
<span data-ttu-id="af756-559">S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="af756-559">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>
  
## <a name="see-also"></a><span data-ttu-id="af756-560">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af756-560">See Also</span></span>  
 <span data-ttu-id="af756-561">[Adaptateurs WCF](../core/wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="af756-561">[WCF Adapters](../core/wcf-adapters.md) </span></span>  
 <span data-ttu-id="af756-562">[\<comportement\> de \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879) </span><span class="sxs-lookup"><span data-stu-id="af756-562">[\<behavior\> of \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879) </span></span>  
 <span data-ttu-id="af756-563">[\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878) </span><span class="sxs-lookup"><span data-stu-id="af756-563">[\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878) </span></span>  
 <span data-ttu-id="af756-564">[\<comportement\> de \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095) </span><span class="sxs-lookup"><span data-stu-id="af756-564">[\<behavior\> of \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095) </span></span>  
 <span data-ttu-id="af756-565">[Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="af756-565">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="af756-566">L’équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="af756-566">Load Balancing</span></span>](http://go.microsoft.com/fwlink/?LinkId=81089)
