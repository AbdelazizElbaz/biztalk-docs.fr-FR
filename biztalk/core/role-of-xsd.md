---
title: "Rôle du langage XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe08f6b-563f-4bae-a5be-551e487b2a6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad2f99b60de5ebb2a3cd7e102a2f3f7b787d1ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="role-of-xsd"></a><span data-ttu-id="3eb09-102">Rôle du langage XSD</span><span class="sxs-lookup"><span data-stu-id="3eb09-102">Role of XSD</span></span>
<span data-ttu-id="3eb09-103">Le langage XSD (XML Schema definition) fournit la syntaxe sous-jacente des schémas de message définis dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3eb09-103">The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk.</span></span> <span data-ttu-id="3eb09-104">Bien que les arborescences de l’Éditeur et du Mappeur BizTalk utilisent une hiérarchie graphique propre à BizTalk pour les nœuds d'enregistrement et de champ (entre autres types de nœuds), chacune associée à son propre ensemble de propriétés, de telles hiérarchies sont élaborées et conservées au format XSD.</span><span class="sxs-lookup"><span data-stu-id="3eb09-104">Although the tree views in BizTalk Editor and BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD.</span></span> <span data-ttu-id="3eb09-105">L’Éditeur BizTalk fournit une vue XSD en lecture seule dans laquelle vous pouvez voir le XSD construit lorsque différents nœuds sont ajoutés ou supprimés de la représentation graphique du schéma dans la vue de l’arborescence et lors de la modification des valeurs des propriétés associées à ces nœuds.</span><span class="sxs-lookup"><span data-stu-id="3eb09-105">BizTalk Editor provides a read-only XSD view in which you can see the XSD that is constructed as various nodes are added to or removed from the graphic representation of the schema in the tree view, and as the values of the properties associated with those nodes are changed.</span></span> <span data-ttu-id="3eb09-106">Bien qu'il ne soit généralement pas nécessaire de comprendre les détails de XSD pour créer correctement des schémas simples avec l’Éditeur BizTalk, si vous étudiez les modifications XSD à mesure que vous apportez des modifications à la hiérarchie de schéma dans la vue d'arborescence, vous apprendrez à utiliser XSD.</span><span class="sxs-lookup"><span data-stu-id="3eb09-106">Although it is usually not necessary to understand the details of XSD to successfully construct simple schemas with BizTalk Editor, if you study the XSD changes as you make changes to the schema hierarchy in the tree view, you will learn to use XSD.</span></span>  
  
 <span data-ttu-id="3eb09-107">Le composant d'annotation de schéma dans XSD, associé au large éventail d’annotations définies par BizTalk Server, permet d’étendre XSD efficacement afin qu'il prenne en charge la sémantique nécessaire à la représentation des messages non XML tels que les fichiers plats.</span><span class="sxs-lookup"><span data-stu-id="3eb09-107">The schema annotation feature within XSD, with the extensive set of annotations defined by BizTalk Server, effectively allows XSD to be extended to support the necessary semantics for representing non-XML messages such as flat files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb09-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eb09-108">See Also</span></span>  
 <span data-ttu-id="3eb09-109">[Ressources XSD sur le Web](../core/xsd-resources-on-the-web.md) </span><span class="sxs-lookup"><span data-stu-id="3eb09-109">[XSD Resources on the Web](../core/xsd-resources-on-the-web.md) </span></span>  
 [<span data-ttu-id="3eb09-110">À propos des schémas</span><span class="sxs-lookup"><span data-stu-id="3eb09-110">About Schemas</span></span>](../core/about-schemas.md)