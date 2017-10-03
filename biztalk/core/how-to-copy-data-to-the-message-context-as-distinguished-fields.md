---
title: "Comment copier des données dans le contexte du Message en tant que les champs distinctifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 004a13ca-a162-4a5e-9f72-8a5c55bbb7a6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ea68bc0b83c5a8f886416107e1dc98ea8ad8d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-distinguished-fields"></a><span data-ttu-id="99249-102">Comment copier des données dans le contexte du Message en tant que champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="99249-102">How to Copy Data to the Message Context as Distinguished Fields</span></span>
<span data-ttu-id="99249-103">Cette rubrique fournit des instructions pas à pas pour promouvoir une propriété comme un **champ distinctif**.</span><span class="sxs-lookup"><span data-stu-id="99249-103">This topic provides step-by-step instructions for promoting a property as a **Distinguished Field**.</span></span>  
  
 <span data-ttu-id="99249-104">Vous pouvez choisir **champ distinctif** plutôt que la promotion **champ de propriété** promotion pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="99249-104">You might choose **Distinguished Field** promotion over **Property Field** promotion for the following reasons:</span></span>  
  
-   <span data-ttu-id="99249-105">**Champ de propriété** valeurs sont limitées à 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="99249-105">**Property Field** values are limited to 255 characters in length.</span></span>  
  
-   <span data-ttu-id="99249-106">**Champ de propriété** valeurs sont stockées dans une base de données et par conséquent ont une charge plus importante que **champs distinctifs**.</span><span class="sxs-lookup"><span data-stu-id="99249-106">**Property Field** values are stored in a database, and therefore have more overhead than **Distinguished Fields**.</span></span> <span data-ttu-id="99249-107">**Champs distinctifs** ne nécessitent pas de stockage supplémentaire ; ils sont essentiellement un alias pour une **XPath**, permettant ainsi aux orchestrations plus accéder facilement aux valeurs pertinentes directement à partir du message.</span><span class="sxs-lookup"><span data-stu-id="99249-107">**Distinguished Fields** do not require any additional storage; they are essentially an alias for an **XPath**, thereby allowing orchestrations to more easily access the relevant values directly from the message.</span></span>  
  
### <a name="to-promote-a-property-as-a-distinguished-field"></a><span data-ttu-id="99249-108">Pour promouvoir une propriété en tant que Champ distinctif</span><span class="sxs-lookup"><span data-stu-id="99249-108">To promote a property as a Distinguished Field</span></span>  
  
1.  <span data-ttu-id="99249-109">Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ distinctif**.</span><span class="sxs-lookup"><span data-stu-id="99249-109">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Distinguished Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99249-110">Nœuds d’enregistrement ne peuvent jamais être promus en tant que **champs distinctifs**, quel que soit le type de contenu qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="99249-110">Record nodes can never be promoted as **Distinguished Fields**, regardless of the type of content they contain.</span></span>  
  
2.  <span data-ttu-id="99249-111">Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **afficher les Promotions**.</span><span class="sxs-lookup"><span data-stu-id="99249-111">Right-click the selected node, click **Promote**, and then click **Show Promotions**.</span></span>  
  
     <span data-ttu-id="99249-112">Le **promouvoir les propriétés** boîte de dialogue s’ouvre avec apparaît le nœud sélectionné dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="99249-112">The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.</span></span>  
  
3.  <span data-ttu-id="99249-113">Dans le **promouvoir les propriétés** boîte de dialogue, sélectionnez le **champs distinctifs** onglet.</span><span class="sxs-lookup"><span data-stu-id="99249-113">In the **Promote Properties** dialog box, select the **Distinguished Fields** tab.</span></span>  
  
4.  <span data-ttu-id="99249-114">Avec le nœud à promouvoir est toujours sélectionné dans l’arborescence de schéma sur le côté gauche de la **promouvoir les propriétés** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="99249-114">With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="99249-115">Si autorisé, le nœud sélectionné est ajouté à la liste dans le **champs distinctifs** onglet. Sinon, une zone de message fournit une explication</span><span class="sxs-lookup"><span data-stu-id="99249-115">If allowed, the selected node is added to the list on the **Distinguished Fields** tab. If not allowed, a message box provides an explanation.</span></span>  
  
5.  <span data-ttu-id="99249-116">Vous pouvez sélectionner pour la promotion des nœuds supplémentaires dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue en cliquant sur **ajouter** après chaque sélection.</span><span class="sxs-lookup"><span data-stu-id="99249-116">You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** after each selection.</span></span>  
  
6.  <span data-ttu-id="99249-117">Lorsque vous avez terminé, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="99249-117">When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="99249-118">Les nœuds que vous avez sélectionné pour promouvoir sont désormais **champs distinctifs**.</span><span class="sxs-lookup"><span data-stu-id="99249-118">The nodes that you selected to promote are now **Distinguished Fields**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99249-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99249-119">See Also</span></span>  
 <span data-ttu-id="99249-120">[Promotion des propriétés](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="99249-120">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="99249-121">[Comment créer des schémas de propriété](../core/how-to-create-property-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="99249-121">[How to Create Property Schemas](../core/how-to-create-property-schemas.md) </span></span>  
 [<span data-ttu-id="99249-122">Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle</span><span class="sxs-lookup"><span data-stu-id="99249-122">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)