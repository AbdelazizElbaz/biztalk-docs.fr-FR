---
title: "Utilisation des en-têtes SOAP dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, properties
- Web services, SOAP headers
- orchestrations, SOAP headers
- creating, SOAP headers
ms.assetid: 4754dd23-386b-4093-8ea4-4da6b4d9279c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faae7013c824926adea67feab296e1993f93e326
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-orchestrations"></a><span data-ttu-id="3ebc0-102">Utilisation des en-têtes SOAP dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="3ebc0-102">Using SOAP Headers in Orchestrations</span></span>
<span data-ttu-id="3ebc0-103">Les schémas de propriété permettent aux orchestrations de définir des propriétés de contexte d'en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-103">Orchestrations use property schemas to define SOAP header context properties.</span></span> <span data-ttu-id="3ebc0-104">L'Éditeur BizTalk vous permet de définir ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-104">You use the BizTalk Editor to set SOAP header context properties.</span></span>  
  
## <a name="defining-soap-header-context-properties-with-property-schemas"></a><span data-ttu-id="3ebc0-105">Définition de propriétés de contexte d'en-tête SOAP à l'aide de schémas de propriété</span><span class="sxs-lookup"><span data-stu-id="3ebc0-105">Defining SOAP header context properties with property schemas</span></span>  
 <span data-ttu-id="3ebc0-106">Un schéma de propriété est requis pour utiliser dans les orchestrations des propriétés de contexte d'en-tête SOAP définies.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-106">You need a property schema to use defined SOAP header context properties in orchestrations.</span></span> <span data-ttu-id="3ebc0-107">Le schéma de propriété doit avoir l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**et le **Property Schema Base** propriété  **MessageContextPropertyBase**.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-107">The property schema must have the target namespace of **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**, and the **Property Schema Base** property set to **MessageContextPropertyBase**.</span></span> <span data-ttu-id="3ebc0-108">Chaque nom d'élément racine du schéma de propriété doit correspondre au nom de l'élément racine de l'en-tête SOAP défini.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-108">Each root element name in the property schema must match the root element name in the defined SOAP header.</span></span> <span data-ttu-id="3ebc0-109">Vous pouvez ensuite définir des valeurs pour les propriétés de contexte en reprenant l'espace de noms du schéma de propriété et le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-109">You can then set values for the context properties using the namespace of the property schema and the property name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ebc0-110">L’espace de noms du schéma de propriété est différente de l’espace de noms du schéma cible (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-110">The namespace of the property schema is different from the namespace of the target schema (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**).</span></span> <span data-ttu-id="3ebc0-111">Votre espace de noms peut prendre la forme de n'importe quelle chaîne ; toutefois, il utilise généralement la valeur par défaut qu'est le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-111">Your namespace can be any string; however, it usually defaults to the name of the project.</span></span>  
  
 <span data-ttu-id="3ebc0-112">Le code suivant illustre l’assignation d’une propriété de contexte d’en-tête SOAP dans lequel l’espace de noms de schéma de propriété est **SOAPHeader** avec le nom de la propriété **OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="3ebc0-112">The following code shows assigning a SOAP header context property where the property schema namespace is **SOAPHeader** with a property name of **OrigDest**:</span></span>  
  
