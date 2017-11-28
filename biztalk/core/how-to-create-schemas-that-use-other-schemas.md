---
title: "Comment créer des schémas utilisant d’autres schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff0bcd9a-6c66-4c3b-bd41-64047a7c8392
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f427e5cd8e3f82e57dc8926c6e00889e1c97afe9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-schemas-that-use-other-schemas"></a><span data-ttu-id="3880f-102">Comment créer des schémas utilisant d’autres schémas</span><span class="sxs-lookup"><span data-stu-id="3880f-102">How to Create Schemas That Use Other Schemas</span></span>
<span data-ttu-id="3880f-103">Le langage XSD (XML Schema Definition) fournit trois mécanismes différents mais liés entre eux qui permettent d'utiliser un schéma dans un autre schéma.</span><span class="sxs-lookup"><span data-stu-id="3880f-103">XML Schema definition (XSD) language provides three different but related mechanisms for using one schema within another schema.</span></span> <span data-ttu-id="3880f-104">Ces mécanismes sont ceux qui consistent à importer un schéma, à inclure un schéma et à redéfinir un schéma.</span><span class="sxs-lookup"><span data-stu-id="3880f-104">These mechanisms are importing a schema, including a schema, and redefining a schema.</span></span> <span data-ttu-id="3880f-105">Pour une brève description de ces mécanismes et leurs différences, consultez [schémas utilisant d’autres schémas](../core/schemas-that-use-other-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="3880f-105">For a brief summary of these mechanisms and how they differ, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md).</span></span> <span data-ttu-id="3880f-106">Pour plus d’informations, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md) pour des liens vers les spécifications et le manuel de XSD.</span><span class="sxs-lookup"><span data-stu-id="3880f-106">For detailed information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md) for links to the XSD primer and specifications.</span></span>  
  
 <span data-ttu-id="3880f-107">Cette rubrique décrit les étapes nécessaires à l'importation, l'inclusion et la redéfinition d'autres schémas dans un schéma en cours de développement.</span><span class="sxs-lookup"><span data-stu-id="3880f-107">This topic describes the steps required to import, include, and redefine other schemas within the schema you are developing.</span></span>  
  
### <a name="to-import-include-or-redefine-one-schema-within-another-schema"></a><span data-ttu-id="3880f-108">Pour importer, inclure ou redéfinir un schéma dans un autre schéma</span><span class="sxs-lookup"><span data-stu-id="3880f-108">To import, include, or redefine one schema within another schema</span></span>  
  
1.  <span data-ttu-id="3880f-109">Dans l'Éditeur BizTalk, ouvrez le schéma dans lequel vous souhaitez importer, inclure ou redéfinir un autre schéma.</span><span class="sxs-lookup"><span data-stu-id="3880f-109">In BizTalk Editor, open the schema to which you want to import, include, or redefine another schema.</span></span> <span data-ttu-id="3880f-110">Vous pouvez ouvrir un schéma en double-cliquant dessus dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="3880f-110">You can open a schema by double-clicking it in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="3880f-111">Sélectionnez le **schéma** nœud en haut de l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="3880f-111">Select the **Schema** node at the top of the schema tree view.</span></span>  
  
3.  <span data-ttu-id="3880f-112">Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3880f-112">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
4.  <span data-ttu-id="3880f-113">Dans la fenêtre Propriétés, dans le **avancé** catégorie, dans la partie valeur de la **importations** propriété, cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="3880f-113">In the Properties window, in the **Advanced** category, in the value portion of the **Imports** property, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="3880f-114">Dans le **importations** boîte de dialogue le **importer le nouveau schéma en tant que** liste, sélectionnez **XSD : importer**, **XSD : inclure**, ou **XSD Redéfinir**, le cas échéant, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3880f-114">In the **Imports** dialog box, in the **Import New Schema as** list, select **XSD Import**, **XSD Include**, or **XSD Redefine**, as appropriate, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="3880f-115">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schéma** nœud dans l’arborescence du projet, sélectionnez le schéma que vous souhaitez importer, inclure, ou redéfinir, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3880f-115">In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the project tree, select the schema that you want to import, include, or redefine, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3880f-116">Dans le **importations** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3880f-116">In the **Imports** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="3880f-117">Les directives XSD appropriées pour implémenter l’importation, inclure ou redéfinir l’opération sont ajoutés à la **schéma** élément dans la vue XSD, y compris un nouveau **importer**, **incluent**, ou **redéfinir** élément, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="3880f-117">The appropriate XSD directives to implement the import, include, or redefine operation are added to the **schema** element in the XSD view, including a new **import**, **include**, or **redefine** element, as appropriate.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3880f-118">Assurez-vous d'avoir bien compris les différentes finalités de ces trois mécanismes et en quoi ils diffèrent en termes d'exigences d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3880f-118">Make sure you understand the different purposes of these three mechanisms, such as how they differ with respect to namespace requirements.</span></span> <span data-ttu-id="3880f-119">Vous pouvez toujours supprimer un schéma précédemment importé, inclus ou redéfini et utiliser ensuite l'un des deux autres mécanismes. Toutefois, si vous avez abondamment référencé ce schéma, vous devrez éventuellement le retravailler.</span><span class="sxs-lookup"><span data-stu-id="3880f-119">You can always delete a previously imported, included, or redefined schema and then use one of the other two mechanisms, but depending on how extensively you have referenced that schema, you may need to rework your schema accordingly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3880f-120">Le mécanisme XSD d'importation, d'inclusion et de redéfinition d'un schéma dans un autre schéma fonctionne par référence au schéma importé, inclus ou redéfini.</span><span class="sxs-lookup"><span data-stu-id="3880f-120">The XSD mechanism for importing, including, and redefining one schema within another schema works by reference to the imported, included, or redefined schema.</span></span> <span data-ttu-id="3880f-121">Cela signifie que si vous apportez une modification au schéma importé, inclus ou redéfini, elle sera répercutée dans le schéma contenant la référence d'importation, d'inclusion ou de redéfinition.</span><span class="sxs-lookup"><span data-stu-id="3880f-121">This means that if you make a change to the imported, included, or redefined schema, that change will be reflected in the schema containing the import, include, or redefine reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3880f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3880f-122">See Also</span></span>  
 <span data-ttu-id="3880f-123">[Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="3880f-123">[Managing Schemas Within Projects](../core/managing-schemas-within-projects.md) </span></span>  
 [<span data-ttu-id="3880f-124">Comment créer des références à un autre nœud ou Type</span><span class="sxs-lookup"><span data-stu-id="3880f-124">How to Create References to Another Node or Type</span></span>](../core/how-to-create-references-to-another-node-or-type.md)