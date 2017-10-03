---
title: "Accès aux en-têtes SOAP dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, properties
- orchestrations, SOAP headers
ms.assetid: 91fe053a-3f16-497c-b4bb-5fb54bec62e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 516b2bcc57bef507a028f30c61fd329a5fd7a598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-orchestrations"></a><span data-ttu-id="f5d78-102">Accès aux en-têtes SOAP dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="f5d78-102">Accessing SOAP Headers in Orchestrations</span></span>
<span data-ttu-id="f5d78-103">Vous pouvez accéder aux propriétés de contexte des en-têtes SOAP définis et inconnus dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="f5d78-103">You can access the SOAP header context properties in orchestrations for defined and unknown SOAP headers.</span></span> <span data-ttu-id="f5d78-104">Pour plus d’informations sur les schémas de propriété et les propriétés de contexte, consultez [les schémas de propriété](../core/property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="f5d78-104">For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
## <a name="defined-soap-header-context-properties"></a><span data-ttu-id="f5d78-105">Propriétés de contexte des en-têtes SOAP définis</span><span class="sxs-lookup"><span data-stu-id="f5d78-105">Defined SOAP header context properties</span></span>  
 <span data-ttu-id="f5d78-106">Les propriétés de contexte d’en-tête SOAP défini dans les orchestrations nécessitent un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="f5d78-106">The defined SOAP header context properties in orchestrations require a property schema.</span></span> <span data-ttu-id="f5d78-107">Le schéma de propriété doit avoir l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**et le **Property Schema Base** propriété  **MessageContextPropertyBase**.</span><span class="sxs-lookup"><span data-stu-id="f5d78-107">The property schema must have the target namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**, and the **Property Schema Base** property set to **MessageContextPropertyBase**.</span></span> <span data-ttu-id="f5d78-108">Chaque nom d’élément racine dans le schéma de propriété doit correspondre au nom d’élément de la racine de l’en-tête SOAP défini.</span><span class="sxs-lookup"><span data-stu-id="f5d78-108">Each root element name in the property schema must match the root element name of the defined SOAP header.</span></span> <span data-ttu-id="f5d78-109">Vous pouvez ensuite accédez aux valeurs des propriétés de contexte à l'aide de l'espace de noms du schéma de propriété et à l'aide du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f5d78-109">You can then access the values of the context properties using the namespace of the property schema and the property name.</span></span> <span data-ttu-id="f5d78-110">L'espace de noms du schéma de propriété diffère de l'espace de noms cible mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="f5d78-110">The namespace of the property schema is different from the target namespace listed above.</span></span> <span data-ttu-id="f5d78-111">Bien que l’espace de noms du schéma de propriété peut être n’importe quelle chaîne, généralement la valeur par défaut le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="f5d78-111">Although the namespace of the property schema can be any string, it usually defaults to the name of the project.</span></span>  
  
 <span data-ttu-id="f5d78-112">L’exemple suivant illustre l’accès à la propriété de contexte d’en-tête SOAP pour un espace de noms du schéma de propriété, **SOAPHeader**et le nom de propriété **OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="f5d78-112">The following example shows accessing the SOAP header context property for a property schema namespace, **SOAPHeader**, and the property name **OrigDest**:</span></span>  
  
```  
stringVar = requestMessageInstance(SOAPHeader.OrigDest);  
```  
  
> [!NOTE]
>  <span data-ttu-id="f5d78-113">Les en-têtes SOAP définis sont traités en tant qu'en-têtes d'« entrée » ou de « sortie ».</span><span class="sxs-lookup"><span data-stu-id="f5d78-113">Defined SOAP headers are treated either as "in" or "out" headers.</span></span> <span data-ttu-id="f5d78-114">Si l'Assistant définit le même en-tête SOAP pour le message de requête et pour le message de réponse, il ne renvoie pas automatiquement la valeur d'entrée dans la réponse.</span><span class="sxs-lookup"><span data-stu-id="f5d78-114">If the wizard defines the same SOAP header for the request and response message, the wizard does not automatically return the incoming value in the response.</span></span> <span data-ttu-id="f5d78-115">Vous devez explicitement copier la propriété de contexte de l'en-tête SOAP du message de requête dans celle du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="f5d78-115">You must explicity copy the SOAP header context property of the request message to the SOAP header context property of the response message.</span></span>  
  
## <a name="copying-soap-header-context-property-of-incoming-message"></a><span data-ttu-id="f5d78-116">Copie de la propriété de contexte de l'en-tête SOAP d'un message entrant</span><span class="sxs-lookup"><span data-stu-id="f5d78-116">Copying SOAP header context property of incoming message</span></span>  
 <span data-ttu-id="f5d78-117">Vous pouvez copier la propriété de contexte de l'en-tête SOAP d'un message entrant dans celle d'un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="f5d78-117">You can copy the SOAP header context property of an incoming message to the same SOAP header context property of the response message.</span></span>  
  
 <span data-ttu-id="f5d78-118">L'exemple suivant illustre la copie de la propriété de contexte d'un en-tête SOAP :</span><span class="sxs-lookup"><span data-stu-id="f5d78-118">The following example shows copying the SOAP header context property:</span></span>  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = RequestMessageInstance(SOAPHeader.OrigDest);  
```  
  
 <span data-ttu-id="f5d78-119">Lors de la création d'en-têtes SOAP pour une réponse SOAP, vous devez en premier lieu vous assurer d'avoir correctement créé les en-têtes SOAP.</span><span class="sxs-lookup"><span data-stu-id="f5d78-119">When you create SOAP headers for the SOAP response, you ensure that you create your SOAP headers correctly.</span></span> <span data-ttu-id="f5d78-120">L'adaptateur SOAP ne vérifie pas le contenu des propriétés de contexte d'un en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="f5d78-120">The SOAP adapter does not verify the contents of the SOAP header context properties.</span></span> <span data-ttu-id="f5d78-121">Si le message de réponse contient des valeurs d'en-têtes SOAP erronées, l'adaptateur SOAP ne peut pas l'envoyer à l'utilisateur de votre service Web.</span><span class="sxs-lookup"><span data-stu-id="f5d78-121">If the values of the response SOAP headers are incorrect, the SOAP adapter cannot send the response message to the consumer of your Web service.</span></span>  
  
## <a name="unknown-soap-header-context-property"></a><span data-ttu-id="f5d78-122">Propriétés de contexte des en-têtes SOAP inconnus</span><span class="sxs-lookup"><span data-stu-id="f5d78-122">Unknown SOAP header context property</span></span>  
 <span data-ttu-id="f5d78-123">La propriété de contexte d'un en-tête SOAP inconnu n'a pas besoin d'un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="f5d78-123">The unknown SOAP header context property does not require a property schema.</span></span> <span data-ttu-id="f5d78-124">Vous pouvez accéder à cette propriété de contexte global **SOAP. UnknownHeaders**.</span><span class="sxs-lookup"><span data-stu-id="f5d78-124">You can access this global context property **SOAP.UnknownHeaders**.</span></span>  
  
 <span data-ttu-id="f5d78-125">L’exemple suivant illustre l’accès à la propriété de contexte d’en-tête SOAP inconnu **SOAP. UnknownHeaders**:</span><span class="sxs-lookup"><span data-stu-id="f5d78-125">The following example shows accessing the unknown SOAP header context property **SOAP.UnknownHeaders**:</span></span>  
  
```  
stringVar = RequestMessageInstance(SOAP.UnknownHeaders);  
```  
  
 <span data-ttu-id="f5d78-126">Les valeurs contenues dans les propriétés de contexte correspondent à des chaînes comportant des données XML.</span><span class="sxs-lookup"><span data-stu-id="f5d78-126">The values contained in the context properties are strings containing XML data.</span></span> <span data-ttu-id="f5d78-127">Pour accéder à ces données le plus simple consiste à utiliser l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** mettre en forme et de charger la chaîne dans un **XmlDocument** et utiliser Requêtes XPATH pour accéder aux champs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f5d78-127">The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape and load the string in an **XmlDocument** and use XPATH queries to access specific fields.</span></span> <span data-ttu-id="f5d78-128">Pour plus d’informations, création de documents XML dans l’éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).</span><span class="sxs-lookup"><span data-stu-id="f5d78-128">For more information creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
 <span data-ttu-id="f5d78-129">Les propriétés de contexte sont associées à un message spécifique.</span><span class="sxs-lookup"><span data-stu-id="f5d78-129">Context properties are associated with a particular message.</span></span> <span data-ttu-id="f5d78-130">Le moteur de messagerie ne mappe pas automatiquement les valeurs des en-têtes SOAP connus depuis un message de requête vers un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="f5d78-130">The Messaging Engine does not automatically map the values of known SOAP headers from the request message to the response message.</span></span> <span data-ttu-id="f5d78-131">Lors de la création d'un message de réponse pour un service Web, vous devez définir de manière spécifique les valeurs de l'en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="f5d78-131">When creating the response message for a Web service, you must specifically set the SOAP header values.</span></span> <span data-ttu-id="f5d78-132">La commande suivante est la méthode la plus simple de configurer une propriété de contexte d’en-tête SOAP :</span><span class="sxs-lookup"><span data-stu-id="f5d78-132">The following command is the simplest method of setting a SOAP header context property:</span></span>  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = "<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination xmlns=\"\">Home</Origination><Destination xmlns=\"\">Work</Destination> </OrigDest>"  
```  
  
 <span data-ttu-id="f5d78-133">Vous pouvez également y parvenir en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="f5d78-133">You can also achieve this by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5d78-134">Si le **SOAP. UnknownHeaders** propriété est null, BizTalk renvoie automatiquement les en-têtes inconnus reçus dans la demande SOAP à la réponse SOAP.</span><span class="sxs-lookup"><span data-stu-id="f5d78-134">If the **SOAP.UnknownHeaders** property is null, BizTalk automatically returns the unknown headers received in the SOAP request to the SOAP response.</span></span> <span data-ttu-id="f5d78-135">Si le **SOAP. UnknownHeaders** propriété de contexte du message de réponse n’est pas null, puis BizTalk renvoie cette valeur à la réponse SOAP.</span><span class="sxs-lookup"><span data-stu-id="f5d78-135">If the **SOAP.UnknownHeaders** context property on the response message is not null, then BizTalk returns that value to the SOAP response.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d78-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5d78-136">See Also</span></span>  
 [<span data-ttu-id="f5d78-137">En-têtes SOAP avec les Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="f5d78-137">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)