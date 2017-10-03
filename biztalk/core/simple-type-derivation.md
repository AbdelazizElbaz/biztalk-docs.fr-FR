---
title: "Dérivation de Type simple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43932a0-039c-4211-82c0-087bae186145
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcc74796de8543f1e0f895d0b3dff705aeb2930e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation"></a><span data-ttu-id="03a34-102">Dérivation de type simple</span><span class="sxs-lookup"><span data-stu-id="03a34-102">Simple Type Derivation</span></span>
<span data-ttu-id="03a34-103">Le langage XSD (XML Schema Definition) fournit plusieurs mécanismes de définition de variantes de types simples, basés sur des dérivations de types simples existants :</span><span class="sxs-lookup"><span data-stu-id="03a34-103">XML Schema definition (XSD) language provides several mechanisms for defining variations of simple types, based on derivations of existing simple types, as follows:</span></span>  
  
-   <span data-ttu-id="03a34-104">**Restriction**.</span><span class="sxs-lookup"><span data-stu-id="03a34-104">**Restriction**.</span></span> <span data-ttu-id="03a34-105">la dérivation de type simple par utilisation du mécanisme de restriction implique l'introduction de restrictions concernant les valeurs possibles pour ce type.</span><span class="sxs-lookup"><span data-stu-id="03a34-105">Simple type derivation by using the restriction mechanism involves the introduction of restrictions to the possible values for that type.</span></span> <span data-ttu-id="03a34-106">Exemples : les valeurs minimum et/ou maximum pour les types numériques, ou une longueur minimum et maximum pour les types de chaîne.</span><span class="sxs-lookup"><span data-stu-id="03a34-106">Examples are minimum and/or maximum values for numeric types, or a minimum and maximum length for string types.</span></span>  
  
-   <span data-ttu-id="03a34-107">**Liste**.</span><span class="sxs-lookup"><span data-stu-id="03a34-107">**List**.</span></span> <span data-ttu-id="03a34-108">la dérivation de type simple par utilisation du mécanisme de liste permet qu'une seule valeur d'attribut ou d'élément dans un message d'instance soit définie comme se composant d'une liste de valeurs séparées par des espaces et d'un type particulier.</span><span class="sxs-lookup"><span data-stu-id="03a34-108">Simple type derivation by using the list mechanism allows a single attribute or element value in an instance message to be defined as consisting of a list of space-separated values of a particular type.</span></span>  
  
-   <span data-ttu-id="03a34-109">**Union**.</span><span class="sxs-lookup"><span data-stu-id="03a34-109">**Union**.</span></span> <span data-ttu-id="03a34-110">la dérivation de type simple par utilisation du mécanisme d'union permet qu'une seule valeur d'attribut ou d'élément dans un message d'instance soit définie comme une valeur unique d'un ou plusieurs types spécifiés.</span><span class="sxs-lookup"><span data-stu-id="03a34-110">Simple type derivation by using the union mechanism allows a single attribute or element value in an instance message to be defined as a single value of one of several specified types.</span></span>  
  
 <span data-ttu-id="03a34-111">Cette section décrit ces dérivations de type simple de façon plus détaillée. Vous y apprendrez notamment comment les définir en définissant les propriétés de nœud appropriées dans la fenêtre Propriétés ainsi que comment l'XSD correspondant est construit.</span><span class="sxs-lookup"><span data-stu-id="03a34-111">This section describes these simple type derivations in more detail, including how to define these derivations by setting the appropriate node properties in the Properties window, as well as how the corresponding XSD is constructed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03a34-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="03a34-112">In This Section</span></span>  
  
-   [<span data-ttu-id="03a34-113">Dérivation de Type simple à l’aide du mécanisme de Restriction</span><span class="sxs-lookup"><span data-stu-id="03a34-113">Simple Type Derivation Using the Restriction Mechanism</span></span>](../core/simple-type-derivation-using-the-restriction-mechanism.md)  
  
-   [<span data-ttu-id="03a34-114">Dérivation de Type simple à l’aide du mécanisme de liste</span><span class="sxs-lookup"><span data-stu-id="03a34-114">Simple Type Derivation Using the List Mechanism</span></span>](../core/simple-type-derivation-using-the-list-mechanism.md)  
  
-   [<span data-ttu-id="03a34-115">Dérivation de Type simple à l’aide du mécanisme d’Union</span><span class="sxs-lookup"><span data-stu-id="03a34-115">Simple Type Derivation Using the Union Mechanism</span></span>](../core/simple-type-derivation-using-the-union-mechanism.md)