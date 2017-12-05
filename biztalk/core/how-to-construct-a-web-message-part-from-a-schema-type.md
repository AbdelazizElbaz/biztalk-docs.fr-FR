---
title: "Comment construire une partie de Message Web à partir d’un Type de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, schema types
- Web messages, creating
- Transform shape [Orchestration Designer]
- Web messages, Transform shape [Orchestration Designer]
ms.assetid: 4452ade6-b10f-4564-bffc-18114896aeeb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da57e32f2ba4d4d5feb60a6f44cc7d92195852c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-construct-a-web-message-part-from-a-schema-type"></a><span data-ttu-id="2a8c4-102">Création d'une partie de message Web à partir d'un type de schéma</span><span class="sxs-lookup"><span data-stu-id="2a8c4-102">How to Construct a Web Message Part from a Schema Type</span></span>
<span data-ttu-id="2a8c4-103">Vous créez une partie de message Web à partir d’un type de schéma en utilisant un **transformer** forme.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-103">You create a Web message part from a schema type by using a **Transform** shape.</span></span> <span data-ttu-id="2a8c4-104">Vous pouvez également utiliser une classe d'assistance .NET pour définir les parties.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-104">Alternatively, you can create a Web message part from a schema type by using a .NET helper class to set the parts.</span></span> <span data-ttu-id="2a8c4-105">Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="2a8c4-105">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
### <a name="to-construct-a-web-message-part-from-a-schema-type"></a><span data-ttu-id="2a8c4-106">Pour construire une partie de message Web à partir d'un type de schéma</span><span class="sxs-lookup"><span data-stu-id="2a8c4-106">To construct a Web message part from a schema type</span></span>  
  
1.  <span data-ttu-id="2a8c4-107">Ajoutez un nouveau mappage.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-107">Add a new map.</span></span> <span data-ttu-id="2a8c4-108">Pour plus d’informations sur la création de mappages, consultez [comment créer un nouveau mappe](../core/how-to-create-new-maps.md).</span><span class="sxs-lookup"><span data-stu-id="2a8c4-108">For information about creating maps, see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span>  
  
2.  <span data-ttu-id="2a8c4-109">Dans le Mappeur BizTalk, cliquez sur **ouvrir le schéma de Destination** dans les **schéma de Destination** volet de la carte et dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le  **Schémas** nœud, sélectionnez le schéma de la référence Web ajoutée, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-109">In BizTalk Mapper, click **Open Destination Schema** in the **Destination Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the schema for the added Web reference, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a8c4-110">Le format du schéma de référence Web est  **\<espace de noms par défaut du projet\>.\< Nom de la référence Web\>. Référence**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-110">The format of the Web reference schema is **\<project default namespace\>.\<Web reference name\>.Reference**.</span></span>  
  
3.  <span data-ttu-id="2a8c4-111">Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez un nœud racine pour le schéma de destination, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-111">In the **Root Node for Target Schema** dialog box, select a root node for the destination schema, and then click **OK**.</span></span> <span data-ttu-id="2a8c4-112">Pour plus d’informations sur la façon de déterminer un nœud racine pour un type de partie de message Web, consultez [comment déterminer un Type de partie de Message Web](../core/how-to-determine-a-web-message-part-type.md).</span><span class="sxs-lookup"><span data-stu-id="2a8c4-112">For more information about how to determine a root node for a Web message part type, see [How to Determine a Web Message Part Type](../core/how-to-determine-a-web-message-part-type.md).</span></span>  
  
4.  <span data-ttu-id="2a8c4-113">Cliquez sur **ouvrir le schéma Source** dans les **schéma Source** volet de la carte et dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud, sélectionnez le schéma source à mapper des données à partir de, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-113">Click **Open Source Schema** in the **Source Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the source schema to map data from, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="2a8c4-114">Dans le Mappeur BizTalk, créez des liens entre le schéma source et le schéma cible.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-114">In the BizTalk Mapper, create links between the source schema and target schema.</span></span>  
  
6.  <span data-ttu-id="2a8c4-115">Ouvrez une orchestration existante (ou créer une nouvelle orchestration), ouvrez le **boîte à outils**, puis cliquez sur le **Orchestrations BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-115">Open an existing orchestration (or create a new orchestration), open the **Toolbox**, and click the **BizTalk Orchestrations** tab.</span></span>  
  
7.  <span data-ttu-id="2a8c4-116">Faites glisser un **construire un Message** forme à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-116">Drag a **Construct Message** shape to the orchestration.</span></span>  
  
8.  <span data-ttu-id="2a8c4-117">Modifier la **Message construit** propriété à inclure le message d’instance qui créée pour le type de message Web.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-117">Edit the **Message Constructed** property to include the message instance that yo created for the Web message type.</span></span>  
  
9. <span data-ttu-id="2a8c4-118">Faites glisser un **transformer** forme sur le **construire un Message** mettre en forme et double-cliquez pour ouvrir la **transformer la Configuration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-118">Drag a **Transform** shape onto the **Construct Message** shape and double-click to open the **Transform Configuration** dialog box.</span></span>  
  
10. <span data-ttu-id="2a8c4-119">Cliquez sur le **mappage existant** bouton et sélectionnez le mappage que vous avez créé à l’étape 1 dans le **nom de mappage complet** zone de liste.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-119">Click the **Existing Map** button and select the map that you created in step one in the **Fully Qualified Map Name** list box.</span></span>  
  
11. <span data-ttu-id="2a8c4-120">Dans le **transformer** volet, sélectionnez **Source**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-120">In the **Transform** pane, select **Source**.</span></span> <span data-ttu-id="2a8c4-121">Dans le **transformation Source** volet, sélectionnez un message valide de l’instance à partir de la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-121">In the **Source Transform** pane, select a valid message instance from the list box.</span></span>  
  
12. <span data-ttu-id="2a8c4-122">Dans le **transformer** volet, sélectionnez **Destination**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-122">In the **Transform** pane, select **Destination**.</span></span> <span data-ttu-id="2a8c4-123">Dans le **transformation de Destination** , sélectionnez le message Web de l’instance à partir de la zone de liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-123">In the **Destination Transform** pane, select the Web message instance from the list box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="2a8c4-124">Pour plus d’informations sur l’utilisation de la **transformer la Configuration** boîte de dialogue, consultez [comment configurer la forme transformer](../core/how-to-configure-the-transform-shape.md).</span><span class="sxs-lookup"><span data-stu-id="2a8c4-124">For more information about using the **Transform Configuration** dialog box, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md).</span></span>  
  
 <span data-ttu-id="2a8c4-125">Vous pouvez également utiliser cette procédure pour mapper l'instance de message de réponse de la méthode Web à une autre instance de message Web.</span><span class="sxs-lookup"><span data-stu-id="2a8c4-125">You can also use this procedure to map the Web method response message instance to another Web message instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a8c4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a8c4-126">See Also</span></span>  
 [<span data-ttu-id="2a8c4-127">Construction de messages web</span><span class="sxs-lookup"><span data-stu-id="2a8c4-127">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)