---
title: "En spécifiant le corps du Message pour les adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF adapters, SOAP messages
- messages, WCF adapters
- WCF adapters, message bodies
- SOAP messages, WCF adapters
ms.assetid: b20364b7-0365-4636-b4d6-bde9c69b8dcb
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 215ba0419bd9e6921c74755a88a17fa639567835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="specifying-the-message-body-for-the-wcf-adapters"></a><span data-ttu-id="d340b-102">Spécification du corps de message pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="d340b-102">Specifying the Message Body for the WCF Adapters</span></span>
<span data-ttu-id="d340b-103">Vous pouvez utiliser la **Messages** onglet dans les adaptateurs WCF pour spécifier la manière dont le corps du message BizTalk est extrait à partir d’un message SOAP entrant, et comment les corps du message BizTalk est placé dans un message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="d340b-103">You can use the **Messages** tab in the WCF adapters to specify how the BizTalk message body is extracted from an incoming SOAP message, and how the BizTalk message body is placed in an outgoing SOAP message.</span></span>  
  
## <a name="specifying-how-the-biztalk-message-body-is-extracted-from-an-incoming-soap-message"></a><span data-ttu-id="d340b-104">Spécification de la manière dont le corps du message BizTalk est extrait d'un message SOAP entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-104">Specifying How the BizTalk Message Body Is Extracted from an Incoming SOAP Message</span></span>  
 <span data-ttu-id="d340b-105">Vous pouvez contrôler la création du corps du message BizTalk entrant à partir de messages SOAP entrant par l'intermédiaire d'adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="d340b-105">You can control how to create the inbound BizTalk message body from the SOAP messages incoming through the WCF adapters.</span></span> <span data-ttu-id="d340b-106">Les illustrations suivantes montrent le **Messages** onglets de WCF-NetNamedPipe adaptateurs de réception et adaptateur d’envoi à titre d’exemple.</span><span class="sxs-lookup"><span data-stu-id="d340b-106">The following figures show the **Messages** tabs of the WCF-NetNamedPipe receive adapter and send adapter as examples.</span></span>  
  
 <span data-ttu-id="d340b-107">![L’onglet des Messages WCF des adaptateurs de réception](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")</span><span class="sxs-lookup"><span data-stu-id="d340b-107">![The Messages tab in the WCF receive adapters](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")</span></span>  
  
 <span data-ttu-id="d340b-108">![L’onglet des Messages WCF des adaptateurs d’envoi](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")</span><span class="sxs-lookup"><span data-stu-id="d340b-108">![The Messages tab in the WCF send adapters](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")</span></span>  
  
 <span data-ttu-id="d340b-109">Pour spécifier comment créer le corps du message BizTalk, sélectionnez une des options suivantes dans le **le corps du message BizTalk entrant** section dans les figures précédentes :</span><span class="sxs-lookup"><span data-stu-id="d340b-109">To specify how to create the BizTalk message body, select one of the following options in the **Inbound BizTalk message body** section in the preceding figures:</span></span>  
  
-   <span data-ttu-id="d340b-110">**: Enveloppe \<soap : Envelope >**.</span><span class="sxs-lookup"><span data-stu-id="d340b-110">**Envelope -- entire \<soap:Envelope>**.</span></span> <span data-ttu-id="d340b-111">Utilise le protocole SOAP **enveloppe** élément d’un message entrant pour créer le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-111">Uses the SOAP **Envelope** element of an incoming message to create the BizTalk message body part.</span></span> <span data-ttu-id="d340b-112">La totalité du message entrant devient le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-112">The entire incoming message becomes the BizTalk message body.</span></span> <span data-ttu-id="d340b-113">Utilisez cette option pour créer le corps du message BizTalk incorporant tous les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="d340b-113">Use this option to create the BizTalk message body incorporating all the headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d340b-114">Les en-têtes SOAP sont placés dans le contexte de message, mais ils ne sont pas promus automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d340b-114">The SOAP headers are placed in the message context, but they are not promoted automatically.</span></span> <span data-ttu-id="d340b-115">La promotion peut être effectuée dans un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d340b-115">Promotion can be done in a custom pipeline component.</span></span>  
  
