---
title: "Traitement des messages de façons d’utiliser le contenu du Message au contrôle de code | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e3792e-9cd4-42b6-8b9d-3c2a022a16d6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d356496d07bb2227aa514ee68f2a2a51e2291b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-message-content-to-control-message-processing"></a><span data-ttu-id="fdf20-102">Utilisations du contenu de message pour contrôler le traitement de message</span><span class="sxs-lookup"><span data-stu-id="fdf20-102">Ways to Use Message Content to Control Message Processing</span></span>
<span data-ttu-id="fdf20-103">Il existe deux types de promotions de propriétés : **champs distinctifs** et **champs de propriété**, le deuxième utilise les schémas de propriété.</span><span class="sxs-lookup"><span data-stu-id="fdf20-103">There are two types of property promotion: **Distinguished Fields** and **Property Fields**, the latter of which uses property schemas.</span></span> <span data-ttu-id="fdf20-104">Dans l’Éditeur BizTalk, vous gérez ces deux types de promotions de propriétés à l’aide de la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la  **Schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="fdf20-104">In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdf20-105">Il existe certaines restrictions concernant les valeurs qu'il est possible de promouvoir.</span><span class="sxs-lookup"><span data-stu-id="fdf20-105">There are some restrictions on values that you can promote.</span></span> <span data-ttu-id="fdf20-106">Pour plus d’informations, consultez le tableau dans [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="fdf20-106">For more information, see the table in [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
 <span data-ttu-id="fdf20-107">En fonction des détails de votre scénario, vous devez décider du type de promotion de propriétés à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fdf20-107">You must decide which type of property promotion to use based on the details of your scenario.</span></span> <span data-ttu-id="fdf20-108">Observez les distinctions entre **champ distinctif** promotion de propriétés et **champ de propriété** promotion de propriétés :</span><span class="sxs-lookup"><span data-stu-id="fdf20-108">Consider the following distinctions between **Distinguished Field** property promotion and **Property Field** property promotion:</span></span>  
  
-   <span data-ttu-id="fdf20-109">**Champs distinctifs** ne peut pas participer au routage des messages et par conséquent, ils n’apparaissent pas dans les expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="fdf20-109">**Distinguished Fields** cannot participate in message routing and therefore they do not appear in the filter expressions.</span></span> <span data-ttu-id="fdf20-110">Ils sont uniquement disponibles dans le contexte d'une orchestration, mais nécessitent moins de traitement lors de l'envoi et de la réception de messages.</span><span class="sxs-lookup"><span data-stu-id="fdf20-110">They are only available within the context of an orchestration but they have less overhead when sending and receiving messages.</span></span>  
  
-   <span data-ttu-id="fdf20-111">**Champs distinctifs** n’ont pas de limitation de taille.</span><span class="sxs-lookup"><span data-stu-id="fdf20-111">**Distinguished Fields** do not have any size limitations.</span></span> <span data-ttu-id="fdf20-112">**Champs de propriété** sont limités à 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="fdf20-112">**Property Fields** are limited to 255 characters.</span></span>  
  
-   <span data-ttu-id="fdf20-113">**Champs distinctifs** ne nécessitent pas d’artefacts distincts tandis que de créer **champs de propriété** nécessitent la création et la maintenance d’un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="fdf20-113">**Distinguished Fields** do not require any separate artifacts to be created whereas **Property Fields** require the creation and maintenance of a property schema.</span></span>  
  
 <span data-ttu-id="fdf20-114">Grâce à ces considérations, vous devez promouvoir des nœuds en tant que **champs de propriété** uniquement lorsque vous envisagez d’utiliser les propriétés promues pour le routage du message ou à des fins de suivi.</span><span class="sxs-lookup"><span data-stu-id="fdf20-114">Drawing upon these considerations, you should promote nodes as **Property Fields** only when you intend to use the promoted properties for message routing or tracking purposes.</span></span> <span data-ttu-id="fdf20-115">Sinon, si vous vous apprêtez uniquement pour accéder aux propriétés promues à partir de vos orchestrations, vous devez tirer parti du fait que **champs distinctifs** sont bien plus économique, plus légers et plus facile à utiliser que  **Champs de propriété**.</span><span class="sxs-lookup"><span data-stu-id="fdf20-115">Otherwise, if you are only going to access the promoted properties from within your orchestrations, you should take advantage of the fact that **Distinguished Fields** are much cheaper, more lightweight, and more easy-to-use than **Property Fields**.</span></span>  
  
 <span data-ttu-id="fdf20-116">Propriétés promues à l’aide de la **champ distinctif** mécanisme sont uniquement accessible à partir d’orchestrations et ne sont pas accessibles à partir des pipelines, les ports et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fdf20-116">Properties promoted by using the **Distinguished Field** mechanism are only accessible from within orchestrations and cannot be accessed from pipelines, ports, and so on.</span></span> <span data-ttu-id="fdf20-117">En revanche, les propriétés promues à l’aide de la **champs de propriété** et le mécanisme de schéma de propriété sont accessibles à partir de tous ces composants.</span><span class="sxs-lookup"><span data-stu-id="fdf20-117">On the other hand, properties promoted by using the **Property Fields** and property schema mechanism are accessible from all of these components.</span></span> <span data-ttu-id="fdf20-118">Une autre différence importante réside dans le fait que les valeurs de champ de propriété sont limitées à 255 caractères et que les valeurs de champ distinctif ne font pas l'objet d'une telle limite.</span><span class="sxs-lookup"><span data-stu-id="fdf20-118">Another important difference is that property field values are limited to 255 characters and distinguished field values have no such limit.</span></span>  
  
 <span data-ttu-id="fdf20-119">Cette section fournit des informations sur ces deux types de promotions de propriétés et notamment sur la manière d'établir de telles propriétés promues pour un schéma de message en utilisant l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fdf20-119">This section provides information about these two types of property promotion, including how information about how to establish such promoted properties for a message schema by using BizTalk Editor.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdf20-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fdf20-120">In This Section</span></span>  
  
-   [<span data-ttu-id="fdf20-121">À propos des propriétés de contexte de Message BizTalk</span><span class="sxs-lookup"><span data-stu-id="fdf20-121">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)  
  
-   [<span data-ttu-id="fdf20-122">Le traitement des messages d’instance à l’aide des champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="fdf20-122">Instance Message Processing Using Distinguished Fields</span></span>](../core/instance-message-processing-using-distinguished-fields.md)  
  
-   [<span data-ttu-id="fdf20-123">Traitement de Message d’instance à l’aide de la Promotion de propriétés</span><span class="sxs-lookup"><span data-stu-id="fdf20-123">Instance Message Processing Using Property Promotion</span></span>](../core/instance-message-processing-using-property-promotion.md)