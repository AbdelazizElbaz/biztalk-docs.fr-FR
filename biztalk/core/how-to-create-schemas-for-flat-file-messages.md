---
title: "Comment créer des schémas pour les Messages de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48f2747b-7f26-4fb2-a855-523e093f3813
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58583037b8fae945dea07aa8af62e969b96e073f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-for-flat-file-messages"></a><span data-ttu-id="d8bb6-102">Création de schémas pour les Messages de fichier plat</span><span class="sxs-lookup"><span data-stu-id="d8bb6-102">Create Schemas for Flat File Messages</span></span>

## <a name="overview"></a><span data-ttu-id="d8bb6-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="d8bb6-103">Overview</span></span>
<span data-ttu-id="d8bb6-104">Après la création d’un schéma de message XML comme décrit dans [création de schémas pour les Messages XML](../core/how-to-create-schemas-for-xml-messages.md), utilisez le **Extensions de l’éditeur de schéma** propriété de la **schéma** nœud pour permettre la extension de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-104">After creating an XML message schema as described in [Creating Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md), use the **Schema Editor Extensions** property of the **Schema** node to enable the flat file extension.</span></span> <span data-ttu-id="d8bb6-105">L'activation de l'extension de fichier plat ajoute un nombre considérable de propriétés à de nombreux types de nœud au sein d’un schéma.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-105">Enabling the flat file extension adds a considerable number of properties to many of the node types within a schema.</span></span> <span data-ttu-id="d8bb6-106">Ces propriétés sont généralement utilisées pour contrôler la façon dont un document commercial de fichier plat est converti depuis et vers son équivalent XML, et leurs valeurs sont conservées sous forme d’annotation en langage XSD (XML Schema definition) dans le fichier de schéma.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-106">These properties are generally used to control how a flat file business document is translated to and from its equivalent XML business document, and their values are stored as XML Schema definition language (XSD ) annotations within the schema file.</span></span> <span data-ttu-id="d8bb6-107">L'utilisation correcte de ces propriétés demande une certaine pratique et une bonne compréhension des aspects du format de fichier plat concernés par chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-107">Using these properties properly takes some practice and a thorough understanding of which aspects of the flat file format they each govern.</span></span> 

<span data-ttu-id="d8bb6-108">Pour conceptuel et les informations de référence sur les propriétés de fichier plat, voir [Considérations lors de la création de Message schémas de fichier plat](../core/considerations-when-creating-flat-file-message-schemas.md) et **des propriétés de nœud supplémentaires pour les schémas de fichier plat** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="d8bb6-108">For conceptual and reference information about the flat file properties, see [Considerations When Creating Flat File Message Schemas](../core/considerations-when-creating-flat-file-message-schemas.md) and **Supplemental Node Properties for Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bb6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8bb6-109">See Also</span></span>  
-  [<span data-ttu-id="d8bb6-110">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="d8bb6-110">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)
-  <span data-ttu-id="d8bb6-111">Plus d’informations sur ces propriétés.[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bb6-111">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>