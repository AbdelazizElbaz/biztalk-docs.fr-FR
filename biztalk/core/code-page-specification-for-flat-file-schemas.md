---
title: "Spécification de Page pour les schémas de fichier plat de code | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 825e75f1-893c-4c61-b566-f893d732a907
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d5cfbc960346e702ed0d4a39ca74bbc4b3634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="code-page-specification-for-flat-file-schemas"></a><span data-ttu-id="c1960-102">Spécification de Page de codes pour les schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="c1960-102">Code Page Specification for Flat File Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="c1960-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c1960-103">Overview</span></span>
<span data-ttu-id="c1960-104">La valeur de la **Page de codes** propriété est utilisée pour créer un objet d’encodage qui est utilisé pendant le désassemblage et assemblage de documents de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="c1960-104">The value in the **Code Page** property is used to create an encoding object that is used during the disassembly and assembly of flat file documents.</span></span> <span data-ttu-id="c1960-105">Cet objet de codage permet à l'analyseur de fichier plat de convertir le codage natif d'un document de fichier plat entrant en codage UTF-8 normalisé, utilisé de façon interne par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c1960-105">This encoding object allows the flat file parser to convert the native encoding of an inbound flat file document into the normalized UTF-8 encoding that is used internally by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c1960-106">L'objet de codage permet également au sérialiseur de fichier plat de reconvertir le codage UTF-8 interne en codage natif du document de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="c1960-106">The encoding object also allows the flat file serializer to convert the internal UTF-8 encoding back into the native encoding of the flat file document.</span></span>  
  
 <span data-ttu-id="c1960-107">Le paramètre de la **Page de codes** propriété joue un rôle d’important mais non exclusif pour déterminer le schéma de codage de caractères utilisé par vos documents commerciaux de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="c1960-107">The setting of the **Code Page** property plays an important, but not exclusive, role in determining the character encoding scheme used by your flat file business documents.</span></span> <span data-ttu-id="c1960-108">Vous devez prendre en compte la manière dont les messages de fichier plat entrants sont interprétés par le désassembleur de fichier plat et dont l'assembleur de fichier plat codera les caractères tandis que les messages sortants seront convertis au format de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="c1960-108">You must consider how inbound flat file messages are interpreted by the flat file disassembler as well as how the flat file assembler will encode characters as outbound messages are translated into flat file format.</span></span>  

## <a name="character-encoding"></a><span data-ttu-id="c1960-109">Encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="c1960-109">Character encoding</span></span>  
 <span data-ttu-id="c1960-110">Plusieurs facteurs déterminent la manière dont le codage de caractères pour un message d'instance donné est géré :</span><span class="sxs-lookup"><span data-stu-id="c1960-110">There are multiple factors that play a role in determining how character encoding for a given instance message is handled, as follows:</span></span>  
  
-   <span data-ttu-id="c1960-111">Lors du désassemblage d'un message d'instance de fichier plat, l'algorithme suivant est utilisé pour déterminer et conserver les informations de codage :</span><span class="sxs-lookup"><span data-stu-id="c1960-111">When disassembling a flat file instance message, the following algorithm is used to determine and preserve encoding information:</span></span>  
  
    1.  <span data-ttu-id="c1960-112">Si le **Charset** dans le corps du Message n’est définie, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-112">If the **Charset** in the Message body part is set, its value is used.</span></span>  
  
    2.  <span data-ttu-id="c1960-113">Sinon, si le schéma d’enveloppe (ou de document) spécifie une page de code à l’aide de la **Page de codes** propriété, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-113">Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.</span></span>  
  
    3.  <span data-ttu-id="c1960-114">Sinon, si une marque d'ordre de tri est présente, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-114">Otherwise, if a byte order mark is present, its value is used.</span></span>  
  
    4.  <span data-ttu-id="c1960-115">Sinon, on suppose UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1960-115">Otherwise, assume UTF-8.</span></span>  
  
-   <span data-ttu-id="c1960-116">Lors de l’assemblage d’un message d’instance de fichier plat, l’algorithme suivant est utilisé pour déterminer le jeu de caractères à utiliser pour le décodage :</span><span class="sxs-lookup"><span data-stu-id="c1960-116">When assembling a flat file instance message, the following algorithm is used to determine the character set to use for decoding:</span></span>  
  
-   <span data-ttu-id="c1960-117">Si le **XMLNorm.TargetCharset** propriété de contexte de message est définie, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-117">If the **XMLNorm.TargetCharset** message context property is set, its value is used.</span></span>  
  
-   <span data-ttu-id="c1960-118">Sinon, si le **TargetCharset** assembleur (au moment du design) est définie, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-118">Otherwise, if the **TargetCharset** assembler (design-time) property is set, its value is used.</span></span>  
  
-   <span data-ttu-id="c1960-119">Sinon, si le schéma d’enveloppe (ou de document) spécifie une page de code à l’aide de la **Page de codes** propriété, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-119">Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.</span></span>  
  
    1.  <span data-ttu-id="c1960-120">Sinon, si le **SourceCharset** propriété de contexte de message est définie, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c1960-120">Otherwise, if the **SourceCharset** message context property is set, its value is used.</span></span>  
  
    2.  <span data-ttu-id="c1960-121">Sinon, utiliser UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1960-121">Otherwise, use UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1960-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1960-122">See Also</span></span>  
 <span data-ttu-id="c1960-123">**Schémas de Message de fichier de considérations relatives à la création de plat** et **(propriété de nœud des schémas de fichier plat) de Page de codes**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c1960-123">**Considerations When Creating Flat File Message Schemas** and **Code Page (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>