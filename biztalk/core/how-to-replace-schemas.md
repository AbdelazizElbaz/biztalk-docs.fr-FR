---
title: "Comment remplacer les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 104e60d3-1303-4e56-b13a-c10ab14ba383
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df444b8169d75408fe6e412135029ae2b051a6d2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-replace-schemas"></a><span data-ttu-id="3ee8b-102">Remplacement de schémas</span><span class="sxs-lookup"><span data-stu-id="3ee8b-102">How to Replace Schemas</span></span>
<span data-ttu-id="3ee8b-103">Il peut arriver que vous souhaitiez remplacer le schéma source ou le schéma de destination dans un mappage existant, par exemple lorsqu'un partenaire commercial vous envoie un schéma mis à jour.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-103">There may be times when you want to replace either the source or destination schema in an existing map, such as when you receive an updated schema from a trading partner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ee8b-104">Le Mappeur BizTalk tente de gérer tous les liens existant entre le schéma conservé et le schéma remplacé.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-104">The BizTalk Mapper attempts to maintain all existing links between the retained schema and the replaced schema.</span></span>  
  
## <a name="replace-a-source-or-destination-schema"></a><span data-ttu-id="3ee8b-105">Remplacer un schéma source ou de destination</span><span class="sxs-lookup"><span data-stu-id="3ee8b-105">Replace a source or destination schema</span></span>  
  
1.  <span data-ttu-id="3ee8b-106">Avec le bouton droit de la source ou la destination arborescence du schéma, puis sélectionnez **remplacer le schéma**.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-106">Right-click either the source or destination schema tree view, and then select **Replace Schema**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ee8b-107">Vous pouvez également appuyer sur CTRL+M, CTRL+S.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-107">Alternatively, you can also press CTRL+M, CTRL+S from the keyboard.</span></span> <span data-ttu-id="3ee8b-108">Pour obtenir une liste complète des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="3ee8b-108">For a complete list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
2.  <span data-ttu-id="3ee8b-109">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud dans l’arborescence, sélectionnez le schéma approprié, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-109">In the **BizTalk Type Picker** dialog box, expand the **Schemas** node in the tree, select the appropriate schema, and then select **OK**.</span></span>  
  
     <span data-ttu-id="3ee8b-110">![Sélectionnez le schéma](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")</span><span class="sxs-lookup"><span data-stu-id="3ee8b-110">![Select the Schema](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")</span></span>  

    > [!TIP] 
    > <span data-ttu-id="3ee8b-111">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre du sélecteur de Type pour afficher le nom complet de votre schéma.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-111">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize the Type Picker window to see the full name of your schema.</span></span>
      
     <span data-ttu-id="3ee8b-112">Si seule une racine unique existe dans le schéma de remplacement, ou un nœud racine a été établi pour le schéma de remplacement à l’aide de la **référence de racine** propriété de la **schéma** ouvre de nœud, le schéma de remplacement dans le volet correspondant, et vous ne devrez pas effectuer l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-112">If only a single root exists in the replacement schema, or a root node has been established for the replacement schema using the **Root Reference** property of the **Schema** node, the replacement schema opens in the relevant pane, and you will not need to perform step 3.</span></span>  
  
3.  <span data-ttu-id="3ee8b-113">Si plusieurs nœuds racine dans le schéma de destination, et aucun nœud racine n’a été établie pour le schéma de destination à l’aide du **référence de racine** propriété de la **schéma** nœud, dans le  **Nœud racine pour \<* Source/cible* \> schéma ** boîte de dialogue, sélectionnez le nœud racine approprié, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-113">If multiple root nodes exist in the destination schema, and no root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, in the **Root Node for \<*Source/Target*\> Schema** dialog box, select the appropriate root node, and then select **OK**.</span></span>  
  
     <span data-ttu-id="3ee8b-114">Le schéma de remplacement s'ouvre dans le volet correspondant.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-114">The replacement schema opens in the relevant pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ee8b-115">Des liens peuvent être perdus lors du remplacement du schéma si des enregistrements/champs appropriés sont introuvables.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-115">While replacing schema, if relevant records/fields are not found, some links may get lost.</span></span> <span data-ttu-id="3ee8b-116">Le schéma est remplacé uniquement lorsque vous sélectionnez **Oui** sur la **Confirmation** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-116">The schema is replaced only when you select **Yes** on the **Confirmation**  dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee8b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ee8b-117">See Also</span></span>  
 [<span data-ttu-id="3ee8b-118">Gestion de mappages dans des projets</span><span class="sxs-lookup"><span data-stu-id="3ee8b-118">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)