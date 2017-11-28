---
title: Codes de fin de fichier plat Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe115a5-4fdc-4779-94f3-437b5a06fbd4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cbeaef3f23de3cb89d873413964cd331ec23f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-message-trailers"></a><span data-ttu-id="ec9bb-102">Codes de fin de message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="ec9bb-102">Flat File Message Trailers</span></span>
<span data-ttu-id="ec9bb-103">Comme avec les en-têtes de message d’instance de fichier plat, l’analyse du code de fin de message d’instance fichier plat facultatif par le désassembleur de fichier plat est contrôlée par le schéma de fichier plat que vous avez configuré dans le **schéma de code de fin** au moment du design propriété désassembleur de fichier plat ou **XMLNORM. TrailerSpecName** propriété de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="ec9bb-103">As with flat file instance message headers, the parsing of the optional flat file instance message trailer by the flat file disassembler is controlled by the flat file schema that you have configured in the **Trailer schema** design-time property of the flat file disassembler or the **XMLNORM.TrailerSpecName** message context property.</span></span> <span data-ttu-id="ec9bb-104">Si vous n'avez pas spécifié de schéma utilisant une de ces deux méthodes, le désassembleur de fichier plat supposera que le message d'instance de fichier plat ne contient pas de code de fin.</span><span class="sxs-lookup"><span data-stu-id="ec9bb-104">If you have not specified a schema using one of these two methods, the flat file disassembler will assume that the flat file instance message does not contain a trailer.</span></span>  
  
 <span data-ttu-id="ec9bb-105">À la différence des en-têtes de message d'instance de fichier plat, les codes de fin de message d'instance de fichier plat ne peuvent ni être enregistrés et restaurés en tant qu'unité unique, ni utiliser la promotion de propriété pour copier des éléments individuels de données dans le contexte de message associé au corps de message d'instance de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="ec9bb-105">Unlike with flat file instance message headers, flat file instance message trailers can neither be saved and restored as a single unit, nor can they use property promotion to copy individual items of data to the message context associated with the flat file instance message body.</span></span> <span data-ttu-id="ec9bb-106">Toutefois, un code de fin peut être ajouté à un message d’instance de fichier plat sortants en spécifiant le schéma approprié dans le **schéma de code de fin** propriété au moment du design de l’assembleur de fichier plat ou **XMLNORM. TrailerSpecName** propriété de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="ec9bb-106">However, a trailer can be added to an outbound flat file instance message by specifying the appropriate schema in the **Trailer schema** design-time property of the flat file assembler or the **XMLNORM.TrailerSpecName** message context property.</span></span> <span data-ttu-id="ec9bb-107">Les données qui constituent la partie variable du code de fin peuvent être spécifiées en utilisant la rétrogradation de propriétés du contexte de message du corps de message d'instance de fichier plat ou en spécifiant des valeurs par défaut ou fixes dans le schéma correspondant.</span><span class="sxs-lookup"><span data-stu-id="ec9bb-107">The data that constitutes the variable portion of the trailer can be specified using property demotion from the message context of the flat file instance message body, or by specifying default or fixed values in the corresponding schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9bb-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec9bb-108">See Also</span></span>  
 <span data-ttu-id="ec9bb-109">[En-têtes de Message de fichier plat](../core/flat-file-message-headers.md) </span><span class="sxs-lookup"><span data-stu-id="ec9bb-109">[Flat File Message Headers](../core/flat-file-message-headers.md) </span></span>  
 <span data-ttu-id="ec9bb-110">[Corps de Message de fichier plat](../core/flat-file-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="ec9bb-110">[Flat File Message Bodies](../core/flat-file-message-bodies.md) </span></span>  
 <span data-ttu-id="ec9bb-111">[Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="ec9bb-111">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="ec9bb-112">Comment créer des schémas pour les Messages de fichier plat</span><span class="sxs-lookup"><span data-stu-id="ec9bb-112">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)