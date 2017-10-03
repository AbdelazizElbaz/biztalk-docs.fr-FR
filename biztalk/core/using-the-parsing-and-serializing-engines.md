---
title: "À l’aide de l’analyse et la sérialisation des moteurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing engine
- pipeline components [custom], engines
- serialization engine
- pipeline components [custom], assembling
- pipeline components [custom], parsing
ms.assetid: a9d19703-b074-402a-971a-b2a6cd5d0724
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e820b2dce1257ec948aa214c9fdf1d43a6a7152
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-parsing-and-serializing-engines"></a><span data-ttu-id="79f63-102">À l’aide de moteurs d’analyse et de sérialisation</span><span class="sxs-lookup"><span data-stu-id="79f63-102">Using the Parsing and Serializing Engines</span></span>
<span data-ttu-id="79f63-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un moteur d'analyse et de sérialisation permettant de simplifier le processus d'analyse et de sérialisation des documents de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="79f63-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes a parsing and serializing engine to simplify the process of parsing and serializing flat file documents.</span></span>  
  
 <span data-ttu-id="79f63-104">Le moteur d'analyse est un cadre piloté par schéma qui peut analyser un grand nombre de formats de document différents dans XML.</span><span class="sxs-lookup"><span data-stu-id="79f63-104">The parsing engine is a schema-driven framework that can parse many different document formats into XML.</span></span> <span data-ttu-id="79f63-105">Par ailleurs, il dispose d'un modèle d'extensibilité bien défini permettant de simplifier encore plus facilement l'analyse des formats personnalisés.</span><span class="sxs-lookup"><span data-stu-id="79f63-105">In addition, the engine has a well-defined extensibility model to make parsing custom formats even easier.</span></span>  
  
 <span data-ttu-id="79f63-106">Des désassembleurs sont utilisés pour les analyses complexes.</span><span class="sxs-lookup"><span data-stu-id="79f63-106">For complex parsing, disassemblers are used.</span></span> <span data-ttu-id="79f63-107">Outre la conversion du format natif en XML, le désassembleur peut également séparer un document unique en plusieurs documents.</span><span class="sxs-lookup"><span data-stu-id="79f63-107">In addition to converting the native format to XML, the disassembler can also separate a single document into multiple documents.</span></span>  
  
 <span data-ttu-id="79f63-108">Le moteur de sérialisation fonctionne de la même manière, excepté qu'il effectue la procédure inverse.</span><span class="sxs-lookup"><span data-stu-id="79f63-108">The serializing engine is similar to the parsing engine, except that it works in the opposite direction.</span></span> <span data-ttu-id="79f63-109">Alors que le moteur d'analyse convertit les formats natifs en XML, celui de sérialisation convertit les XML en formats natifs.</span><span class="sxs-lookup"><span data-stu-id="79f63-109">Where the parsing engine converts native formats to XML, the serializing engine converts XML to native formats.</span></span> <span data-ttu-id="79f63-110">Et tout comme le moteur d'analyse utilise des désassembleurs, celui de sérialisation utilise des assembleurs.</span><span class="sxs-lookup"><span data-stu-id="79f63-110">And just as the parsing engine uses disassemblers, the serializing engine uses assemblers.</span></span>  
  
 <span data-ttu-id="79f63-111">Cette section explique comment procéder au codage des caractères, à l'analyse et à la sérialisation basées sur les schémas XSD (XML Schema Definition language), ainsi qu'à d'autres tâches courantes à l'aide des API des moteurs d'analyse et de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="79f63-111">This section discusses how to perform character encoding, parse and serialize based on XML Schema definition language (XSD) schemas, and perform other common tasks using the parsing engine and serializing engine APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79f63-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="79f63-112">In This Section</span></span>  
  
-   [<span data-ttu-id="79f63-113">Implémentation d’encodage de caractères dans un composant de Pipeline</span><span class="sxs-lookup"><span data-stu-id="79f63-113">Implementing Character Encoding in a Pipeline Component</span></span>](../core/implementing-character-encoding-in-a-pipeline-component.md)  
  
-   [<span data-ttu-id="79f63-114">À l’aide de schémas</span><span class="sxs-lookup"><span data-stu-id="79f63-114">Using Schemas</span></span>](../core/using-schemas.md)  
  
-   [<span data-ttu-id="79f63-115">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="79f63-115">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)  
  
-   [<span data-ttu-id="79f63-116">Utilisation du moteur de sérialisation de fichier plat</span><span class="sxs-lookup"><span data-stu-id="79f63-116">Using the Flat File Serializing Engine</span></span>](../core/using-the-flat-file-serializing-engine.md)