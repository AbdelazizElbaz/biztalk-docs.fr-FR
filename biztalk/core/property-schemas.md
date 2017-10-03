---
title: "Schémas de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8018bb72-a037-4eeb-bbbe-dd0cc6209aec
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2fb50536b2521e77994baf0b6457206614b7eed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-schemas"></a><span data-ttu-id="c7e94-102">Schémas de propriété</span><span class="sxs-lookup"><span data-stu-id="c7e94-102">Property Schemas</span></span>

## <a name="promoted-properties"></a><span data-ttu-id="c7e94-103">Propriétés promues</span><span class="sxs-lookup"><span data-stu-id="c7e94-103">Promoted properties</span></span>
<span data-ttu-id="c7e94-104">Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les propriétés promues permettent à divers composants BizTalk Server d'accéder à des éléments clés de données, connues dans ce contexte sous le nom de champs distinctifs et de champs de propriétés et qui arrivent dans un message d'instance sans avoir besoin de savoir comment les rechercher dans le message lui-même.</span><span class="sxs-lookup"><span data-stu-id="c7e94-104">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], promoted properties enable various BizTalk Server components to access key items of data, known in this context as distinguished fields and property fields that arrive within an instance message without needing to know how to look for them within the message itself.</span></span> <span data-ttu-id="c7e94-105">Vous pouvez déterminer les éléments de données qui requièrent la promotion à un niveau plus visible pour des types de messages différents.</span><span class="sxs-lookup"><span data-stu-id="c7e94-105">For different types of messages, you can determine which items of data require promotion to a more visible level.</span></span> <span data-ttu-id="c7e94-106">Selon la manière dont vous choisissez de promouvoir ces champs, vous pourrez avoir besoin de créer et de définir un schéma de propriété associé.</span><span class="sxs-lookup"><span data-stu-id="c7e94-106">Depending on how you choose to promote such fields, you may need to create and define an associated property schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7e94-107">Les propriétés promues sont limitées à des éléments/attributs non répétés.</span><span class="sxs-lookup"><span data-stu-id="c7e94-107">Promoted properties are restricted to non-repeating elements/attributes.</span></span>  
  
 <span data-ttu-id="c7e94-108">Les champs distinctifs ne sont accessibles que dans les orchestrations et ne nécessitent pas la création d'un schéma de propriété correspondant.</span><span class="sxs-lookup"><span data-stu-id="c7e94-108">Distinguished fields are accessible only within orchestrations and do not require the creation of a corresponding property schema.</span></span> <span data-ttu-id="c7e94-109">Si vous avez uniquement besoin d'accéder à des données de message promues à partir d'une orchestration, vous pouvez les promouvoir sous la forme d'un ou de plusieurs champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="c7e94-109">If you only need to access promoted message data from within an orchestration, you can promote the data as one or more distinguished fields.</span></span>  
  
 <span data-ttu-id="c7e94-110">Les champs de propriété sont accessibles à partir de divers composants BizTalk Server et notamment à partir de pipelines et d'orchestrations.</span><span class="sxs-lookup"><span data-stu-id="c7e94-110">Property fields are accessible from within various BizTalk Server components, including pipelines and orchestrations.</span></span> <span data-ttu-id="c7e94-111">Les champs de propriétés peuvent également être utilisés pour le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="c7e94-111">Property fields can also be used for message routing.</span></span> <span data-ttu-id="c7e94-112">Si vous avez besoin d'accéder à des données de message promues à partir de contextes autres que des orchestrations, vous devez créer un ou plusieurs schémas de propriété pour décrire les données dont vous assurez la promotion.</span><span class="sxs-lookup"><span data-stu-id="c7e94-112">If you need to access promoted message data from contexts other than within orchestrations, you must create one or more property schemas to describe the data you are promoting.</span></span>  
  
 <span data-ttu-id="c7e94-113">Un schéma de propriété est un schéma spécial que l'on associe à un schéma de message.</span><span class="sxs-lookup"><span data-stu-id="c7e94-113">A property schema is a special schema that you associate with a message schema.</span></span> <span data-ttu-id="c7e94-114">On l'utilise pour la promotion de valeurs spécifiques à partir d'un message d'instance vers le contexte de message.</span><span class="sxs-lookup"><span data-stu-id="c7e94-114">It is used for promoting specific values from within an instance message into the message context.</span></span> <span data-ttu-id="c7e94-115">La promotion de propriété fournit un mécanisme centralisé pour extraire des éléments d'information clés que vous définissez à partir d'un message d'instance et pour rendre ces éléments plus accessibles aux composants BizTalk Server qui gèrent le message lors de sa transmission via BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7e94-115">Property promotion provides a centralized mechanism for pulling key pieces of information that you define from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server.</span></span>  
  
