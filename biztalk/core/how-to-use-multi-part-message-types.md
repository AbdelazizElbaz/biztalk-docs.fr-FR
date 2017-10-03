---
title: "Comment utiliser les Types de Message à parties multiples | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi-part message types, parts
- multi-part message types, creating
- multi-part message types, type modifiers
- messages
- multi-part message types, deleting
- orchestrations, messages
- deleting, multi-part messages
- multi-part message types, about multi-part message types
- orchestrations, type modifier
- messages, multi-parts
- creating, multi-part messages
- messages, about messages
ms.assetid: 009a39bd-cfc4-42d9-918c-88ac24bfc370
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87f210c4b0d2969edc9ddfa27b1d8494310eb6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-multi-part-message-types"></a><span data-ttu-id="d3707-102">Comment utiliser les Types de Message à parties multiples</span><span class="sxs-lookup"><span data-stu-id="d3707-102">How to Use Multi-part Message Types</span></span>
<span data-ttu-id="d3707-103">Chaque message possède un type de message à parties multiples (description de la structure du message qui est composée de zéro partie ou plus).</span><span class="sxs-lookup"><span data-stu-id="d3707-103">Each message has a multi-part message type, a description of the message structure that consists of zero or more message parts.</span></span> <span data-ttu-id="d3707-104">Les parties sont déterminées par les schémas de langage XSD (XML Schema Definition) ou les classes .NET.</span><span class="sxs-lookup"><span data-stu-id="d3707-104">The parts are defined by XML Schema Definition (XSD) language schemas or .NET classes.</span></span> <span data-ttu-id="d3707-105">Vous avez la possibilité de définir vos propres types de messages à parties multiples ou d'utiliser les classes .NET et schémas existants.</span><span class="sxs-lookup"><span data-stu-id="d3707-105">You can define your own multi-part message types, or you can use existing .NET classes and schemas.</span></span>  
  
 <span data-ttu-id="d3707-106">Vous pouvez accéder directement à des parties de messages ou les affecter à partir de votre orchestration. Vous avez également la possibilité d'utiliser des éléments distincts des parties de message exposées en tant que champs distinctifs ou champs de propriété.</span><span class="sxs-lookup"><span data-stu-id="d3707-106">You can access or assign message parts directly within your orchestration, or you can use individual elements of message parts that are exposed as distinguished fields or property fields.</span></span> <span data-ttu-id="d3707-107">Pour plus d’informations, consultez [à l’aide des champs distinctifs et les propriétés de Message](../core/using-distinguished-fields-and-property-fields.md).</span><span class="sxs-lookup"><span data-stu-id="d3707-107">For more information, see [Using Distinguished Fields and Message Properties](../core/using-distinguished-fields-and-property-fields.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3707-108">Un type de message à parties multiples ne contient pas forcément plusieurs parties.</span><span class="sxs-lookup"><span data-stu-id="d3707-108">A multi-part message type does not necessarily contain multiple parts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3707-109">Une partie de message peut être définie par le type .NET **XmlDocument**, qui peut être utilisé pour contenir un document XML arbitraire, type de prise en charge de sérialisation personnalisée par n’importe quel type .NET qui est sérialisable XML, ou un .NET.</span><span class="sxs-lookup"><span data-stu-id="d3707-109">A message part can be defined by the .NET type **XmlDocument**, which can be used to contain an arbitrary XML document, by any .NET type that is XML-serializable, or by any .NET type supporting custom serialization.</span></span>  
  
## <a name="add-a-multi-part-message-type"></a><span data-ttu-id="d3707-110">Ajouter un type de message à parties multiples</span><span class="sxs-lookup"><span data-stu-id="d3707-110">Add a multi-part message type</span></span>  
  
1.  <span data-ttu-id="d3707-111">Dans le **Vue Orchestration** fenêtre, développez le **Types** nœud.</span><span class="sxs-lookup"><span data-stu-id="d3707-111">In the **Orchestration View** window, expand the **Types** node.</span></span>  
  
2.  <span data-ttu-id="d3707-112">Avec le bouton droit **Types Message à parties multiples** puis cliquez sur **nouveau Type de Message de parties multiples**.</span><span class="sxs-lookup"><span data-stu-id="d3707-112">Right-click **Multi-part Message Types** and then click **New Multi-part Message Type**.</span></span>  
  
     <span data-ttu-id="d3707-113">Le **Types Message à parties multiples** dossier se développe, s’il était réduit et un nouveau type de message à parties multiples est ajouté avec la partie de message par défaut.</span><span class="sxs-lookup"><span data-stu-id="d3707-113">The **Multi-part Message Types** folder expands, if collapsed, and a new multi-part message type is added with one default message part.</span></span>  
  
