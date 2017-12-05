---
title: "À l’aide des champs distinctifs et les champs de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- messages, properties
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b5d5ee3b29c068b3a37d248b9fb20f07bdfbb2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-distinguished-fields-and-property-fields"></a><span data-ttu-id="b2054-102">À l’aide des champs distinctifs et les champs de propriété</span><span class="sxs-lookup"><span data-stu-id="b2054-102">Using Distinguished Fields and Property Fields</span></span>
<span data-ttu-id="b2054-103">les champs distinctifs constituent des données de message d'un intérêt particulier, que vous utilisez essentiellement pour prendre des décisions ou pour manipuler des données dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b2054-103">Distinguished fields are message data of special interest that you use primarily to make decisions or to manipulate data in your orchestration.</span></span>  
  
 <span data-ttu-id="b2054-104">Les propriétés de message sont des données (contenu du message) ou des « métadonnées » (informations contextuelles relatives au message, telles que les horodatages ou les informations de routage).</span><span class="sxs-lookup"><span data-stu-id="b2054-104">Message properties are either data—contents of the message itself—or "metadata"—context information about the message such as time stamps or routing information.</span></span> <span data-ttu-id="b2054-105">Vous pouvez utiliser les propriétés de contexte des messages ou du transport définies par le système, ou définir vos propres propriétés en faisant référence aux champs d'un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="b2054-105">You can use system-defined message context properties or transport context properties, or you can define your own properties by making reference to schema fields from within a property schema.</span></span> <span data-ttu-id="b2054-106">Les propriétés sont utilisées dans les abonnements et les corrélations.</span><span class="sxs-lookup"><span data-stu-id="b2054-106">Properties are used in subscriptions and correlations.</span></span>  
  
-   <span data-ttu-id="b2054-107">Vous pouvez désigner un champ dans un schéma en tant que champ distinctif ou champ de propriété à l’aide de la **promouvoir les propriétés** boîte de dialogue à partir de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b2054-107">You can designate a field in a schema as a distinguished field or property field by using the **Promote Properties** dialog box from within the Editor.</span></span> <span data-ttu-id="b2054-108">Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md)</span><span class="sxs-lookup"><span data-stu-id="b2054-108">For more information, see [Promoting Properties](../core/promoting-properties.md)</span></span>  
  
-   <span data-ttu-id="b2054-109">Vous pouvez désigner un champ d'un type .NET comme champ distinctif en le décorant avec l'attribut DistinguishedField, ou comme propriété avec l'attribut Propriété.</span><span class="sxs-lookup"><span data-stu-id="b2054-109">You can designate a field in a .NET type as a distinguished field by decorating it with the DistinguishedField attribute, or as a property by the Property attribute.</span></span>  
  
## <a name="using-distinguished-fields"></a><span data-ttu-id="b2054-110">Utilisation des champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="b2054-110">Using Distinguished Fields</span></span>  
 <span data-ttu-id="b2054-111">Les champs distinctifs sont désignés par le chemin d'accès au champ dans le message, avec des points séparant le nom du message, les noms des enregistrements qui entourent le champ (le cas échéant) et le nom du champ lui-même :</span><span class="sxs-lookup"><span data-stu-id="b2054-111">Distinguished fields are referred to by the path to the field in the message, using periods to separate the message name, the names of any records that enclose the field, and the name of the field itself:</span></span>  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## <a name="using-property-fields"></a><span data-ttu-id="b2054-112">Utilisation des champs de propriété</span><span class="sxs-lookup"><span data-stu-id="b2054-112">Using Property Fields</span></span>  
 <span data-ttu-id="b2054-113">Une fois un champ ajouté au schéma de propriété, sa valeur est accessible dans le code de l'orchestration et dans les expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="b2054-113">Once you have added a field to a property schema, its value can be accessed in the orchestration with code and in filter expressions.</span></span> <span data-ttu-id="b2054-114">Pour plus d’informations sur les schémas de propriété, consultez [les schémas de propriété](../core/property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="b2054-114">For more information about property schemas, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2054-115">Propriétés de contenu ou les données de message sont essentiellement des raccourcis vers les données sous-jacentes : Si vous modifiez la propriété, les données seront modifiées et vice versa.</span><span class="sxs-lookup"><span data-stu-id="b2054-115">Message content or data properties are essentially shortcuts to the underlying data: if you modify the property, the data will be modified, and vice versa.</span></span>  
  
 <span data-ttu-id="b2054-116">Les propriétés de message sont désignées par le nom du message suivi par l'espace de noms (le schéma) et le nom de propriété entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="b2054-116">Message properties are referred to by the name of the message followed by the namespace (the schema) and property name in parentheses:</span></span>  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  <span data-ttu-id="b2054-117">Lorsque vous utilisez un mot clé réservé comme nom d’un champ dans un schéma et promouvoir le champ en sélectionnant Promotion rapide, le nom de propriété du champ est modifié en __\<mot clé réservé\>.</span><span class="sxs-lookup"><span data-stu-id="b2054-117">When you use a reserved keyword as the name of a field in a schema, and you promote the field by selecting Quick Promotion, the property name of the field is changed to __\<Reserved Keyword\>.</span></span> <span data-ttu-id="b2054-118">(Un double trait de soulignement est ajouté devant le nom de la propriété.) Cependant, si vous utilisez ce nom de propriété dans une expression d'orchestration, vous recevrez une erreur du compilateur lors de la création de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b2054-118">(The double underscore is added before the property name.) However, if you use this property name in an orchestration expression, you will receive a compiler error when building the orchestration.</span></span>  <span data-ttu-id="b2054-119">Pour éviter cette erreur, vous devez ajouter manuellement @ devant le double trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="b2054-119">To work around this error, you need to manually add @ before the double underscore.</span></span> <span data-ttu-id="b2054-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b2054-120">For example,</span></span>  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## <a name="property-sets"></a><span data-ttu-id="b2054-121">Jeux de propriétés</span><span class="sxs-lookup"><span data-stu-id="b2054-121">Property Sets</span></span>  
 <span data-ttu-id="b2054-122">Vous pouvez également assigner toutes les propriétés de contexte d'un message (ou jeu de propriétés) aux propriétés de contexte d'un autre message.</span><span class="sxs-lookup"><span data-stu-id="b2054-122">You can also assign all of the context properties of one message (a property set) to the context properties of another message.</span></span> <span data-ttu-id="b2054-123">Pour assigner un jeu de propriétés, vous devez simplement placer un astérisque entre parenthèses après le nom de chaque message, de la même manière que vous placez une propriété entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="b2054-123">To assign a property set, you simply place an asterisk in parentheses after both message names, in the same way you would put a property in parentheses:</span></span>  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 <span data-ttu-id="b2054-124">Une fois le jeu de propriétés assigné à MyMessage2 dans l'exemple, toutes les propriétés de MyMessage2 ont les mêmes valeurs que les propriétés de MyMessage1.</span><span class="sxs-lookup"><span data-stu-id="b2054-124">After the property set has been assigned to MyMessage2 in the example, all of the properties in MyMessage2 contain the same values as the properties in MyMessage1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2054-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2054-125">See Also</span></span>  
 <span data-ttu-id="b2054-126">[Promotion des propriétés](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b2054-126">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="b2054-127">[Utilisation des filtres avec la forme d’un Message de réception](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="b2054-127">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 <span data-ttu-id="b2054-128">[À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="b2054-128">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="b2054-129">À propos des propriétés de contexte de message BizTalk</span><span class="sxs-lookup"><span data-stu-id="b2054-129">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)