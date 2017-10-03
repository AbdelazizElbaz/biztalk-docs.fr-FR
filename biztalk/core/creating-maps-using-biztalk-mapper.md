---
title: "Création de mappages à l’aide du Mappeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, maps
- maps, creating
- orchestrations, maps
- translations [maps]
- maps, about maps
- transformations [maps]
- maps
ms.assetid: 265e61d8-8cff-44c9-a717-8e895cb4b9bf
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12da6732729052119bfcc7841424db6d0dcaff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-maps-using-biztalk-mapper"></a><span data-ttu-id="4f3c0-102">Création de mappages à l'aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="4f3c0-102">Creating Maps Using BizTalk Mapper</span></span>
<span data-ttu-id="4f3c0-103">Le Mappeur BizTalk est un outil s'exécutant dans l'environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f3c0-103">BizTalk Mapper is a tool that runs within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="4f3c0-104">Le Mappeur BizTalk peut servir à créer et modifier des mappages qui permettront de convertir ou de transformer des messages xml.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-104">BizTalk Mapper can be used to create and edit maps, which are used for translating or transforming xml messages.</span></span> <span data-ttu-id="4f3c0-105">Les mappages sont utilisés dans les orchestrations, comme le montre l'illustration suivante, et peuvent également être utilisés pour traiter les messages reçus sur le port d'envoi, puis pour transformer le message à envoyer via les ports de réception.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-105">Maps are used in orchestrations, as the following figure suggest, and can also be used for processing messages received at a receive port, and then transforming the message to be sent via send port(s).</span></span>  
  
 <span data-ttu-id="4f3c0-106">![Diagramme de traitement entreprise avec mappages. ] (../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")</span><span class="sxs-lookup"><span data-stu-id="4f3c0-106">![Business processing diagram with maps.](../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")</span></span>  
<span data-ttu-id="4f3c0-107">Mappages dans les processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="4f3c0-107">Maps in Business Processing</span></span>  
  
 <span data-ttu-id="4f3c0-108">Les mappages vous permettent de convertir et de transformer des messages.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-108">Maps enable you to translate and to transform messages.</span></span> <span data-ttu-id="4f3c0-109">La conversion consiste à convertir un message d'un format dans un autre, par exemple convertir un fichier plat en fichier XML.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-109">Translation is the process of converting a message from one format to another format, such as converting a flat file into an XML file.</span></span> <span data-ttu-id="4f3c0-110">La transformation consiste à prendre les informations d'un message et à les placer dans un autre message.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-110">Transformation is the process of taking information from one message and inserting it in another message.</span></span> <span data-ttu-id="4f3c0-111">Par exemple, vous pouvez récupérer les adresses d'expédition et de facturation d'un bon de commande pour les insérer dans un document de facturation.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-111">For example, you might take shipping and billing addresses from a purchase order and insert them in an invoice document.</span></span>  
  
 <span data-ttu-id="4f3c0-112">Le Mappeur BizTalk utilise son propre système graphique d'icônes et de liens pour représenter la conversion et la transformation des messages d'instance d'entrée en messages d'instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-112">BizTalk Mapper uses its own graphical system of icons and links to represent the translation and transformation of input instance messages to output instance messages.</span></span> <span data-ttu-id="4f3c0-113">Il utilise la même représentation graphique de schémas que l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-113">Mapper uses the same graphical representation of schemas as BizTalk Editor.</span></span> <span data-ttu-id="4f3c0-114">Le Mappeur BizTalk conserve ses mappages sous la forme de feuilles de style XSLT (Extensible Stylesheet Language Transformations).</span><span class="sxs-lookup"><span data-stu-id="4f3c0-114">BizTalk Mapper stores its maps as Extensible Stylesheet Language Transformations (XSLT) stylesheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f3c0-115">Le Mappeur BizTalk prend en charge XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-115">BizTalk Mapper supports XSLT 1.0.</span></span> <span data-ttu-id="4f3c0-116">Il ne prend pas en charge XSLT 2.0.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-116">Using XSLT 2.0 in BizTalk Mapper is not supported.</span></span>  
  
 <span data-ttu-id="4f3c0-117">Pour plus d’informations sur la création de schémas, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).</span><span class="sxs-lookup"><span data-stu-id="4f3c0-117">For information about creating schemas, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span> <span data-ttu-id="4f3c0-118">Pour plus d’informations sur l’utilisation de mappages dans les orchestrations, consultez [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4f3c0-118">For information about using maps within orchestrations, see [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f3c0-119">Les performances d'un mappage dépendent de sa complexité (le nombre et le type de fonctoids, la taille des schémas d'entrée et de sortie), de la taille du message entrant et de votre configuration matérielle.</span><span class="sxs-lookup"><span data-stu-id="4f3c0-119">The performance of a map depends on the complexity of the map - the number and type of functoids, size of input and output schemas, the size of the input message, and your hardware.</span></span>  
  
 <span data-ttu-id="4f3c0-120">Pour plus d’informations sur l’utilisation des raccourcis clavier pour le Mappeur BizTalk, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="4f3c0-120">For information about using the keyboard shortcuts for BizTalk Mapper, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f3c0-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4f3c0-121">In This Section</span></span>  
  
-   [<span data-ttu-id="4f3c0-122">Planification de la création de mappages</span><span class="sxs-lookup"><span data-stu-id="4f3c0-122">Planning to Create Maps</span></span>](../core/planning-to-create-maps.md)  
  
-   [<span data-ttu-id="4f3c0-123">À propos des mappages</span><span class="sxs-lookup"><span data-stu-id="4f3c0-123">About Maps</span></span>](../core/about-maps.md)  
  
-   [<span data-ttu-id="4f3c0-124">À l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="4f3c0-124">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)  
  
-   [<span data-ttu-id="4f3c0-125">Création de mappages</span><span class="sxs-lookup"><span data-stu-id="4f3c0-125">Creating Maps</span></span>](../core/creating-maps.md)  
  
-   [<span data-ttu-id="4f3c0-126">La compilation et test des mappages</span><span class="sxs-lookup"><span data-stu-id="4f3c0-126">Compiling and Testing Maps</span></span>](../core/compiling-and-testing-maps.md)  
  
-   [<span data-ttu-id="4f3c0-127">Résolution des problèmes de mappages</span><span class="sxs-lookup"><span data-stu-id="4f3c0-127">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)