3.  <span data-ttu-id="d3707-114">Nommez ce type ainsi que la partie du message fournie.</span><span class="sxs-lookup"><span data-stu-id="d3707-114">Name the multi-part message type and the provided message part.</span></span>  
  
     <span data-ttu-id="d3707-115">Si votre type de message à parties multiples nécessite plus d’une partie de message, vous pouvez ajouter des parties supplémentaires en affectant un nom pour le \<Nouveau > partie de message.</span><span class="sxs-lookup"><span data-stu-id="d3707-115">If your multi-part message type requires more than one message part, you can add additional parts by assigning a name to the \<New> message part.</span></span>  
  
4.  <span data-ttu-id="d3707-116">Associez chaque partie du message à un type, comme une classe .NET ou un schéma.</span><span class="sxs-lookup"><span data-stu-id="d3707-116">Associate each message part with a type, such as a .NET class or schema.</span></span>  
  
## <a name="remove-a-multi-part-message-type"></a><span data-ttu-id="d3707-117">Supprimer un type de message à parties multiples</span><span class="sxs-lookup"><span data-stu-id="d3707-117">Remove a multi-part message type</span></span>  
  
-   <span data-ttu-id="d3707-118">Dans le **Vue Orchestration** (fenêtre), avec le bouton droit le multi-part message type que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d3707-118">In the **Orchestration View** window, right-click the multi-part message type you want to remove and then click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3707-119">La suppression d'un type de message à parties multiples de votre orchestration supprime également les informations sur le type dans les messages qui l'utilisent.</span><span class="sxs-lookup"><span data-stu-id="d3707-119">Removing a multi-part message type from your orchestration will also remove the type information from messages that use it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3707-120">Les éléments apparaissant en lecture seule sont définis dans une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="d3707-120">Items that appear as read-only are defined in another orchestration.</span></span>  
  
## <a name="remove-a-part-from-a-multi-part-message-type"></a><span data-ttu-id="d3707-121">Supprimer un composant d’un type de message à parties multiples</span><span class="sxs-lookup"><span data-stu-id="d3707-121">Remove a part from a multi-part message type</span></span>  
  
-   <span data-ttu-id="d3707-122">Dans le **Vue Orchestration** fenêtre, avec le bouton droit de la partie que vous souhaitez supprimer, cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d3707-122">In the **Orchestration View** window, right-click the part you want to remove and click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3707-123">Vous ne pouvez pas supprimer la partie de message d’un type de message si le **corps du Message** est définie sur true.</span><span class="sxs-lookup"><span data-stu-id="d3707-123">You cannot delete a message type's message part if the **Message Body Part** property is set to true.</span></span> <span data-ttu-id="d3707-124">Vous devez d’abord définir le **corps du Message** propriété sur True pour une autre des parties du type de message.</span><span class="sxs-lookup"><span data-stu-id="d3707-124">You must first set the **Message Body Part** property to True for another of the message type's parts.</span></span>  
  
## <a name="set-the-type-modifier-for-a-multi-part-message-type"></a><span data-ttu-id="d3707-125">Définir le modificateur de type pour un type de message à parties multiples</span><span class="sxs-lookup"><span data-stu-id="d3707-125">Set the type modifier for a multi-part message type</span></span>  
  
-   <span data-ttu-id="d3707-126">Dans le **propriétés** fenêtre, définissez la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="d3707-126">In the **Properties** window, set the following property:</span></span>  
  
    |<span data-ttu-id="d3707-127">Propriété</span><span class="sxs-lookup"><span data-stu-id="d3707-127">Property</span></span>|<span data-ttu-id="d3707-128"> Description</span><span class="sxs-lookup"><span data-stu-id="d3707-128">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="d3707-129">**Modificateur de type**</span><span class="sxs-lookup"><span data-stu-id="d3707-129">**Type Modifier**</span></span>|<span data-ttu-id="d3707-130">Détermine l'étendue du type de message à parties multiples :</span><span class="sxs-lookup"><span data-stu-id="d3707-130">Determines the scope of the multi-part message type:</span></span><br /><br /> <span data-ttu-id="d3707-131">-   **Privé :**l’accès à ce type de message à parties multiples est limité au module contenant.</span><span class="sxs-lookup"><span data-stu-id="d3707-131">-   **Private—**Access to this multi-part message type is limited to the containing module.</span></span><br /><span data-ttu-id="d3707-132">-   **Public :**l’accès à ce type de message à parties multiples n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="d3707-132">-   **Public—**Access to this multi-part message type is not limited.</span></span><br /><span data-ttu-id="d3707-133">-   **Interne —**accès à ce type de message à parties multiples est limité aux modules dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="d3707-133">-   **Internal—**Access to this multi-part message type is limited to modules within the same project.</span></span>|  
  
