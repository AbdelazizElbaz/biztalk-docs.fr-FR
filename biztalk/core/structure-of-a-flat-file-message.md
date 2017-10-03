---
title: "Structure d’un Message de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00f2adf6-a47c-498b-b5ae-c6bd55bafceb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badb8aacf6f2ed8ce9e38f1ea6bbe432a1d3b89e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-a-flat-file-message"></a><span data-ttu-id="523bb-102">Structure d'un message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="523bb-102">Structure of a Flat File Message</span></span>
<span data-ttu-id="523bb-103">Dans le contexte de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un message d’instance de fichier plat est un fichier texte qui peut contenir trois parties logiques : un en-tête, un corps et un code de fin, dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="523bb-103">In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a flat file instance message is a text file that can contain three logical parts: a header, a body, and a trailer, in that order.</span></span> <span data-ttu-id="523bb-104">L’en-tête et le code de fin sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="523bb-104">Both the header and the trailer are optional.</span></span> <span data-ttu-id="523bb-105">L’exemple suivant indique un message d’instance de fichier plat constitué des trois parties, le corps affiché en caractères gras.</span><span class="sxs-lookup"><span data-stu-id="523bb-105">The following example shows a flat file instance message that consists of all three parts, with the body shown in bold type.</span></span>  
  
```  
Microsoft Corporation  
One Microsoft Way  
Redmond, WA 98033  
  
TRANSACTION-1111,1  
  
```  
  
 <span data-ttu-id="523bb-106">Pour que le désassembleur de fichier plat puisse distinguer correctement l'en-tête du corps et du code de fin d'un message d'instance de fichier plat, vous devez créer et configurer un schéma séparé pour chaque.</span><span class="sxs-lookup"><span data-stu-id="523bb-106">For the flat file disassembler to correctly distinguish the header, the body, and the trailer of a flat file instance message, you must create and configure a separate schema for each of them.</span></span>  
  
 <span data-ttu-id="523bb-107">Au sein d’une partie précise d’un message d’instance de fichier plat, différents éléments de données sont regroupés en enregistrements, qui peuvent à leur tour contenir des sous-enregistrements comprenant des éléments de données individuels, correspondant aux champs.</span><span class="sxs-lookup"><span data-stu-id="523bb-107">Within a particular part of a flat file instance message, different items of data are grouped into records, which themselves can contain subrecords and ultimately the individual items of data, known as fields.</span></span> <span data-ttu-id="523bb-108">Ces enregistrements et champs sont distingués les uns des autres à l’aide de deux méthodologies de base différentes.</span><span class="sxs-lookup"><span data-stu-id="523bb-108">These records and fields are distinguished from each other using one of two different basic methodologies.</span></span> <span data-ttu-id="523bb-109">La première méthodologie, dite positionnelle, définit une longueur pré-établie pour chaque élément de données,  en utilisant des caractères de remplissage pour agrandir un élément de données plus court de façon qu'il s’adapte à la longueur attendue.</span><span class="sxs-lookup"><span data-stu-id="523bb-109">The first methodology, known as positional, defines each item of data to be of a pre-established length, with pad characters being used to bring a shorter item of data up to its expected length.</span></span> <span data-ttu-id="523bb-110">La seconde méthodologie, dite délimitée, utilise un ou plusieurs caractères spéciaux pour séparer les éléments de données les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="523bb-110">The second methodology, known as delimited, uses one or more special characters to separate items of data from each other.</span></span> <span data-ttu-id="523bb-111">Cette méthodologie permet d’éviter d’avoir à ajouter des caractères de remplissage superflus, mais implique de nouvelles considérations lorsque les données elles-mêmes contiennent le caractère ou la séquence de caractères utilisée comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="523bb-111">This methodology avoids the need for otherwise superfluous pad characters, but introduces some special considerations when the data itself contains the character or sequence of characters being used as a delimiter.</span></span>  
  
 <span data-ttu-id="523bb-112">Le reste de cette section propose une présentation détaillée de la gestion par BizTalk Server des en-têtes, corps et codes de fin dans les messages d'instance de fichier plat. Vous y apprendrez en particulier comment BizTalk Server décide s'il faut inclure ou non les éléments facultatifs, comment il sépare les parties des messages d’instance de fichier plat entrants et associe les parties des messages d'instance de fichier plat sortants.</span><span class="sxs-lookup"><span data-stu-id="523bb-112">The remainder of this section provides a high-level overview of how BizTalk Server handles headers, bodies, and trailers in flat file instance messages, and specifically, how it decides whether the optional parts are present, and how it separates the parts of inbound flat file instance messages and combines the parts of outbound flat file instance messages.</span></span> <span data-ttu-id="523bb-113">Cette section propose également des informations supplémentaires sur les différences existant entre les messages d'instance de fichier plat utilisant des champs et enregistrements positionnels et les messages d'instance de fichier plat utilisant des champs et enregistrements délimités.</span><span class="sxs-lookup"><span data-stu-id="523bb-113">This section also provides additional information about the differences between flat file instance messages that employ positional records and fields and flat file instance messages that employ delimited records and fields.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="523bb-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="523bb-114">In This Section</span></span>  
  
-   [<span data-ttu-id="523bb-115">En-têtes de Message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="523bb-115">Flat File Message Headers</span></span>](../core/flat-file-message-headers.md)  
  
-   [<span data-ttu-id="523bb-116">Corps de Message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="523bb-116">Flat File Message Bodies</span></span>](../core/flat-file-message-bodies.md)  
  
-   [<span data-ttu-id="523bb-117">Codes de Message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="523bb-117">Flat File Message Trailers</span></span>](../core/flat-file-message-trailers.md)  
  
-   [<span data-ttu-id="523bb-118">Messages de fichier plat avec des enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="523bb-118">Flat File Messages with Positional Records</span></span>](../core/flat-file-messages-with-positional-records.md)  
  
-   [<span data-ttu-id="523bb-119">Messages de fichier plat avec des enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="523bb-119">Flat File Messages with Delimited Records</span></span>](../core/flat-file-messages-with-delimited-records.md)  
  
-   [<span data-ttu-id="523bb-120">Migration des enregistrements de fichier plat</span><span class="sxs-lookup"><span data-stu-id="523bb-120">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)