## <a name="create-property-schema-overview"></a><span data-ttu-id="c7e94-116">Créer la vue d’ensemble du schéma de propriété</span><span class="sxs-lookup"><span data-stu-id="c7e94-116">Create property schema overview</span></span>
 <span data-ttu-id="c7e94-117">Vous pouvez automatiquement créer un schéma de propriété par défaut en utilisant la fonctionnalité de promotion rapide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7e94-117">You can automatically create a default property schema by using the quick promotion feature of BizTalk Server.</span></span> <span data-ttu-id="c7e94-118">C'est la méthode la plus aisée pour créer le schéma de propriété requis par la promotion de champ de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-118">This is the easiest way to create the property schema required for property field promotion.</span></span> <span data-ttu-id="c7e94-119">Pour plus d’informations sur la réalisation de promotions rapides, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span><span class="sxs-lookup"><span data-stu-id="c7e94-119">For more information about how to perform quick promotions, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
 <span data-ttu-id="c7e94-120">Vous pouvez également créer le nouveau schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-120">You can also create new property schema.</span></span> <span data-ttu-id="c7e94-121">Lorsqu’un projet BizTalk est ouvert, sélectionnez le projet BizTalk, avec le bouton droit et sélectionnez **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="c7e94-121">When a BizTalk project is open, select the BizTalk project, right-click and select **Add**, click **New Item**, and then click **Schema**.</span></span>  
  
> [!NOTE]
>  - <span data-ttu-id="c7e94-122">Si un schéma de propriété est associé à un schéma de message, ils doivent tous deux faire partie du même projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c7e94-122">If a property schema is associated with a message schema, then these two must be in the same BizTalk project.</span></span> <span data-ttu-id="c7e94-123">Séparer un schéma de propriété de son schéma de message associé dans divers projets BizTalk n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c7e94-123">Separating property schema from its associated message schema in different BizTalk projects is not supported.</span></span>  
>
>  - <span data-ttu-id="c7e94-124">Si vous disposez de deux schémas de propriété ayant le même espace de noms, bien qu'ils soient définis dans des assemblys différents, les schémas ne seront pas résolus correctement lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c7e94-124">If you have two property schemas that have the same namespace, even though they are defined in different assemblies, the schemas will not resolve properly at runtime.</span></span> <span data-ttu-id="c7e94-125">Vous obtiendrez une erreur de routage lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c7e94-125">You will get a routing failure at runtime.</span></span>  

## <a name="distinguished-fields-and-property-fields"></a><span data-ttu-id="c7e94-126">Les champs distinctifs et les champs de propriété</span><span class="sxs-lookup"><span data-stu-id="c7e94-126">Distinguished fields and property fields</span></span> 
 <span data-ttu-id="c7e94-127">Il existe deux types de promotions de propriétés : champs distinctifs et les champs de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-127">There are two types of property promotion: distinguished fields and property fields.</span></span> <span data-ttu-id="c7e94-128">Le deuxième cité utilise des schémas de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-128">The latter type uses property schemas.</span></span> <span data-ttu-id="c7e94-129">Dans l’Éditeur BizTalk, vous gérez ces deux types de promotions de propriétés à l’aide de la **promouvoir les propriétés** boîte de dialogue, vous accédez en utilisant le **promouvoir les propriétés** propriété de la  **Schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="c7e94-129">In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which you access by using the **Promote Properties** property of the **Schema** node.</span></span>  
  