-   <span data-ttu-id="d340b-116">**Corps : contenu de \<soap : Body > élément**.</span><span class="sxs-lookup"><span data-stu-id="d340b-116">**Body -- contents of \<soap:Body> element**.</span></span> <span data-ttu-id="d340b-117">Utilise le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-117">Uses the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part.</span></span> <span data-ttu-id="d340b-118">Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-118">If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.</span></span>  
  
-   <span data-ttu-id="d340b-119">**Chemin--contenu localisé par le chemin du corps**.</span><span class="sxs-lookup"><span data-stu-id="d340b-119">**Path -- content located by body path**.</span></span> <span data-ttu-id="d340b-120">Utilise l’expression de chemin d’accès au corps de la **expression de chemin de corps** zone de texte pour créer le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-120">Uses the body path expression in the **Body path expression** text box to create the BizTalk message body part.</span></span> <span data-ttu-id="d340b-121">L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant.</span><span class="sxs-lookup"><span data-stu-id="d340b-121">The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message.</span></span> <span data-ttu-id="d340b-122">Lorsque des messages entrants ont des données binaires, vous pouvez utiliser cette option pour que le corps du message BizTalk inclue uniquement les données binaires sans balise.</span><span class="sxs-lookup"><span data-stu-id="d340b-122">When incoming messages have binary data, you can use this option for the BizTalk message body to include only the binary data without any tags.</span></span>  
  
 <span data-ttu-id="d340b-123">Lorsque le **chemin--contenu localisé par le chemin du corps** option est sélectionnée, le **codage de nœud** propriété peut être configurée pour spécifier le type de codage attendu pour le nœud spécifié par l’expression de chemin de corps dans le **expression de chemin de corps** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d340b-123">When the **Path -- content located by body path** option is selected, the **Node encoding** property can be configured to specify the expected encoding type for the node specified by the body path expression in the **Body path expression** text box.</span></span> <span data-ttu-id="d340b-124">Si l'expression du chemin du corps correspond à plusieurs éléments, seul le premier élément correspondant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d340b-124">If the body path expression matches more than one element, only the first matched element is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d340b-125">Pour le **expression de chemin de corps** propriété, uniquement le XPath expressions appropriées pour le traitement de type avant uniquement de XML sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d340b-125">For the **body path expression** property, only the XPath expressions suitable for forward-only processing of XML are supported.</span></span> <span data-ttu-id="d340b-126">Pour plus d’informations sur les expressions XPath disponibles pour cette propriété, consultez « La meilleure de tous deux mondes : combinant XPath with the XmlReader » à [http://go.microsoft.com/fwlink/?LinkID=75701](http://go.microsoft.com/fwlink/?LinkID=75701).</span><span class="sxs-lookup"><span data-stu-id="d340b-126">For more information about the XPath expressions available for this property, see "The Best of Both Worlds: Combining XPath with the XmlReader" at [http://go.microsoft.com/fwlink/?LinkID=75701](http://go.microsoft.com/fwlink/?LinkID=75701).</span></span>  
  
 <span data-ttu-id="d340b-127">Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **chaîne**, les adaptateurs WCF attendent que le nœud correspondant a UTF-8 données de caractères encodés.</span><span class="sxs-lookup"><span data-stu-id="d340b-127">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **String**, the WCF adapters expect that the matched node has UTF-8 encoded character data.</span></span> <span data-ttu-id="d340b-128">Si les messages entrants sont échappés telles que les données de caractères pour les caractères spéciaux XML \< et >, les adaptateurs WCF rétablissent les données de caractères d’échappement lors de la création du corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d340b-128">If the incoming messages include escaped character data for the XML special characters such as \< and >, the WCF adapters restore the escaped character data when creating the BizTalk message body part.</span></span> <span data-ttu-id="d340b-129">Par exemple, si le nœud correspondant a échappement des données de type caractère tel que  **&lt;FirstName&gt;CONTOSO&lt;/prénom&gt;**  les adaptateurs WCF créent  **\< FirstName > CONTOSO\</Prénom >** corps du message dans BizTalk entrant.</span><span class="sxs-lookup"><span data-stu-id="d340b-129">For example, if the matched node has escaped character data such as **&lt;FirstName&gt;CONTOSO&lt;/FirstName&gt;** the WCF adapters create **\<FirstName>CONTOSO\</FirstName>** in the inbound BizTalk message body.</span></span>  
  
 <span data-ttu-id="d340b-130">Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **Hex** ou **Base64**, le nœud correspondant peut avoir une valide **au format BinHex** ou **Base64** séquence.</span><span class="sxs-lookup"><span data-stu-id="d340b-130">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **Hex** or **Base64**, the matched node can have a valid **BinHex** or **Base64** sequence.</span></span> <span data-ttu-id="d340b-131">Si le nœud correspondant a une séquence non valide, le client WCF reçoit **FaultException**, un message d’erreur est consigné dans le journal des événements sur votre ordinateur BizTalk Server et aucun message n’est suspendu.</span><span class="sxs-lookup"><span data-stu-id="d340b-131">If the matched node has an invalid sequence, the WCF client receives **FaultException**, an error message is logged in the event log on your BizTalk Server computer, and no message is suspended.</span></span>  
  
 <span data-ttu-id="d340b-132">Si le **chemin--contenu localisé par le chemin du corps** option est sélectionnée et la **codage de nœud** est définie sur **XML**, les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de la **expression de chemin de corps** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d340b-132">If the **Path -- content located by body path** option is selected and the **Node encoding** property is set to **XML**, the WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the **Body path expression** text box.</span></span>  
  
 <span data-ttu-id="d340b-133">Si le nœud correspondant n’a pas de données encodées en tant que spécifié dans le **codage de nœud** propriété, un corps de message BizTalk entrant vide est créé.</span><span class="sxs-lookup"><span data-stu-id="d340b-133">If the matched node does not have data encoded as specified in the **Node encoding** property, an empty inbound BizTalk message body is created.</span></span>  
  
 <span data-ttu-id="d340b-134">Par exemple, supposons que les adaptateurs d'envoi WCF reçoivent le message SOAP suivant de clients WCF :</span><span class="sxs-lookup"><span data-stu-id="d340b-134">For example, suppose the WCF send adapters receive the following SOAP message from WCF clients:</span></span>  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/OrderRefresh</a:Action>   
    <a:MessageID>urn:uuid:59e74507-66d0-4d50-be70-c3ec248b6f78</a:MessageID>   
    <a:ReplyTo>  
       <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>   
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>   
  </s:Header>  
  <s:Body>  
    <Order xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
     <OrderDetail>  
       <CustomerID>CONTOSO</CustomerID>   
       <OrderID>00000000</OrderID>   
     </OrderDetail>  
    </Order>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="d340b-135">Si vous configurez le **corps du message BizTalk entrant** section comme indiqué dans le tableau suivant, le précédent message SOAP entrant devient le corps du message BizTalk entrant.</span><span class="sxs-lookup"><span data-stu-id="d340b-135">If you configure the **Inbound BizTalk message body** section as shown in the following table, the previous incoming SOAP message becomes the inbound BizTalk message body part.</span></span>  
  
|<span data-ttu-id="d340b-136">Corps de message BizTalk entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-136">Inbound BizTalk message body</span></span>|<span data-ttu-id="d340b-137">Expression du chemin du corps</span><span class="sxs-lookup"><span data-stu-id="d340b-137">Body path expression</span></span>|<span data-ttu-id="d340b-138">Codage de nœud</span><span class="sxs-lookup"><span data-stu-id="d340b-138">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="d340b-139">**: Enveloppe \<soap : Envelope >**</span><span class="sxs-lookup"><span data-stu-id="d340b-139">**Envelope -- entire \<soap:Envelope>**</span></span>|<span data-ttu-id="d340b-140">Néant</span><span class="sxs-lookup"><span data-stu-id="d340b-140">N/A</span></span>|<span data-ttu-id="d340b-141">Néant</span><span class="sxs-lookup"><span data-stu-id="d340b-141">N/A</span></span>|  
  
 <span data-ttu-id="d340b-142">Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent le corps BizTalk entrant message contienne uniquement les **commande** élément dans la liste précédente messages SOAP entrants.</span><span class="sxs-lookup"><span data-stu-id="d340b-142">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters create the inbound BizTalk message body part to contain only the **Order** element in the previous incoming SOAP message.</span></span>  
  
|<span data-ttu-id="d340b-143">Corps de message BizTalk entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-143">Inbound BizTalk message body</span></span>|<span data-ttu-id="d340b-144">Expression du chemin du corps</span><span class="sxs-lookup"><span data-stu-id="d340b-144">Body path expression</span></span>|<span data-ttu-id="d340b-145">Codage de nœud</span><span class="sxs-lookup"><span data-stu-id="d340b-145">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="d340b-146">**Corps : contenu de \<soap : Body > élément**</span><span class="sxs-lookup"><span data-stu-id="d340b-146">**Body -- contents of \<soap:Body> element**</span></span>|<span data-ttu-id="d340b-147">Néant</span><span class="sxs-lookup"><span data-stu-id="d340b-147">N/A</span></span>|<span data-ttu-id="d340b-148">Néant</span><span class="sxs-lookup"><span data-stu-id="d340b-148">N/A</span></span>|  
  
 <span data-ttu-id="d340b-149">Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF attendent que le nœud entrant correspondant de l’expression de chemin de corps aura des données de type caractère encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d340b-149">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters expect that the incoming node that the body path expression matches will have UTF-8 encoded character data.</span></span>  
  
|<span data-ttu-id="d340b-150">Corps de message BizTalk entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-150">Inbound BizTalk message body</span></span>|<span data-ttu-id="d340b-151">Expression du chemin du corps</span><span class="sxs-lookup"><span data-stu-id="d340b-151">Body path expression</span></span>|<span data-ttu-id="d340b-152">Codage de nœud</span><span class="sxs-lookup"><span data-stu-id="d340b-152">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="d340b-153">**Chemin--contenu localisé par le chemin du corps**</span><span class="sxs-lookup"><span data-stu-id="d340b-153">**Path -- content located by body path**</span></span>|<span data-ttu-id="d340b-154">/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]</span><span class="sxs-lookup"><span data-stu-id="d340b-154">/*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="d340b-155">**Chaîne**</span><span class="sxs-lookup"><span data-stu-id="d340b-155">**String**</span></span>|  
  
 <span data-ttu-id="d340b-156">Pour le précédent message SOAP entrant, les adaptateurs WCF utilisent les données de caractères, **CONTOSO**, de la **CustomerID** élément pour créer le corps du message BizTalk entrant.</span><span class="sxs-lookup"><span data-stu-id="d340b-156">For the previous incoming SOAP message, the WCF adapters use the character data, **CONTOSO**, of the **CustomerID** element to create the inbound BizTalk message body part.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d340b-157">Vous ne pouvez pas utiliser la syntaxe abrégée de XPath, **/Order/OrderDetail/CustomerID**, pour le précédent message SOAP entrant.</span><span class="sxs-lookup"><span data-stu-id="d340b-157">You cannot use the abbreviated syntax of XPath, **/Order/OrderDetail/CustomerID**, for the previous incoming SOAP message.</span></span> <span data-ttu-id="d340b-158">Il s’agit, car la syntaxe abrégée de XPath renvoie le nœud non déclaré dans un espace de noms et le **CustomerID** élément dans le précédent message SOAP est déclaré dans le **http:// Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess** espace de noms par des espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="d340b-158">This is because the abbreviated syntax of XPath returns the node not declared in a namespace, and the **CustomerID** element in the previous SOAP message is declared in the **http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess** namespace by default namespaces.</span></span>  
  
 <span data-ttu-id="d340b-159">Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, le **CustomID** élément dans le précédent message SOAP entrant doit avoir une valide **BinHex**ou **Base64** séquence.</span><span class="sxs-lookup"><span data-stu-id="d340b-159">If you configure the **BizTalk message body** section as shown in the following table, the **CustomID** element in the previous incoming SOAP message should have a valid **BinHex** or **Base64** sequence.</span></span>  
  
|<span data-ttu-id="d340b-160">Corps de message BizTalk entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-160">Inbound BizTalk message body</span></span>|<span data-ttu-id="d340b-161">Expression du chemin du corps</span><span class="sxs-lookup"><span data-stu-id="d340b-161">Body path expression</span></span>|<span data-ttu-id="d340b-162">Codage de nœud</span><span class="sxs-lookup"><span data-stu-id="d340b-162">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="d340b-163">**Chemin--contenu localisé par le chemin du corps**</span><span class="sxs-lookup"><span data-stu-id="d340b-163">**Path -- content located by body path**</span></span>|<span data-ttu-id="d340b-164">/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]</span><span class="sxs-lookup"><span data-stu-id="d340b-164">/*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="d340b-165">**Hex** ou **en Base64**</span><span class="sxs-lookup"><span data-stu-id="d340b-165">**Hex** or **Base64**</span></span>|  
  
 <span data-ttu-id="d340b-166">Si vous configurez le **corps du message BizTalk** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent le corps du message BizTalk entrant pour le précédent message SOAP entrant comme indiqué dans le code après le tableau.</span><span class="sxs-lookup"><span data-stu-id="d340b-166">If you configure the **BizTalk message body** section as shown in the following table, the WCF adapters create the inbound BizTalk message body for the previous incoming SOAP message as shown in the code after the table.</span></span>  
  
|<span data-ttu-id="d340b-167">Corps de message BizTalk entrant</span><span class="sxs-lookup"><span data-stu-id="d340b-167">Inbound BizTalk message body</span></span>|<span data-ttu-id="d340b-168">Expression du chemin du corps</span><span class="sxs-lookup"><span data-stu-id="d340b-168">Body path expression</span></span>|<span data-ttu-id="d340b-169">Codage de nœud</span><span class="sxs-lookup"><span data-stu-id="d340b-169">Node encoding</span></span>|  
|----------------------------------|--------------------------|-------------------|  
|<span data-ttu-id="d340b-170">**Chemin--contenu localisé par le chemin du corps**</span><span class="sxs-lookup"><span data-stu-id="d340b-170">**Path -- content located by body path**</span></span>|<span data-ttu-id="d340b-171">/ * [local-name () = 'Order'] /\*[local-name () = 'OrderDetail'] /\*[local-name () = « CustomerID »]</span><span class="sxs-lookup"><span data-stu-id="d340b-171">/*[local-name()='Order']/\*[local-name()='OrderDetail']/\*[local-name()='CustomerID']</span></span>|<span data-ttu-id="d340b-172">**XML**</span><span class="sxs-lookup"><span data-stu-id="d340b-172">**XML**</span></span>|  
  
```  
<CustomerID xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">CONTOSO</CustomerID>   
```  
  
## <a name="specifying-the-source-of-the-outbound-wcf-message-body"></a><span data-ttu-id="d340b-173">Spécification de la source du corps du message WCF sortant</span><span class="sxs-lookup"><span data-stu-id="d340b-173">Specifying the Source of the Outbound WCF Message Body</span></span>  
 <span data-ttu-id="d340b-174">Vous pouvez contrôler la création du corps du message BizTalk sortant à partir d'un corps de message BizTalk à envoyer par l'intermédiaire d'adaptateurs WCF.</span><span class="sxs-lookup"><span data-stu-id="d340b-174">You can control how to create the outbound WCF message body from a BizTalk message body to send through the WCF adapters.</span></span> <span data-ttu-id="d340b-175">Pour spécifier comment le corps du message BizTalk est placé dans le corps du message WCF sortant, vous pouvez utiliser une des options suivantes dans le **le corps du message WCF sortant** section sur le **Messages** onglet comme indiqué dans les chiffres dans la section précédente :</span><span class="sxs-lookup"><span data-stu-id="d340b-175">To specify how the BizTalk message body is placed in the outbound WCF message body, you can use one of the following options in the **Outbound WCF message body** section on the **Messages** tab as shown in the figures in the previous section:</span></span>  
  
-   <span data-ttu-id="d340b-176">**Corps--Corps du message de réponse de BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="d340b-176">**Body -- BizTalk response message body**.</span></span> <span data-ttu-id="d340b-177">Utilise le corps du message BizTalk pour créer le contenu de SOAP **corps** élément d’un message sortant.</span><span class="sxs-lookup"><span data-stu-id="d340b-177">Uses the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.</span></span> <span data-ttu-id="d340b-178">Le corps du message BizTalk sortant devient le corps du message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="d340b-178">The outgoing BizTalk message body becomes the body of the outbound SOAP message.</span></span>  
  
-   <span data-ttu-id="d340b-179">**Modèle--contenu spécifié par le modèle**.</span><span class="sxs-lookup"><span data-stu-id="d340b-179">**Template -- content specified by template**.</span></span> <span data-ttu-id="d340b-180">Utilise le modèle fourni dans le **XML** zone de texte pour créer le contenu de SOAP **corps** élément d’un message sortant.</span><span class="sxs-lookup"><span data-stu-id="d340b-180">Uses the template supplied in the **XML** text box to create the content of the SOAP **Body** element for an outgoing message.</span></span> <span data-ttu-id="d340b-181">Les adaptateurs WCF avec **corps--corps du message de réponse BizTalk** (la valeur par défaut) option n’autorisent pas l’envoi de message non-XML tels que des images bitmap et des données de caractères.</span><span class="sxs-lookup"><span data-stu-id="d340b-181">The WCF adapters with **Body -- BizTalk response message body** (the default value) option do not allow sending non-XML message such as character data and bitmap images.</span></span> <span data-ttu-id="d340b-182">Vous pouvez utiliser la **modèle--contenu spécifié par le modèle** option pour les adaptateurs WCF envoyer des messages non XML codés dans **base64**, **hexadécimal**, ou **chaîne** .</span><span class="sxs-lookup"><span data-stu-id="d340b-182">You can use the **Template -- content specified by template** option for the WCF adapters to send non-XML messages encoded in **base64**, **hex**, or **string**.</span></span>  
  
 <span data-ttu-id="d340b-183">Lorsque le **modèle--contenu spécifié par le modèle** option est sélectionnée, vous devez fournir un élément XML de modèle arbitraire dans le **corps de message WCF sortant - XML** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d340b-183">When the **Template -- content specified by template** option is selected, you must provide an arbitrary template XML element in the **Outbound WCF message body - XML** text box.</span></span> <span data-ttu-id="d340b-184">L’élément XML du modèle doit contenir les éléments suivants **bts-msg-body** élément qu’une seule fois et qu’une seule fois, sauf si l’élément XML de modèle est vide :</span><span class="sxs-lookup"><span data-stu-id="d340b-184">The template XML element must contain the following **bts-msg-body** element once and only once unless the template XML element is left empty:</span></span>  
  
```  
<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2010" encoding="[base64|hex|string|xml]"/>  
```  
  
 <span data-ttu-id="d340b-185">Les adaptateurs WCF encodent le corps du message BizTalk en fonction de la **codage** d’attribut dans le modèle XML, puis remplacez le **bts-msg-body** élément avec le corps du message BizTalk encodé lors de la création messages WCF sortants.</span><span class="sxs-lookup"><span data-stu-id="d340b-185">The WCF adapters encode the BizTalk message body according to the **encoding** attribute in the XML template, and then replace the **bts-msg-body** element with the encoded BizTalk message body when creating outbound WCF messages.</span></span> <span data-ttu-id="d340b-186">Si le **corps de message WCF sortant - XML** zone de texte est vide, les adaptateurs WCF encodent le corps du message BizTalk dans **Base64**, puis placez le **Base64** de séquence dans le corps du message SOAP sortant.</span><span class="sxs-lookup"><span data-stu-id="d340b-186">If the **Outbound WCF message body - XML** text box is left empty, the WCF adapters encode the BizTalk message body in **Base64**, and then place the **Base64** sequence in the outbound SOAP message body.</span></span>  
  
 <span data-ttu-id="d340b-187">Si le **codage** attribut dans le modèle XML est défini sur **chaîne**, les adaptateurs WCF encodent le corps du message BizTalk en tant que données de type caractère encodé UTF-8, dans lequel les XML caractères spéciaux tels que \< et > sont échappés.</span><span class="sxs-lookup"><span data-stu-id="d340b-187">If the **encoding** attribute in the XML template is set to **string**, the WCF adapters encode the BizTalk message body part as UTF-8 encoded character data, in which the XML special characters such as \< and > are escaped.</span></span>  
  
 <span data-ttu-id="d340b-188">Si le **codage** attribut dans le modèle XML est défini sur **base64** ou **hexadécimal**, les adaptateurs WCF encodent le corps du message BizTalk en tant qu’un **BinHex** ou **Base64** séquence.</span><span class="sxs-lookup"><span data-stu-id="d340b-188">If the **encoding** attribute in the XML template is set to **base64** or **hex**, the WCF adapters encode the BizTalk message body part as a **BinHex** or **Base64** sequence.</span></span>  
  
 <span data-ttu-id="d340b-189">Si le **codage** attribut dans le modèle XML est défini sur **xml**, les adaptateurs WCF remplacent le **bts-msg-body** élément avec le corps du message BizTalk sortant pour créer le messages WCF sortants.</span><span class="sxs-lookup"><span data-stu-id="d340b-189">If the **encoding** attribute in the XML template is set to **xml**, the WCF adapters replace the **bts-msg-body** element with the outbound BizTalk message body to create the outgoing WCF message.</span></span>  
  
 <span data-ttu-id="d340b-190">Par exemple, supposons que les adaptateurs WCF doivent envoyer le corps du message BizTalk suivant à des clients WCF :</span><span class="sxs-lookup"><span data-stu-id="d340b-190">For example, suppose the WCF adapters need to send the following BizTalk message body part to WCF clients:</span></span>  
  
```  
<ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
```  
  
 <span data-ttu-id="d340b-191">Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.</span><span class="sxs-lookup"><span data-stu-id="d340b-191">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  
  
|<span data-ttu-id="d340b-192">Corps de message WCF sortant</span><span class="sxs-lookup"><span data-stu-id="d340b-192">Outbound WCF message body</span></span>|<span data-ttu-id="d340b-193">XML</span><span class="sxs-lookup"><span data-stu-id="d340b-193">XML</span></span>|  
|-------------------------------|---------|  
|<span data-ttu-id="d340b-194">**Corps : Corps du message de réponse de BizTalk**</span><span class="sxs-lookup"><span data-stu-id="d340b-194">**Body -- BizTalk response message body**</span></span>|<span data-ttu-id="d340b-195">Néant</span><span class="sxs-lookup"><span data-stu-id="d340b-195">N/A</span></span>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:6a706a54-c4f5-4767-909d-a992c7c26dba</a:MessageID>  
    <a:ReplyTo>  
<a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="d340b-196">Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.</span><span class="sxs-lookup"><span data-stu-id="d340b-196">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  
  
|<span data-ttu-id="d340b-197">Corps de message WCF sortant</span><span class="sxs-lookup"><span data-stu-id="d340b-197">Outbound WCF message body</span></span>|<span data-ttu-id="d340b-198">XML</span><span class="sxs-lookup"><span data-stu-id="d340b-198">XML</span></span>|  
|-------------------------------|---------|  
|<span data-ttu-id="d340b-199">**Corps : Corps du message de réponse de BizTalk**</span><span class="sxs-lookup"><span data-stu-id="d340b-199">**Body -- BizTalk response message body**</span></span>|<span data-ttu-id="d340b-200">\<Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-200">\<Book></span></span><br /><br /> <span data-ttu-id="d340b-201">\<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = »**chaîne**» / ></span><span class="sxs-lookup"><span data-stu-id="d340b-201">\<**bts-msg-body** xmlns="http://www.microsoft.com/schemas/bts2010" encoding="**string**"/></span></span><br /><br /> <span data-ttu-id="d340b-202">\</ Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-202">\</Book></span></span>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:05dde292-eedd-467e-b0d2-f1b8f0757410</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <Book><ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  <ns0:OrderDetail>    <ns0:CustomerID>CONTOSO</ns0:CustomerID>    <ns0:OrderID> 01A2c</ns0:OrderID>  </ns0:OrderDetail></ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="d340b-203">Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.</span><span class="sxs-lookup"><span data-stu-id="d340b-203">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  
  
|<span data-ttu-id="d340b-204">Corps de message WCF sortant</span><span class="sxs-lookup"><span data-stu-id="d340b-204">Outbound WCF message body</span></span>|<span data-ttu-id="d340b-205">XML</span><span class="sxs-lookup"><span data-stu-id="d340b-205">XML</span></span>|  
|-------------------------------|---------|  
|<span data-ttu-id="d340b-206">**Corps : Corps du message de réponse de BizTalk**</span><span class="sxs-lookup"><span data-stu-id="d340b-206">**Body -- BizTalk response message body**</span></span>|<span data-ttu-id="d340b-207">\<Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-207">\<Book></span></span><br /><br /> <span data-ttu-id="d340b-208">\<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = »**base64**» / ></span><span class="sxs-lookup"><span data-stu-id="d340b-208">\<**bts-msg-body** xmlns="http://www.microsoft.com/schemas/bts2010" encoding="**base64**"/></span></span><br /><br /> <span data-ttu-id="d340b-209">\</ Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-209">\</Book></span></span>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://ww  
w.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe  
/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:cb3cac6d-a542-4a90-bad8-cdbfa8251112</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessSer  
vice</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>77u/PG5zMDpPcmRlciB4bWxuczpuczA9Imh0dHA6Ly9NaWNyb3NvZnQuU2FtcGxlcy5CaX  
pUYWxrLk5ldE5hbWVkUGlwZS9PcmRlclByb2Nlc3MiPg0KICA8bnMwOk9yZGVyRGV0YWlsPg0KICAgID  
xuczA6Q3VzdG9tZXJJRD5DT05UT1NPPC9uczA6Q3VzdG9tZXJJRD4NCiAgICA8bnMwOk9yZGVySUQ+MD  
FBMmM8L25zMDpPcmRlcklEPg0KICA8L25zMDpPcmRlckRldGFpbD4NCjwvbnMwOk9yZGVyPg==</Book  
>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="d340b-210">Si vous configurez le **le corps du message WCF sortant** section comme indiqué dans le tableau suivant, les adaptateurs WCF créent les messages WCF sortants comme indiqué dans le code après le tableau.</span><span class="sxs-lookup"><span data-stu-id="d340b-210">If you configure the **Outbound WCF message body** section as shown in the following table, the WCF adapters create the outbound WCF messages as shown in the code after the table.</span></span>  
  
|<span data-ttu-id="d340b-211">Corps de message WCF sortant</span><span class="sxs-lookup"><span data-stu-id="d340b-211">Outbound WCF message body</span></span>|<span data-ttu-id="d340b-212">XML</span><span class="sxs-lookup"><span data-stu-id="d340b-212">XML</span></span>|  
|-------------------------------|---------|  
|<span data-ttu-id="d340b-213">**Corps : Corps du message de réponse de BizTalk**</span><span class="sxs-lookup"><span data-stu-id="d340b-213">**Body -- BizTalk response message body**</span></span>|<span data-ttu-id="d340b-214">\<Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-214">\<Book></span></span><br /><br /> <span data-ttu-id="d340b-215">\<**BTS-msg-body** xmlns = « http://www.microsoft.com/schemas/bts2010 » encoding = «**xml**« / ></span><span class="sxs-lookup"><span data-stu-id="d340b-215">\<**bts-msg-body** xmlns="http://www.microsoft.com/schemas/bts2010" encoding="**xml**"/></span></span><br /><br /> <span data-ttu-id="d340b-216">\</ Book ></span><span class="sxs-lookup"><span data-stu-id="d340b-216">\</Book></span></span>|  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:A  
ction>  
    <a:MessageID>{513C123C-0600-4A1C-BEE2-EF83E0EFEB15}</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>  
      <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CustomerID_0</ns0:CustomerID>  
    <ns0:OrderID>OrderID_0</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```