---
title: "SWIFT désassembleur et assembleur fonctionnalités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, about disassembler
- assembler, about assembler
- assembler, functionality
- disassembler, functionality
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0109979fbb9bf61fc0e1be833061b2a15b470690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler-and-assembler-functionality"></a><span data-ttu-id="d4465-102">SWIFT désassembleur et assembleur fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d4465-102">SWIFT Disassembler and Assembler Functionality</span></span>
<span data-ttu-id="d4465-103">Le désassembleur SWIFT peut effectuer les tâches suivantes lorsqu’elle est appelée dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline de réception :</span><span class="sxs-lookup"><span data-stu-id="d4465-103">The SWIFT disassembler can perform the following tasks when invoked in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
-   <span data-ttu-id="d4465-104">Détecter le type de message et de résoudre le schéma de document dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="d4465-104">Dynamically discover the message type and resolve document schema.</span></span> <span data-ttu-id="d4465-105">Cela permet un seul port de réception et pipeline pour gérer plusieurs types de messages SWIFT.</span><span class="sxs-lookup"><span data-stu-id="d4465-105">This enables a single receive port and pipeline to handle multiple SWIFT message types.</span></span>  
  
-   <span data-ttu-id="d4465-106">Analyser un fichier plat SWIFT dans XML.</span><span class="sxs-lookup"><span data-stu-id="d4465-106">Parse a SWIFT flat file into XML.</span></span>  
  
-   <span data-ttu-id="d4465-107">Appeler le lecteur pour effectuer une validation XML (schéma), telles que la vérification de la validité des types de données, le format de données ou mise en conformité de la longueur de la validation de XML.</span><span class="sxs-lookup"><span data-stu-id="d4465-107">Invoke the XML validating reader to perform XML (schema) validation, such as checking data type validity, data format, or length conformance.</span></span>  
  
-   <span data-ttu-id="d4465-108">Appeler le moteur de règles d’entreprise (BRE) pour effectuer une validation BRE, telles que la vérification de la conformité aux règles de réseau rapide ou l’exécution d’autres validations complexes qui n’implémente pas le schéma.</span><span class="sxs-lookup"><span data-stu-id="d4465-108">Invoke the Business Rule Engine (BRE) to perform BRE validation, such as checking conformance to SWIFT network rules or performing other complex validation that the schema does not implement.</span></span>  
  
-   <span data-ttu-id="d4465-109">Publier un message XML analysé dans la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML (qui fournit des informations sur les erreurs rencontrées pendant la validation ou d’analyse).</span><span class="sxs-lookup"><span data-stu-id="d4465-109">Publish a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML (providing information about any errors encountered during parsing or validation).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4465-110">Si le désassembleur rencontre des erreurs irrécupérables lors de l’analyse, le désassembleur publiera le message dans la base de données MessageBox dans le format de fichier plat natif plutôt que XML.</span><span class="sxs-lookup"><span data-stu-id="d4465-110">If the disassembler encounters fatal failures during parsing, the disassembler will publish the message to the MessageBox database in native flat file format rather than XML.</span></span>  
  
-   <span data-ttu-id="d4465-111">Traiter des lots entrants, comme suit :</span><span class="sxs-lookup"><span data-stu-id="d4465-111">Process inbound batches, as follows:</span></span>  
  
    -   <span data-ttu-id="d4465-112">Analyser et conserver les enveloppes de lot (en-tête de lot, code de fin du lot)</span><span class="sxs-lookup"><span data-stu-id="d4465-112">Parse and preserve batch envelopes (batch header, batch trailer)</span></span>  
  
    -   <span data-ttu-id="d4465-113">Analyser et conserver les enveloppes de message (en-tête de message, le code de fin)</span><span class="sxs-lookup"><span data-stu-id="d4465-113">Parse and preserve message envelopes (message header, message trailer)</span></span>  
  
    -   <span data-ttu-id="d4465-114">Analyser et valider les messages SWIFT dans le lot individuellement</span><span class="sxs-lookup"><span data-stu-id="d4465-114">Parse and validate SWIFT messages in the batch individually</span></span>  
  
    -   <span data-ttu-id="d4465-115">Publier des messages SWIFT individuellement à la base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="d4465-115">Publish SWIFT messages to the MessageBox database individually</span></span>  
  
    -   <span data-ttu-id="d4465-116">Publier la totalité du traitement entrant à la base de données MessageBox en tant qu’un seul message (copie exacte de l’entrée)</span><span class="sxs-lookup"><span data-stu-id="d4465-116">Publish the entire inbound batch to the MessageBox database as a single message (exact copy of input)</span></span>  
  
    -   <span data-ttu-id="d4465-117">Promouvoir les propriétés de contexte de lot liées pour le tri ou de mettre en corrélation les messages provenant du même lot</span><span class="sxs-lookup"><span data-stu-id="d4465-117">Promote batch-related context properties for sorting or correlating messages originating from the same batch</span></span>  
  
 <span data-ttu-id="d4465-118">L’assembleur SWIFT peut effectuer les tâches suivantes lorsqu’elle est appelée dans un pipeline d’envoi BizTalk :</span><span class="sxs-lookup"><span data-stu-id="d4465-118">The SWIFT assembler can perform the following tasks when invoked in a BizTalk send pipeline:</span></span>  
  
-   <span data-ttu-id="d4465-119">Détecter le type de message et résoudre le schéma de document dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="d4465-119">Dynamically discover the message type and resolve the document schema.</span></span> <span data-ttu-id="d4465-120">Ainsi, un port d’envoi unique et un pipeline à gérer SWIFT plusieurs types de messages.</span><span class="sxs-lookup"><span data-stu-id="d4465-120">This allows a single send port and pipeline to handle multiple SWIFT message types.</span></span>  
  
-   <span data-ttu-id="d4465-121">Sérialiser du code XML analysé dans un fichier plat SWIFT.</span><span class="sxs-lookup"><span data-stu-id="d4465-121">Serialize parsed XML into a SWIFT flat file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4465-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4465-122">See Also</span></span>  
 [<span data-ttu-id="d4465-123">Utilisation de SWIFT désassembleur et assembleur</span><span class="sxs-lookup"><span data-stu-id="d4465-123">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)