```  
requestMessageInstance(SOAPHeader.OrigDest) = stringVar;  
```  
  
 <span data-ttu-id="3ebc0-113">Pour plus d’informations sur les schémas de propriété et les propriétés de contexte, consultez [les schémas de propriété](../core/property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-113">For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
## <a name="using-biztalk-editor-to-set-soap-header-context-properties"></a><span data-ttu-id="3ebc0-114">Utilisation de l'Éditeur BizTalk pour définir des propriétés de contexte d'en-tête SOAP</span><span class="sxs-lookup"><span data-stu-id="3ebc0-114">Using BizTalk Editor to set SOAP header context properties</span></span>  
 <span data-ttu-id="3ebc0-115">Pour les orchestrations, les propriétés de contexte d'en-tête SOAP sont définies sur les chaînes qui contiennent des données XML.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-115">For orchestrations, the SOAP header context properties are set to strings that contain XML data.</span></span> <span data-ttu-id="3ebc0-116">Vous pouvez définir celles-ci à l’aide de l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-116">You set these strings using the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span>  
  
 <span data-ttu-id="3ebc0-117">L'exemple suivant illustre la chaîne définissant la propriété de contexte :</span><span class="sxs-lookup"><span data-stu-id="3ebc0-117">The following example shows the string setting the context property:</span></span>  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = "<?xml version=\"1.0\"?>  
<OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
<Origination>Home</Origination>  
<Destination>Work</Destination>  
</OrigDest>"  
```  
  
## <a name="using-biztalk-editor-to-create-an-instance-of-a-soap-header-root-element"></a><span data-ttu-id="3ebc0-118">Utilisation de l'Éditeur BizTalk pour créer une instance d'un élément racine d'en-tête SOAP</span><span class="sxs-lookup"><span data-stu-id="3ebc0-118">Using BizTalk Editor to create an instance of a SOAP header root element</span></span>  
 <span data-ttu-id="3ebc0-119">Il peut être difficile de configurer l'en-tête SOAP sur la chaîne appropriée.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-119">Setting the SOAP header to the correct string can be difficult.</span></span> <span data-ttu-id="3ebc0-120">Lors de l'ajout d'une référence Web à un projet BizTalk, toutes les parties d'un message Web complexe sont ajoutées en tant qu'éléments racines au fichier Reference.xsd.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-120">When adding a Web reference to a BizTalk project, all complex Web message parts are added to Reference.xsd as root elements.</span></span> <span data-ttu-id="3ebc0-121">Ce fichier contient également les éléments racines de chaque en-tête SOAP défini.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-121">Reference.xsd also contains root elements for each defined SOAP header.</span></span> <span data-ttu-id="3ebc0-122">Pour garantir que vous ayez défini l'en-tête SOAP sur la bonne chaîne, il est recommandé d'utiliser l'Éditeur BizTalk pour créer une instance de l'élément racine de l'en-tête SOAP correspondant à Reference.xsd.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-122">To ensure that you set the SOAP header with the correct string, you should use BizTalk Editor to create an instance of the SOAP header root element for Reference.xsd.</span></span> <span data-ttu-id="3ebc0-123">Les données de l'instance générées ou les données de l'instance peuvent être utilisées directement ou servir à contenir les données réelles.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-123">You can use the generated instance data directly or the instance data to contain your real data.</span></span>  
  
 <span data-ttu-id="3ebc0-124">Pour plus d’informations sur l’utilisation de l’Éditeur BizTalk pour générer des données d’instance, consultez [comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-124">For more information about using the BizTalk Editor to generate instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).</span></span>  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a><span data-ttu-id="3ebc0-125">Création d'un élément XmlDocument pour définir des propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="3ebc0-125">Creating an XmlDocument to set context properties</span></span>  
 <span data-ttu-id="3ebc0-126">Vous pouvez définir des propriétés de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-126">You can set context properties by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span> <span data-ttu-id="3ebc0-127">Vous déclarez une variable de type **XMLDocument** et affecter les données XML.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-127">You declare a variable of type **XMLDocument** and assign the XML data.</span></span>  
  
 <span data-ttu-id="3ebc0-128">L’exemple suivant illustre la définition d’une déclaration d’une variable de type **XMLDocument** et affecter les données XML :</span><span class="sxs-lookup"><span data-stu-id="3ebc0-128">The following example shows setting a declaring a variable of type **XMLDocument** and assign the XML data:</span></span>  
  
```  
xmlDoc.LoadXml("<?xml version=\"1.0\"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination>Home</Origination><Destination>Work</Destination></OrigDest>");  
```  
  
 <span data-ttu-id="3ebc0-129">L'exemple suivant illustre la configuration de la propriété de contexte :</span><span class="sxs-lookup"><span data-stu-id="3ebc0-129">The following example shows setting the context property:</span></span>  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = xmlDoc.OuterXml;  
```  
  
 <span data-ttu-id="3ebc0-130">Pour plus d’informations sur l’utilisation de l’éditeur d’Expression BizTalk, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-130">For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span> <span data-ttu-id="3ebc0-131">Pour plus d’informations sur l’appel des classes .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-131">For more information about calling .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="creating-soap-headers-for-a-soap-request"></a><span data-ttu-id="3ebc0-132">Création d'en-têtes SOAP pour une requête SOAP</span><span class="sxs-lookup"><span data-stu-id="3ebc0-132">Creating SOAP headers for a SOAP request</span></span>  
 <span data-ttu-id="3ebc0-133">Lors de la création d'en-têtes SOAP pour une requête SOAP, vous devez en premier lieu vous assurer d'avoir correctement créé les en-têtes SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-133">When you create SOAP headers for the SOAP request, you must ensure that you have correctly created the SOAP headers.</span></span> <span data-ttu-id="3ebc0-134">L'adaptateur SOAP ne vérifie pas le contenu des propriétés de contexte d'un en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-134">The SOAP adapter does not verify the contents of the SOAP header context properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ebc0-135">Si l'en-tête est incorrect, BizTalk ne sera pas en mesure d'envoyer la requête SOAP au service Web.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-135">If the SOAP header is incorrect, BizTalk cannot send the SOAP request to the Web service.</span></span>  
  
 <span data-ttu-id="3ebc0-136">La réponse SOAP que BizTalk renvoie au service Web est également susceptible de contenir des en-têtes SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-136">The SOAP response that BizTalk returns to the Web service may also contain SOAP headers.</span></span> <span data-ttu-id="3ebc0-137">Vous pouvez uniquement accéder à ces en-têtes s'il s'agit d'en-têtes SOAP définis.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-137">You can only access these SOAP headers if they are defined SOAP headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ebc0-138">Les services Web utilisés prennent uniquement en charge les en-têtes SOAP définis.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-138">Consumed Web services support only defined SOAP headers.</span></span>  
  
 <span data-ttu-id="3ebc0-139">Pour plus d’informations sur les en-têtes SOAP définis, consultez [à l’aide des en-têtes SOAP](../core/using-soap-headers.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-139">For more information about defined SOAP headers, see [Using SOAP Headers](../core/using-soap-headers.md).</span></span> <span data-ttu-id="3ebc0-140">Les en-têtes SOAP de réponse sont définis en tant que propriétés de contexte grâce à la même syntaxe que celle des en-têtes SOAP de requête.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-140">The response SOAP headers are set to context properties using the same syntax as the request SOAP headers.</span></span>  
  
 <span data-ttu-id="3ebc0-141">Le code suivant illustre l'accès aux en-têtes SOAP de réponse :</span><span class="sxs-lookup"><span data-stu-id="3ebc0-141">The following code shows how to access the response SOAP headers:</span></span>  
  
```  
stringVar = ResponseMessageInstance(SOAPHeader.OrigDest);  
```  
  
 <span data-ttu-id="3ebc0-142">Les valeurs contenues dans les propriétés de contexte correspondent à des chaînes comportant des données XML.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-142">The values contained in the context properties are strings containing XML data.</span></span> <span data-ttu-id="3ebc0-143">Vous pouvez définir celles-ci à l’aide d’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-143">You set these strings using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span> <span data-ttu-id="3ebc0-144">Chargement de la chaîne dans un **XmlDocument** et utiliser des requêtes XPath pour accéder aux champs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3ebc0-144">You load the string in an **XmlDocument** and use XPath queries to access specific fields.</span></span>  
  
 <span data-ttu-id="3ebc0-145">Pour plus d’informations sur la création de documents XML dans Éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc0-145">For more information about creating XML documents in BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ebc0-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ebc0-146">See Also</span></span>  
 <span data-ttu-id="3ebc0-147">[Langage XLANG-s](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="3ebc0-147">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 [<span data-ttu-id="3ebc0-148">En-têtes SOAP avec les Services Web utilisés</span><span class="sxs-lookup"><span data-stu-id="3ebc0-148">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)