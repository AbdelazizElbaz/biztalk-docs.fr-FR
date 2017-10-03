---
title: "Étape 5 : Promouvoir les propriétés de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, pomoted properties
- promoted properties
- schemas, promoted properties
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9000b0466c8c0fc8d466f8174bc0e900a93bf392
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-promote-schema-properties"></a><span data-ttu-id="55346-102">Étape 5 : Promouvoir les propriétés de schéma</span><span class="sxs-lookup"><span data-stu-id="55346-102">Step 5: Promote Schema Properties</span></span>
<span data-ttu-id="55346-103">Dans cette étape, vous promouvez les propriétés de schéma afin qu’un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration peut faire référence à ces valeurs de propriété que vous créez dans les étapes ultérieures.</span><span class="sxs-lookup"><span data-stu-id="55346-103">In this step, you promote schema properties so that a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration can reference those property values that you create in later steps.</span></span> <span data-ttu-id="55346-104">La promotion est un mécanisme qui vous permet de faire référence à une valeur spécifique au sein d’une instance de message et le rendre accessible aux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composants tels que de l’orchestration ou pour le routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="55346-104">Promotion is a mechanism that you use to reference a specific value within a message instance and make it accessible to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] components such as orchestration or for content-based routing purposes.</span></span> <span data-ttu-id="55346-105">En outre, une propriété promue est visible par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] IntelliSense dans l’éditeur d’Expression de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55346-105">Additionally, a promoted property is visible by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] IntelliSense in the Expression Editor of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="55346-106">l’audit et la fonctionnalité de journalisation avec l’outil de contrôle d’intégrité de BizTalk et l’activité de suivi du fonctionnement (HAT) peuvent suivre les propriétés de schéma promues uniquement.</span><span class="sxs-lookup"><span data-stu-id="55346-106"> auditing and logging functionality with the BizTalk Health and Activity Tracking (HAT) tool can track only promoted schema properties.</span></span>  
  
### <a name="to-promote-schema-properties"></a><span data-ttu-id="55346-107">Pour promouvoir des propriétés de schéma</span><span class="sxs-lookup"><span data-stu-id="55346-107">To promote schema properties</span></span>  
  
1.  <span data-ttu-id="55346-108">Dans l’Explorateur de solutions, sous **BTAHL7 projet**, double-cliquez sur le **DoorBell.xsd** nœud pour ouvrir le schéma.</span><span class="sxs-lookup"><span data-stu-id="55346-108">In Solution Explorer, under **BTAHL7 Project**, double-click the **DoorBell.xsd** node to open the schema.</span></span>  
  
2.  <span data-ttu-id="55346-109">Cliquez sur le **FirstName** élément de champ, pointez sur **promouvoir**, puis cliquez sur **Promotion rapide**.</span><span class="sxs-lookup"><span data-stu-id="55346-109">Right-click the **FirstName** field element, point to **Promote**, and then click **Quick Promotion**.</span></span>  
  
3.  <span data-ttu-id="55346-110">Cliquez sur **OK** pour ajouter le schéma de propriété au projet.</span><span class="sxs-lookup"><span data-stu-id="55346-110">Click **OK** to add the property schema to the project.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="55346-111">Ajoute un cercle orange sur l’icône pour le **FirstName** élément, indiquant que l’élément a été promu.</span><span class="sxs-lookup"><span data-stu-id="55346-111"> adds an orange circle to the icon for the **FirstName** element, indicating that the element has been promoted.</span></span>  
  
4.  <span data-ttu-id="55346-112">Répétez ces étapes pour promouvoir les éléments de champ suivants :</span><span class="sxs-lookup"><span data-stu-id="55346-112">Repeat these steps to promote the following field elements:</span></span>  
  
    -   <span data-ttu-id="55346-113">**MiddleName**</span><span class="sxs-lookup"><span data-stu-id="55346-113">**MiddleName**</span></span>  
  
    -   <span data-ttu-id="55346-114">**LastName**</span><span class="sxs-lookup"><span data-stu-id="55346-114">**LastName**</span></span>  
  
    -   <span data-ttu-id="55346-115">**SSN**</span><span class="sxs-lookup"><span data-stu-id="55346-115">**SSN**</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="55346-116">Il est important de noter que promouvoir un patient ID (PID) comme un numéro de sécurité sociale (SSN) provoque [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pour effectuer le suivi de cette propriété pour tous les messages entrants via le système.</span><span class="sxs-lookup"><span data-stu-id="55346-116">It is important to note that promoting a patient ID (PID) such as a social security number (SSN) causes [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to track that property for every inbound message through the system.</span></span> <span data-ttu-id="55346-117">L’effet secondaire de cette situation est que la base de données de suivi des messages conserve une copie du patient numéros de sécurité sociale.</span><span class="sxs-lookup"><span data-stu-id="55346-117">The side effect of this situation is that the message-tracking database keeps a copy of patient SSNs.</span></span> <span data-ttu-id="55346-118">Cela peut créer un problème de sécurité importantes.</span><span class="sxs-lookup"><span data-stu-id="55346-118">This can create a significant security issue.</span></span> <span data-ttu-id="55346-119">Vous devez protéger le magasin de données avec une extrême prudence ou éviter la promotion des données PID complètement.</span><span class="sxs-lookup"><span data-stu-id="55346-119">You must either protect this data store with extreme care or avoid the promotion of PID data completely.</span></span>  
  
     <span data-ttu-id="55346-120">Pour plus d’informations sur le suivi de documents basées sur les éléments de schéma que vous avez promues, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide pour plus d’informations sur le suivi des activités et de contrôle d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="55346-120">For more information about tracking documents based on the schema elements that you promoted, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help for information on Health and Activity Tracking.</span></span>  
  
 <span data-ttu-id="55346-121">Passez à [étape 6 : valider les schémas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="55346-121">Proceed to [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55346-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55346-122">See Also</span></span>  
 [<span data-ttu-id="55346-123">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="55346-123">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)