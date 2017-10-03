---
title: "Le traitement des messages d’instance à l’aide des champs distinctifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b8f3f77-5385-4294-b441-bcb28bdc51b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4dca22ff1b09a0d1cfb261a9d5726da8b1b17b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-distinguished-fields"></a><span data-ttu-id="e194a-102">Traitement des messages d'instance à l'aide de champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="e194a-102">Instance Message Processing Using Distinguished Fields</span></span>
<span data-ttu-id="e194a-103">Promotion des propriétés à l’aide de la **champ distinctif** mécanisme ne nécessite pas la création d’un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="e194a-103">Promoting properties by using the **Distinguished Field** mechanism does not require the creation of a property schema.</span></span> <span data-ttu-id="e194a-104">Comme avec toutes les promotions de propriété, vous utilisez la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la **schéma** nœud schémas de message ou à l’aide de la **promouvoir &#124; Afficher les Promotions** commande sur le **BizTalk** ou les menus contextuels.</span><span class="sxs-lookup"><span data-stu-id="e194a-104">As with all property promotion, you use the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node in message schemas, or by using the **Promote &#124; Show Promotions** command on the **BizTalk** or shortcut menus.</span></span>  
  
 <span data-ttu-id="e194a-105">Dans le **promouvoir les propriétés** boîte de dialogue zone, vérifiez que le **champs distinctifs** onglet est sélectionné dans la partie droite de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e194a-105">In the **Promote Properties** dialog box, ensure the **Distinguished Fields** tab is selected in the right side of the dialog box.</span></span> <span data-ttu-id="e194a-106">Ensuite développez les nœuds dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue pour rechercher et sélectionner les **élément de champ** nœud ou **attribut de champ** nœud que vous souhaitez promouvoir en tant que champ distinctif, puis Cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e194a-106">Then you expand the nodes in the schema tree on the left side of the dialog box to find and select the **Field Element** node or **Field Attribute** node that you want to promote as a distinguished field, and then click **Add**.</span></span> <span data-ttu-id="e194a-107">Pour obtenir des instructions sur la promotion des propriétés à **champs distinctifs** à l’aide de la **promouvoir les propriétés** boîte de dialogue, consultez [copie de données dans le contexte du Message en tant qu’unique Champs](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md).</span><span class="sxs-lookup"><span data-stu-id="e194a-107">For step-by-step instructions about promoting properties to **Distinguished Fields** using the **Promote Properties** dialog, see [Copying Data to the Message Context as Distinguished Fields](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e194a-108">Vous pouvez également promouvoir un **enregistrement** nœud à un nœud d’élément de champ dans le schéma de propriété, mais uniquement si le **le Type de contenu** propriété de la **enregistrement** nœud a la valeur  **SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="e194a-108">You can also promote a **Record** node to a Field Element node in the property schema, but only if the **Content Type** property of the **Record** node is set to **SimpleContent**.</span></span>  
  
 <span data-ttu-id="e194a-109">Pour supprimer un nœud de l’ensemble des propriétés promues en tant que champs distinctifs, sélectionnez la propriété promue dans le **champs distinctifs** onglet, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="e194a-109">To remove a node from the set of properties being promoted as distinguished fields, select the promoted property on the **Distinguished Fields** tab, and click **Remove**.</span></span>  
  
 <span data-ttu-id="e194a-110">Lorsque vous assurez la promotion de propriétés à l'aide du mécanisme des champs distinctifs, un fragment de langage XSD (XML Schema Definition) est ajouté dans le sous-élément d'annotation de l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="e194a-110">When you promote properties by using the distinguished field mechanism, an XML Schema definition (XSD) language fragment is added within the annotation subelement of the root element.</span></span> <span data-ttu-id="e194a-111">Dans l'exemple ci-dessous, le fragment montre deux propriétés promues à l'aide du mécanisme des champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="e194a-111">In the following example, the fragment shows two properties promoted by using the distinguished field mechanism.</span></span>  
  
```  
<b:properties>  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field1']" />  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field5' and position()='1']" />  
</b:properties>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e194a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e194a-112">See Also</span></span>  
 <span data-ttu-id="e194a-113">[Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="e194a-113">[Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md) </span></span>  
 [<span data-ttu-id="e194a-114">Comment copier des données dans le contexte du Message en tant que champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="e194a-114">How to Copy Data to the Message Context as Distinguished Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)