---
title: "À propos des schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ec2b79c-7cfe-4b00-bcff-dfad3944c83b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a452675cb11b13ae83f940ce10b09c72a622dc8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-schemas"></a><span data-ttu-id="5bb22-102">À propos des schémas</span><span class="sxs-lookup"><span data-stu-id="5bb22-102">About Schemas</span></span>
<span data-ttu-id="5bb22-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le langage XSD (XML Schema definition) pour définir la structure de tous les messages qu'il traite et fait référence à ces définitions de structure de message en tant que schémas.</span><span class="sxs-lookup"><span data-stu-id="5bb22-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the XML Schema definition (XSD) language to define the structure of all messages that it processes, and refers to these definitions of message structure as schemas.</span></span> <span data-ttu-id="5bb22-104">À de rares exceptions près, les messages structurés constituent le noyau de toute application.</span><span class="sxs-lookup"><span data-stu-id="5bb22-104">With few exceptions, structured messages are the core of any application.</span></span> <span data-ttu-id="5bb22-105">Ces messages structurés peuvent prendre n’importe quelle forme, petite ou grande, et ciblent un grand éventail de systèmes principaux et de banques de données.</span><span class="sxs-lookup"><span data-stu-id="5bb22-105">These structured messages can take any form, large or small, and target a wide array of back-end systems and data stores.</span></span> <span data-ttu-id="5bb22-106">Les systèmes qui créent et utilisent fréquemment les messages structurés font appel à des formats différents,</span><span class="sxs-lookup"><span data-stu-id="5bb22-106">Systems that create and consume the structured messages frequently use different formats.</span></span> <span data-ttu-id="5bb22-107">XML et les fichiers plats étant les deux formats les plus courants.</span><span class="sxs-lookup"><span data-stu-id="5bb22-107">Two of the most common formats for structured messages are XML and flat files.</span></span>  
  
 <span data-ttu-id="5bb22-108">L’Éditeur BizTalk est conçu pour simplifier le processus de définition d'un schéma de message et le processus de vérification de la conformité d’un message particulier à ce schéma.</span><span class="sxs-lookup"><span data-stu-id="5bb22-108">BizTalk Editor is designed to simplify the process of defining a message schema and validating whether a particular message conforms to that schema.</span></span> <span data-ttu-id="5bb22-109">Tandis que vous définissez des schémas et validez des messages, vous risquez d’être amené à effectuer certaines des tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bb22-109">In the process of defining schemas and validating messages, you will likely perform some of the following tasks:</span></span>  
  
-   <span data-ttu-id="5bb22-110">créer des schémas pour des messages XML structurés ;</span><span class="sxs-lookup"><span data-stu-id="5bb22-110">Create schemas for structured XML messages.</span></span>  
  
-   <span data-ttu-id="5bb22-111">créer des schémas pour des messages de fichier plat ;</span><span class="sxs-lookup"><span data-stu-id="5bb22-111">Create schemas for flat file messages.</span></span>  
  
-   <span data-ttu-id="5bb22-112">générer des schémas à partir de données d’instance XML correctement formées ;</span><span class="sxs-lookup"><span data-stu-id="5bb22-112">Generate schemas from well-formed XML instance data.</span></span>  
  
-   <span data-ttu-id="5bb22-113">valider la conformité d’un message à un schéma spécifique ;</span><span class="sxs-lookup"><span data-stu-id="5bb22-113">Validate message conformance to a specific schema.</span></span>  
  
-   <span data-ttu-id="5bb22-114">effectuer la validation de schémas au moment la conception.</span><span class="sxs-lookup"><span data-stu-id="5bb22-114">Perform design-time validation of schemas.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5bb22-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5bb22-115">In This Section</span></span>  
  
-   [<span data-ttu-id="5bb22-116">Différents Types de schémas BizTalk</span><span class="sxs-lookup"><span data-stu-id="5bb22-116">Different Types of BizTalk Schemas</span></span>](../core/different-types-of-biztalk-schemas.md)  
  
-   [<span data-ttu-id="5bb22-117">Rôle du langage XSD</span><span class="sxs-lookup"><span data-stu-id="5bb22-117">Role of XSD</span></span>](../core/role-of-xsd.md)  
  
-   [<span data-ttu-id="5bb22-118">Ressources XSD sur le Web</span><span class="sxs-lookup"><span data-stu-id="5bb22-118">XSD Resources on the Web</span></span>](../core/xsd-resources-on-the-web.md)  
  
-   [<span data-ttu-id="5bb22-119">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="5bb22-119">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)  
  
-   [<span data-ttu-id="5bb22-120">Schémas utilisant d’autres schémas</span><span class="sxs-lookup"><span data-stu-id="5bb22-120">Schemas That Use Other Schemas</span></span>](../core/schemas-that-use-other-schemas.md)  
  
-   [<span data-ttu-id="5bb22-121">Type réutilisation et dérivations</span><span class="sxs-lookup"><span data-stu-id="5bb22-121">Type Reuse and Derivations</span></span>](../core/type-reuse-and-derivations.md)  
  
-   [<span data-ttu-id="5bb22-122">Migration de schéma à partir de Versions précédentes de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5bb22-122">Schema Migration from Previous Versions of BizTalk Server</span></span>](../core/schema-migration-from-previous-versions-of-biztalk-server.md)  
  
-   [<span data-ttu-id="5bb22-123">Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle</span><span class="sxs-lookup"><span data-stu-id="5bb22-123">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)  
  
-   [<span data-ttu-id="5bb22-124">Validation de schéma dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5bb22-124">Schema Validation in Visual Studio</span></span>](../core/schema-validation-in-visual-studio.md)  
  
-   [<span data-ttu-id="5bb22-125">Validation et génération de Message d’instance</span><span class="sxs-lookup"><span data-stu-id="5bb22-125">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)