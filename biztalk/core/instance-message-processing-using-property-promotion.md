---
title: "Le traitement des messages à l’aide de la Promotion des propriétés de l’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 753571b8-4609-4ac4-a974-8bd6dfecb077
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 288657d43443582c5a05df5dd6e67059eca572e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-property-promotion"></a><span data-ttu-id="6db83-102">Traitement des messages d'instance à l'aide de la promotion de propriétés</span><span class="sxs-lookup"><span data-stu-id="6db83-102">Instance Message Processing Using Property Promotion</span></span>
<span data-ttu-id="6db83-103">Promotion des propriétés à l’aide de la **champ de propriété** méthode requiert la création d’un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="6db83-103">Promoting properties by using the **Property Field** method requires the creation of a property schema.</span></span> <span data-ttu-id="6db83-104">Pour plus d’informations sur la création d’un schéma de propriété, consultez [comment créer des schémas de propriété](../core/how-to-create-property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="6db83-104">For more information about creating a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).</span></span> <span data-ttu-id="6db83-105">Comme avec toutes les promotions de propriété, vous utilisez la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la **schéma** nœud schémas de message.</span><span class="sxs-lookup"><span data-stu-id="6db83-105">As with all property promotion, you use the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node in message schemas.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6db83-106">Vous devez choisir un pipeline qui promeut les propriétés afin de pouvoir accéder à et utiliser les propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="6db83-106">You must choose a pipeline that promotes properties in order to access and use the promote properties.</span></span> <span data-ttu-id="6db83-107">Par exemple, si vous utilisez le pipeline PassthruReceive, aucune propriété ne sera promue et le routage basé sur le contenu ainsi que d'autres fonctionnalités ne fonctionneront pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="6db83-107">For example, if you use the PassthruReceive pipeline, no properties will be promoted; as a result, content-based routing and other functionality will not work as expected.</span></span>  
  
 <span data-ttu-id="6db83-108">Dans le **promouvoir les propriétés** boîte de dialogue zone, assurez-vous que le **champs de propriété** onglet est sélectionné dans la partie droite de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6db83-108">In the **Promote Properties** dialog box, make sure the **Property Fields** tab is selected in the right side of the dialog box.</span></span> <span data-ttu-id="6db83-109">Vérifiez ensuite le schéma de propriété approprié est inclus dans la liste des schémas de propriété en haut de la **champs de propriété** onglet. Si nécessaire, utilisez le bouton de dossier pour sélectionner le schéma de propriété approprié à l’aide de la **sélecteur de Type BizTalk** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6db83-109">Next, ensure the appropriate property schema is included in the Property Schemas List at the top of the **Property Fields** tab. If necessary, use the folder button to select the appropriate property schema by using the **BizTalk Type Picker** dialog box.</span></span> <span data-ttu-id="6db83-110">Ensuite, développez les nœuds dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue pour rechercher et sélectionner le **Fieldelement** nœud ou **attribut de champ** nœud que vous souhaitez promouvoir en tant que champ de propriété, puis cliquez sur  **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6db83-110">Next, expand the nodes in the schema tree on the left side of the dialog box to find and select the **Field Element** node or **Field Attribute** node that you want to promote as a property field, and then click **Add**.</span></span> <span data-ttu-id="6db83-111">Enfin, utilisez la liste déroulante dans le **propriété** colonne de la **dictionnaire des champs de propriété** table pour sélectionner un **élément de champ** nœud dans un schéma de propriété avec lequel associer la propriété promue.</span><span class="sxs-lookup"><span data-stu-id="6db83-111">Finally, use the drop-down list in the **Property** column of the **Property-Fields dictionary** table to select a **Field Element** node in a property schema with which to associate the promoted property.</span></span> <span data-ttu-id="6db83-112">Pour obtenir des instructions sur la promotion des propriétés pour les champs de propriété à l’aide de la **promouvoir les propriétés** ox de la boîte de dialogue, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span><span class="sxs-lookup"><span data-stu-id="6db83-112">For step-by-step instructions about promoting properties to property fields using the **Promote Properties** dialog ox, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6db83-113">Vous pouvez également promouvoir un **enregistrement** nœud à un **élément de champ** nœud dans le schéma de propriété, mais uniquement si le **le Type de contenu** propriété de la **enregistrement**nœud a la valeur **SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="6db83-113">You can also promote a **Record** node to a **Field Element** node in the property schema, but only if the **Content Type** property of the **Record** node is set to **SimpleContent**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6db83-114">Une même propriété peut être promue plusieurs fois dans un schéma tant que les promotions sont effectuées sous différents nœuds racine.</span><span class="sxs-lookup"><span data-stu-id="6db83-114">The same property can be promoted multiple times within a schema as long as all of these promotions are performed under different root nodes.</span></span> <span data-ttu-id="6db83-115">En effet, le message est validé par rapport à un nœud racine unique et seules les propriétés promues sous ce nœud racine sont évaluées lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6db83-115">This is because the message is validated against a single root node and only properties promoted under that root node are evaluated at run time.</span></span>  
  
 <span data-ttu-id="6db83-116">Pour supprimer un **élément de champ** nœud ou **attribut de champ** à partir de l’ensemble des propriétés promues en tant que champs de propriété, sélectionnez la propriété promue dans le **dictionnaire des champs de propriété**  table sur le **champs de propriété** onglet, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="6db83-116">To remove a **Field Element** node or **Field Attribute** node from the set of properties being promoted as property fields, select the promoted property in the **Property-Fields dictionary** table on the **Property Fields** tab, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="6db83-117">Le **chemin d’accès du nœud** colonne dans la **dictionnaire des champs de propriété** table indique le XPath vers le nœud de schéma correspondant à la propriété promue.</span><span class="sxs-lookup"><span data-stu-id="6db83-117">The **Node Path** column in the **Property-Fields dictionary** table shows the XPath to the schema node corresponding to the promoted property.</span></span> <span data-ttu-id="6db83-118">Vous pouvez modifier cette valeur directement à l’aide du **modifier le XPath d’Instance** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6db83-118">You can edit this value directly by using the **Edit Instance XPath** dialog box.</span></span> <span data-ttu-id="6db83-119">Vous pouvez ouvrir cette boîte de dialogue en cliquant sur le bouton de sélection (**...** ) bouton qui apparaît à l’extrémité droite de la cellule correspondante lorsque vous sélectionnez cette cellule.</span><span class="sxs-lookup"><span data-stu-id="6db83-119">You can open this dialog box by clicking the ellipsis (**...**) button that appears at the right end of the corresponding cell when you select that cell.</span></span> <span data-ttu-id="6db83-120">La modification directe de valeurs XPath doit se faire avec discernement, car les XPath qui ne peuvent pas être résolus par l'Éditeur BizTalk empêchent le bon déroulement des opérations de validation.</span><span class="sxs-lookup"><span data-stu-id="6db83-120">Care must be taken when editing XPath values directly because XPaths that cannot be resolved by BizTalk Editor will prevent proper validation operations.</span></span>  
  
 <span data-ttu-id="6db83-121">L’Éditeur BizTalk fournit également une commande simplifiée pour la promotion de propriétés à l’aide de la **champ de propriété** mécanisme.</span><span class="sxs-lookup"><span data-stu-id="6db83-121">BizTalk Editor also provides a streamlined command for promoting properties using the **Property Field** mechanism.</span></span> <span data-ttu-id="6db83-122">Cette commande est appelée Promotion rapide, et il est disponible à l’aide du **promouvoir &#124; Promotion rapide** commande dans les menus BizTalk et contextuel.</span><span class="sxs-lookup"><span data-stu-id="6db83-122">This command is called Quick Promotion, and it is available using the **Promote &#124; Quick Promotion** command on the BizTalk and shortcut menus.</span></span> <span data-ttu-id="6db83-123">Cette commande promeut sélectionné **champ** nœud (ou **enregistrement** nœud) à un champ de propriété qui est créé automatiquement dans le schéma de propriété spécifié par le **nom du schéma de propriété par défaut**  propriété dans le **Pages de propriétés** boîte de dialogue du schéma contenant.</span><span class="sxs-lookup"><span data-stu-id="6db83-123">This command promotes the selected **Field** node (or **Record** node) to a property field that is automatically created in the property schema specified by the **Default Property Schema Name** property in the **Property Pages** dialog box for the containing schema.</span></span> <span data-ttu-id="6db83-124">Pour obtenir des instructions sur la promotion des propriétés pour les champs de propriété à l’aide de la commande Promotion rapide, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span><span class="sxs-lookup"><span data-stu-id="6db83-124">For step-by-step instructions about promoting properties to property fields using the Quick Promotion command, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
 <span data-ttu-id="6db83-125">Lorsque vous assurez la promotion d'une propriété à l'aide du mécanisme des champs de propriété, deux fragments de langage XSD (XML Schema Definition) sont ajoutés à la représentation XSD du schéma de message.</span><span class="sxs-lookup"><span data-stu-id="6db83-125">When you promote a property by using the property field mechanism, two XML Schema definition (XSD) language fragments are added to the XSD representation of the message schema.</span></span> <span data-ttu-id="6db83-126">Le premier fragment XSD est un fragment d’annotation associé à la **schéma** qui identifie le schéma de propriété correspondant, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6db83-126">The first XSD fragment is an annotation fragment associated with the **schema** element that identifies the corresponding property schema, as in the following example:</span></span>  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:imports>  
            <b:namespace prefix="ns0"  
                uri="http://BizTalk_Server_Project1.PropertySchema1"  
                location=".\propertyschema1.xsd" />  
        </b:imports>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
 <span data-ttu-id="6db83-127">Le deuxième fragment XSD est un fragment d’annotation associé à la **racine** élément (indépendamment de si elle a été renommé) qui identifie le **élément de champ** nœud ou **champ Attribut** les valeurs de nœud qui ont été promues à l’aide de la propriété de champ mécanisme, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6db83-127">The second XSD fragment is an annotation fragment associated with the **Root** element (regardless of whether it has been renamed) that identifies the **Field Element** node or **Field Attribute** node values that have been promoted by using the property field mechanism, as in the following example:</span></span>  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:properties>  
            <b:property name="ns0:PromProp1"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/@*[local-  
                 name()='Field_x0020_1']" />  
            <b:property name="ns0:PromProp2"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/*[local-  
                 name()='ProgramManager']/*[local-name()='Name']" />  
        </b:properties>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6db83-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6db83-128">See Also</span></span>  
 <span data-ttu-id="6db83-129">[Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="6db83-129">[Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md) </span></span>  
 [<span data-ttu-id="6db83-130">Comment copier des données dans le contexte du Message en tant que champs de propriété</span><span class="sxs-lookup"><span data-stu-id="6db83-130">How to Copy Data to the Message Context as Property Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)