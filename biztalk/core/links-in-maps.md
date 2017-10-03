---
title: Les liens dans les mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Looping
- Looping functoids
- maps, links
- BizTalk Mapper, links
ms.assetid: 3db77b8d-7b86-4c00-99a0-0513aff9b56b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32d2a9ef07cf2d79037d7983e49b26c6cfe5e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="links-in-maps"></a><span data-ttu-id="a1de0-102">Liens figurant dans les mappages</span><span class="sxs-lookup"><span data-stu-id="a1de0-102">Links in Maps</span></span>
<span data-ttu-id="a1de0-103">Les liens spécifient la fonction de base de copie des données d'un élément ou d'un attribut d'un message d'instance d'entrée vers un élément ou un attribut d'une instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1de0-103">Links specify the basic function of copying data from an element or attribute in an input instance message to an element or attribute in an output instance.</span></span> <span data-ttu-id="a1de0-104">Vous créez des liens entre les enregistrements et les champs des schémas source et de destination au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="a1de0-104">You create links between records and fields in the source and destination schemas at design time.</span></span> <span data-ttu-id="a1de0-105">Cela se traduit par la création, au moment de l’exécution, d’un message d’instance de sortie conforme au schéma de destination à partir d’un message d’instance d'entrée conforme au schéma source.</span><span class="sxs-lookup"><span data-stu-id="a1de0-105">This drives the creation, at run time, of an output instance message conforming to the destination schema from an input instance message conforming to the source schema.</span></span>  
  
 <span data-ttu-id="a1de0-106">Le Mappeur BizTalk prend en charge les liens un-à-un et un-à-plusieurs.</span><span class="sxs-lookup"><span data-stu-id="a1de0-106">BizTalk Mapper supports one-to-one links and one-to-many links.</span></span> <span data-ttu-id="a1de0-107">Par exemple, un lien peut connecter un enregistrement ou un champ unique d'un schéma source à un enregistrement ou un champ unique du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="a1de0-107">For example, a link can connect a single record or field from the source schema to a single record or field in the destination schema.</span></span> <span data-ttu-id="a1de0-108">Il peut également connecter un enregistrement ou un champ unique d'un schéma source à de multiples enregistrements ou champs du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="a1de0-108">A link can also connect a single record or field from the source schema to multiple records or fields in the destination schema.</span></span>  
  
 <span data-ttu-id="a1de0-109">Les liens peuvent également connecter plusieurs enregistrements ou champs d’un schéma source à un fonctoid, qui se connecte ensuite à un ou plusieurs enregistrements ou champs du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="a1de0-109">Links can also connect multiple records or fields from the source schema to a functoid, which then connects to a single (or multiple) record(s) and/or field(s) in the destination schema.</span></span> <span data-ttu-id="a1de0-110">En général, les liens reliant directement plusieurs enregistrements ou champs source à un enregistrement ou un champ de destination unique ne sont pas valides et génèrent un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a1de0-110">In general, direct links from multiple source records or fields to a single destination record or field are not valid and produce a warning.</span></span> <span data-ttu-id="a1de0-111">Une exception à cela est la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="a1de0-111">One exception to this is the **Looping** functoid.</span></span> <span data-ttu-id="a1de0-112">Pour plus d’informations sur la **bouclage** fonctoid, consultez [fonctoid Bouclage](../core/looping-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="a1de0-112">For more information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).</span></span>  
  
 <span data-ttu-id="a1de0-113">Les rubriques de cette section décrivent des concepts liés à la création et à l'utilisation des liens dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a1de0-113">The topics in this section describe concepts related to creating and working with links in BizTalk Mapper.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1de0-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a1de0-114">In This Section</span></span>  
  
-   [<span data-ttu-id="a1de0-115">Types de liens</span><span class="sxs-lookup"><span data-stu-id="a1de0-115">Types of Links</span></span>](../core/types-of-links.md)  
  
-   [<span data-ttu-id="a1de0-116">Création de liens</span><span class="sxs-lookup"><span data-stu-id="a1de0-116">Creating Links</span></span>](../core/creating-links.md)  
  
-   [<span data-ttu-id="a1de0-117">Configuration des liaisons</span><span class="sxs-lookup"><span data-stu-id="a1de0-117">Configuring Links</span></span>](../core/configuring-links.md)  
  
-   [<span data-ttu-id="a1de0-118">Création de liens enregistrement à enregistrement</span><span class="sxs-lookup"><span data-stu-id="a1de0-118">Record-to-Record Linking</span></span>](../core/record-to-record-linking.md)  
  
-   [<span data-ttu-id="a1de0-119">Liens vers et à partir de tout élément et tout attribut nœuds</span><span class="sxs-lookup"><span data-stu-id="a1de0-119">Links To and From the Any Element and anyAttribute Nodes</span></span>](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)  
  
-   [<span data-ttu-id="a1de0-120">Liens et des Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="a1de0-120">Compiler Directives and Links</span></span>](../core/compiler-directives-and-links.md)