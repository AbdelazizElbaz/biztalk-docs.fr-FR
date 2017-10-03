---
title: "À l’aide de liens pour spécifier l’enregistrement et les mappages de champs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c669d93-e088-459e-8f45-87c359874a7e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a79595e3acc916e61919d77c4f39fe24ff43b00f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-links-to-specify-record-and-field-mappings"></a><span data-ttu-id="b53d5-102">Utilisation de liens pour spécifier des mappages d'enregistrements et de champs</span><span class="sxs-lookup"><span data-stu-id="b53d5-102">Using Links to Specify Record and Field Mappings</span></span>
<span data-ttu-id="b53d5-103">Dans le Mappeur BizTalk, un lien permet d'associer un élément de données du schéma source à un élément de données du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b53d5-103">In BizTalk Mapper, a link is the way you associate a data item in the source schema with a data item in the destination schema.</span></span> <span data-ttu-id="b53d5-104">Généralement, dans un mappage terminé, il existe de nombreux liens entre le schéma source et le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b53d5-104">Typically, in a completed map there are many links between the source schema and the destination schema.</span></span> <span data-ttu-id="b53d5-105">L’ensemble de ces liens spécifie la façon dont les données des messages de l'instance source seront transformées en messages d’instance de destination, sémantiquement équivalents, mais syntaxiquement différents.</span><span class="sxs-lookup"><span data-stu-id="b53d5-105">All together the links specify how the data in the source instance messages will be transformed into a semantically equivalent, but syntactically distinct, destination instance messages.</span></span>  
  
 <span data-ttu-id="b53d5-106">Cette section offre des informations spécifiques aux tâches sur la création de liens, l'utilisation de liens existants, la création automatique de liens ainsi que d’autres opérations sur les liens.</span><span class="sxs-lookup"><span data-stu-id="b53d5-106">This section provides task-specific information about creating new links, working with existing links, creating links automatically, and other linking operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b53d5-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b53d5-107">In This Section</span></span>  
  
-   [<span data-ttu-id="b53d5-108">Comment créer des liens</span><span class="sxs-lookup"><span data-stu-id="b53d5-108">How to Create Links</span></span>](../core/how-to-create-links.md)  
  
-   [<span data-ttu-id="b53d5-109">Procédure : modifier les propriétés de lien</span><span class="sxs-lookup"><span data-stu-id="b53d5-109">How to Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)  
  
-   [<span data-ttu-id="b53d5-110">Comment lier automatiquement des enregistrements</span><span class="sxs-lookup"><span data-stu-id="b53d5-110">How to Link Records Automatically</span></span>](../core/how-to-link-records-automatically.md)  
  
-   [<span data-ttu-id="b53d5-111">Comment gérer des liens existants</span><span class="sxs-lookup"><span data-stu-id="b53d5-111">How to Manage Existing Links</span></span>](../core/how-to-manage-existing-links.md)  
  
-   [<span data-ttu-id="b53d5-112">Comment configurer la hiérarchie de nœuds correspondant</span><span class="sxs-lookup"><span data-stu-id="b53d5-112">How to Configure Node Hierarchy Matching</span></span>](../core/how-to-configure-node-hierarchy-matching.md)  
  
-   [<span data-ttu-id="b53d5-113">Comment définir la valeur du compilateur Source de liens</span><span class="sxs-lookup"><span data-stu-id="b53d5-113">How to Set the Source Links Compiler Value</span></span>](../core/how-to-set-the-source-links-compiler-value.md)  
  
-   [<span data-ttu-id="b53d5-114">Comment afficher et masquer les liaisons du compilateur</span><span class="sxs-lookup"><span data-stu-id="b53d5-114">How to Show and Hide Compiler Links</span></span>](../core/how-to-show-and-hide-compiler-links.md)  
  
-   [<span data-ttu-id="b53d5-115">Comment copier, couper et coller des liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="b53d5-115">How to Copy, Cut, and Paste Links and Functoids</span></span>](../core/how-to-copy-cut-and-paste-links-and-functoids.md)  
  
-   [<span data-ttu-id="b53d5-116">L’étiquette à un lien</span><span class="sxs-lookup"><span data-stu-id="b53d5-116">How to Label a Link</span></span>](../core/how-to-label-a-link.md)  
  
-   [<span data-ttu-id="b53d5-117">Comment sélectionner plusieurs liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="b53d5-117">How to Select Multiple Links and Functoids</span></span>](../core/how-to-select-multiple-links-and-functoids.md)  
  
-   [<span data-ttu-id="b53d5-118">Comment définir des étiquettes et commentaires sur plusieurs liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="b53d5-118">How to Set Label and Comment on Multiple Links and Functoids</span></span>](../core/how-to-set-label-and-comment-on-multiple-links-and-functoids.md)