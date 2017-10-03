---
title: "Gestionnaires de propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 823352a0-e397-464a-a163-1dbf8feea8d7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aff8fc39612ed79e6e9602ed39874d014bb4a11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-managers"></a><span data-ttu-id="a9e10-102">Gestionnaires de propriétés</span><span class="sxs-lookup"><span data-stu-id="a9e10-102">Property Managers</span></span>
<span data-ttu-id="a9e10-103">Les gestionnaires de propriétés permettent à une extension d'ajouter des propriétés personnalisées (comme annotations XSD généralement) à des éléments et des attributs dans la représentation XSD du schéma, ainsi que d'étendre la fenêtre Propriétés pour inclure les propriétés personnalisées associées à l'extension.</span><span class="sxs-lookup"><span data-stu-id="a9e10-103">Property Managers allow an extension to add custom properties (generally as XSD annotations) to elements and attributes in the XSD representation of the schema, as well as extending the Properties window to include the custom properties associated with the extension.</span></span>  
  
 <span data-ttu-id="a9e10-104">Un gestionnaire de propriétés est un objet qui implémente le **IPropertyManager** interface, une référence à ce qui est obtenue en appelant **IExtension.GetPropertyManager**et en passant un  **ITreeNode** objet en tant que paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a9e10-104">A Property Manager is an object that implements the **IPropertyManager** interface, a reference to which is obtained by calling **IExtension.GetPropertyManager**, and passing an **ITreeNode** object as the input parameter.</span></span> <span data-ttu-id="a9e10-105">L’extension fournit généralement une **IPropertyManager** objet pour chaque **ITreeNode** objet.</span><span class="sxs-lookup"><span data-stu-id="a9e10-105">Typically the extension provides one **IPropertyManager** object for each **ITreeNode** object.</span></span> <span data-ttu-id="a9e10-106">Le Gestionnaire de propriétés est responsable de la collection de propriétés personnalisées pour ce **ITreeNode** objet.</span><span class="sxs-lookup"><span data-stu-id="a9e10-106">The Property Manager is responsible for the collection of custom properties for that **ITreeNode** object.</span></span>  
  
 <span data-ttu-id="a9e10-107">Une propriété personnalisée est représentée par un **System.ComponentModel.PropertyDescriptor** objet, qui peut être obtenu à partir de la collection retournée par la **IPropertyManager.GetProperties** (méthode).</span><span class="sxs-lookup"><span data-stu-id="a9e10-107">A custom property is represented by a **System.ComponentModel.PropertyDescriptor** object, which can be obtained from the collection returned by the **IPropertyManager.GetProperties** method.</span></span>  
  
 <span data-ttu-id="a9e10-108">À l’aide de **PropertyDescriptor** objets pour représenter les propriétés personnalisées associées à l’extension facilite l’intégration à Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="a9e10-108">Using **PropertyDescriptor** objects to represent the custom properties associated with the extension facilitates integration with the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span> <span data-ttu-id="a9e10-109">Lorsque **PropertyDescriptor** objets sont utilisés, il est facile pour l’Éditeur BizTalk pour intégrer les propriétés personnalisées de l’extension de l’ensemble de propriétés de nœud standard déjà en cours d’intégration dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="a9e10-109">When **PropertyDescriptor** objects are used, it is easy for BizTalk Editor to integrate the custom properties of the extension into the set of standard node properties already being integrated into the Properties window.</span></span> <span data-ttu-id="a9e10-110">Informations sur les propriétés personnalisées telles que le nom d’affichage, la valeur d’affichage, le type de contrôle de la propriété, la description de la propriété et la catégorie de propriété sont obtenues à partir de la **PropertyDescriptor** objet.</span><span class="sxs-lookup"><span data-stu-id="a9e10-110">Custom property information such as the display name, the display value, the type of property control, the property description, and the property category is obtained from the **PropertyDescriptor** object.</span></span>  
  
 <span data-ttu-id="a9e10-111">Des propriétés personnalisées sont stockées dans la représentation XSD du schéma en tant qu'attributs d'un élément au sein de l'élément d'annotation dans l'élément correspondant au nœud pertinent de l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="a9e10-111">Custom properties are stored in the XSD representation of the schema as attributes of an element within the annotation element within the element corresponding to the relevant node in the schema tree.</span></span> <span data-ttu-id="a9e10-112">Chaque propriété personnalisée d'un nœud d'arborescence de schéma peut être un attribut d'un élément commun mais chacune peut également avoir son propre élément associé.</span><span class="sxs-lookup"><span data-stu-id="a9e10-112">Each custom property of a schema tree node can be an attribute of a common element, or alternatively, each can have its own associated element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e10-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9e10-113">See Also</span></span>  
 [<span data-ttu-id="a9e10-114">Extension de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="a9e10-114">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)