## <a name="add-parts-to-an-existing-multi-part-message"></a><span data-ttu-id="d3707-134">Ajouter des parties à un message à parties multiples existant</span><span class="sxs-lookup"><span data-stu-id="d3707-134">Add parts to an existing multi-part message</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d3707-135"> permet d'ajouter des parties à un message XLANG à parties multiples, mais également de faire référence à une partie du message par un index supérieur au nombre initialement déclaré de parties existantes.</span><span class="sxs-lookup"><span data-stu-id="d3707-135"> provides the ability to add parts to a multi part XLANG message and also to refer to a message part by an index greater than the originally declared number of parts if the part exists.</span></span> <span data-ttu-id="d3707-136">Cette fonction peut s'avérer particulièrement utile pour l'envoi et la réception de messages SMTP ayant un nombre variable de pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="d3707-136">This functionality may be useful for sending or receiving SMTP messages with a variable number of attachments.</span></span> <span data-ttu-id="d3707-137">Cette fonctionnalité est implémentée comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d3707-137">This functionality is implemented as follows:</span></span>  
  
-   <span data-ttu-id="d3707-138">À partir de votre projet, ajoutez une référence à **Microsoft.XLANGs.BaseTypes**.</span><span class="sxs-lookup"><span data-stu-id="d3707-138">From your project, add a reference to **Microsoft.XLANGs.BaseTypes**.</span></span>  
  
-   <span data-ttu-id="d3707-139">Créez une variable (par exemple *xlangPart*) de type **Microsoft.XLANGs.BaseTypes.XLANGMessage**.</span><span class="sxs-lookup"><span data-stu-id="d3707-139">Create a variable (for example *xlangPart*) of type **Microsoft.XLANGs.BaseTypes.XLANGMessage**.</span></span>  
  
-   <span data-ttu-id="d3707-140">Appelez *xlangPart***. AddPart(...)**  en utilisant les arguments appropriés à partir d’une forme Expression.</span><span class="sxs-lookup"><span data-stu-id="d3707-140">Call *xlangPart***.AddPart(…)** using the appropriate arguments from an Expression shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3707-141">Les parties ajoutées sont de type **XmlDocument** afin que vous ne pouvez pas ajouter une partie de message mis en forme personnalisé à l’aide de la **AddPart()** (méthode).</span><span class="sxs-lookup"><span data-stu-id="d3707-141">The added parts are of type **XmlDocument** so you cannot add a custom formatted message part using the **AddPart()** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3707-142">Si un message à parties multiples contenant supérieur au nombre de parties déclarés est reçu, les lectures du moteur d’orchestration combien dénombre les parties contenues dans le message, construit ensuite les types de parties propres pour les parties qui correspondant au nombre de parties du message déclaré type et constructions **XmlDocument** parties pour les parties restantes.</span><span class="sxs-lookup"><span data-stu-id="d3707-142">If a multi part message that contains greater than the number of declared parts is received, the orchestration engine reads how many parts there are in the message, then constructs the proper part types for the parts that match the number of parts in the declared message type and then constructs **XmlDocument** parts for the remaining parts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3707-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3707-143">See Also</span></span>  
 <span data-ttu-id="d3707-144">**Méthode IBaseMessage.AddPart (COM)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d3707-144">**IBaseMessage.AddPart Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
 <span data-ttu-id="d3707-145">[Ressources XSD sur le Web](../core/xsd-resources-on-the-web.md) </span><span class="sxs-lookup"><span data-stu-id="d3707-145">[XSD Resources on the Web](../core/xsd-resources-on-the-web.md) </span></span>  
 <span data-ttu-id="d3707-146">[À l’aide des champs distinctifs et les champs de propriété](../core/using-distinguished-fields-and-property-fields.md) </span><span class="sxs-lookup"><span data-stu-id="d3707-146">[Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md) </span></span>  
 [<span data-ttu-id="d3707-147">À l’aide de Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="d3707-147">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)