> [!NOTE]
>  - <span data-ttu-id="c7e94-130">Il existe certaines restrictions concernant les valeurs qu'il est possible de promouvoir.</span><span class="sxs-lookup"><span data-stu-id="c7e94-130">There are some restrictions on values that you can promote.</span></span> <span data-ttu-id="c7e94-131">Pour plus d’informations, consultez le tableau dans [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c7e94-131">For more information, see the table in [Promoting Properties](../core/promoting-properties.md).</span></span>  
>
>  - <span data-ttu-id="c7e94-132">Les champs distinctifs n'apparaissent pas dans les expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="c7e94-132">Distinguished fields do not appear in filter expressions.</span></span> <span data-ttu-id="c7e94-133">C'est uniquement le cas des champs de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-133">Only property fields appear in filter expressions.</span></span>  
  
 <span data-ttu-id="c7e94-134">Les schémas de propriété sont simples comparés aux schémas de message.</span><span class="sxs-lookup"><span data-stu-id="c7e94-134">Property schemas are simple when compared to message schemas.</span></span> <span data-ttu-id="c7e94-135">Dans l’arborescence du schéma, vous êtes uniquement autorisé à insérer **élément de champ** nœuds en tant que nœuds enfants immédiats de le **schéma** nœud, en créant une structure qui comprend deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="c7e94-135">In the schema tree, you are only allowed to insert **Field Element** nodes as immediate child nodes of the **Schema** node, creating a structure that is two levels deep.</span></span> <span data-ttu-id="c7e94-136">Dans la plupart des cas, vous définissez les propriétés de la **élément de champ** nœuds comme vous le feriez pour **élément de champ** nœuds figurant dans un schéma de message.</span><span class="sxs-lookup"><span data-stu-id="c7e94-136">For the most part, you set the properties of the **Field Element** nodes as you would for **Field Element** nodes appearing in a message schema.</span></span> <span data-ttu-id="c7e94-137">Vous êtes limité à utilisation des seuls types simples XSD.</span><span class="sxs-lookup"><span data-stu-id="c7e94-137">You are limited to using only XSD simple types.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7e94-138">Ne renommez pas un schéma utilisé par un autre schéma.</span><span class="sxs-lookup"><span data-stu-id="c7e94-138">You should not rename any schema that is being used by another schema.</span></span> <span data-ttu-id="c7e94-139">Cela concerne également les schémas de propriété pour lesquels des promotions ont déjà été établies.</span><span class="sxs-lookup"><span data-stu-id="c7e94-139">This includes property schemas for which promotions have already been established.</span></span> <span data-ttu-id="c7e94-140">Si vous ne respectez pas cette règle, le schéma utilisé ne pourra pas retrouver l'autre schéma, car le nom qu'il contient ne sera plus exact.</span><span class="sxs-lookup"><span data-stu-id="c7e94-140">If you do so, the schema that is being used will not be able to find the other schema because the name it contains will no longer be accurate.</span></span>  
  
 <span data-ttu-id="c7e94-141">Le **Property Schema Base** propriété est unique **élément de champ** nœuds tels qu’ils apparaissent dans les schémas de propriété.</span><span class="sxs-lookup"><span data-stu-id="c7e94-141">The **Property Schema Base** property is unique to **Field Element** nodes as they appear in property schemas.</span></span> <span data-ttu-id="c7e94-142">Cette propriété est vide par défaut, mais peut être définie avec la valeur **MessageDataPropertyBase** ou **MessageContextPropertyBase**, ce qui engendre une **propSchFieldBase** attribut ajouté à la **fieldInfo** élément d’annotation avec une ou l’autre de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="c7e94-142">This property is blank by default, but can be set to either **MessageDataPropertyBase** or **MessageContextPropertyBase**, resulting in a **propSchFieldBase** attribute being added to the **fieldInfo** annotation element with one or the other of these values.</span></span>  
  
 <span data-ttu-id="c7e94-143">Lorsque le **propSchFieldBase** attribut a la valeur **MessageDataPropertyBase**, cela signifie que la valeur de la propriété promue correspond aux données dans le message, telles que la valeur d’un champ.</span><span class="sxs-lookup"><span data-stu-id="c7e94-143">When the **propSchFieldBase** attribute is set to **MessageDataPropertyBase**, it means that the value of the promoted property corresponds to data in the message, such as the value of some field.</span></span> <span data-ttu-id="c7e94-144">Lorsque le **propSchFieldBase** attribut a la valeur **MessageContextPropertyBase**, cela signifie que la valeur de la propriété promue peut-être provenir d’un autre endroit, par exemple une enveloppe, ou qu’il peut être définie par un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c7e94-144">When the **propSchFieldBase** attribute is set to **MessageContextPropertyBase**, it means that the value of the promoted property may be from somewhere else, such as an envelope, or that it may be set by a pipeline component.</span></span>  
  
 <span data-ttu-id="c7e94-145">**Élément de champ** nœuds dans les schémas de propriété possèdent également une propriété appelée **des informations sensibles**, lorsque la valeur **Oui**, empêche la valeur correspondante d’être visible à partir de L’Explorateur BizTalk et le message d’événement et instances de service de suivi, conservant ainsi sa nature confidentielle.</span><span class="sxs-lookup"><span data-stu-id="c7e94-145">**Field Element** nodes in property schemas also have a property called **Sensitive Information**, which when set to **Yes**, will keep the corresponding value from being visible from within BizTalk Explorer and message event and service instance tracking, thereby preserving its sensitive nature.</span></span>  <span data-ttu-id="c7e94-146">Consultez **des informations sensibles** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="c7e94-146">See **Sensitive Information** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for more details.</span></span>
  
 <span data-ttu-id="c7e94-147">La représentation de langage XSD (XML Schema Definition) suivante d'un schéma de propriété contient une annotation associée à l'élément de schéma qui identifie ce schéma en tant que schéma de propriété (schema_type="property").</span><span class="sxs-lookup"><span data-stu-id="c7e94-147">The following XML Schema definition (XSD) language representation of a property schema contains an annotation associated with the schema element that identifies this schema as a property schema (schema_type="property").</span></span> <span data-ttu-id="c7e94-148">Il contient également trois **Fieldelement** nœuds ci-dessous le **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="c7e94-148">It also contains three **Field Element** nodes below the **Schema** node.</span></span> <span data-ttu-id="c7e94-149">La première **élément de champ** nœud, nommé PromProp1, n’a pas une valeur définie pour sa **Property Schema Base** propriété, mais les deux derniers **élément de champ** nœuds ont qui propriété **MessageDataPropertyBase** et **MessageContextPropertyBase**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="c7e94-149">The first **Field Element** node, named PromProp1, does not have a value defined for its **Property Schema Base** property, but the latter two **Field Element** nodes have that property set to **MessageDataPropertyBase** and **MessageContextPropertyBase**, respectively.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
           targetNamespace="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
       <xs:appinfo>  
  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7e94-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7e94-150">See Also</span></span>  
 [<span data-ttu-id="c7e94-151">Différents Types de schémas BizTalk</span><span class="sxs-lookup"><span data-stu-id="c7e94-151">Different Types of BizTalk Schemas</span></span>](../core/different-types-of-biztalk-schemas.md)