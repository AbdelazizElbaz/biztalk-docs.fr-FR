---
title: "Dérivation de Type Global complexe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbf429d0-64f4-4c43-a5f7-e8af050803b9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee4e6235af62b2c08c08382b897632d15e34e0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-global-type-derivation"></a><span data-ttu-id="925d8-102">Dérivation de types globaux complexes</span><span class="sxs-lookup"><span data-stu-id="925d8-102">Complex Global Type Derivation</span></span>
<span data-ttu-id="925d8-103">Il existe deux types d’héritages dans XSD : extension et restriction.</span><span class="sxs-lookup"><span data-stu-id="925d8-103">There are two types of inheritance in XSD: extension and restriction.</span></span> <span data-ttu-id="925d8-104">L’Éditeur BizTalk fournit l’accès à ces fonctionnalités XSD à l’aide de deux suivants **enregistrement** propriétés de nœud :</span><span class="sxs-lookup"><span data-stu-id="925d8-104">BizTalk Editor provides access to this XSD functionality by using the following two **Record** node properties:</span></span>  
  
-   <span data-ttu-id="925d8-105">**Type de données de base**.</span><span class="sxs-lookup"><span data-stu-id="925d8-105">**Base Data Type**.</span></span> <span data-ttu-id="925d8-106">cette propriété fournit la liste de tous les types complexes globaux et types simples disponibles en tant que type de données de base.</span><span class="sxs-lookup"><span data-stu-id="925d8-106">This property provides the list of all global complex types and simple types available for use as a base data type.</span></span> <span data-ttu-id="925d8-107">Les types globaux complexes peuvent se trouver dans un même schéma ou dans n'importe quel schéma importé.</span><span class="sxs-lookup"><span data-stu-id="925d8-107">The complex global types can be in the same schema or in any imported schema.</span></span>  
  
-   <span data-ttu-id="925d8-108">**Derived By**.</span><span class="sxs-lookup"><span data-stu-id="925d8-108">**Derived By**.</span></span> <span data-ttu-id="925d8-109">cette propriété sert à faire un choix entre la dérivation par extension et la dérivation par restriction.</span><span class="sxs-lookup"><span data-stu-id="925d8-109">This property is used to choose between deriving by extension or by restriction.</span></span> <span data-ttu-id="925d8-110">Cette propriété est automatiquement définie sur **Extension** lorsque vous définissez la **Base Data Type** propriété à n’importe quel type dans la liste.</span><span class="sxs-lookup"><span data-stu-id="925d8-110">This property is automatically set to **Extension** when you set the **Base Data Type** property to any type in the list.</span></span> <span data-ttu-id="925d8-111">Si vous définissez cette propriété sur **(par défaut)**, tout type dans le **Base Data Type** propriété est supprimée, la désactivation de l’héritage pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="925d8-111">If you set this property to **(Default)**, any type in the **Base Data Type** property is removed, disabling inheritance for the node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="925d8-112">Le **le Type de contenu** est également définie automatiquement à **ComplexContent** lorsque la dérivation par restriction ou extension est utilisée.</span><span class="sxs-lookup"><span data-stu-id="925d8-112">The **Content Type** property is also set automatically to **ComplexContent** when derivation by extension or restriction is being used.</span></span>  
  
 <span data-ttu-id="925d8-113">Cette section explique la dérivation de type complexe en utilisant les mécanismes d'extension et restriction de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="925d8-113">This section explains complex type derivation by using the extension and restriction mechanisms in greater detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="925d8-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="925d8-114">In This Section</span></span>  
  
-   [<span data-ttu-id="925d8-115">Dérivation de Type complexe à l’aide du mécanisme d’Extension</span><span class="sxs-lookup"><span data-stu-id="925d8-115">Complex Type Derivation Using the Extension Mechanism</span></span>](../core/complex-type-derivation-using-the-extension-mechanism.md)  
  
-   [<span data-ttu-id="925d8-116">Dérivation de Type complexe à l’aide du mécanisme de Restriction</span><span class="sxs-lookup"><span data-stu-id="925d8-116">Complex Type Derivation Using the Restriction Mechanism</span></span>](../core/complex-type-derivation-using-the-restriction-mechanism.md)