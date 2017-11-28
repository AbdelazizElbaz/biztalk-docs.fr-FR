---
title: Comment utiliser des mappages dans les Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd628d8-c163-431d-8ad7-d7d77007c549
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e67249857ec00b2ca66648c1985f0c336d93b3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-maps-in-orchestrations"></a><span data-ttu-id="52cef-102">Utilisation des mappages dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="52cef-102">How to Use Maps in Orchestrations</span></span>
<span data-ttu-id="52cef-103">Le Mappeur BizTalk est un outil s'exécutant dans l'environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52cef-103">BizTalk Mapper is a tool that runs within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="52cef-104">Il vous permet de créer et de modifier des mappages dans lesquels vous utilisez des liens et des fonctoids pour définir la relation entre un schéma d'entrée et un schéma de sortie.</span><span class="sxs-lookup"><span data-stu-id="52cef-104">You use BizTalk Mapper to create and edit maps in which you use links and functoids to define the relationship between an input and an output schema.</span></span> <span data-ttu-id="52cef-105">Les liens définissent une copie de données directe d'un enregistrement ou d'un champ.</span><span class="sxs-lookup"><span data-stu-id="52cef-105">A link defines a direct data copy of a record or field.</span></span> <span data-ttu-id="52cef-106">Ils peuvent établir des connexions directes avec les éléments de l'autre schéma ou peuvent former des connexions avec des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="52cef-106">Links may directly connect to items in the other schema, or they may form connections to functoids.</span></span> <span data-ttu-id="52cef-107">Les fonctoids effectuent des manipulations de données plus complexes.</span><span class="sxs-lookup"><span data-stu-id="52cef-107">Functoids perform more complex data manipulations.</span></span>  
  
## <a name="examples-of-using-maps"></a><span data-ttu-id="52cef-108">Exemples d'utilisation de mappages</span><span class="sxs-lookup"><span data-stu-id="52cef-108">Examples of Using Maps</span></span>  
 <span data-ttu-id="52cef-109">Les exemples suivants vous présentent comment utiliser les mappages :</span><span class="sxs-lookup"><span data-stu-id="52cef-109">The following samples show ways in which you can use maps:</span></span>  
  
-   [<span data-ttu-id="52cef-110">Outils XML (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="52cef-110">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="52cef-111">PartyResolution (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="52cef-111">PartyResolution (BizTalk Server Sample)</span></span>](../core/partyresolution-biztalk-server-sample.md)  
  
-   <span data-ttu-id="52cef-112">Téléchargez l’exemple du Kit de développement logiciel « À l’aide du fonctoid copie de masse » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="52cef-112">Download the SDK sample "Using the Mass Copy Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="52cef-113">Téléchargez l’exemple du Kit de développement logiciel « À l’aide du fonctoid de bouclage » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="52cef-113">Download the SDK sample "Using the Looping Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="52cef-114">Téléchargez l’exemple du Kit de développement logiciel « Mapping to a Repeating Structure » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="52cef-114">Download the SDK sample "Mapping to a Repeating Structure" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="52cef-115">Téléchargez l’exemple du Kit de développement logiciel « À l’aide du fonctoid Bouclage de Table » [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="52cef-115">Download the SDK sample "Using the Table Looping Functoid" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="52cef-116">Téléchargez l’exemple de kit de développement logiciel « Using de mappage de valeur et de Value Mapping (Flattening) Functoids » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="52cef-116">Download the SDK sample "Using the Value Mapping and Value Mapping (Flattening) Functoids" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cef-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52cef-117">See Also</span></span>  
 <span data-ttu-id="52cef-118">[Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="52cef-118">[Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md) </span></span>  
 <span data-ttu-id="52cef-119">[Construction de Messages](../core/constructing-messages.md) </span><span class="sxs-lookup"><span data-stu-id="52cef-119">[Constructing Messages](../core/constructing-messages.md) </span></span>  
 <span data-ttu-id="52cef-120">[Comment configurer la forme Transformer](../core/how-to-configure-the-transform-shape.md) </span><span class="sxs-lookup"><span data-stu-id="52cef-120">[How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md) </span></span>  
 [<span data-ttu-id="52cef-121">Comment utiliser des Expressions pour transformer dynamiquement des Messages</span><span class="sxs-lookup"><span data-stu-id="52cef-121">How to Use Expressions to Dynamic Transform Messages</span></span>](../core/how-to-use-expressions-to-dynamic-transform-messages.md)